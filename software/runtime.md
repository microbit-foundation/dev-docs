---
layout: page
order:
title: The micro:bit runtime and mbed programming
heading: The micro:bit runtime and mbed programming
description: Information on developing with the micro:bit runtime, the low level C/C++ tool on which much of the software ecosystem for the micro:bit is built.
permalink: /software/runtime/
ref: software
lang: en
---


# Overview
{:.no_toc}

* TOC
{:toc}

This page provides an overview of the micro:bit runtime - software that runs on a micro:bit to support the majority of the micro:bit programming languages. It can help you understand how the micro:bit works, and also will help you understand where to start if you want to dive deeper into the micro:bit, write support software for your own micro:bit hardware extensions, and tailor or improve something on the micro:bit.

![Architectural Diagram](/docs/software/assets/software-overview.png){: style="max-width:50%;"}

There are a number of important software layers that run on the micro:bit to enable easy to use languages such as Javascript and Makecode to be used. Some of these, like ARM mbed and MicroPython existed before the BBC micro:bit project started, and others, such as the micro:bit runtime were written specifically for the micro:bit.

ARM mbed provides something called a Hardware Abstraction Layer (HAL) for chips using ARM Cortex processors. This abstraction layer presents a uniform layer that developers can use to write software for any ARM based processor - including the Nordic nRF51822 used on the micro:bit. It provides easy access to peripheral interfaces such as SPI, I2C and serial for user by higher level environments.

# The micro:bit runtime Device Abstraction Layer

## Purpose - What Does the micro:bit Runtime Do?

The micro:bit runtime provides a Device Abstraction Layer (often called the DAL, but 'Runtime' is the term we want to standardise on), that is built using ARM mbed. Lancaster University has written this runtime for the micro:bit as part of its ongoing efforts to support the adoption of Computer Science in schools. It is designed to provide a useful set of functions for higher level languages to consume, and make programming the micro:bit in C or C++ easier. Many of the 'blocks' you use in Makecode are directly calling functions provided by the DAL. The micro:bit runtime DAL is written in C/C++ and builds on the ARM mbed HAL.

Key components of the micro:bit runtime are:

* a scheduler, that lets your micro:bit do more than one task at a time.
* an eventing system called the message bus, that lets you write reactive code. It can inform your program when things happen on your micro:bit - everything from a button click to a message being received on the radio.
* device drivers representing the major hardware blocks on the micro:bit, including the LED display, sensors, file system, radio and bluetooth profile.
* managed types that help keep your programs safe from the complexities of memory management. Originally implemented for higher level languages to exploit, they have also proven very useful for C/C++ programmers too.

When writing C/C++ code for the micro:bit, use of the micro:bit runtime is highly recommended. It provides an easy to use API for C/C++ programs, and is written in a componentised manner so that you can use only the parts you need (for example, just the MicroBitDisplay). The micro:bit can also be programmed using the mbed HAL directly, for those developers seeking more low level access to the hardware.

## micro:bit runtime Documentation

The micro:bit runtime has extensive documentation, which can be found here:

https://lancaster-university.github.io/microbit-docs/

## Contributing to the micro:bit Runtime

The micro:bit runtime is an open source project, distributed under the MIT license, and contributions and collaborations are very much welcomed from the micro:bit community. There are still many things that could be merged into the micro:bit runtime, and with Makecode moving forward and adding new features, things that go into the runtime can also be exposed to the higher level languages if they work well and prove useful for coding in education.

Firstly, you should get yourself into a situation where you can build the micro:bit runtime DAL. You can choose either an online build environment inside your web browser through mbed.org, or an downloadable compiler. The [getting started docs] (https://lancaster-university.github.io/microbit-docs/#getting-started) guide you through this process.

If you would have a feature request, or would like to get involved in the micro:bit runtime development, visit the list of open issues [list of open issues](https://github.com/lancaster-university/microbit-dal/issues) and raise a new issue if it isn't already in there. You can also join the microbit-community slack channel if you'd like to discuss the micro:bit runtime and its components.

## Reporting Bugs

If you think you've found a bug in the DAL, please report the issue on GitHub: [log a new issue](https://github.com/lancaster-university/microbit-dal/issues/new)

## DAL Source Code

[Device Abstraction Layer, source code](https://github.com/lancaster-university/microbit-dal)

[Sample C/C++ programs, source code](https://github.com/lancaster-university/microbit-samples)

[Device Abstraction Layer, documentation sources](https://github.com/lancaster-university/microbit-docs)

# ARM mbed

## Hardware and Low Level Software

The micro:bit hardware is based on the mbed HDK, and the software on the mbed SDK. Any program that runs on an mbed platform will run on the micro:bit provided the required peripherals and memory are present. This means that developers using the micro:bit already have access to a huge [library of components](https://developer.mbed.org/components/) that they can use with the micro:bit. Furthermore, it means that things developed on the micro:bit can be used on other mbed platforms.

Of particular interest are the mbed BLE projects, many of which were developed on nRF51-based hardware very similar to the micro:bit. The mbed [Bluetooth Low Energy Team](https://developer.mbed.org/teams/Bluetooth-Low-Energy/) has many useful links and examples.

## Online IDE

mbed also provides an online C/C++ IDE with which you can program the micro:bit. To get started with this, please see the [micro:bit Platform Page](http://developer.mbed.org/platforms/Microbit) on the mbed site, where there's a getting started video.

## mbed Source Code and Versions Used

The main mbed repository is at [https://github.com/ARMmbed/mbed-os](https://github.com/ARMmbed/mbed-os). For official builds of the micro:bit, ie. when using the [online editors on microbit.org](https://microbit.org/code), a branch of mbed with some micro:bit specific bugfixes and changes specific to micro:bit is used. This can be found in [https://github.com/lancaster-university/mbed-classic](https://github.com/lancaster-university/mbed-classic). This branch is currently being merged back into mbed.

micro:bit was based on the well-established mbed 2.0 SDK, with which mbed 5 is compatible. Work is ongoing to bring the micro:bit runtime onto mbed 5. If you're interested in this project, jump into the microbit-community slack channel or follow [this issue](https://github.com/lancaster-university/microbit-dal/issues/224)

# Nordic nRF51 SDK

The mbed abstraction for the nRF51 is built on top of the Nordic nRF51 SDK
https://www.nordicsemi.com/eng/Products/Bluetooth-low-energy/nRF5-SDK

Crucially, this includes [Nordic's SoftDevice](https://devzone.nordicsemi.com/documentation/nrf51/4.2.0/html/group__nrf518__lib__ble__s110__intro.html), a binary object that gets included into any hex file for the micro:bit that manages control of the radio to allow the micro:bit to use the industry standard Bluetooth Low Energy protocols.

The SoftDevice runs on the same MCU as the user's code, and when using the mbed BLE APIs (that the micro:bit runtime also uses), calls are made into SoftDevice. SoftDevice also occupies the highest priority interrupts, so that user code can be pre-empted by SoftDevice when this is required for the radio to function properly.

By default, all micro:bit programs use SoftDevice S110, which only allows the device to be a GAP Peripheral. It is possible to use S130 with the micro:bit by compiling offline with mbed, though that is beyond the scope of this documentation.
