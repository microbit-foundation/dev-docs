---
layout: page
order:
title: Power consumption
heading: Power consumption
description: Power consumption on the micro:bit
permalink: /hardware/power-consumption/
ref: hardware
lang: en
---

## Power modes
The micro:bit v2 <span class="v2">V2</span> board revision has a range of modes that enable us to conserve power, for example when the board is not being used or when it is powered by battery pack.

**Awake** Board is fully operational. The nRF52 and KL27 will try and conserve power if they can. Power LED is lit.

**Sleep** Put the nRF52 to sleep when instructed by CODAL. Wake when USB is connected, reset is pressed or instructed to by CODAL. 

On USB - Press and hold power/reset for 5 seconds to enter sleep. The micro:bit power LED will dim from bright red to off. It will then flash on/off, showing you that it is still connnected to the power source. Press power/reset to wake up. 

Removing the USB power cable and re-adding it will also wake the micro:bit

**Power off** Power off the device. Triggered by pressing and holding the reset button.

On battery - Press and hold power/reset for 5 seconds to power off the micro:bit. The micro:bit power LED will dim from bright red to off. It will then remain off until you press the power/reset to wake up. 

Inserting a USB power lead will also wake the device.

## LED display
The LED display on the <span class="v2">V2</span> board revision is also brighter than previous revisions, so when using at full brightness you will notice faster battery rundown than an equivalent program on a <span class="v1">v1</span> board. 

See our tips on [prolonging battery life](https://support.microbit.org/en/support/solutions/articles/19000087231-prolonging-battery-life)