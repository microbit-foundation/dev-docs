---
layout: page
order:
title: Power Supply
heading: Power Supply
description: Power Supply
permalink: /hardware/powersupply/
ref: hardware
lang: en
---


# Overview

Power to the micro:bit may be provided via the USB connection via the
interface chip (which has an on-board regulator), or via a battery plugged into the top
connector. It is also possible (with care) to power the micro:bit from the 3V pad at the
bottom. The 3V pad at the bottom can be used to provide power to small external circuits.

It runs from battery, USB, or from the pads on the bottom,
so it's quite a flexible device - but beware to stay within
the design parameters of the device so you don't cause any
damage to it.

* The nRF51 datasheet states that the operating range of the chip is 1.8V to 3.6V.

* When powered from USB, the on board interface chip (KL26) uses it's on chip
regulator to provide power, and this chip is rated at a maximum of 120mA.

* The on-board current budget will vary depending on the use of the display,
the Bluetooth, and other peripherals. You should allow a worst case budget
of 30mA for when all on board peripherals are in use, leaving 90mA for circuits
plugged into the edge connector.

* When powered from a battery, the KL26 is not powered up (and note that the
System LED will not light up when powered from battery)

* A low-Vf diode is used to switch between sources. The diode prevents back-powering of any source from any other source and means you can have a USB cable and battery pack connected simultaneously.

* All key facts can be independently verified and understood further by looking
at the [schematic](/hardware/schematic/) and refering to the appropriate chip data
sheets also listed on that page.


# Practicalities

## USB Powering

When powered from USB, the KL26 interface chip's on-board regulator is used
to provide 3.3V to the rest of the board.

The [data sheet](http://www.nxp.com/docs/pcn_attachments/16440_KL26P64M48SF5_Rev.4.pdf)
section 3.8.2, Table 30. "USB VREG electrical specifications" indicates the maximum
current from the regulated supply is 120mA. Some of this current is required to
run on-board devices, such as the KL26 itself, the nRF51 application processor, the motion sensor, and the LED display. When Bluetooth is enabled, the current
consumption of the nRF51 increases slightly. You should budget your current
requirements for anything you attach to the micro:bit to not exceed about
90mA to give enough safe headroom for worst case with all on board peripherals
in use.

This means that if you require more than 90mA from the edge connector,
(e.g. driving lots of NeoPixels or a small motor) these should have power supplied
to them externally. You can back-power the micro:bit via it's 3V pad, but please
be sure to use a properly regulated supply and a protection diode, as explained
below, so that your micro:bit always has a supply within the operating range of
all the on board peripherals and the supplies are not able to power each other.

It is advised that you do not power the micro:bit from USB battery packs. This is
because some makes and models of USB battery packs can generate out of range
voltages when they are not suitably loaded that could damage your micro:bit
(i.e. when a small current is drawn).
Also, some USB battery packs will switch off automatically when the current
drawn from them is too low.

## Battery Powering

When powered from a battery plugged into the top battery connector, the
KL26 interface chip is not powered up, and the System LED will not be
turned on. If your code does not display anything on the display,
this might look like the micro:bit is not working, but it is.

Because the nRF51822 is powered almost directly (there is only one BAT60 diode
between the supply and the nRF51 power rails), a fully charged **LiPoly battery**
that is specced to reach 4.2V **will be give greater than the [3.6V maximum that
the nRF51822 can withstand**](#key-voltages)

There is further information about the [battery connection and use](https://support.microbit.org/solution/articles/19000013982-how-do-i-power-my-micro-bit-/en) in our knowledgebase

## 3V Ring Powering

The micro:bit may be powered from the 3V/GND rings on the edge connector.
There are also two losenge shaped pads on the far right of the back of the PCB
that can be used to supply power (e.g. solderable pads for a 2xAAA holder that
has wires or pins at one edge). [The topmost losenge is 0V and the bottom most
losenge is 3V](../../accessories/making-accessories/#battery-pads).

When powering from the 3V ring or the losenge on the PCB, you should take
appropriate best practice precautions:

1. Fit an external protection diode (preferably with a low Vf rating)
to prevent damage due to the power supply being connected the wrong way
round.

2. If powered from a voltage source that could generate a voltage higher
than the maximum operating voltage of the micro:bit, fit some form
of over voltage protection, or proper regulation.


## Power Supply Architecture

The [schematic](/hardware/schematic/) shows the architecture of the power supply.
Key points to note are that there are two BAT60A diodes, one from the 3.3V
supply from the KL26 interface chip, and one from the external battery connector.
Note that the 3V ring on the edge connector is V_TGT, which is the raw
supply provided to all on board chips, so this is why extra care
should be taken when connecting directly to the 3V ring or the 3V losenge.

The BAT60A devices have a low Vf rating, you can read about this in the
[BAT60A datasheet](http://www.infineon.com/dgdl/Infineon-BAT60ASERIES-DS-v01_01-en.pdf?fileId=db3a304313d846880113def70c9304a9)


## Key Voltages

As taken from each of the chip data sheets, it can be seen that different
devices have slightly different operating voltage ranges and absolute
maximum voltages. Manufacturers state the operating voltage range as well
as the absolute maximum tolerable by the device. You should never exceed
the operating voltage range of any of the devices.

| Device     | min   | max  | absolutemax
| NRF51      | 1.8V  | 3.6V | 3.9Vabs
| KL26       | 1.7V  | 3.6V | 3.8Vabs
| LSM303     | 1.71V | 3.6V | 3.6Vabs
| MMA8653FC  | 1.95V | 3.6V | 3.6Vabs
| MAG3110    | 1.95V | 3.6V | 3.6Vabs

This table implies an operating voltage range of the micro:bit device as a whole
as being 1.8V min (for 1.5 variants) or 1.95V min (for 1.3* variants dictated by the motion sensor) and
3.6V max (dictated by all devices).
