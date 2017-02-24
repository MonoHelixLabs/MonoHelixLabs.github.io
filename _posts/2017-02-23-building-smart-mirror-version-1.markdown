---
layout: post
title:  "The Mirror Assistant - The First Version of Our Smart Mirror"
date:   2017-02-23 10:48:00 +0100
categories: smarthome iot smartmirror magicmirror
author: paula
permalink: /building-smart-mirror-version-1.html
thumbnail: /images/smart_mirror_v1_thumb.png
---

Brushing teeth in the morning just got better! A smart mirror can tell time, weather, news and more. This is our first prototype of a smart mirror, and we believe it is amongst the simplest and cheapest methods of building a smart mirror.

![smart_mirror_v1_08](/images/smart_mirror_v1_08.jpg)

<h3>Background</h3>

A smart mirror can be loosly defined as a mirror that is able to display information or allows for some kind of interaction, for example by voice, touch or hand-gestures. Many of the home-built smart mirrors are powered either by a Raspberry Pi or an Android tablet. Common use cases are presenting time, weather forecast, latest news, traffic information, calendars, and any other information that can improve the routine of getting up in the morning and/or preparing to go out.

There are many smart mirrors DIY projects shared over the internet (check this <a href="https://dk.pinterest.com/paulapetcu/smart-mirrors/" target="_blank">Pinterest board</a> cataloging some of them), and the interest in smart mirrors has clearly increased over time. Here is Google's trend analysis of the search term "smart mirror" from 2004 until now, measured in percentage of interest over time relative to the highest point of interest:

<script type="text/javascript" src="https://ssl.gstatic.com/trends_nrtr/925_RC01/embed_loader.js"></script> <script type="text/javascript"> trends.embed.renderExploreWidget("TIMESERIES", {"comparisonItem":[{"keyword":"smart mirror","geo":"","time":"all"}],"category":0,"property":""}, {"exploreQuery":"date=all&q=smart%20mirror","guestPath":"https://trends.google.com:443/trends/embed/"}); </script> 

<br/>There is also clearly some interest in making a business in this area. There have been several crowdfunding project initiaves (like <a href="https://www.kickstarter.com/projects/1377326093/perseus-the-worlds-smartest-mirror" target="_blank">Perseus</a>, <a href="https://www.kickstarter.com/projects/appsmith/doodlevu-the-smart-mirror" target="_blank">DoodleVU</a>, <a href="https://www.kickstarter.com/projects/513673859/smartmirror" target="_blank">SmartMirror</a>, <a href="https://www.indiegogo.com/projects/selfiemirror-the-first-smart-mirror-music-photo#/" target="_blank">Selfiemirror</a>), but we can't yet buy a smart mirror from a store. Trends are followed of course by internet domains. Many domains based on "smart mirror" or "magic mirror" are already taken, but products are not available yet (for example: magicmirrors.dk).

It will be interesting to see how the market for smart mirrors will be developing in the future, but as the perfect smart mirror is not available yet to buy, we set out to build one. We will guide you how to build your own in the rest of this article.

<h3>Components</h3>

We used an old Asus Nexus 7 tablet as the computational power for the mirror. A new tablet with similar capabilities would cost around 40$. The total cost of building the mirror was around 20$ (excluding the tablet that we already had lying around). Here's the bill of materials (BOM):

| Item | Est. Price | Description | 
| --- | --- | --- |
| 1 x Mirror Film Sheet | from 5$ | These sheets are usually marketed as privacy films for windows. We bought our mirror film from AliExpress but this <a target="_blank" href="https://www.amazon.com/gp/product/B00CWGIHBE/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B00CWGIHBE&linkCode=as2&tag=monohelixlabs-20&linkId=9f74eeff353ef58ff87556df315a54b3">One Way Mirror Film</a><img src="//ir-na.amazon-adsystem.com/e/ir?t=monohelixlabs-20&l=am2&o=1&a=B00CWGIHBE" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" /> from Amazon should be pretty similar.| 
| 1 x Frame with glass | 14$ | We could have bought the glass separately and built the frame, but we took advantage that these two materials are usually put together as picture frames, so we bought ours at our local supermarket. You can find several on Amazon, for example this <a target="_blank" href="https://www.amazon.com/gp/product/B010EYRUEU/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B010EYRUEU&linkCode=as2&tag=monohelixlabs-20&linkId=53b7d6da69098c9391c03f14a4c85469">Black Frame</a><img src="//ir-na.amazon-adsystem.com/e/ir?t=monohelixlabs-20&l=am2&o=1&a=B010EYRUEU" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />.| 
| 1 x Black paper |  1$ | Is needed in order to cover the back of the glass to ensure that you get the mirror effect. We bought a roll of black giftwrap paper, and used less than 1 meter from it for this project.| 
| 1 x Android tablet with power supply | 0$ - 60$ | The price depends on whether you already have a tablet around or if you want a new one, and with what specifications. The 7" Amazon <a target="_blank" href="https://www.amazon.com/gp/product/B00TSUGXKE/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B00TSUGXKE&linkCode=as2&tag=monohelixlabs-20&linkId=fe9606070ee13115091f4bf63569885e">Fire Tablet</a><img src="//ir-na.amazon-adsystem.com/e/ir?t=monohelixlabs-20&l=am2&o=1&a=B00TSUGXKE" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" /> is 49.99$.|
| Black tape, scissors, cutter, glass cleaner spray, squeegee, baby shampoo mixed with water in a spray bottle | 0$ - 10$ | These are needed for putting the components together. The squeegee and the extra spray bottle with the shampoo mix can be bought as part of a <a target="_blank" href="https://www.amazon.com/gp/product/B002YXPITY/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B002YXPITY&linkCode=as2&tag=monohelixlabs-20&linkId=8b63d669d5a5a8611e0fdae33a4896e3">Window Film Application Tool Kit</a><img src="//ir-na.amazon-adsystem.com/e/ir?t=monohelixlabs-20&l=am2&o=1&a=B002YXPITY" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />.| 
| --- | --- | --- | 
{:.mbtablestyle}
<br/>

<iframe style="width:120px;height:240px;" marginwidth="0" marginheight="0" scrolling="no" frameborder="0" src="//ws-na.amazon-adsystem.com/widgets/q?ServiceVersion=20070822&OneJS=1&Operation=GetAdHtml&MarketPlace=US&source=ac&ref=qf_sp_asin_til&ad_type=product_link&tracking_id=monohelixlabs-20&marketplace=amazon&region=US&placement=B00CWGIHBE&asins=B00CWGIHBE&linkId=b42264e68249a983fadcd304049f8826&show_border=false&link_opens_in_new_window=true&price_color=333333&title_color=0066c0&bg_color=ffffff"></iframe>
<iframe style="width:120px;height:240px;" marginwidth="0" marginheight="0" scrolling="no" frameborder="0" src="//ws-na.amazon-adsystem.com/widgets/q?ServiceVersion=20070822&OneJS=1&Operation=GetAdHtml&MarketPlace=US&source=ac&ref=qf_sp_asin_til&ad_type=product_link&tracking_id=monohelixlabs-20&marketplace=amazon&region=US&placement=B010EYRUEU&asins=B010EYRUEU&linkId=6470923d0b8afd9f1bc227ecf95f9780&show_border=false&link_opens_in_new_window=true&price_color=333333&title_color=0066c0&bg_color=ffffff"></iframe>
<iframe style="width:120px;height:240px;" marginwidth="0" marginheight="0" scrolling="no" frameborder="0" src="//ws-na.amazon-adsystem.com/widgets/q?ServiceVersion=20070822&OneJS=1&Operation=GetAdHtml&MarketPlace=US&source=ac&ref=qf_sp_asin_til&ad_type=product_link&tracking_id=monohelixlabs-20&marketplace=amazon&region=US&placement=B00TSUGXKE&asins=B00TSUGXKE&linkId=f51bbfab6dff53773ee607ffca2dd913&show_border=false&link_opens_in_new_window=true&price_color=333333&title_color=0066c0&bg_color=ffffff"></iframe>
<iframe style="width:120px;height:240px;" marginwidth="0" marginheight="0" scrolling="no" frameborder="0" src="//ws-na.amazon-adsystem.com/widgets/q?ServiceVersion=20070822&OneJS=1&Operation=GetAdHtml&MarketPlace=US&source=ac&ref=tf_til&ad_type=product_link&tracking_id=monohelixlabs-20&marketplace=amazon&region=US&placement=B002YXPITY&asins=B002YXPITY&linkId=c6388f81bcb10fccc5354a3f8ec12ec2&show_border=false&link_opens_in_new_window=true&price_color=333333&title_color=0066c0&bg_color=ffffff"></iframe>

<h3>Method</h3>

<h4>Prerequisites</h4>

 * Find a suitable dust-free work area and have all the materials within reach. 

![smart_mirror_v1_01](/images/smart_mirror_v1_01.jpg)

<h4>Step 1: Add the mirror film sheet on the glass</h4>

 * Take the glass out of the picture frame and clean it with glass/window cleaner spray. 
 * Make a mix of baby shampoo and water and put it in a spray bottle. Or use the spray from the Application Kit if you bought one.
 * Cut the mirror film sheet to the size of the glass plus 1-2 extra centimeters.
 * Spray the glass with the shampoo mix.
 * Add two pieces of tape, one on each side of one of the corners of the film sheet. This will make it easier to take out the protective sheet from the actual sticky film.
 * Separate the protective sheet from the sticky film and add it on the glass.
 * Spray some shampoo mix over the film.
 * Using a squegee, remove the air bubbles starting from the middle and going towards the sides. 
 * Then use a cutter to cut the extra foil on the sides of the mirror.

 There are many videos on how to apply the film on windows or glass, so you can just search for "How to apply window film" for inspiration.

<h4>Step 2: Add the black paper on the back of the glass</h4>

 * Turn the mirror around, with the side where you applied the film down.
 * Cut a sheet of black paper to the size of the mirror, leaving some space on the sides for the tape.
 * Measure where the tablet will be positioned (recommended to be in a corner as to not interfere too much with the normal mirror usage) and trace some guide lines over the paper.
 * Cut the paper in the area where the tablet will be placed:

![smart_mirror_v1_02](/images/smart_mirror_v1_02.jpg)

 * Then tape the paper onto the glass:

![smart_mirror_v1_03](/images/smart_mirror_v1_03.jpg)

 * The result (back and front):

![smart_mirror_v1_04](/images/smart_mirror_v1_04.jpg)

<h4>Step 3: Add the tablet to the back of the mirror</h4>

 * Install the Home Mirror app from the Play Store.

![smart_mirror_v1_00](/images/smart_mirror_v1_00.jpg)

 * Open and configure with your preferences. Launch as full screen.
 * To hold the tablet in place you have several options. 
   * You can simply tape the tablet to the paper, but then it will be very difficult to take it out. 
   * An alternative is to use some elastic to keep the tablet in place while offering the flexibility of being able to take the tablet out for maintenance when needed. We used the back of the picture frame, which was made from a cardboard-like material. We cut out the area needed for the tablet and added some pins to keep two strips of elastic in place.

![smart_mirror_v1_09](/images/smart_mirror_v1_09.png)

<h3>Final thoughts and next steps</h3>

This was a great weekend project, simple to make (both in terms of skills and components needed), and a great use of the old Android tablet that we had sitting in a drawer until this project came to be.

The mirror foil looks better than expected. We had some doubts whether we should even try the mirror foil, but since getting a two-sided mirror was a bit more difficult, we gave it a try. It was the first time we put a foil on the glass and we would probably do better the second time. Clearing the work area from dust and having two people operate the transfer of the foil to the glass can improve the results. 

<h4>Mirror film vs. two-way miror</h4>

For the next version we would however go with a two-way mirror glass (or acrylic) instead of the mirror foil, to get more clarity in the mirror. The current mirror looks reasonably good and the foil was easier and cheaper to acquire than a two-sided mirror. However, it is not bathroom mirror like quality.

Here are some side-by-side comparisons with a sample of a two-way acrylic on the left and the film based mirror on the right:

![smart_mirror_v1_05](/images/smart_mirror_v1_05.jpg)

![smart_mirror_v1_06](/images/smart_mirror_v1_06.png)

![smart_mirror_v1_07](/images/smart_mirror_v1_07.jpg)

<h4>Android vs. Raspberry Pi</h4>

There was one thing we did not expect -- the battery of this tablet couldn't handle showing the dashboard app in full-brightess 24 hours a day, so after some time, we would find that the tablet powered itself off. The number of apps installed was set to a minimum and still the continuous power supply was not enough. We reduced the brightess to somewhere around 75% which resulted in having the mirror displaying the dashboard app for more than 24 hours, but it still powered itself off after a while.

Our tablet is more than 3 years old. If you are building the mirror yourself with an old tablet, we recommend that you do a quick test first. Install the Home Mirror app (or another app that you intend to use in the mirror), set the brightness to 100%, leave the app running in full screen mode, and test how much battery is consumed over time. 

As for us, we will probably replace the tablet with a Raspberry Pi in the next version of our smart mirror.

<h4>Want your own smart mirror?</h4>

We can recommend this as a weekend DIY project, and you can use the links above to buy all or some of the components. If you just want your own ready-to-use smart mirror prototype, contact us and we'll see what we can do. 
