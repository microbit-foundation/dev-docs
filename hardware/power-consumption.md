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
The micro:bit v2 <span class="v2">v2</span> board revision has a range of modes configured in DAPLink that enable us to conserve power, for example when the board is not being used or when it is powered by battery pack.

**Awake** Do not conserve power and assume power is provided by USB. Power and USB activity LEDs are lit.
**Sleep** Put the nRF52 to sleep when instructed by the DAL. Wake when USB is connected, reset is pressed or instructed to by the DAL. LED TBC
**Power off** Power off the device. Triggered by pressing and holding the reset button. Power LED is TBC

*The device can accidentally be woken by the combined sensor interrupt on P0.25 as the pin does not have a deault pull. To prevent this behaviour, a pull up needs to be applied to the pin in the nRF configuration*

## LED display 
The LED display on the <span class="v2">v2</span> board revision is also brighter than previous revisions, so when using at full brightness you will notice faster battery rundown than an equivalent program on a <span class="v1">v1</span> board. 

See our tips on [prolonging battery life](https://support.microbit.org/en/support/solutions/articles/19000087231-prolonging-battery-life)