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

The micro:bit processor has an on board
Bluetooth transceiver. Combined with a PCB trace aerial and other minor
components, and the Nordic [Soft Device 110](https://www.nordicsemi.com/Software-and-Tools/Software/S110) v1{:.v1} / [Soft Device 140](https://www.nordicsemi.com/Software-and-tools/Software/S140) v2{:.v2} stack, this gives
the micro:bit a certified and credible Bluetooth capability.

Using Bluetooth, you can connect to other devices and send and receive
data from and to the micro:bit.

## micro:bit Bluetooth Features

Bluetooth features available on the micro:bit are defined in a
[Bluetooth profile](/bluetooth/profile). The micro:bit supports one, custom developed profile.

## Bluetooth and the micro:bit software

Bluetooth software features appear in many of the languages,
including MakeCode and C++, as well
as their being micro:bit compatible applications for Android and iOS
devices (phones and tablets).

The processor also has a number of non-bluetooth proprietary
modes of operation, one of which is called Gazell. The Gazell
protocol only works between micro:bits (or other Nordic enabled
devices), and this surfaces as the 'radio' feature in
Makecode and MicroPython, as well as mbed C++.

# Links

[What is bluetooth](http://blog.bluetooth.com/a-developers-guide-to-bluetooth/)

[Pairing your Bluetooth device](https://support.microbit.org/solution/articles/19000051025-pairing-and-flashing-code-via-bluetooth)

[Bluetooth Developer Studio](https://www.bluetooth.com/download-developer-studio)

[Bluetooth Developer Studio and micro:bit](http://matchboxmobile.com/blog/bds-and-the-bbc-microbit/)

[Bluetooth Specification](https://www.bluetooth.com/specifications/adopted-specifications)

[Nordic Gazell proprietary protocol](https://devzone.nordicsemi.com/documentation/nrf51/4.3.0/html/group__gzll__02__user__guide.html)
