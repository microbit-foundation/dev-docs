---
layout: page
order:
title: micro:bit Reference Design
heading: micro:bit Reference Design
description: the micro:bit reference design is 100% binary compatible with the micro:bit but based on an nRF51 module instead of the chip directly on the board - this means you don't need to worry about antenna tuning or radio compliance when you make your own micro:bit derived design.
permalink: /hardware/reference-design/
ref: hardware
lang: en
assigned-to: jonnya
review-with: jonnya
---

# Reference Design

As well as learning about how the micro:bit is designed from the [schematic](../../hardware/schematic/),
we want to enable people to build their own hardware products and projects based
on the micro:bit. This means taking all the hardware that you've connected
to your micro:bit and putting down on one circuit board.

![micro:bit plant monitor](../assets/referencedesign-57055.png){:width="40%"}

*Turn all these cables into a single board!*

Because the micro:bit has a Bluetooth radio, building your own boards just like
the micro:bit is complicated - you need to tune the antenna, add the right
resonance circuit and then certify the board, if you'd like to build more than
just a few of them. Therefore, in order to make it easier to build things based
on the micro:bit, we've made a version of the board that uses an nRF51-based
module, so that you can just worry about adding your own components to the board.

Furthermore, the micro:bit has a built in programmer and debugger, which is
important for a development board, but might not be worth the cost if you're
just building fixed-function product. The programmer on the reference design
can be easily extracted and used to program other boards - so you can make one
programmer to program all your micro:bit based designs!

# Reference Design Features

* **100% binary compatible with the micro:bit, including all the same hardware
features: 3xbuttons, 5x5 display, accelerometer, magnetometer)**
* Released under the [SolderPad License 0.51](http://solderpad.org/licenses/SHL-0.51/) (based on Apache-2.0, but tailored
  towards Open Hardware)
* Based on an [nRF5188 module](#Module Choice) for ease of use
* Separate programmer and debugger circuits so that you can strip back
things that you don't need
* Standard 2.54mm pitch connector for
  * all the micro:bit edge connector pins
  * programming the KL26Z and the nRF51822
* Modified power supply for more flexible use, standalone regulator
  * drive more components without additional power supply
  * Use Lithium ion polymer batteries as well as AAA (which you shouldn't do
  on the micro:bit)
* Design available in Eagle and Altium and KiCad formats.
* Coin cell connection and holder option ([but beware the dangers of coin cells to children](http://www.bbc.co.uk/news/health-37410343))

Any code that you write for your micro:bit can be run on the reference design
without modification.

![micro:bit reference design back](../assets/referencedesign-76a11.png){:width="40%"}
![micro:bit reference design front](../assets/referencedesign-2988d.png){:width="37%"}

# Modularity

The reference design is laid out in a very modular way, so that someone working
with it can easily customise the board to include only the parts they need.

![the reference design is modular](../assets/referencedesign-9cfb5.png).

For example, if you want to make something really tiny that doesn't make use
of all the expansion or the LEDs, you could make use of the 'bare minimum subset'
section of the board, and have a separate programmer.

# Module Choice

Because the micro:bit uses every pin on the nRF51822, only modules that exposed
all of the GPIO of the chip could be used. We have started with the
[Raytac MDBT40](http://www.raytac.com/products.php), which is available from outlets like
Seedstudio, and commonly used on things like Adafruit BLE boards.

This design is fully open source, and we're happy to accept pull requests for
variants that use other modules, or improvements.

For your own projects, using a different module is as simple as wiring the right
pins. The [hardware](../../hardware/) page has a detailed pinmap. Likewise,
contributions to this pinmap document for other popular modules are welcome.

There is a [list of nRF51882 modules maintained by Nordic Semiconductor](https://www.nordicsemi.com/eng/Products/3rd-Party-Bluetooth-low-energy-Modules),
from which you could choose any module that has all 31GPIOs broken out. If your
design doesn't use all of the pins on the edge connector and you are able to
recompile your software for your custom design ([for example using mbed](../software/dal/))
then you could choose a range of other modules.

# Software bringup

Unlike a micro:bit, your device won't come pre-flashed! Neither of the MCUs will
have any software, so you'll need a debugger, or to ask the people manufacturing
your board to flash it for you

## KL26 software

As described on the [interface firmware](/software/daplink-interface) page, there is
a bootloader and a main interface program that needs to be flashed to the KL26Z.

The hex file/image that contains both of these together can be found
here: [hex file](../assets/kl26z_bl_if_BL0233_IF0234.hex.zip)

You should flash this onto your KL26Z using the header labelled MKL26 prog:

![KL26 program header](../assets/referencedesign-7eaaa.png)

If you don't have a debugger, the nRF51-DK board can be used as a J-link
debugger with the following configuration.

![Using an nRF51-DK as a debugger](../assets/referencedesign-609b1.png){:width="40%"}

Please see [this page](https://developer.mbed.org/users/MarceloSalazar/notebook/programming-a-minibeacon-bluetooth-module-nordic-n/) for more information


## nRF51 software

Once you have flashed the KL26Z then you can use the USB interface on the
reference design itself in order to program any micro:bit hex file onto the
device.

If you have chosen not to include a KL26Z circuit then you can use an external
programmer and the nRF51prog header:

![nRF51 prog header](../assets/referencedesign-d1599.png)

# Design and BOM

The reference design is hosted at GitHub and the BOM and layout are included
there.

[micro:bit reference design GitHub page](https://github.com/microbit-foundation/microbit-reference-design)

The reference design uses the same ICs as the micro:bit itself, so to avoid
duplication, please refer to the [hardware page](../../hardware/)

# Design Software

The reference design can be loaded and used in:

* [Altium](http://www.altium.com/)
* [Eagle Express/Maker/Educational](https://cadsoft.io/pricing/)
* [KiCad EDA](http://kicad-pcb.org/)

Currently, the design is 'Altium First' and we would appreciate any support or
expertise around doing better imports for KiCad and Eagle.

If anyone has experience with Eagle import, and needs any Altium / Protel export versions and libraries, they can be supplied, please see [this GitHub issue](https://github.com/microbit-foundation/microbit-reference-design/issues/1)
