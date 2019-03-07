---
layout: page
order:
title: Bluetooth Profile
heading: micro:bit Bluetooth Profile
description: The micro:bit can be interacted with in an open way using the standard Bluetooth Low Energy (BLE) protocol. This page outlines the details of the micro:bit protocol
permalink: /bluetooth/profile/
ref: bluetooth
lang: en
---

# Overview

The micro:bit supports Bluetooth via a single profile BBC micro:bit profile 
which was custom developed for the device. This profile
allows it to communicate with other BLE capable devices.

If you are looking for information about the 'radio' feature, it is a [proprietary protocol from Nordic
and Lancaster University](https://lancaster-university.github.io/microbit-docs/ubit/radio/). This is not Bluetooth.


## BBC micro:bit Bluetooth Profile

The BBC micro:bit [Bluetooth profile is defined in the DAL](https://lancaster-university.github.io/microbit-docs/ble/profile/)

There are [pre-compiled Hex files available](https://lancaster-university.github.io/microbit-docs/ble/profile/#all-services-enabled-hex-file) that enable bluetooth services available on the micro:bit and some [example programs in the microbit-samples repository](https://github.com/lancaster-university/microbit-samples)

The micro:bit has a Bluetooth 4.1 stack with Bluetooth Low Energy (BLE) and supports
the [GAP Perhipheral Role](http://bluetooth-mdw.blogspot.co.uk/2016/07/microbit-and-bluetooth-roles.html).

As per all all Bluetooth, it operates in the ISM (Industrial Scientific Medical) band
and this starts at **2.4GHz and ends at 2.41GHz**. BLE divides the frequency
band into 50 x 2MHz bands of which 40 are used.
These are called **channels** and numbered **0 to 39**.
Channels 37, 38 and 39 are used for “advertising”.

When devices are connected, they use the other channels in a particular sequence
controlled by a feature called **adaptive frequency hopping**.
This helps reduce the impact of congestion from other radio users.

Data transfer rates will only be a few 100K per second at best and it very much depends on
how your application uses the Bluetooth features; lots of small temperature containing packets
would have a lower data transfer rate than using the UART service, as it depends on the
proportion of system protocol information vs. application data.

There are some useful [advanced configuration options in the micro:bit runtime code](https://lancaster-university.github.io/microbit-docs/advanced/#compile-time-options-with-yotta)


## Challenge

It would be possible for anyone with the appropriate knowledge to define and
implement other Bluetooth profiles. You would need to use the mbed C/C++ environment
to do this.


# Further information

[Martin Woolley's Bluetooth Blog](http://bluetooth-mdw.blogspot.co.uk/p/bbc-microbit.html) has a range of information on using Bluetooth with micro:bit

[BittySoftware](http://www.bittysoftware.com/) has a range of Bluetooth enabled software for the micro:bit

[Original micro:bit "Out of the Box" experience](https://support.microbit.org/a/solutions/articles/19000021613), including some of the attributes in the Bluetooth Profile

[Full profile with the display unused](https://lancaster-university.github.io/microbit-docs/resources/microbit-1_4_17_pwr0.zip). If you want to write to the display over bluetooth then you should use this file instead of the 'Out of the Box' hex, which uses the display.
