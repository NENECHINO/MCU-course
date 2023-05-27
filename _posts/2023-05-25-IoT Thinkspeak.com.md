---
layout: post
title: IoT Thinkspeak.com
author: [Tony ]
category: [Lecture]
tags: [jekyll, ai]
---

This project is to implement a bluetooth remote controlled robotcar.

---
## OTA初始操作

將網站搭建好

### 程式
```
/*
  Rui Santos
  Complete project details
   - Arduino IDE: https://RandomNerdTutorials.com/esp32-ota-over-the-air-arduino/
   - VS Code: https://RandomNerdTutorials.com/esp32-ota-over-the-air-vs-code/
  
  This sketch shows a Basic example from the AsyncElegantOTA library: ESP32_Async_Demo
  https://github.com/ayushsharma82/AsyncElegantOTA
*/

#include <Arduino.h>
#include <WiFi.h>
#include <AsyncTCP.h>
#include <ESPAsyncWebServer.h>
#include <AsyncElegantOTA.h>

const char* ssid = "BrokenJade";
const char* password = "aaaaaaaa";

AsyncWebServer server(80);

void setup(void) {
  Serial.begin(115200);
  WiFi.mode(WIFI_STA);
  WiFi.begin(ssid, password);
  Serial.println("");

  // Wait for connection
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }
  Serial.println("");
  Serial.print("Connected to ");
  Serial.println(ssid);
  Serial.print("IP address: ");
  Serial.println(WiFi.localIP());

  server.on("/", HTTP_GET, [](AsyncWebServerRequest *request) {
    request->send(200, "text/plain", "Hi! I am ESP32.");
  });

  AsyncElegantOTA.begin(&server);    // Start ElegantOTA
  server.begin();
  Serial.println("HTTP server started");
}

void loop(void) {

}
```
### 網頁展示
![](https://github.com/NENECHINO/MCU-course/blob/main/images/1_wifi.png?raw=true)<br>
![](https://github.com/NENECHINO/MCU-course/blob/main/images/1_connect.png?raw=true)<br>
![](https://github.com/NENECHINO/MCU-course/blob/main/1_OTA%E7%B6%B2%E7%AB%99.png?raw=true)<br>
### 製造bin檔與上傳
![](https://github.com/NENECHINO/MCU-course/blob/main/images/1_bin.png?raw=true)<br>
將製作好的bin檔利用網頁上傳
### 成果展示
![](https://github.com/NENECHINO/MCU-course/blob/main/1_OTA%20%20off.png?raw=true)<br>
![](https://github.com/NENECHINO/MCU-course/blob/main/1_red.jpg?raw=true)<br>
![](https://github.com/NENECHINO/MCU-course/blob/main/1_OTA%20%20on.png?raw=true)<br>
![](https://github.com/NENECHINO/MCU-course/blob/main/1_green.jpg?raw=true)<br>

<br>
<br>
*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*
