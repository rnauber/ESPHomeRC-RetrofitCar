
# Retrofit RC car

TL;DR

I retrofit an old RC car with ESP32-CAM module and wrote an  
<a href="https://github.com/rnauber/ESPHomeRC">Open Source Android app <img src="https://raw.githubusercontent.com/rnauber/ESPHomeRC/master/logo3.png" height="16" > ESPHomeRC</a> to control it via WiFi.  




|   |   |   | 
|---|---|---|
| [![a test rig with a RC car](media/testrig.gif "a test rig with a RC car")<br> click for higher quality video](media/testrig.mp4)  |   |   [![a test rig with a RC car](media/drive.gif "test drive")<br> click for higher quality video](media/drive.mp4)|  



## The Hardware
### Bill of Materials
besides an old RC car stripped of the electronics you need:

* an ESP32-CAM module like [this](https://www.amazon.de/gp/product/B08BL6VG76/ref=ppx_yo_dt_b_asin_title_o01_s01?ie=UTF8&psc=1)
~15 Euro

* H-bridge module (based on [L298](https://www.st.com/resource/en/datasheet/l298.pdf)) like [this](https://www.amazon.de/DollaTek-Controller-Board-Modul-verdoppeln-Smart-Auto-Roboter/dp/B07DK6Q8F9/ref=pd_sbs_3?pd_rd_w=YfmdQ&pf_rd_p=c47a53d1-d94f-481c-a018-dcea8bd5c736&pf_rd_r=19XZHN6QXJM3M1M12XJW&pd_rd_r=7e4fbca7-6231-4c72-b9dd-0d53c0ab2fb4&pd_rd_wg=XVdYy&pd_rd_i=B07DK6Q8F9&psc=1)
~5 Euro
* two Li-Ion 18650 batteries like [these](https://www.amazon.de/kraftmax-Pack-18650er-Akku-Schutzschaltung/dp/B08PL1HRBQ/ref=sr_1_3?__mk_de_DE=%C3%85M%C3%85%C5%BD%C3%95%C3%91) and a holder ~25 Euro

so the total cost should be below 50 Euro

### The Assembly

|   |   |   | 
|---|---|---|
| <img src="media/assembly1.jpg" height="400"> | <img src="media/assembly2.jpg" height="400"> |


|ESP Pin |   H Bridge           | 
|--------|--------------|
|GPIO3 / VOR  | in1 |
|GPIO2     | in2 |
|GPIO14   | in3 |
|GPIO15   | in4 |
|GPIO12   | en1 |
|GPIO13   | en2 |

## The Firmware
[The firmware](firmware/rccar.yaml) is completely open and easily hackable. 
It is based on <a href="https://esphome.io/"><img src="https://esphome.io/_images/logo-text.png" height="16" ></a>. You just describe your setup in a yaml file and a firmware will be generated.

### Preparation
<a href="https://esphome.io/guides/getting_started_command_line.html#installation">Install  <img src="https://esphome.io/_images/logo-text.png" height="16"></a>

### Build  and upload

Get a *3.3V USB to serial adapter* (like [this](https://www.amazon.de/gp/product/B089YTXK8V?psc=1)) and connect it:

|ESP Pin |  ... to         | 
|--------|--------------|
|GPIO0  | GND |
|3.3V     | 3.3V |
|VCR  | RX |
|VCT   | TX  |
|GND  | GND  |



```
esphome rccar.yaml run 

...
RAM:   [=         ]  13.4% (used 43816 bytes from 327680 bytes)
Flash: [=====     ]  51.4% (used 942546 bytes from 1835008 bytes)
Configuring upload protocol...
...
```
Now briefly press "RST".
```
Connecting........
Chip is ESP32-D0WDQ6 (revision 1)
Features: WiFi, BT, Dual Core, 240MHz, VRef calibration in efuse, Coding Scheme None
Crystal is 40MHz
MAC: ...
Uploading stub...
Running stub...
Stub running...
Configuring flash size...
Auto-detected Flash size: 4MB
Compressed 15872 bytes to 10319...
Writing at 0x00001000... (100 %)
...
```



## The software
Then you can control your vehicle with this <a href="https://github.com/rnauber/ESPHomeRC">Open Source Android app <img src="https://raw.githubusercontent.com/rnauber/ESPHomeRC/master/logo3.png" height="16" > ESPHomeRC</a>.





