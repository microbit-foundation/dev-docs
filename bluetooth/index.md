---
layout: page
order:
title: Bluetooth
heading: Bluetooth
description: Bluetooth implementation on the micro:bit
permalink: /bluetooth/
ref: bluetooth
lang: en
---

## Overview

The micro:bit processor has an on-board [Bluetooth](http://blog.bluetooth.com/a-developers-guide-to-bluetooth/) transceiver. This is combined with a PCB trace aerial and other minor components alongside a software stack that gives the micro:bit a certified and credible Bluetooth capability.

## Bluetooth software stack

<span class="v1">v1</span> Nordic Semiconductor [Soft Device S110](https://www.nordicsemi.com/Software-and-Tools/Software/S110)
<span class="v2">V2</span> Nordic Semiconductor [Soft Device S113](https://www.nordicsemi.com/Software-and-tools/Software/S113)

Using Bluetooth, you can connect to other devices and send and receive data from and to the micro:bit.

## micro:bit Bluetooth Features

Bluetooth features available on the micro:bit are defined in a [Bluetooth profile](/bluetooth/profile). The micro:bit supports one, custom-developed profile.

## Bluetooth and the micro:bit software

The [DAL/C++ reference documentation](https://lancaster-university.github.io/microbit-docs/ble/profile/#reference-documentation) lists the adopted and custom features available within the profile. [MakeCode](https://makecode.microbit.org/reference/bluetooth) contains a set of blocks to make use of the various micro:bit services.

The processor also has several non-bluetooth, proprietary modes of operation upon which the micro:bit radio protocol is based. This protocol works only between micro:bits and is defined as 'Micro:bit Radio' in the DAL and 'radio' in MakeCode, MicroPython, and Mbed C++.

## Apps

- [Android App](https://play.google.com/store/apps/details?id=com.samsung.microbit) facilitates [pairing and flashing programs to the micro:bit](https://support.microbit.org/en/support/solutions/articles/19000051025-pairing-and-flashing-code-via-bluetooth)
- [iOS App](https://apps.apple.com/gb/app/micro-bit/id1092687276)faciliates [pairing and flashing programs to the micro:bit](https://support.microbit.org/en/support/solutions/articles/19000051025-pairing-and-flashing-code-via-bluetooth)
- [Swift Playgrounds](https://github.com/microbit-foundation/microbit-swift-playgrounds) contains a Playground Book available in the Swift app and a micro:bit Swift API to develop further resources
Scratch.

## Further information

- [Bluetooth Specification](https://www.bluetooth.com/specifications/adopted-specifications)
- [DAL/C++ Bluetooth Reference Documentation](https://lancaster-university.github.io/microbit-docs/ble/profile/#reference-documentation)