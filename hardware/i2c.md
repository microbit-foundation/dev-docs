---
layout: page
order:
title: i2c
heading: Schematics
description: micro:bit i2c pins
permalink: /hardware/schematic/
ref: i2c
lang: en
assigned-to: markw
review-with: jonnya
---

If you make an accessory for the micro:bit, please help us by editing the page and sharing the details of the i2c addresses you use.

## Use of the shared I2C bus

The motion sensors on the board are on the same I2C bus as the edge connector I2C pins. This means that if you have an accessory that uses I2C on this bus, you need to check it won’t clash with the new sensors.

Because we want to avoid having to do another revision in the future, we are designing in two possible sensor devices, but all micro:bits will ship with only one combined magnetometer and accelerometer. The DAL will automatically select which driver to instantiate (and hence this will work in MicroPython and MakeCode without any issues).

## Table of addresses used

|                     | accelerometer    | magnetometer (compass) |
|---------------------|------------------|------------------------|
| micro:bit v1.3      | 0x1D (0x3A/0x3B) | 0x0E (0x1C/0x1D)       |
| micro:bit variant 1 | 0x19 (0x32/0x33) | 0x1E (0x3C/0x3D)       |
| micro:bit variant 2 | 0x1E (0x3C/0x3D) | 0x1E (0x3C/0x3D)       |


Overall, this means 0x1D, 0x0E (from v1.3), 0x1E and 0x19 (for the revision) are reserved for onboard use.

We have checked all the micro:bit ‘approved packages’ to ensure that the new addresses do not clash with existing accessories, and have not found any accessories that clash.

## Limitations

In our recent testing for the motion sensor change, we found that a 10nF cap connected SCL-GND slowed down the i2c bus, but it continued to operate. Separately, capacitance was added to SDA until it ceased operation:
- 100KHz continued with 1nF but failed with 2nF.
- 400kHz continued with 150pF but failed with 180pF.
No difference was seen between the revisions.
