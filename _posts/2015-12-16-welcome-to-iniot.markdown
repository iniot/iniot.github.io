---
layout: post
title:  "Welcome to InIoT!"
date:   2015-12-16 22:45:33 -0300
---
We want to develop an Greenhouse Automation Platform, with integration and interoperability as part of our main focus.

Therefore we will use eclipse kura as our intelligent gateway iot to connect and manage the sensors and actuators to the cloud.

Our proof of concept is to interact with Zigbee HA devices, a main power and a light, and if we have time, light and moisture sensor too.

For connecting to the cloud we want to use something like lwm2m/coap or lwm2m over mqtt, or other commonly used/standar  protocol.

To focus in the development and scalability we want to use a serveless cloud services, for that reason aws iot/mqtt + aws lambda/Event-driven Code can be a very good choice.

The hardware we have is:

* main power [psm-29zbsr]
* light [A806S-Q1R]
* zigbee module [cc2530] and [XBEE / XBEE-PRO ZB (S2)]
* board [BeagleBone Black]
* some arduinos

Feedback & Hints are very welcome

[open-iot-challenge]: http://iot.eclipse.org/open-iot-challenge/
[psm-29zbsr]: http://www.climax.com.tw/psm29zb-zb.php
[A806S-Q1R]: http://www.leedarson.com/Products/Connected/LightingProduct/104.html
[cc2530]: http://www.dx.com/p/zigbee-cc2530-development-module-deep-blue-276438
[XBEE / XBEE-PRO ZB (S2)]: http://www.digi.com/support/productdetail?pid=3430
[BeagleBone Black]: http://beagleboard.org/BLACK
