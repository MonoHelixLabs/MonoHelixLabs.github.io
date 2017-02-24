---
layout: post
title:  "Fridge Heatmap (or Coolmap)"
date:   2016-11-19 17:42:00 +0100
categories: iot kitchen temperature wifi
author: paula
permalink: /fridge-heatmap.html
thumbnail: /images/fridge_heatmap_thumb.png
---

The cool temperature inside the fridge helps to keep the food fresh and slow down the creation of bacteria. However, it has been reported (<a href="http://www.food.gov.uk/northern-ireland/nutritionni/niyoungpeople/survivorform/dontgetsick/chilling" target="_blank">food.gov.uk</a>, <a href="http://www.eufic.org/article/en/food-safety-quality/farm-to-fork/artid/food-storage-refrigerator/" target="_blank">eufic.org</a>, <a href="https://www.cnet.com/news/understand-your-fridge/" target="_blank">cnet.com</a>) that the temperature is not constant inside the fridge and that there is a proper way of organizing the food based on that. Is that true? And if so, how would a heatmap (or coolmap) of a fridge look like? Let's find out!

<h3>Method</h3>

Our objective is to compare the temperature between the shelves of our fridge. 

We know that the temperature goes up and down based on the built-in fridge thermostat and internal airflow, so we want to track the temperature simultaneously from several positions in the fridge. This means that we need several sensors. Also, we want to log the information over a longer period of time for further analysis.

For this, we decided to use the following:

| Item | Est. Price | Description | 
| --- | --- | --- |
| 1 x Adafruit Feather HUZZAH with ESP8266 WiFi | 15.95$ | Pretty small development board with built-in WiFi and smarts from <a href="https://www.adafruit.com/products/2821" target="_blank">Adafruit</a>. Can also buy with <a target="_blank" href="https://www.amazon.com/gp/product/B019MGW6N6/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B019MGW6N6&linkCode={{linkCode}}&tag=monohelixlabs-20&linkId={{link_id}}">Amazon Prime</a><img src="//ir-na.amazon-adsystem.com/e/ir?t=monohelixlabs-20&l=am2&o=1&a=B019MGW6N6" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />.| 
| 3 x DS18B20 | 3 x 1$-4.25$ | Digital temperature sensors. Can be bought for example from <a target="_blank" href="https://www.amazon.com/gp/product/B00OZGWWQA/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B00OZGWWQA&linkCode={{linkCode}}&tag=monohelixlabs-20&linkId={{link_id}}">Amazon</a><img src="//ir-na.amazon-adsystem.com/e/ir?t=monohelixlabs-20&l=am2&o=1&a=B00OZGWWQA" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />, <a href="https://www.sparkfun.com/products/245" target="_blank">SparkFun Electronics</a> or maybe your local electronics store. For the setup of the pins check <a href="http://datasheets.maximintegrated.com/en/ds/DS18B20.pdf" target="_blank">this document</a>.|
| 1 x Power supply with micro USB | ~5$ | The Huzzah can be powered using a micro USB cable. Alternatively, can use a Lithium Ion Polymer Battery. |
| --- | --- | --- | 
{:.mbtablestyle}
<br/>

<iframe style="width:120px;height:240px;" marginwidth="0" marginheight="0" scrolling="no" frameborder="0" src="//ws-na.amazon-adsystem.com/widgets/q?ServiceVersion=20070822&OneJS=1&Operation=GetAdHtml&MarketPlace=US&source=ac&ref=qf_sp_asin_til&ad_type=product_link&tracking_id=monohelixlabs-20&marketplace=amazon&region=US&placement=B019MGW6N6&asins=B019MGW6N6&linkId=81f4063e59a8fe23ac339ea05c964565&show_border=false&link_opens_in_new_window=false&price_color=333333&title_color=0066c0&bg_color=ffffff"></iframe>
<iframe style="width:120px;height:240px;" marginwidth="0" marginheight="0" scrolling="no" frameborder="0" src="//ws-na.amazon-adsystem.com/widgets/q?ServiceVersion=20070822&OneJS=1&Operation=GetAdHtml&MarketPlace=US&source=ac&ref=qf_sp_asin_til&ad_type=product_link&tracking_id=monohelixlabs-20&marketplace=amazon&region=US&placement=B00OZGWWQA&asins=B00OZGWWQA&linkId=b341c67fb4b8c0940d19a520d72b8370&show_border=false&link_opens_in_new_window=false&price_color=333333&title_color=0066c0&bg_color=ffffff"></iframe>

<i>Just a side note. While we are not depending on any income from this blog, we do accept donations, and if you are following along and building this project, we would appreciate if you would use our affiliate links when buying components. Thanks!</i>

The DS18B20 temperature sensors are digital and we can use several sensors on same wire. According to the <a href="http://datasheets.maximintegrated.com/en/ds/DS18B20.pdf" target="_blank">datasheet</a>, these can measure temperatures from -55°C to +125°C, so this is suitable for the temperatures we expect in the fridge. Accuracy is of ±0.5°C at temperature from -10°C to +85°C, which is not great but hopefully sufficient.

<h4>Step 1: Assembly</h4>

Here's the setup, with 3 temperature sensors connected to the Feather Huzzah:

![fridge_heatmap_06](/images/fridge_heatmap_06.png)

We first tested that the setup works on a breadboard.

![fridge_heatmap_03](/images/fridge_heatmap_03.jpg)

And then measured the distances between the top and bottom shelves and prepared the corresponding wires. We used white heat shrink tubes to keep the cables together. 

![fridge_heatmap_04](/images/fridge_heatmap_04.jpg)

<h4>Step 2: Calibration</h4>

As a baseline for our measurements, we first put all the sensors in the same place in the fridge, waited for the values to 'stabilize' for one hour and then checked the values.

![fridge_heatmap_02](/images/fridge_heatmap_02.jpg)

In this chart, TMP1 is green, TMP2 is red, TMP3 is blue.

![fridge_heatmap_01](/images/fridge_heatmap_01.png)

Note that even if we positioned all sensors next to each other and waited for the temperature to stabilize, we still can see some differences in the values recorded by each of the sensors. However, this is expected given the ±0.5°C accuracy mentioned in the datasheet.

<h4>Step 3: Collecting shelf temperatures</h4>

We then placed the 3 sensors on the fridge side at different positions: top shelf, middle, and bottom shelf.

![fridge_heatmap_05](/images/fridge_heatmap_05.jpg)

<h3>Results</h3>

We have collected data from the 3 sensors over 4 days and mapped it to the different fridge shelves. The fridge stayed mostly empty but we opened the door a few times to get the jug of cold water. 

Here's the result in °C averaged hourly, as a Tableau Dashboard:

<div class='tableauPlaceholder' id='viz1479579997465' style='position: relative'><noscript><a href='#'><img alt='Dashboard ' src='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;Fr&#47;FridgeColdmap&#47;Dashboard&#47;1_rss.png' style='border: none' /></a></noscript><object class='tableauViz'  style='display:none;'><param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' /> <param name='site_root' value='' /><param name='name' value='FridgeColdmap&#47;Dashboard' /><param name='tabs' value='no' /><param name='toolbar' value='yes' /><param name='static_image' value='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;Fr&#47;FridgeColdmap&#47;Dashboard&#47;1.png' /> <param name='animate_transition' value='yes' /><param name='display_static_image' value='yes' /><param name='display_spinner' value='yes' /><param name='display_overlay' value='yes' /><param name='display_count' value='yes' /></object></div>
<script type='text/javascript'>
                    var divElement = document.getElementById('viz1479579997465');
                    var vizElement = divElement.getElementsByTagName('object')[0];
                    vizElement.style.width='100%';vizElement.style.height=(divElement.offsetWidth*0.75)+'px';                    var scriptElement = document.createElement('script');                    scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';                    vizElement.parentNode.insertBefore(scriptElement, vizElement);                
</script>
<br/>

<h3>Conclusion: Proper Food Storage in the Refrigerator</h3>

We have measured temperature at 3 different shelves in our fridge and concluded that there are temperature differences between shelves, from the coldest at the bottom shelf to the warmest on the top shelf. This finding corresponds to other reports. 

While the hourly averages over the 4 days are somewhere between 2 and 6 °C, it should be noted though that at the bottom shelf the minimum temperature we recorded over these days was of -3°C (at the bottom shelf) and the maximum temperature recorded was of 9°C (at the top shelf). 

![fridge_heatmap_08](/images/fridge_heatmap_08.png)

Based on this data, we can now make more informed decisions about the storage of the food in our fridge. It was surprising to see actually that the temperature went under 0°C, however it does explain why sometimes if we put the watermelon at the back of the fridge on the bottom shelf (because it's easier to fit it in there) we take it out half frozen!

![fridge_heatmap_09_watermelon_in_the_fridge](/images/fridge_heatmap_09_watermelon_in_the_fridge.jpg)
