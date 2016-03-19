---
layout: post
title:  "Open IoT Challenge 2.0 - Update #3 - Late Post"
---

I haven't had the time in the last weeks to work in my side projects, therefore I couldn't send the last resume of "Open IoT Challenge 2.0" on time.

The projects idea is to develop a Greenhouse Automation Platform.

My fist step is to develop a proof of concept(POC) to understand and involved in the problem and the technologies around it.

To build the first POC, we must first complete some smaller tasks, like connect end devices to sensor and actuators, then share data with a gateway, and connect the gateway to a central service.

As I have a lot of tasks to do I choosed a tool to help me with the planning and development process, github issues and Waffle.io [https://waffle.io/iniot/Open-IoT-Challenge-2.0]

I want to use wireless connections in all possible parts of the project, I'm playing with zigbee and arduino, and I've some zigbee devices. The technologies changed and evolve over time so I don't want to coupling the project with zigbee or other wireless communications, so the project can evolve easily, therefore I need a easy to develop and customizable gateway, and multi purpose and lightway protocol communication, that was some reasons to choose Eclipse Kura and MQTT to my first POC.

The way of move from development to production, is a crucial point which affect the evolve and growth capabilities of the project, and I'm using Docker in my work with Deis, and I really love the git-push-deployment and The Twelve-Factor App methodology, I choose Docker and Resin.io.

Hardware:

* BeagleBoneBlack [BeagleBone Black]
* Mains Power Outlet [psm-29zbsr]
* TXInstruments CC2530 [cc2530]
* Auto flower watering kit [KIT0003]

Software:

* EclipseIoT kura + ConnectionFactory [Kura]
* zigbee4java [zigbee4java]
* docker + resin_io [Resin.io]

## Issues

### Resin.io + kura (Docker)
I worked to make it work Resin.io + kura in BeagleBoneBlack, therfore I built a docker image with jave for armv7hf and docker image with Eclipse Kura for BeagleBoneBlack

* [https://github.com/jpizarrom/armv7hf-java-dockerhub]
* [https://github.com/jpizarrom/armv7hf-kura-bbb]

[![](http://iniot.github.io/images/62ab6f68-ede5-11e5-b287-e715c0d8bd15.png)][kura]

### zigbee4java docker
Based on armv7hf-java-dockerhub I built a docker image with zigbee-console-javase to run zigbee in docker using zigbee4java

* [https://github.com/jpizarrom/armv7hf-zigbee-console-javase-dockerhub]
* [https://github.com/tlaukkan/zigbee4java]

### CC2530, resin.io and ti stack
I worked to connect CC2530, resin.io and ti stack using uart ports

* [port connections, firmware and sw configuration to control zigbee Mains Power Outlet psm-29zbsr using BBB board]
* [https://talk.resin.io/t/serial-port-usage-uart4-in-bbb/187]

### arduino zigbee auto watering: sense
I've developed an arduino sketch to connect the Auto flower watering kit with zigbee home profile. I've used some code of smart_sprinkle to improve and stabilize my sketch

* [https://github.com/jpizarrom/arduino-zigbee-auto-watering]
* [https://github.com/d8adrvn/smart_sprinkler]

### Kura zigbee4java console in configuration
I've added a configuration to kura admin to send commands to the zigbee-console-javase

[![](https://pbs.twimg.com/media/CV8DvrPUsAELTW8.png)][POC-0-pic-0]
[![](https://pbs.twimg.com/media/CV8DvwwVEAAkTyj.png)][POC-0-pic-1]

### Kura zigbee4java mqtt greenhouse
I've extended the greenhouse sample app [https://github.com/kartben/kura-greenhouse-demo] to support zigbee and so I send data and control end devices with mqtt providers, like aws iot, m2x.att.com or other cloud provider supporting mqtt.

* [https://m2x.att.com/catalog/0a61c655c0617b6dfa2e5db2f8fb8193]

[![](http://iniot.github.io/images/6d39125a-ede5-11e5-9378-17b7652c0573.png)][mqtt]
[![](http://iniot.github.io/images/72594336-ede5-11e5-9185-f79f4788828f.png)][greenhouse]
[![](http://iniot.github.io/images/5f088a8c-ede3-11e5-b8db-3f11051db4e5.png)][temp]
[![](http://iniot.github.io/images/644fdaea-ede3-11e5-a3c6-cf6226b8695b.png)][hum]
[![](http://iniot.github.io/images/68719e10-ede3-11e5-912e-0708d2718900.png)][moisture]

### Kura zigbee4java mqtt console commands(m2x.att.com)
I've configured/integrated kura and greenhouse app with m2x.att.com commands, so I can send commands to the devices(join enable) using Do Button App [do/button]

[![](http://iniot.github.io/images/c56d3e54-ede7-11e5-94f1-43cbc9fe990e.png)][do/png]

### Code
[![](https://pbs.twimg.com/media/CV8DvrUUkAAOMYN.png)][POC-0-pic-2]
[![](https://pbs.twimg.com/media/CV8DvutUEAEA4pp.png)][POC-0-pic-3]

### Kura zigbee4java mqtt docker image and video
My next steps are:

* I'll build a kura docker image with preintalled
* record a video
* build an architecture diagram

[![](http://iniot.github.io/images/679d52ac-ede5-11e5-a55f-0f5f67232364.png)][Kura-preintalled]


[github repo issues]: https://github.com/iniot/Open-IoT-Challenge-2.0/issues
[POC-0]: https://twitter.com/jpizarrom/status/675262588633092096
[POC-0-pic-0]: https://pbs.twimg.com/media/CV8DvrPUsAELTW8.png
[POC-0-pic-1]: https://pbs.twimg.com/media/CV8DvwwVEAAkTyj.png
[POC-0-pic-2]: https://pbs.twimg.com/media/CV8DvrUUkAAOMYN.png
[POC-0-pic-3]: https://pbs.twimg.com/media/CV8DvutUEAEA4pp.png
[Kura]: http://www.eclipse.org/kura/
[Resin.io]: https://resin.io/
[zigbee4java]: https://github.com/tlaukkan/zigbee4java
[open-iot-challenge]: http://iot.eclipse.org/open-iot-challenge/
[psm-29zbsr]: http://www.climax.com.tw/psm29zb-zb.php
[A806S-Q1R]: http://www.leedarson.com/Products/Connected/LightingProduct/104.html
[cc2530]: http://www.dx.com/p/zigbee-cc2530-development-module-deep-blue-276438
[XBEE / XBEE-PRO ZB (S2)]: http://www.digi.com/support/productdetail?pid=3430
[BeagleBone Black]: http://beagleboard.org/BLACK
[KIT0003]: http://www.dfrobot.com/wiki/index.php/Auto_flower_watering_kit_(SKU:_KIT0003)
[do/button]: https://ifttt.com/products/do/button
[https://waffle.io/iniot/Open-IoT-Challenge-2.0]: https://waffle.io/iniot/Open-IoT-Challenge-2.0
[https://github.com/jpizarrom/armv7hf-java-dockerhub]: https://github.com/jpizarrom/armv7hf-java-dockerhub
[https://github.com/jpizarrom/armv7hf-kura-bbb]: https://github.com/jpizarrom/armv7hf-kura-bbb
[https://github.com/jpizarrom/armv7hf-zigbee-console-javase-dockerhub]: https://github.com/jpizarrom/armv7hf-zigbee-console-javase-dockerhub
[https://github.com/tlaukkan/zigbee4java]: https://github.com/tlaukkan/zigbee4java
[https://github.com/jpizarrom/arduino-zigbee-auto-watering]: https://github.com/jpizarrom/arduino-zigbee-auto-watering
[https://github.com/kartben/kura-greenhouse-demo]: https://github.com/kartben/kura-greenhouse-demo
[port connections, firmware and sw configuration to control zigbee Mains Power Outlet psm-29zbsr using BBB board]: https://github.com/iniot/Open-IoT-Challenge-2.0/issues/14
[https://talk.resin.io/t/serial-port-usage-uart4-in-bbb/187]: https://talk.resin.io/t/serial-port-usage-uart4-in-bbb/187
[https://github.com/d8adrvn/smart_sprinkler]: https://github.com/d8adrvn/smart_sprinkler
[https://m2x.att.com/catalog/0a61c655c0617b6dfa2e5db2f8fb8193]: https://m2x.att.com/catalog/0a61c655c0617b6dfa2e5db2f8fb8193

[greenhouse]: http://iniot.github.io/images/72594336-ede5-11e5-9185-f79f4788828f.png
[temp]: http://iniot.github.io/images/5f088a8c-ede3-11e5-b8db-3f11051db4e5.png
[hum]: http://iniot.github.io/images/644fdaea-ede3-11e5-a3c6-cf6226b8695b.png
[moisture]: http://iniot.github.io/images/68719e10-ede3-11e5-912e-0708d2718900.png
[kura]: http://iniot.github.io/images/62ab6f68-ede5-11e5-b287-e715c0d8bd15.png
[mqtt]: http://iniot.github.io/images/6d39125a-ede5-11e5-9378-17b7652c0573.png
[do/png]: http://iniot.github.io/images/c56d3e54-ede7-11e5-94f1-43cbc9fe990e.png
[Kura-preintalled]: http://iniot.github.io/images/679d52ac-ede5-11e5-a55f-0f5f67232364.png
