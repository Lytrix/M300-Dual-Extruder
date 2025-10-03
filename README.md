## Zortrax M300 Dual Extruder Communication Protocol ##

This repo is for a project to reverse engineer the communication to a M300 Dual Extruder Toolhead which I bought second hand for 8% of a new one. I don't own a M300, so I want to reverse engineer the communication to be able to use it with Klipper in my own 3d printer.

The design is really ingenious and much less bulky than other designs like:
https://properprinting.pro/product/dual-extrusion-system-for-creality-printers-aka-the-rocker/

The Makerteck Dual Switching Hotend
https://makertech-3d.dozuki.com/c/Dual_Switching_Hotend_v2#main

Or the Snapmaker dual extruder motherboard:
https://eu.snapmaker.com/products/mainboard-for-dual-extrusion-3d-printing-module?currency=EUR&variant=42937079103627&stkn=7aab4a6d2456&utm_source=chatgpt.com


### Extruder Design ###

It only requires 1 extruder motor. which rolls 2 filaments over 1 cogwheel by turning left, or right. So if one is used to be pushed down, the other one is moved upwards and vice versa.

It uses a mechanical end push X-axis mechanism to move the 2 hotends up or down by pushing a brass lever to the left or right.

Inside there are to 

Reference photos:
https://support.zortrax.com/extruder-maintenance/

Zortrax documentation reverse engineering:
https://github.com/zharijs/zmxxxp-re


### ICs ###
The TI 72 marking I2c GPIO chip is a [TCA9536](https://www.ti.com/lit/ds/symlink/tca9536.pdf?ts=1759416374937) which can control 4 pins P0 to P3 on i2c address 0x41 (page 19)

P0 Up Fan
P1 SLD_OUT1
P2 SLD_OUT2
P3 Down Fan

I found this on the [i2c io evaluation board of TI](https://www.ti.com/lit/ug/slvua59a/slvua59a.pdf):


### Connectors ###

The 51 pin LVDS LCD type connector is a: JAE FI-RE51S-HF (right angle shell type, VF is a straight version)
https://docs.rs-online.com/6644/0900766b816cba71.pdf


The ribbon connector was traced to a generic LVDS 51 pin cable used for LCD screens.
https://nl.mouser.com/ProductDetail/JAE-Electronics/FI-RE51CL?qs=jTL5mzL44UxeL1dHzJmr4w%3D%3D

Long cables can be bought on amazon or aliexpress:
https://www.amazon.nl/QUARKZMAN-Flexibele-lintkabel-lcd-scherm-dvd-speler/dp/B0FD9N6NVC/
https://nl.aliexpress.com/item/1005007577351243.html

