---
layout: page
title: Guidance on using the latest micro:bit revision
heading: micro:bit v2 - accessories
description: Guidance on using the latest micro:bit revision, for accessory makers
permalink: /latest-revision/accessories/
ref: latest-revision-accessories
lang: en
---

{% include alert-info.html content="This article is specifically for people who make accessories for the micro:bit. Please also see our [general user information about the latest micro:bit revision](../)" %}

* TOC
{:toc}

## Overview

Thanks for your continuing support of the micro:bit. The breadth and diversity of accessories available for the micro:bit is a great strength and we’ve worked extremely hard to make the latest revision of the micro:bit work as smoothly as possible with as many accessories as possible.

This article provides information to help you continue to support the 5 million existing micro:bits in the world and the latest board revision with the exciting new features of a speaker and microphone.

If you’d like to keep up to date with technical information about the device, please sign up to our [DAL, Devices and Editors mailing list](http://eepurl.com/dyRx-v) which provides information on hardware revisions, or key low-level software changes as early as possible.

### MakeCode Arcade
Microsoft Research are designing a reference design for [MakeCode Arcade](https://arcade.makecode.com/) accessories that allow the latest revision of the micro:bit to be used as an Arcade platform. This will include a number of options for the size, quality and cost of the extensions allowing a range of unique designs. The Foundation are working closely with Microsoft on the specification and will not approve extensions or add to the website any accessories for the micro:bit that are specifically for MakeCode Arcade but do not follow this specification, as it risks too much fragmentation and complexity for our users.

----------

Accessories that make use of the [large ring pins,](http://tech.microbit.org/hardware/edgeconnector/)  should be unaffected by this revision.

The edge connector should be completley compatible electrically; The latest revision has one additional non-shared GPIO, all other pins and pin modes are compatible.

There are inevitably small layout differences in the placement of the components, and the possible implications of these is covered below.

If you publish hex files for demonstrating your accessories, then please see our [guidance for content publishers](http://#) that covers the need to update hex files in the editor in which they were created.

There are a few considerations for people who have made accessories.


## Denoting compatibility

The Foundation Brand Guidelines set out how to denote board compatibility for your accessory. An updated version will be published at https://microbit.org/brand-guidelines/. In the meantime, please [get in contact for an updated copy](mailto:support@microbit.org?subject=Request%20for%20access%20to%20brand%20book).


## Board changes

### Speaker
The obvious physical change is the addition of the speaker on the back of the board. The profile of the rear of the board does not change, it should still fit in accessories that make use of the edge connector, but if your accessory is mounted closer to the board than the depth of the current JST connector, you will need to check that it still fits the latest board revision and how it affects the use of the speaker.

By default the micro:bit will output sound to **both** the edge connector pins and the on-board speaker. If your accessory makes use of a speaker, you may wish to disable the onboard speaker. This will need to be done in software;  extensions for MakeCode and objects for the Python Editor will support this.

### Microphone
The on-board microphone is also rear-mounted, but has a sound input hole on the front of the board, alongside a microphone activity LED, which will be lit red when in use. If the micro:bit is mounted horizontally on your accessory, you may need to consider how this affects the response of the microphone and the visibility of the microphone LED

### Touch sensitive logo
The micro:bit logo is copper plated and responds to capacitive touch in the same way that the large pins do. In previous revisions, the micro:bit only supported resisitive touch.

### Antenna
The position of the antenna has altered so that it is on an angle and it has also been copper coated to make it more visible. It will still behave in the same way, but if your accessory makes use of radio or Bluetooth we suggest taht you test your software packages with both board revisions in case any threshold tweaks are neccssary.


## Hardware changes

### I2C bus
Whereas on previous revisions, the I2C bus was shared between the motion sensor chip and the edge connector, this is no longer the case. The latest revision has dedictated external i2c lines from the nRF52 to use with accessories. These are the addresses used by the micro:bit.

|                                      | accelerometer    | magnetometer (compass) |
| ------------------------------------ | ---------------- | ---------------------- |
| motion sensor variant 1 (LSM303AGR)  | 0x19 (0x32/0x33) | 0x1E (0x3C/0x3D)       |
| motion sensor variant 2 (FXOS8700CQ) | 0x1F (0x3E/0x3F) | 0x1F (0x3E/0x3F)       |


### Power
The micro:bit can now be powered from the two losenge shaped pads on the rear of the board and the 3V/GND pins. 

If you use the losenge pads, you must diode (or otherwise) protect themselves from the micro:bit having power via another source. This was still necessary on the previous revision when the board was powered from battery, but is now true for USB and edge-connector power also.

The nRF52 supplies 300mA to drive the board.   100mA is reserved for powering on-board components. **200mA** is then available for accessories.

### Schematic
The schematic will be published on the tech site when the hardware is publically available. Please get in touch to [request early access to the v2 schematic](mailto:support@microbit.org?subject=Request%20for%20access%20to%20schematic&body=Name%3A%0D%0A%0D%0AGitHub%20ID%3A).


## Software changes

### MakeCode extensions
If your MakeCode extension makes use of mBed or the DAL, you may need to revise them to be compatible with CODAL and both revisions of the board. The latest revision no longer makes use of mBED.

If the extension is incompatible, the MakeCode editor will fail to compile the program.

We are working behind the scenes on patching all MakeCode extensions that are currently incompatible. If we have not made contact or you wish to discuss any issues, please get in touch.

### Python modules
The additional memory available to the latest revision means that you have more space to create python modules to work with your accessories and the micro:bit.
