---
layout: page
order:
title: Bluetooth
heading: Bluetooth
description: Bluetooth implementation on the micro:bit
permalink: /bluetooth/
ref: bluetooth
lang: en
assigned-to: markw
review-with: jonnya
---


# Overview

The micro:bit uses a Nordic nRF51822 processor, which has an on board
Bluetooth transceiver. Combined with a PCB trace aerial and other minor
components, and the Nordic S100 SoftDevice Bluetooth stack, this gives
the micro:bit a certified and credible Bluetooth capability.

With Bluetooth, you can connect to other devices and send and receive
data. Bluetooth software features appear in many of the languages,
including Makecode and mbed C++, as well
as their being micro:bit compatible applications for Android and iOS
devices (phones and tablets).

The Nordic nRF51 also has a number of non-bluetooth proprietary
modes of operation, one of which is called Gazell. The Gazell
protocol only works between micro:bits (or other Nordic enabled
devices), and this surfaces as the 'radio' feature in
Makecode and MicroPython, as well as mbed C++.


## micro:bit Bluetooth Features

Bluetooth features available on the micro:bit are defined in a
Bluetooth profile. The micro:bit supports one profile, which was
custom developed for the micro:bit. Read about it
[here](/bluetooth/profile/)


# Links

[What is bluetooth](http://blog.bluetooth.com/a-developers-guide-to-bluetooth/)

[Pairing your Bluetooth device](https://codethemicrobit.com/--docs#doc:reference/bluetooth/bluetooth-pairing)

[Bluetooth Developer Studio](https://www.bluetooth.com/download-developer-studio)

[Bluetooth Developer Studio and micro:bit](http://matchboxmobile.com/blog/bds-and-the-bbc-microbit/)

[Bluetooth Specification](https://www.bluetooth.com/specifications/adopted-specifications)

[Nordic Gazell proprietary protocol](https://devzone.nordicsemi.com/documentation/nrf51/4.3.0/html/group__gzll__02__user__guide.html)
