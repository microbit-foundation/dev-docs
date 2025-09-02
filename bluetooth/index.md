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

The micro:bit processor has an on-board [Bluetooth](https://www.bluetooth.com/specifications/) transceiver. This is combined with a PCB trace aerial and other minor components alongside a software stack that gives the micro:bit a certified and credible Bluetooth capability.

## Bluetooth software stack

<span class="v1">V1</span> Nordic Semiconductor [Soft Device S110](https://www.nordicsemi.com/Software-and-Tools/Software/S110).

<span class="v2">V2</span> Nordic Semiconductor [Soft Device S113](https://www.nordicsemi.com/Software-and-tools/Software/S113).

[SoftDevice](https://infocenter.nordicsemi.com/index.jsp?topic=%2Fug_gsg_ses%2FUG%2Fgsg%2Fsoftdevices.html) is the Nordic Bluetooth Software Stack, and different versions of the SoftDevice provide different Bluetooth capabilities for different Nordic chips.

Using Bluetooth, you can connect to other devices and send and receive data from and to the micro:bit.

Bluetooth is [distinct from the micro:bit to micro:bit radio feature](https://support.microbit.org/support/solutions/articles/19000083637-using-the-micro-bit-wirelessly-), which has been built by [Lancaster University on top of the ShockBurst proprietary protocol from Nordic](https://lancaster-university.github.io/microbit-docs/ubit/radio/).

## BBC micro:bit Bluetooth Profile

The micro:bit supports Bluetooth via a single, custom-developed, BBC micro:bit profile. This profile allows it to communicate with other BLE capable devices.

## CODAL

A pre-compiled hex file is available to download for <span class="v2">V2</span> that enables all Bluetooth services. 

[Bluetooth all services CODAL]({{ "/docs/bluetooth/assets/BLE_All_Services_CODAL_0-2-40-ABDLIMTU-P.hex" | relative_url }}){: .btn.sm-btn download}

The source for this can be found in the [microbit-v2-samples](https://github.com/lancaster-university/microbit-v2-samples/blob/master/source/samples/BLETest.cpp) repository.

### DAL

The BBC micro:bit <span class="v1">V1</span> [Bluetooth profile is defined in the DAL](https://lancaster-university.github.io/microbit-docs/ble/profile/).

You can flash one of two pre-compiled Hex files to the micro:bit <span class="v1">V1</span> that enable bluetooth services. As Bluetooth is memory intensive, these are supplied as either 'without Magnetometer Service' or 'without DFU Service':

[Without magnetometer]({{ "/docs/bluetooth/assets/BLE_All_Services_DAL_2-1-1-No-Mag.hex" | relative_url }}){: .btn.sm-btn download}

[Without DFU]({{ "/docs/bluetooth/assets/BLE_All_Services_DAL_2-1-1-No-DFU.hex" | relative_url }}){: .btn.sm-btn download}

The DAL contains the [C++ source for the BLE service files](https://github.com/lancaster-university/microbit-samples/blob/master/source/examples/bluetooth-services/main.cpp).

There are also some example programs in the [microbit-samples](https://github.com/lancaster-university/microbit-samples) repository:

- [bluetooth-eddystone-uid](https://github.com/lancaster-university/microbit-samples/tree/master/source/examples/bluetooth-eddystone-uid)

- [bluetooth-eddystone-url](https://github.com/lancaster-university/microbit-samples/tree/master/source/examples/bluetooth-eddystone-url)

- [bluetooth-uart](https://github.com/lancaster-university/microbit-samples/tree/master/source/examples/bluetooth-uart)

The micro:bit has a <span class="v2">V2</span>Bluetooth 5.0/<span class="v1">V1</span>Bluetooth 4.1 stack with Bluetooth Low Energy (BLE) and supports the [GAP Peripheral Role](https://bluetooth-developer.blogspot.com/2016/07/microbit-and-bluetooth-roles.html) by default in DAL/CODAL and can support GAP Peripheral and Central device roles by modifying DAL/CODAL to use a different SoftDevice.

It operates in the ISM (Industrial Scientific Medical) band, as per all Bluetooth devices. This starts at **2.4GHz and ends at 2.41GHz**. BLE divides the frequency band into 50 x 2MHz bands of which 40 are used. These are called **channels** and numbered **0 to 39**. Channels 37, 38 and 39 are used for "advertising".

When devices are connected, they use the other channels in a particular sequence controlled by a feature called **adaptive frequency hopping**. This helps reduce the impact of congestion from other radio users.

Data transfer rates will only be a few hundred Kilobytes per second at best, and throughput depends on how your application uses the Bluetooth features. Throughput depends on the proportion of system protocol overheads to application data. Lots of small packets containing - for example - temperature data would have a lower data transfer rate than using the UART service.

There are some useful [advanced configuration options in the micro:bit runtime code](https://lancaster-university.github.io/microbit-docs/advanced/#compile-time-options-with-yotta).

## Challenge

It would be possible for anyone with the appropriate knowledge to define and implement other Bluetooth profiles.

We are seeking collaborators to help us define the new profile elements that expose some of the <span class="v2">V2</span> features.

## Further information

- [Martin Woolley's Bluetooth Blog](https://bluetooth-developer.blogspot.com/) has a range of information on using Bluetooth with micro:bit

- [BittySoftware](https://bittysoftware.blogspot.com) has a range of Bluetooth enabled software for the micro:bit

- [Original micro:bit "Out of the Box" experience](https://microbit.org/get-started/user-guide/out-of-box-experience/), including some of the attributes in the Bluetooth Profile

- [Full profile with the display unused](https://lancaster-university.github.io/microbit-docs/resources/microbit-1_4_17_pwr0.zip). If you want to write to the display over bluetooth then you should use this file instead of the 'Out of the Box' hex, which uses the display.

- [micro:bit radio API documentation](https://lancaster-university.github.io/microbit-docs/ubit/radio/)


## Bluetooth and the micro:bit software

The [DAL/C++ reference documentation](https://lancaster-university.github.io/microbit-docs/ble/profile/#reference-documentation) lists the adopted and custom features available within the profile. 

The processor also has several non-bluetooth, proprietary modes of operation upon which the micro:bit radio protocol is based. This protocol works only between micro:bits and is defined as 'Micro:bit Radio' in the DAL/CODAL or 'radio' in MakeCode and MicroPython.

### Bluetooth in MakeCode

There is a ["Bluetooth" extension](https://makecode.microbit.org/reference/bluetooth) in Microsoft MakeCode that can be used to instantiate individual services from the micro:bit Bluetooth profile, as well as events for connection and disconnection. It is mutually exclusive to the ["Radio" extension](https://makecode.microbit.org/reference/radio).

These services can then be used in conjunction with things like [the micro:bit web components](https://github.com/thegecko/microbit-web-components) to interact with the micro:bit over Bluetooth.

As an example, the tools at [ML Machine](https://ml-machine.org/) have been built with this extension in MakeCode.

Note: on micro:bit V1, there is very limited memory available when also using the Bluetooth extension.

Here is an example of how to add and use the Bluetooth extension in MakeCode:
![adding makecode bluetooth extension]({{ "/docs/bluetooth/assets/add_bluetooth_extension.gif" | relative_url }})

## Apps

- [Android App](https://play.google.com/store/apps/details?id=com.samsung.microbit) facilitates [pairing and flashing programs to the micro:bit](https://support.microbit.org/en/support/solutions/articles/19000051025-pairing-and-flashing-code-via-bluetooth)
- [iOS App](https://apps.apple.com/gb/app/micro-bit/id1092687276) faciliates [pairing and flashing programs to the micro:bit](https://support.microbit.org/en/support/solutions/articles/19000051025-pairing-and-flashing-code-via-bluetooth)
- [Swift Playgrounds](https://github.com/microbit-foundation/microbit-swift-playgrounds) contains a Playground Book available in the Swift app and a micro:bit Swift API to develop further resources
- [Scratch](https://scratch.mit.edu/microbit) supports using a range of micro:bit Bluetooth services via the Scratch Link software and a custom built pairing .hex
