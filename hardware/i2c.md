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

The internal lines run to the Nordic chip and communicate with the motion sensor and KL27 interface.

The external lines run to the edge connector and can be used for accessories.

### I2c block diagram
![i2c block](/docs/hardware/assets/i2c-block.svg)

### Table of addresses used

|                     | accelerometer    | magnetometer (compass) |
|---------------------|------------------|------------------------|
| motion sensor variant 1 (LSM303AGR) | 0x19 (0x32/0x33) | 0x1E (0x3C/0x3D)  |
| motion sensor variant 2 (FXOS8700CQ) | 0x1F (0x3E/0x3F) | 0x1F (0x3E/0x3F) |

This means 0x1E and 0x19 are reserved for onboard use.

### Table of address used by micro:bit accessories (please edit)
If you make an accessory for the micro:bit, please help us by editing the table below and sharing the details of the i2c addresses you use.

| accessory name | organisation | i2c address(es) used | 
|----------------|--------------|-----------------------|
| eg [banana-bit]()|eg Banana enterprises | eg 0x76, 0x29 |
