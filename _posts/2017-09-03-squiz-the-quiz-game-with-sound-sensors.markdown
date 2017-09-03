---
layout: post
title:  "sQuiz - Quiz Game with Sound Sensors"
date:   2017-09-03 12:31:00 +0100
categories: sound mic
author: paula
permalink: /squiz-the-quiz-game-with-sound-sensors.html
thumbnail: /images/squiz_thumb.jpg
---

Buttons are pretty common in quiz games and are also easy to work with as input to a project. However, to make the quiz game more interesting, it was decided that some squeak toys should be used instead. The participants would have to squeeze the toys, resulting in all kinds of high pitched sounds. This is a weekend project that uses sounds sensors in a quiz game to identify which team answered first.

<h3>Materials</h3>

The squeak toys represent 5 different animals and are fitted with pieces of metal that are intended for placement on bike horns. 

![squiz_01](/images/squiz_01.png)

Given that the toys are going to be squeezed, we initially thought that in order to identify when a team answers using one of the toys we could use buttons or pressure sensors (such as FSRs). However, given the size of the toys it would be difficult to anticipate where to place such buttons or pressure sensors on the toy so we can ensure that we capture the input in the heat of the game. 

We haven't experimented with sound sensors before, but this seemed like a good project to give them a try. We would place one sound sensor on each of the toys, and connect this to an Arduino to read the values constantly. A person would read out loud the quiz question and then the teams would squeeze the toys to get a chance to answer. The values read from the sound sensors would then be able to tell who squeezed first.

Here's the bill of materials (BOM) for the hardware (excludes the 5 toys and a computer to which the Arduino is to be connected to show the results). Note that we also added a button so that we can "freeze" the data collection and have time to interpret the data (when multiple teams squeeze and we need to decide which was first).

| Item | Est. Price | Description | 
| --- | --- | --- |
| 5 x <a target="_blank" href="https://www.amazon.com/gp/product/B00K9M6S1O/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B00K9M6S1O&linkCode=as2&tag=monohelixlabs-20&linkId=aa2fd9d3556842044d309bbfdaf9a9f1">MAX4466</a><img src="//ir-na.amazon-adsystem.com/e/ir?t=monohelixlabs-20&l=am2&o=1&a=B00K9M6S1O" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" /> | 5x7.9$ | This is the sound sensor (microphone). One sensor per toy will be needed. A product description is available at <a href="https://www.adafruit.com/product/1063" target="_blank">Adafruit</a>.| 
| 1 x <a target="_blank" href="https://www.amazon.com/gp/product/B008GRTSV6/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B008GRTSV6&linkCode=as2&tag=monohelixlabs-20&linkId=2b89ba7373509682c174577450f118d4">Arduino Uno</a><img src="//ir-na.amazon-adsystem.com/e/ir?t=monohelixlabs-20&l=am2&o=1&a=B008GRTSV6" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" /> | 18$ | This is the brain of the project (and a good investment for future projects). | 
| 1 x Button & 10K ohm resistor | <1$ | A button to control the sensors data collection. We bought a bunch of buttons and so we had some around to choose from, but for example <a target="_blank" href="https://www.amazon.com/gp/product/B01E38OS7K/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B01E38OS7K&linkCode=as2&tag=monohelixlabs-20&linkId=5380d225e31c74cbdf49fd450fe7a205">these buttons on Amazon</a><img src="//ir-na.amazon-adsystem.com/e/ir?t=monohelixlabs-20&l=am2&o=1&a=B01E38OS7K" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" /> look pretty nice for this project. If you are new to using buttons in your project, see this <a href="https://www.arduino.cc/en/Tutorial/Button" target="_blank">simple example</a> on using buttons on Arduino's page. | 
| long wires | ~5$ | The amount of wires will depend on how far away the toys (teams) will be from each other. We used around 15 x 1.5 meters of wire that we had around. If you don't have so many wires, this <a target="_blank" href="https://www.amazon.com/gp/product/B00B4ZQ3L0/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B00B4ZQ3L0&linkCode=as2&tag=monohelixlabs-20&linkId=ec7b51699cd3ed67ce9ccf01f3ee7ab8">wire kit from Amazon</a><img src="//ir-na.amazon-adsystem.com/e/ir?t=monohelixlabs-20&l=am2&o=1&a=B00B4ZQ3L0" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" /> would be a start. We can reuse the wires after the project is done. | 
| --- | --- | --- | 
{:.mbtablestyle}
<br/>

We used five MAX4466 electret michropone amplifiers:

![squiz_02](/images/squiz_02.png)

They are pretty easy to work with (check out <a href="https://learn.adafruit.com/adafruit-microphone-amplifier-breakout/overview" target="_blank">this Adafruit tutorial</a>). The sensors have only 3 connections: VCC, GND and OUT.

![squiz_03](/images/squiz_03.png)

<h3>Assembly</h3>

Here's the hardware setup:

![squiz_04](/images/squiz_04.png)

To each of the MAX4466 we solder wires connecting the sensor to the Arduino.

![squiz_05](/images/squiz_05.jpg)

Then we add the sensor under the belly of each animal toy and fix it in place with some tape.

![squiz_06](/images/squiz_06.png)

In the end there will be a network of wires going from the Arduino to the toys. We used tape to keep the long wires in place.

![squiz_07](/images/squiz_07.png)


<h3>The sQuiz Game</h3>

The code used in this project is available on <a href="https://github.com/MonoHelixLabs/arduino-sound" target="_blank">GitHub</a>. 

In the Arduino sketch we loop through the values from all sound sensors and print them to the serial. When the button is pressed, it will print "save" on serial and will stop reading values until the button is pressed again. The output from the Serial Plotter in the Arduino IDE would look like this:

![squiz_11](/images/squiz_10.png)

However, we wanted a bit more flexibility in plotting the data (including some help in remembering which color corresponds to which toy), so we used Python and Matplotlib, and modified the Python script from a blog post on <a href="http://electronut.in/plotting-real-time-data-from-arduino-using-python/" target="_blank">Plotting read-time data from Arduino using Python from Electronut.in</a>. We adapted the code to read 5 sensor values, add a legend with the name of the animal toys and their color, and to capture a picture when the "save" string is sent on the serial port (sent when the button is pressed). This is how the saved figure looks like:

![squiz_10](/images/squiz_09.png)

The gain can be adjusted on the MAX4466 sensors using a screwdriver, to adapt to the level of sound generated from each of the toys. We were satisfied with the initial results, so we did not end up changing the gain in this project.  

A note if you are trying this project. Due to the high pitched sounds, testing can be difficult at times when your neighbors might be sleeping. We tried to keep it quiet despite lots of excitement. We did not get any complains from our neighbors (yet).

<h3>Results</h3>

After being satisfied with the test results, we fixed the toys on wood pieces with the same screws that came with the toys (remember, they were designed for bike horns). 

![squiz_08](/images/squiz_08.jpg)

![squiz_12](/images/squiz_11.jpg)

The setup worked excellent during the quiz session, the participants had fun, and the winning team got to keep the toys! 

(We kept the sensors.)

