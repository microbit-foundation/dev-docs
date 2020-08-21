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
The micro:bit v2 <span class="v2">v2</span> board revision has a range of modes that enable us to conserve power, for example when the board is not being used or when it is powered by battery pack.

**Awake** Board is fully operational. The nRF52 and KL27 will try and conserve power if they can. Power LED is lit.

**Sleep** Put the nRF52 to sleep when instructed by CODAL. Wake when USB is connected, reset is pressed or instructed to by CODAL. LED TBC

**Power off** Power off the device. Triggered by pressing and holding the reset button. Power LED is TBC

## LED display
The LED display on the <span class="v2">v2</span> board revision is also brighter than previous revisions, so when using at full brightness you will notice faster battery rundown than an equivalent program on a <span class="v1">v1</span> board. 

See our tips on [prolonging battery life](https://support.microbit.org/en/support/solutions/articles/19000087231-prolonging-battery-life)