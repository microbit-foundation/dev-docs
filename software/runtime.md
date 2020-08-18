---
layout: page
order:
title: The micro:bit runtime DAL/CODAL
heading: The micro:bit runtime DAL/CODAL
description: Information on developing with the micro:bit runtime, the low level C/C++ tool on which much of the software ecosystem for the micro:bit is built.
permalink: /software/runtime/
ref: software
lang: en
---

## Overview
{:no_toc}

* TOC
{:toc}

The micro:bit runtime, also known as the DAL/CODAL is software that runs on a micro:bit to support the majority of the micro:bit programming languages. It can help you understand how the micro:bit works, and also will help you understand where to start if you want to dive deeper into the micro:bit, write support software for your own micro:bit hardware extensions, and tailor or improve something on the micro:bit.

| v2   | v1
| ---- | ---- 
|![Software Architectural Diagram v1](/docs/software/assets/software-overview-v2.svg) | ![Software Architectural Diagram v2](/docs/software/assets/software-overview.svg)

There are a number of important software layers that run on the micro:bit to enable easy to use languages such as Javascript to be used. Some of these, like ARM mbed and MicroPython existed before the BBC micro:bit project started, and others, such as the micro:bit runtime were written specifically for the micro:bit.

ARM mbed provides a Hardware Abstraction Layer (HAL) for chips using ARM Cortex processors. This abstraction layer presents a uniform layer that developers can use to write software for any ARM based processor - including the Nordic chip used on the micro:bit. It provides easy access to peripheral interfaces such as SPI, I2C and serial for user by higher level environments.

### The micro:bit runtime Device Abstraction Layer (DAL)

The micro:bit runtime provides a [Device Abstraction Layer (DAL)](https://lancaster-university.github.io/microbit-docs/), that is built using ARM mbed. Lancaster University has written this runtime for the micro:bit as part of its ongoing efforts to support the adoption of Computer Science in schools. It is designed to provide a useful set of functions for higher level languages to consume, and make programming the micro:bit in C or C++ easier. Many of the 'blocks' you use in Makecode are directly calling functions provided by the DAL. The micro:bit runtime DAL is written in C/C++ and builds on the ARM mbed HAL.

Key components of the micro:bit DAL are:

* a scheduler, that lets your micro:bit do more than one task at a time.
* an eventing system called the message bus, that lets you write reactive code. It can inform your program when things happen on your micro:bit - everything from a button click to a message being received on the radio.
* device drivers representing the major hardware blocks on the micro:bit, including the LED display, sensors, file system, radio and bluetooth profile.
* managed types that help keep your programs safe from the complexities of memory management. Originally implemented for higher level languages to exploit, they have also proven very useful for C/C++ programmers too.

When writing C/C++ code for the micro:bit, use of the micro:bit runtime is highly recommended. It provides an easy to use API for C/C++ programs, and is written in a componentised manner so that you can use only the parts you need (for example, just the MicroBitDisplay). The micro:bit can also be programmed using the mbed HAL directly, for those developers seeking more low level access to the hardware.

### Component Oriented Device Abstraction Layer (CODAL)
The [Component Oriented Device Abstraction Layer (CODAL)](https://lancaster-university.github.io/codal/) is an evolution of the DAL runtime that abstracts each hardware component of the micro:bit as a software component. CODAL supports a range of devices and processors.

Key components of micro:bit CODAL are:

* A unified eventing subsystem (common to all components) that provides a mechanism to map asynchronous hardware and software events to event handlers;
* A non-preemptive fiber scheduler that enables concurrency while minimizing the need for resource locking primitives.
* A simple memory management system based on reference counting to provide a basis for managed types.
* A set of drivers, that abstract microcontroller hardware components into higher level software components,each represented by a C++ class.
* A parameterized object model composed from these components that represents a physical device.

(Source: [MakeCode and CODAL - intuitive and efficient embedded systems programming for education](https://tech.microbit.org/projects/MakeCode-and-CODAL/)

### Building CODAL

Instructions for building CODAL

### Contributing to the micro:bit Runtime

The micro:bit runtime is an open source project, distributed under the MIT license, and contributions and collaborations are very much welcomed from the micro:bit community. There are still many things that could be merged into the micro:bit runtime, and with Makecode moving forward and adding new features, things that go into the runtime can also be exposed to the higher level languages if they work well and prove useful for coding in education.

Firstly, you should get yourself into a situation where you can build the micro:bit runtime DAL. You can choose either an online build environment inside your web browser through mbed.org, or an downloadable compiler. The [getting started docs] (https://lancaster-university.github.io/microbit-docs/#getting-started) guide you through this process.


### Asking for features and reporting bugs

If you would have a feature request, or would like to get involved in the micro:bit runtime development, visit the [list of open issues](https://github.com/lancaster-university/microbit-dal/issues) and raise a new issue if it isn't already in there. 

You can also join the [microbit developer community on Slack](/community) if you'd like to discuss the micro:bit runtime and its components.

If you think you've found a bug in the DAL, please [log a new issue in the GitHub DAL repository](https://github.com/lancaster-university/microbit-dal/issues/new)

### DAL Source Code

[Device Abstraction Layer, source code](https://github.com/lancaster-university/microbit-dal)

[Sample C/C++ programs, source code](https://github.com/lancaster-university/microbit-samples)

[Device Abstraction Layer, documentation sources](https://github.com/lancaster-university/microbit-docs)

## ARM mbed (v1 only)

The information on ARM mbed applies to <span class="v1">v1</span> only.

### Hardware and Low Level Software

The micro:bit hardware is based on the mbed HDK, and the software on the mbed SDK. Any program that runs on an mbed platform will run on the micro:bit provided the required peripherals and memory are present. This means that developers using the micro:bit already have access to a huge [library of components](https://developer.mbed.org/components/) that they can use with the micro:bit. Furthermore, it means that things developed on the micro:bit can be used on other mbed platforms.

Of particular interest are the mbed BLE projects, many of which were developed on nRF51-based hardware very similar to the micro:bit. The mbed [Bluetooth Low Energy Team](https://developer.mbed.org/teams/Bluetooth-Low-Energy/) has many useful links and examples.

### Online IDE

mbed also provides an online C/C++ IDE with which you can program the micro:bit. To get started with this, please see the [micro:bit Platform Page](http://developer.mbed.org/platforms/Microbit) on the mbed site, where there's a getting started video.

### mbed Source Code and Versions Used

The Mbed repository for micro:bit is [https://github.com/lancaster-university/mbed-classic](https://github.com/lancaster-university/mbed-classic), this is a fork of Mbed OS 2 (classic) with changes and fixes needed for the micro:bit project. This is the version of Mbed used with the offline DAL toolchain, [Mbed Online Compiler](https://ide.mbed.com/compiler/), and the [online editors on microbit.org](https://microbit.org/code).

micro:bit was based on the well-established mbed 2.0 SDK, with which mbed 5 is compatible. Work is ongoing to [bring the micro:bit runtime onto mbed 5](https://github.com/lancaster-university/microbit-dal/issues/224).

## Nordic nRF5 SDK

The mbed abstraction for the Nordic chip is built on top of the Nordic nRF5 SDK
https://www.nordicsemi.com/eng/Products/Bluetooth-low-energy/nRF5-SDK

Crucially, this includes Nordic's [Soft Device 110](https://www.nordicsemi.com/Software-and-Tools/Software/S110) <span class="v1">v1</span> / [Soft Device 140](https://www.nordicsemi.com/Software-and-tools/Software/S140) <span class="v2">v2</span>, a binary object that gets included into any hex file for the micro:bit that manages control of the radio to allow the micro:bit to use the industry standard Bluetooth Low Energy protocols.

The SoftDevice runs on the same MCU as the user's code, and when using the mbed BLE APIs (that the micro:bit runtime also uses), calls are made into SoftDevice. SoftDevice also occupies the highest priority interrupts, so that user code can be pre-empted by SoftDevice when this is required for the radio to function properly.

<span class="v1">v1</span> only. Micro:bit programs use SoftDevice S110 by default, which only allows the device to be a [GAP Peripheral](http://bluetooth-mdw.blogspot.co.uk/2016/07/microbit-and-bluetooth-roles.html). It is possible to use [Soft Device S130](https://www.nordicsemi.com/Software-and-tools/Software/S130) with the micro:bit by compiling offline with mbed, though that is beyond the scope of this documentation.
