---
layout: i2c
order:
title: I2C int/ext bus
heading: I2C information for internal and external bus
description: I2C information for internal and external bus
permalink: /hardware/i2c/
ref: i2c
lang: en
---

## Use of the I2C bus

The I2C bus for the latest revision of the micro:bit separates the I2C lines into Internal and External use. The [previous revisions share the I2C bus](../i2c-shared/) with the Edge connector and nRF chip.

The internal lines run to the Nordic chip and communicate with the motion sensor and KL27 interface.

The external lines run to the edge connector and can be used for accessories.

### I2C block diagram

![I2C block](/docs/hardware/assets/i2c-diagram.png)

### Table of addresses used

|                     | accelerometer    | magnetometer (compass) | KL27 Power Mng | KL27 Storage |
|---------------------|------------------|------------------------|----------------|--------------|
| motion sensor variant 1 (LSM303AGR)  | 0x19 (0x32/0x33) | 0x1E (0x3C/0x3D) | 0x70 (0xE0/0xE1) | 0x72 (0xE4/0xE5) |
| motion sensor variant 2 (FXOS8700CQ) | 0x1F (0x3E/0x3F) | 0x1F (0x3E/0x3F) | 0x70 (0xE0/0xE1) | 0x72 (0xE4/0xE5) |

While the micro:bit <span class="v2">V2</span> has a dedicated bus for the on-board I2C peripherals, the micro:bit <span class="v1">V1</span> shares the same bus for on-board and external I2C devices. Please check the [V1 shared bus](../i2c-shared/) documentation to check the reserved I2C addresses.

### Table of address used by micro:bit accessories (please edit)

If you make an accessory for the micro:bit, please help us by editing the table below and sharing the details of the I2C addresses you use.

| accessory name | organisation | I2C address(es) used |
|----------------|--------------|-----------------------|
| [EDU:BIT](https://www.cytron.io/p-edubit)| Cytron Technologies | 0x08 (0x10/0x11) |

### Acceptable capacitance for I2C accessories

In our recent testing for the motion sensor change, we found that a 10nF cap connected SCL-GND slowed down the I2C bus, but it continued to operate. Separately, capacitance was added to SDA until it ceased operation:

- 100KHz continued with 1nF but failed with 2nF.
- 400kHz continued with 150pF but failed with 180pF.

No difference was seen between the revisions.

## Notes

The <span class="v2">V2</span> device can be woken by activating (by pulling low) the combined sensor interrupt on P0.25. This open drain signal is connected between the nRF52, the KL27, and motion sensors and requires the nRF52 internal pull up to be configured, even while the device is sleeping.
