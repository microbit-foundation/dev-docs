---
layout: page
order:
title: Power Supply
heading: Power Supply
description: Powering the micro:bit via USB, 3V ring and battery
permalink: /hardware/powersupply/
ref: hardware
lang: en
---


## Overview

Power to the micro:bit may be provided via:

- USB connection via the interface chip (which has an on-board regulator)
- A battery plugged into the JST connector
- The 3V and GND pins on the edge connector
- The two rounded-rectangle pads on the rear right of the board

Power from the micro:bit can be provided by the 3V and GND pins to small external circuits.

It is important to stay within the design parameters of the board:

* When powered from USB, the on board interface chip (KL26<span class="v1">v1</span>/KL27<span class="v2">V2</span>) uses its on-chip regulator to provide power. This chip is rated at a maximum of 120mA.

* The on-board current budget will vary depending on the use of the display, Bluetooth, microphone, speaker and other peripherals. You should allow a worst-case budget of 30mA for when all on-board peripherals are in use, leaving <span class="v1">v1</span>90mA/<span class="v2">V2</span>270mA for circuits plugged into the edge connector.

* When powered from a battery, the KL chip is not powered up and the USB Indicator LED will not light up.

* A low-Vf diode is used to switch between sources. The diode prevents back-powering of any source from any other source and means you can have a USB cable and battery pack connected simultaneously.

### Key Voltages

As taken from each of the chip datasheets, it can be seen that different devices have slightly different operating voltage ranges and absolute maximum voltages. Manufacturers state the operating voltage range and the absolute maximum tolerable by the device. You should never exceed the operating voltage range of any of the devices.

### v1 revision

| Device     | min   | max  | absolutemax
|------------|-------|------|------------
| NRF51      | 1.8V  | 3.6V | 3.9Vabs
| KL26       | 1.7V  | 3.6V | 3.8Vabs
| LSM303     | 1.71V | 3.6V | 3.6Vabs
| MMA8653FC  | 1.95V | 3.6V | 3.6Vabs
| MAG3110    | 1.95V | 3.6V | 3.6Vabs

This table implies an operating voltage range of the micro:bit device as a whole as being 1.8V min (for 1.5 variants) or 1.95V min (for 1.3* variants dictated by the motion sensor) and 3.6V max (dictated by all devices).

### V2 revision

| Device     | min   | max  | absolutemax
|------------|-------|------|------------
| NRF52      | 1.7V  | 3.6V | 3.9Vabs
| KL27       | 1.71V | 3.6V | 3.8Vabs
| LSM303     | 1.71V | 3.6V | 3.6Vabs

This table implies an operating voltage range of the micro:bit device as a whole
as being 1.7V min and 3.6V max.

## Practicalities

### USB Powering

<!-- TODO: Update these paragraphs to detail that 270mA is TBC budget for V2 -->

When powered from USB, the KL26 <span class="v1">v1</span> interface chip's on-board regulator is used to provide 3.3V to the rest of the board. The latest revision <span class="v2">V2</span> has a separate regulator on the board.

The [KL26 data sheet](http://www.nxp.com/docs/pcn_attachments/16440_KL26P64M48SF5_Rev.4.pdf)<span class="v1">v1</span> section 3.8.2, Table 30. "USB VREG electrical specifications" indicates the maximum current from the regulated supply is 120mA. Some of this current is required to run on-board devices, such as the KL26 itself, the nRF application processor, the motion sensor, and the LED display. When Bluetooth is enabled, the current consumption of the nRF increases slightly. You should budget your current
requirements for anything you attach to the micro:bit <span class="v1">v1</span> to not exceed about 90mA, giving enough safe headroom for worst case with all on-board peripherals in use.

If you require more than 90mA from the edge connector, (e.g. driving lots of NeoPixels or a small motor) these should have power supplied to them externally. You can back-power the micro:bit via its 3V pad, but please be sure to use a properly regulated supply and a protection diode, as explained below, so that your micro:bit always has a supply within the operating range of all the on-board peripherals and the supplies are not able to power each other.

It is advised that you do not power the micro:bit from USB battery packs. This is because some makes and models of USB battery packs can generate out of range voltages when they are not suitably loaded that could damage your micro:bit (i.e. when a small current is drawn).
Additionally, some USB battery packs will switch off automatically when the current drawn from them is too low.

### Battery Powering

When powered from a battery plugged into the top battery connector, the KL26 interface chip is not powered up, and the System LED will not be turned on. If your code does not display anything on the display, this might look like the micro:bit is not working, but it is.

Because the nRF51 chip is powered almost directly (there is only one BAT60 diode between the supply and the nRF51 power rails), a fully charged **LiPoly battery** that is specced to reach 4.2V **will be give greater than the [3.6V maximum that the nRF51 can withstand**](#key-voltages)

There is further information about the [battery connection and use](https://support.microbit.org/solution/articles/19000013982-how-do-i-power-my-micro-bit-/en) in our knowledge-base

### 3V Ring Powering

The micro:bit may be powered from the 3V/GND rings on the edge connector.
There are also two rounded-rectangle pads on the far right of the back of the PCB that can be used to supply power (e.g. solderable pads for a 2xAAA holder that has wires or pins at one edge). [The topmost pad is 0V and the bottom most pad is 3V](../../accessories/making-accessories/#battery-pads).

When powering from the 3V ring or the rounded-rectangle pads on the PCB, you should take appropriate best practice precautions:

1. Fit an external protection diode (preferably with a low Vf rating) to prevent damage due to the power supply being connected the wrong way round.

2. If powered from a voltage source that could generate a voltage higher than the maximum operating voltage of the micro:bit, fit some form of over-voltage protection, or proper regulation.


### Power Supply Architecture v1

The [schematic](/hardware/schematic/) shows the architecture of the power supply.
Note that there are two BAT60A diodes, one from the 3.3V supply from the KL26/27 interface chip, and one from the external battery connector.
The 3V ring on the edge connector is V_TGT, which is the raw supply provided to all on board chips.
Extra care should be taken when connecting directly to the 3V ring or the elongated 3V pad on the rear of the board.

The BAT60A devices have a low Vf rating, you can read about this in the [BAT60A datasheet](http://www.infineon.com/dgdl/Infineon-BAT60ASERIES-DS-v01_01-en.pdf?fileId=db3a304313d846880113def70c9304a9)

### Power Supply Architecture V2 TBC
<!-- TODO -->
