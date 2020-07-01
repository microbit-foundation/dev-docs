---
layout: i2c
order:
title: I2c shared bus
heading: I2c information for shared bus
description: I2c information for shared bus
permalink: /hardware/i2c-shared/
ref: i2c-shared
lang: en
---

## Use of the shared I2C bus

The motion sensors on the board are on the same I2C bus as the edge connector I2C pins. This means that if you have an accessory that uses I2C on this bus, you need to check it won’t clash with any of the possible on-board sensors.

The v1.5 micro:bit has a footprint for two different motion sensors: one made by ST (the LSM303AGR) and one by NXP (FXOS8700CQ). The micro:bit DAL supports both of these sensors, detecting them at runtime. To date, all v1.5 boards have been manufactured with the LSM303AGR, however we may switch to the NXP part. Before doing so we will perform a round of testing and notify the [DAL and Devices mailing list.](http://eepurl.com/dyRx-v)

### i2c block diagram
![i2c block](/docs/hardware/assets/i2c-block.svg)


### Table of addresses used

|                     | accelerometer    | magnetometer (compass) |
|---------------------|------------------|------------------------|
| micro:bit v1.3 (MMA8653+MAG3110) | 0x1D (0x3A/0x3B) | 0x0E (0x1C/0x1D) |
| micro:bit v1.5 variant 1 (LSM303AGR) | 0x19 (0x32/0x33) | 0x1E (0x3C/0x3D)  |
| micro:bit v1.5 variant 2 (FXOS8700CQ) | 0x1E (0x3C/0x3D) | 0x1E (0x3C/0x3D) |

Overall, this means 0x1D, 0x0E (from v1.3), 0x1E and 0x19 (for the revision) are reserved for onboard use.

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
