---
layout: page
order:
title: Bluetooth Profile
heading: micro:bit Bluetooth Profile
description: The micro:bit can be interacted with in an open way using the standard Bluetooth Low Energy protocol. This page outlines the details of the micro:bit protocol
permalink: /bluetooth/profile/
ref: bluetooth
lang: en
assigned-to: jonnya
review-with: jonnya
---

# Overview

The micro:bit supports Bluetooth via a single profile. This profile
allows it to communicate with smart phones and tablets. Technically, the
micro:bit supports one profile only, the BBC micro:bit profile, which was
custom developed for the device.

If you are looking for information about the 'radio' feature, then
that is not Bluetooth, it is a proprietary protocol from Nordic
called Gazell, which you can find out more about in the links
below.


## BBC micro:bit Bluetooth Profile

The BBC micro:bit Bluetooth profile is defined
[here](https://lancaster-university.github.io/microbit-docs/ble/profile/)

The micro:bit has a Bluetooth 4.1 stack with Bluetooth low energy. It supports
the
[GAP Perhipheral Role](http://bluetooth-mdw.blogspot.co.uk/2016/07/microbit-and-bluetooth-roles.html)

As per all all Bluetooth, it operates in the ISM (Industrial Scientific Medical) band
and this starts at 2.4GHz and ends at 2.41GHz. Bluetooth low energy divides the frequency
band into 50 x 2MHz bands of which 40 are used.
These are called “channels” and numbered 0 to 39.
Channels 37, 38 and 39 are used for “advertising”.

When devices are connected, they use the other channels in a particular sequence
controlled by a feature called “adaptive frequency hopping”.
This helps reduce the impact of congestion from other radio users.

Data transfer rates will only be a few 100K per second at best and it very much depends on
how your application uses the Bluetooth features; lots of teeny temperature containing packets
would have a lower data transfer rate than using the UART service, as it depends on the
proportion of system protocol information vs application data.

There are some useful advanced configuration options in the micro:bit runtime code,
documented
[here](https://lancaster-university.github.io/microbit-docs/advanced/#compile-time-options-with-yotta)


## Challenge

It would be possible for anyone with the appropriate knowledge to define and
implement other Bluetooth profiles. You would need to use the mbed C/C++ environment
to do this.


# Links

[Nordic Gazell proprietary protocol](https://devzone.nordicsemi.com/documentation/nrf51/4.3.0/html/group__gzll__02__user__guide.html)

[Martin Woolley Bluetooth Blog](http://bluetooth-mdw.blogspot.co.uk/p/bbc-microbit.html)

[BittySoftware](http://www.bittysoftware.com/)

[Original micro:bit "Out of the Box" hex file](https://lancaster-university.github.io/microbit-docs/resources/BBC_MICROBIT_OOB_FINAL.zip), including all the attributes in the Bluetooth Profile

[Full profile with the display unused](https://lancaster-university.github.io/microbit-docs/resources/microbit-1_4_17_pwr0.zip). If you want to write to the display over bluetooth then you should use this file instead of the 'Out of the Box' hex, which uses the display.
