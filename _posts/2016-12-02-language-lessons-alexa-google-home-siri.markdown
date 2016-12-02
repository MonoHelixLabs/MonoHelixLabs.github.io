---
layout: post
title:  "Voice Assistants Language Lesson 101"
date:   2016-12-02 20:11:00 +0100
categories: iot alexa siri google syntax voice smarthome
author: paula
permalink: /language-lessons-alexa-google-home-siri.html
---

One of the challenges for users of the voice assistants such as Amazon Echo, Google Assistant or Apple's Siri is the "what can I say?" aspect, in that users have to remember the invocation and action phrases that work with the device. It's almost like we need to take language lessons to be able to speak to these devices - and that's exactly what we prepared for you. 

Well, these language lessons probably wouldn't count on your CV, but might help you get a better understanding of how to formulate your commands. 

<iframe width="740" height="416" src="https://www.youtube.com/embed/epsyg3fCY_o" frameborder="0" allowfullscreen></iframe>

Some utterances come more natural than others, and therefore are easier to remember, however there are at least 2 more aspects to consider: 

  1. the expected phrases can be different between the assistants

  2. these phrases might come more naturally to native speakers of the languages supported but can be more challenging for non-native speakers of these languages (for example, on Amazon Echo the <a href="https://developer.amazon.com/public/community/post/Tx2XUAQ741IYQI4/How-to-Build-a-Multi-Language-Alexa-Skill" target="_blank">currently</a> supported languages are English and German). Also, things are even more complicated if you have to combine multiple languages in same question, as illustrated in <a href="http://www.theverge.com/2016/3/24/11297072/smart-voice-assistant-language-issues-siri-alexa" target="_blank">this The Verge article</a>.

<h3>Alexa</h3>

![voiceassist_00](/images/voiceassist_00_alexa.jpg)

<h4>Understanding Alexa's Syntax</h4>

If we look into the documentation of how new Alexa skills are created, we can see that the developers are required to predefine various utterances to which a skill can respond, which means that they have to anticipate how the questions will be worded. 

However, in general, Alexa is pretty good at understanding natural language and at approximating incomplete utterances, be it because the predefined utterances were well thought or because Alexa is getting smarter with time.

The general syntax is the following:

  1. To invoke Alexa you have to say the wake word. This wake word is set from the Settings menu item in the Alexa application and by default it is 'Alexa'.
  
  2. Ask Alexa a question or command.

  3. Depending on the command, Alexa will either reply or confirm, or will provide a follow-up question. If a follow-up question was provided by Alexa, it will wait for input, and next step is step (2) again.

Accompanying the voice interaction there is an Alexa app, and in the app you can see the history of the various questions that have been asked over time. It's not all commands that are tracked here however. For example, the commands to turn the lights on or off are not visible.

One thing to remember is that you can't ask about multiple things in the same command, but can only ask one thing at a time. For example, in order to turn off the lights and your TV, you would have to divide this in two statements and first ask to turn off the lights, wait to get the confirmation from Alexa, and then ask about the TV. (A possible workaround for this would be to use <a href="https://ifttt.com" target="_blank">IFTTT</a> or <a href="http://www.logitech.com/harmony-remotes" target="_blank">Harmony</a> and set up a recipe that will trigger several things sequentially.)

Also, at the time of writing, Alexa is not capable of keeping contextual information within a session of questions, which is something that Google Home Assistant performs better on. This means that, for example, if you ask about the age of an actor and where he is from, you are limited by two things with Alexa: (1) cannot ask both questions in one go, and (2) you need to mention the name of the actor each time. 

<h4>Voice training</h4>

The Alexa app allows you to train Alexa to recognize your voice. It takes a few minutes and consists of you reading some sentences. It is important to note that the intonation, cadence, pronunciation and volume of your voice as well as surrounding noise should be similar to how the device will be used under normal conditions, and that no special preparation should be done. 

<h4>Alexa Language Lessons</h4>

Before anything, we should mention that the commands we cover in the video and this blog post is not a complete list. Alexa is being improved over time and new skills appear every day, so it would be a very difficult task to keep track of all commands. However, some of these commands will hopefully help you get to know the basics and avoid common pitfalls.

One would usually not be too worried about the usage of the word 'timer' versus 'reminder', however, in Alexa's world, there are significant differences between these words.  

Setting a timer vs. reminder:

 * If you say "Alexa, remind me to take out the trash in 10 minutes", she will put the "take out the trash" task on your to-do list.
 * However, the following utterance will set the timer, even though it won't remind you what it is about: "Alexa, set timer for 10 minutes" (and then checking how much is left with "Alexa, how much time is left on the timer?" or simply "Alexa: How much time?") 

Another difficulty for some of those with English as their second language is the usage of opening vs turning on, and similarly, closing vs turning off, for example the lights. It appears (according to <a href="https://www.quora.com/Why-do-some-people-say-close-open-the-lights-rather-than-turn-on-off-the-lights" target="_blank">a thread on Quora</a>) that this can be the case for native French or Chinese speakers, where the nearest translation is the open/close versus turn on/off.

Open vs. turn on vs. start:

 * If you have set up smart lights in your home, then you can say "Alexa, turn on the lights." However, if you say "Alexa, open the lights", nothing will happen.
 * Using Apple TV and a Harmony Remote, you <a href="https://support.myharmony.com/en-us/harmony-experience-with-amazon-alexa" target="_blank">can set up Alexa to control the Apple TV</a> by saying "Alexa, turn on Apple TV". Saying "Alexa, open Apple TV" will not work.
 * In general, for home connected devices, can use "Alexa, turn on/off <Device/Scene/Program>", or simply "Alexa, (turn) (the) <Device/Scene/Program > on/off".
 * "Alexa, start Apple TV" will however work (but "Alexa, stop Apple TV" did not work).

Using ask and tell:

* The Alexa Skills Developer documentation <a href="https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/defining-the-voice-interface" target="_blank">notes</a> that "the preferred phrases for beginning an interaction with an Alexa ability are ask and tell" (though there are other <a href="https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/supported-phrases-to-begin-a-conversation">supported phrases to begin a conversation</a> as well), so in general you can use the following to invoke a skill:  "Alexa, ask/tell \<Skill\> (for/to) <Action/Question>". Here are some examples: "Alexa, ask Uber to request a ride", or "Alexa, ask MyFridge what's the temperature inside".

Listening to podcasts:

* "Alexa, play BBC News podcast on TuneIn" or simply "Alexa, play BBC News".
* Or listen live with "Alexa, listen to BBC live" or "Alexa, listen to TWIT live".

Here are some links to other articles listing possible commands: <a href="https://www.cnet.com/how-to/the-complete-list-of-alexa-commands/" target="_blank">CNET</a> and <a href="http://lifehacker.com/the-seven-best-things-you-can-do-with-an-amazon-echo-1766989219" target="_blank">Lifehacker</a>.

If you would like to buy the Amazon Echo or Echo Dot, and at the same time support this site, then we would appreciate if you would use the following affiliate links: <a target="_blank" href="https://www.amazon.com/gp/product/B00X4WHP5E/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B00X4WHP5E&linkCode={{linkCode}}&tag=monohelixlabs-20&linkId={{link_id}}">Amazon Echo - Black</a><img src="//ir-na.amazon-adsystem.com/e/ir?t=monohelixlabs-20&l=am2&o=1&a=B00X4WHP5E" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />, <a target="_blank" href="https://www.amazon.com/gp/product/B01E6AO69U/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B01E6AO69U&linkCode={{linkCode}}&tag=monohelixlabs-20&linkId={{link_id}}">Amazon Echo - White</a><img src="//ir-na.amazon-adsystem.com/e/ir?t=monohelixlabs-20&l=am2&o=1&a=B01E6AO69U" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />, or <a target="_blank" href="https://www.amazon.com/gp/product/B01DFKC2SO/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B01DFKC2SO&linkCode={{linkCode}}&tag=monohelixlabs-20&linkId={{link_id}}">All-New Echo Dot (2nd Generation) - Black</a><img src="//ir-na.amazon-adsystem.com/e/ir?t=monohelixlabs-20&l=am2&o=1&a=B01DFKC2SO" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />.

<div align="center">
<iframe style="width:120px;height:240px;" marginwidth="0" marginheight="0" scrolling="no" frameborder="0" src="//ws-na.amazon-adsystem.com/widgets/q?ServiceVersion=20070822&OneJS=1&Operation=GetAdHtml&MarketPlace=US&source=ac&ref=qf_sp_asin_til&ad_type=product_link&tracking_id=monohelixlabs-20&marketplace=amazon&region=US&placement=B00X4WHP5E&asins=B00X4WHP5E&linkId=fcf9c7bd1d06509923672a42dc845fe4&show_border=false&link_opens_in_new_window=false&price_color=333333&title_color=0066c0&bg_color=ffffff"></iframe>
<iframe style="width:120px;height:240px;" marginwidth="0" marginheight="0" scrolling="no" frameborder="0" src="//ws-na.amazon-adsystem.com/widgets/q?ServiceVersion=20070822&OneJS=1&Operation=GetAdHtml&MarketPlace=US&source=ac&ref=qf_sp_asin_til&ad_type=product_link&tracking_id=monohelixlabs-20&marketplace=amazon&region=US&placement=B01E6AO69U&asins=B01E6AO69U&linkId=6983dfea1bc7cb0ce2d3ab447463e161&show_border=false&link_opens_in_new_window=false&price_color=333333&title_color=0066c0&bg_color=ffffff"></iframe>
<iframe style="width:120px;height:240px;" marginwidth="0" marginheight="0" scrolling="no" frameborder="0" src="//ws-na.amazon-adsystem.com/widgets/q?ServiceVersion=20070822&OneJS=1&Operation=GetAdHtml&MarketPlace=US&source=ac&ref=qf_sp_asin_til&ad_type=product_link&tracking_id=monohelixlabs-20&marketplace=amazon&region=US&placement=B01DFKC2SO&asins=B01DFKC2SO&linkId=bafa7ac88ca20dcda3ff5a25be3650a3&show_border=false&link_opens_in_new_window=false&price_color=333333&title_color=0066c0&bg_color=ffffff"></iframe>
</div>

<h3>Siri</h3>

![voiceassist_01](/images/voiceassist_03.png)

<h4>Understanding Siri's Syntax</h4>

The general syntax is the following and is similar to Alexa's:

  1. To invoke Siri, you can either press the Home button on the device or say "Hey Siri" (if you activated this feature).  
  
  2. Ask Siri a question or command.

  3. Depending on the command, Siri will either reply or confirm, or will provide a follow-up question. If a follow-up question was provided, it will wait for input, and next step is step (2) again.


Similar to Alexa Skills, iOS developers can build integrations with Siri, however limited at the moment to some predefined categories such as messaging, photos, bookings and similar (and the integration can be done using <a href="https://developer.apple.com/library/content/documentation/Intents/Conceptual/SiriIntegrationGuide/" target="_blank">SiriKit</a>).

As compared to Alexa, Siri can keep track of contextual information, so for example you can ask about the age of actor and then ask where he was born without mentioning his name again: "Hey Siri, how old is Brad Pitt?", and then "Where was he born?". 

However, experiments with Siri with being able to ask for multiple commands in the same phrase have resulted in weird mixed results. If you ask "Hey Siri, how old is Brad Pitt and where was he born?" then the answer is "Brad Pitt was born 18 December 1963". The answer to "Hey Siri, how tall is Brad Pitt and where was he born?" is "Brad Pitt was born in ...", but the answer to "Hey Siri, how tall is Brad Pitt and when was he born?" is "I'm afraid I couldn't find anything on '1.8 meters'".

![voiceassist_01](/images/voiceassist_01.png)


<h4>Voice training</h4>

When you activate the "Hey Siri" feature, you can train Siri to recognize your voice by saying a few phrases. If it actually does voice recognition (and indeed it appears to be able to distinguish between the two owners of MonoHelix Labs), then it is something that Alexa does not do at the moment.

<h4>Siri Language Lessons</h4>

Here are some links to articles listing possible commands: <a href="https://www.cnet.com/how-to/the-complete-list-of-siri-commands/" target="_blank">CNET</a> and <a href="https://hey-siri.io/" target="_blank">Hey-Siri.io</a>. Many of the utterances are similar, and appear somewhat more flexible than Alexa's. Here are for example some differences from the points made previously for Alexa:

* "Hey Siri, remind me to take out the trash in 10 minutes" actually sets a reminder for a certain time and a pop-up will go off after 10 mins with the reminder text.
* The answer to "Hey Siri, turn on my Apple TV" is unfortunately "Surprisingly, that is not within my capabilities."

![voiceassist_02](/images/voiceassist_02.png)

<h3>Google Assistant</h3>

Google Assistant (Google Home) is new on the market and we haven't tested it yet. It has great potential on the kind of information it can provide given the access to Google Search capabilities.

To invoke the Google Assistant, you can say "Hey Google" or "OK Google", and looking at the example commands it seems to be quite flexible.

However the number of features (including the integration with smart home devices) is at the moment limited in comparison to Alexa, and it is not clear whether it will allow for custom "skills" development like Alexa's Skills and Siri's SiriKit.

Here are some links to articles listing possible commands for Google Home: <a href="https://www.cnet.com/how-to/the-complete-list-of-google-home-commands-so-far/" target="_blank">CNET</a> and <a href="http://www.androidauthority.com/google-home-voice-commands-727911/" target="_blank">AndroidAuthority</a>.

<h3>Final thoughts on voice interaction</h3>

Going through the example commands for Alexa, Siri and Google Assistant, it appears that Alexa's are the ones that are more restrictive and require a bit more getting used to, while the discussions with Siri and the Google Assistant look more natural. 

One thing that makes the conversation with Alexa more artificial is that it's not a conversation, but rather a series of questions or commands in which Alexa forgets all the context from one second to the other. This contextual awareness do give Siri and Google Assistant some advantage. 

While Alexa is limited by this and a few other things (doesn't support multiple commands in one go, and is not proactive), it is a very attractive platform for those who want to extend it with Skills. In September 2016, it was <a href="https://www.cnet.com/news/amazons-alexa-assistant-now-knows-over-3000-skills/" target="_blank">reported</a> that Alexa knows over 3000 skills. And now you hopefully understand the basics of Alexa's syntax to cope with them.
