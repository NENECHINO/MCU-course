---
layout: post
title: Innovative Project Proposal
author: [Tony Liu]
category: [Lecture]
tags: [jekyll, ai]
---

This homework is to propose an innovative project and describe the key features, list all Design Considerations and the required technologies, then draw the System Block Diagram.

---
## Homework Report Format
**Contents:**<br>
* **Application function description**
  - Specify the future home application, and Describe the key features
  - Describe the key features which may be applied to the home space (kitchen, living room, play room, study room, bed room)
* **Design Considerations and Related Technologies Required**
  - List all design considerations and the required technologies
* **System Block Diagram**
  - Draw a System Block Diagram

---
## KICHEN ROBOT!

![]([https://github.com/NENECHINO/MCU-course/blob/main/images/The-Assistive-Kitchen-containing-a-robot-and-a-variety-of-sensors.png])

### Application function description
1. Operating kitchen utensils：Coffee machine + juice machine + toaster + microwave oven + oven + air fryer
2. Access refrigerator：Identify food》Store ingredients or take out ingredients》Send to kitchen utensils

### Design Considerations and Related Technologies Required
**System Design Considerations：**<br>
1. Operation method:Vertical lift arm/suspension arm
2. Way of moving:Two-wheel/rail suspension
3. Power supply:lithium battery
4. Networking method:WiFi/BT》phone!

**Required technology：**
1. Slide rail robot arm and soft fixture
2. Food Identification Classification：Jetson-Nano + IMX219
3. Electronic Nose: Odor Sensing and Recognition MQ2

### System Block Diagram
![](https://github.com/rkuo2000/MCU-course/blob/main/images/FutureHome_kitchen_robot.png?raw=true)
![](https://github.com/NENECHINO/MCU-course/blob/main/images/The-Assistive-Kitchen-containing-a-robot-and-a-variety-of-sensors.png)

---
### Outcome video
<iframe width="878" height="494" src="https://www.youtube.com/embed/GyEHRXA_aA4" title="&#39;Kitchen robot&#39; that will cook meals from scratch unveiled" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
<br>
<br>

*This site was last updated {{ site.time | date: "%B %d, %Y" }}!:)*


