---
layout: i2c
order:
title: I2c int/ext bus
heading: I2c information for internal and external bus
description: I2c information for internal and external bus
permalink: /hardware/i2c/
ref: i2c
lang: en
---

## Use of the  I2c bus

The I2c bus for the latest revision of the micro:bit seperates the I2c lines into Internal and External use. 

I2C_INT_SCL and I2C_INT_SDA run to the Nordic chip and communicate with the motion sensor and KL27 interface.

I2C_EXT_SCL and I2C_EXT_SDA run to the edge connector and can be used for accessories.

The v2 micro:bit has a footprint for two different motion sensors: one made by ST (the LSM303AGR) and one by NXP (FXOS8700CQ). The micro:bit DAL supports both of these sensors, detecting them at runtime. To date, all v2 boards have been manufactured with the LSM303AGR, however we may switch to the NXP part. Before doing so we will perform a round of testing and notify the [DAL and Devices mailing list.](http://eepurl.com/dyRx-v)

### I2c block diagram
![i2c block](/docs/hardware/assets/i2c-block.svg)

### Table of addresses used

|                     | accelerometer    | magnetometer (compass) |
|---------------------|------------------|------------------------|
| motion sensor variant 1 (LSM303AGR) | 0x19 (0x32/0x33) | 0x1E (0x3C/0x3D)  |
| motion sensor variant 2 (FXOS8700CQ) | 0x1E (0x3C/0x3D) | 0x1E (0x3C/0x3D) |

This means 0x1E and 0x19 are reserved for onboard use.

### Table of address used by micro:bit accessories (please edit)
If you make an accessory for the micro:bit, please help us by editing the table below and sharing the details of the i2c addresses you use.

| accessory name | organisation | i2c address(es) used | 
|----------------|--------------|-----------------------|
| eg [banana-bit]()|eg Banana enterprises | eg 0x76, 0x29 |


### Acceptable capacitance for I2C accessories

In our recent testing for the motion sensor change, we found that a 10nF cap connected SCL-GND slowed down the i2c bus, but it continued to operate. Separately, capacitance was added to SDA until it ceased operation:
- 100KHz continued with 1nF but failed with 2nF.
- 400kHz continued with 150pF but failed with 180pF.
No difference was seen between the revisions.
