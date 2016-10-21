---
layout: post
title:  "Inside an Estimote Location Beacon"
date:   2016-09-01 20:00:00 +0100
categories: beacons nearables iot
author: paula
permalink: /inside-estimote-beacon.html
---

Estimote Location Beacons are small wireless sensors that talk Bluetooth Low Energy (BLE), have motion, temperature, ambient light and magnetometer sensors integrated, and also have a GPIO connector. 


![estimote_beacon_00](/images/estimote_beacon_00.JPG)

They look very compact, and have a nice organic design. We were curious to see what is inside and have seen pictures online of people that cut open these cute beacons, but then the entire enclosure was destroyed.

So it was a nice surprise when we found out that Estimotes produced after December 2015 (ours included) had a redesign that provides the possibility to change the battery without damaging the case. 

We just removed the bottom layer of tape and took the module out.

![estimote_beacon_01](/images/estimote_beacon_01.JPG)

And here it is, powered by 4 (four) CR2477 batteries!

![estimote_beacon_02](/images/estimote_beacon_02.JPG)

There's the Nordic Semiconductor nRF51822, the BLE antenna, probably some sensors, and there's an LED that blinks when you're connected to the beacon from the Estimote app.

![estimote_beacon_03](/images/estimote_beacon_03.JPG)

The headers soldered on the board that can be seen in the bottom part in the picture are for GPIO connections. Their position matches with the placeholders on the outside of the enclosure, marked with 1, 2, 3 and 4. 

![estimote_beacon_04](/images/estimote_beacon_04.JPG)

In terms of ease of use, there is room for improvement. We had some issues with connecting to (or in estimotes terms, "owning") the beacons. They were not available in the Estimote account that was used when buying the package, and the alternative of using an activation code was not an option for us as there was no activation code on our package. Therefore we used the claim ownership functionality from the estimote app, however the email service had some delays, so we couldn't just get started using them. 

It was also dissapointing that the packaging includes 3 beacons but the Indoor Location Mapping functionality requires 4 beacons. Even if the indoor location mapping app allows you to get started with indoor mapping using less beacons (and it did a decent job with 3 beacons), in the end it still forces you to have 4 beacons connected. This limits the usage of the app even if it is just for testing purposes. 

![estimote_beacon_05](/images/estimote_beacon_05.JPG)

It is also confusing what type of beacons are actually needed for the Indoor Location Mapping, as the text documentation mentions only the Estimote Location beacons, however the marketing material for this functionality often shows the Estimote Proximity beacons, which might suggest that one should give those a try. 

As for the Estimote Proximity beacons, they are a bit smaller and lack some of the sensors, but have NFC. Here's how the Location and Proximity beacons look side by side.

![estimote_beacon_06](/images/estimote_beacon_06.JPG)

For more info about these beacons, check the <a href="http://estimote.com/" target="_blank">producer website</a>.