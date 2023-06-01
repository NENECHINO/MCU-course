---
layout: post
title: IoT Thinkspeak.com
author: [Tony ]
category: [Lecture]
tags: [jekyll, ai]
---

This project is to implement a bluetooth remote controlled robotcar.

---

### 程式
```
#include <WiFi.h>
#include "DHT.h"

#define DHTPIN 23     
DHT dht(DHTPIN, DHT11, 15);

const char* ssid     = "BrokenJade";
const char* password = "aaaaaaaa";


const char* host = "api.thingspeak.com";
const char* thingspeak_key = "6ZHGDW5IFK4VSMYD ";

void turnOff(int pin) {
  pinMode(pin, OUTPUT);
  digitalWrite(pin, 1);
}

void setup() {
  Serial.begin(115200);

  turnOff(0);
  turnOff(2);
  turnOff(4);
  turnOff(5);
  turnOff(12);
  turnOff(13);
  turnOff(14);
  turnOff(15);

  dht.begin();
  delay(10);

  Serial.println();
  Serial.println();
  Serial.print("Connecting to ");
  Serial.println(ssid);
  
  WiFi.begin(ssid, password);
  
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }

  Serial.println("");
  Serial.println("WiFi connected");  
  Serial.println("IP address: ");
  Serial.println(WiFi.localIP());
}

int value = 0;

void loop() {
  delay(5000);
  ++value;

  Serial.print("connecting to ");
  Serial.println(host);
  
  WiFiClient client;
  const int httpPort = 80;
  if (!client.connect(host, httpPort)) {
    Serial.println("connection failed");
    return;
  }

  String temp = String(dht.readTemperature());
  String humidity = String(dht.readHumidity());
  String url = "/update?key=";
  url += thingspeak_key;
  url += "&field1=";
  url += temp;
  url += "&field2=";
  url += humidity;
  
  Serial.print("Requesting URL: ");
  Serial.println(url);
  
  // This will send the request to the server
  client.print(String("GET ") + url + " HTTP/1.1\r\n" +
               "Host: " + host + "\r\n" + 
               "Connection: close\r\n\r\n");
  delay(10);
  
  while(client.available()){
    String line = client.readStringUntil('\r');
    Serial.print(line);
  }
  
  Serial.println();
  Serial.println("closing connection. going to sleep...");
  delay(1000);

  delay(1*10*1000);
}
```
### 網頁展示
![](https://github.com/NENECHINO/MCU-course/blob/main/1_com4%E9%80%A3%E6%8E%A5.png?raw=true)<br>

### 系統方塊圖
![](https://github.com/NENECHINO/MCU-course/blob/main/1_thingP.png?raw=true)<br>

### 成果展示
![](https://github.com/NENECHINO/MCU-course/blob/main/1_iot%E7%89%A9%E9%80%A3.png?raw=true)<br>


<br>
<br>
*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*
