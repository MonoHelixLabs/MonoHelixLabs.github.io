---
layout: post
title:  "Spying on Roomba with a Noise Sensor"
date:   2017-09-30 10:51:00 +0100
categories: sound noise roomba
author: paula
permalink: /spying-on-roomba.html
thumbnail: /images/noise_roomba_thumb.jpg
---

The Roomba vacuum cleaning robot has been in the news a lot recently with claims that it is "spying" on its owners. Well, there is no reason then to not spy back. What is Roomba actually doing while you're away?

We have an iRobot Roomba 980 that is connected to the Wi-Fi and that we can control through the iRobot app. It also generates a map of the cleaning area (thus the controversy), and we get notifications when the cleaning job is completed or when it gets stuck. And the more obstacles there are in cleaning area, the more Roomba is likely to get stuck. We get the "Roomba is stuck and needs assistance" error message maybe 1-2 times in 10 cleaning jobs.

![noise_roomba_01](/images/noise_roomba_01.png)

Notice however the time difference between the two messages. Does this mean that during the 1h 30min from when Roomba says that the wheel is stuck and when it says it ended the job, it will still try to move and run its motors and keep alerting (through beeps or voice) that it needs assistance? That would be a waste of energy and potentially annoying for neighbours. 

In order to find out what is happening, we have set out to spy on our Roomba with a sound sensor. 

![noise_roomba_05](/images/noise_roomba_05.jpg)

<h3>Materials and Assembly</h3>

Here's the bill of materials (BOM) for the hardware:

| Item | Est. Price | Description | 
| --- | --- | --- |
| 1 x <a target="_blank" href="https://www.amazon.com/gp/product/B00K9M6S1O/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B00K9M6S1O&linkCode=as2&tag=monohelixlabs-20&linkId=aa2fd9d3556842044d309bbfdaf9a9f1">MAX4466</a><img src="//ir-na.amazon-adsystem.com/e/ir?t=monohelixlabs-20&l=am2&o=1&a=B00K9M6S1O" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" /> | 7.9$ | This is the sound sensor (microphone). A product description is available at <a href="https://www.adafruit.com/product/1063" target="_blank">Adafruit</a>.| 
| 1 x WeMos D1 mini (or WeMos D1 mini PRO)| 3.5-5$ | This is the brain of the project, a small board with Wi-Fi connectivity. See our <a href="http://www.monohelixlabs.com/wemos-d1-mini-pro-esp8266.html" target="_blank">blog post</a> on these boards.| 
| --- | --- | --- | 
{:.mbtablestyle}
<br/>

And here's the hardware setup:
![noise_roomba_02](/images/noise_roomba_02.png)

<h3>Detecting Noise Level</h3>

To get started with programming a WeMos, check out our <a href="http://www.monohelixlabs.com/wemos-d1-mini-pro-esp8266.html" target="_blank">other post</a>. Then we can simply read the value from the Analog pin. 

The MAX4466 mic has an adjustable gain, and we have tested the output of the sound level on different sounds (quiet room, music at an acceptable level, loud music etc.) to set the gain so that we capture the difference between a quiet environment and a loud one. This was done by having different sounds, looking at a plot of the output sound level, and adjusting the screw on the back of the mic accordingly. 

The final code is on GitHub: <a href="https://github.com/MonoHelixLabs/arduino-sound" target="_blank">WemosD1mini_Sound</a>.

As we are only interested in the noise level, we sample the sounds from the mic and average them over a number of samples. This processing is done on the Wemos, and each 3-4 minutes we send an average of the sound level to the <a href="https://io.adafruit.com" target="_blank">Adafruit IO</a> service through MQTT.

![noise_roomba_03](/images/noise_roomba_03.jpg)

We don't record the sounds or voices, so there is no privacy implication. It's just the sound level (or noise) that we are interested in.

<h3>Verdict</h3>

The noise level data (recorded through Adafruit IO and seen below in our free <a href="http://datafeeds.monohelixlabs.com" target="_blank">DataFeeds app</a>) can clearly identify when Roomba's job started: 9 AM. The level goes up and down a bit and corresponds to Roomba probably going from one room to another. Then the noise level goes down 9:45 AM. That corresponds to when the notification "Roomba's right wheel is stuck" is sent out. 

![noise_roomba_04](/images/noise_roomba_04.png)

The "Roomba ended the job stuck" notification is sent later, at 11:15, but we can now clearly see from the data that Roomba actually suffers quietly during this time period. 

Mystery solved!