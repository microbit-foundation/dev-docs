---
title: micro:bit firmware
description: The firmware that enables programming, debugging, and USB features on the micro:bit, including DAPLink, the hex file format, and hardware specifications.
slug: /firmware/
---

## Overview

The micro:bit has a separate interface chip dedicated to USB connections, programming, and debugging. This chip runs [DAPLink](/firmware/daplink-interface/) firmware from Arm Mbed, providing drag-and-drop programming, a serial port, and a debug channel.

Code editors produce [.hex files](/firmware/hex-format/) that are copied onto the micro:bit via the USB drive interface. The [Universal Hex](/firmware/universal-hex-creator/) format allows a single hex file to work on all micro:bit versions.

## Specifications

The interface and target MCUs on the V2 micro:bit communicate using documented protocols:

- [I2C protocol specification](/firmware/spec-i2c-protocol/) — communication between the interface and target MCUs
- [Power management specification](/firmware/spec-power-management/) — collaborative power management between the two MCUs
- [Universal Hex format specification](/firmware/spec-universal-hex/) — the file format for cross-version compatibility
