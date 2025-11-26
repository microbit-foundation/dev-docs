---
layout: page
order:
title: The micro:bit runtime DAL/CODAL
heading: The micro:bit runtime DAL/CODAL
description: Developing with the micro:bit runtime, the low level C/C++ tool on which much of the software ecosystem for the micro:bit is built.
permalink: /software/runtime/
ref: software
lang: en
---

## Overview
{:no_toc}

* TOC
{:toc}

The micro:bit runtime, also known as the DAL/CODAL, is software that runs on a micro:bit to support the majority of the micro:bit programming languages. It can help you understand how the micro:bit works, and also will help you understand where to start if you want to dive deeper into the micro:bit, write support software for your own micro:bit hardware extensions, and tailor or improve something on the micro:bit.

| V2   | V1
| ---- | ---- 
|![Software Architectural Diagram v1]({{ "/docs/software/assets/software-overview-v2.svg" | relative_url }}) | ![Software Architectural Diagram v2]({{ "/docs/software/assets/software-overview.svg" | relative_url }})

There are a number of important software layers that run on the micro:bit to enable easy to use languages such as Javascript to be used. Some of these, like Arm Mbed and MicroPython existed before the BBC micro:bit project started, and others, such as the micro:bit runtime were written specifically for the micro:bit.

## The micro:bit Runtime

The micro:bit runtime, created by Lancaster University, is a Hardware Abstraction Layer (HAL) providing a useful set of functions for higher level languages to consume, and to make programming the micro:bit in C or C++ easier.

Many of the MakeCode 'blocks' or MicroPython functions are directly calling functions provided by the micro:bit runtime.

Key components of the micro:bit runtime are:

- A fiber scheduler, that lets your micro:bit do more than one task at a time.
- An eventing system called the message bus, that lets you write reactive code. It can inform your program when things happen on your micro:bit - everything from a button click to a message being received on the radio.
- Device drivers representing the major hardware blocks on the micro:bit, including the LED display, sensors, radio and bluetooth profile.
- Managed types that help keep your programs safe from the complexities of memory management. Originally implemented for higher level languages to exploit, they have also proven very useful for C/C++ programmers too.

The initial version of the micro:bit runtime developed for micro:bit V1 was called DAL (Device Abstraction Layer), which evolved into CODAL (Component Oriented Device Abstraction Layer) for micro:bit V2.


### micro:bit V2 - Component Oriented Device Abstraction Layer (CODAL)

The Component Oriented Device Abstraction Layer (CODAL) is an evolution of the micro:bit V1 DAL runtime that abstracts each hardware component of the micro:bit as a software component.
CODAL was created to generalise and evolve the original DAL, so it could better meet scalability, performance, and cross‑device requirements beyond the first micro:bit board.

CODAL supports a range of devices and processors, including the micro:bit <span class="v2">V2</span> device:
[CODAL target for micro:bit V2](https://github.com/lancaster-university/codal-microbit-v2)

More information can be found in this paper: [MakeCode and CODAL - intuitive and efficient embedded systems programming for education](https://tech.microbit.org/projects/MakeCode-and-CODAL/))

#### Building CODAL

The [instructions for building CODAL](https://github.com/lancaster-university/microbit-v2-samples) are currently located in the micro:bit V2 samples repository. You can clone this repository and build examples from the source folder.

#### CODAL Source Code

- [Sample C/C++ programs](https://github.com/lancaster-university/microbit-v2-samples)
- [CODAL target for micro:bit V2](https://github.com/lancaster-university/codal-microbit-v2)
  - CODAL micro:bit V2 target dependencies:
    - [CODAL core](https://github.com/lancaster-university/codal-core/)
    - [CODAL nRF52](https://github.com/lancaster-university/codal-nrf52/)
    - [CODAL Nordic SDK](https://github.com/microbit-foundation/codal-microbit-nrf5sdk)

### micro:bit V1 - Device Abstraction Layer (DAL)

The original micro:bit runtime provides a [Device Abstraction Layer (DAL)](https://lancaster-university.github.io/microbit-docs/), that is built on top of Arm Mbed.

Arm Mbed provides a Hardware Abstraction Layer (HAL) for chips using Arm Cortex processors. This abstraction layer presents a uniform layer that developers can use to write software for any Arm based processor - including the Nordic chip used on the micro:bit <span class="v1">V1</span>. It provides easy access to peripheral interfaces such as SPI, I2C and serial for use by higher level environments.

The micro:bit <span class="v1">V1</span> can also be programmed using the Mbed HAL directly, for those developers seeking more low level access to the hardware.

#### Building DAL

The [instructions for building DAL](https://lancaster-university.github.io/microbit-docs/offline-toolchains/) are located in the official documentation.

Some of the Arm Mbed tooling, specifically [Yotta, has been deprecated](https://support.microbit.org/support/solutions/articles/19000123284-arm-yotta-registry-deprecation) and installing it in moderm development environments can be difficult. This [Docker image with the micro:bit C++ toolchain](https://github.com/carlosperate/docker-microbit-toolchain) provides a pre-configure build environment that can simplify the process to build DAL.

#### DAL Source Code

- [Device Abstraction Layer, source code](https://github.com/lancaster-university/microbit-dal)
- [Sample C/C++ programs, source code](https://github.com/lancaster-university/microbit-samples)
- [Device Abstraction Layer, documentation sources](https://github.com/lancaster-university/microbit-docs)

## Contributing, asking for features and reporting bugs

The micro:bit runtime is an open source project, distributed under the MIT license, and contributions and collaborations are very much welcomed from the micro:bit community. There are still many things that could be merged into the micro:bit runtime, and with MakeCode moving forward and adding new features, things that go into the runtime can also be exposed to the higher level languages if they work well and prove useful for coding in education.

The micro:bit runtime work is managed via GitHub issue trackers. This is the best place to contribute, send a feature request, or report an bug.
- [CODAL issue tracker](https://github.com/lancaster-university/codal-microbit-v2/issues) for micro:bit <span class="v2">V2</span>
- [DAL issue tracker](https://github.com/lancaster-university/microbit-dal/issues) for micro:bit <span class="v1">V1</span>

If you are unfamiliar with GitHub, you can also send a [micro:bit support ticket](https://support.microbit.org/support/tickets/new).

## Arm Mbed (v1 only)

The information on Arm Mbed applies to micro:bit <span class="v1">V1</span> only.

### Hardware and Low Level Software

The micro:bit hardware is based on the Mbed HDK, and the software on the Mbed SDK. Any program that runs on an Mbed platform will run on the micro:bit provided the required peripherals and memory are present. This means that developers using the micro:bit already have access to a huge [library of components](https://os.mbed.com/components/) that they can use with the micro:bit. Furthermore, it means that things developed on the micro:bit can be used on other Mbed platforms.

Of particular interest are the Mbed BLE projects, many of which were developed on nRF51-based hardware very similar to the micro:bit. The Mbed [Bluetooth Low Energy Team](https://os.mbed.com/teams/Bluetooth-Low-Energy/) has many useful links and examples.

### Online IDE

Mbed useddd to provide an online C/C++ IDE which could be usedd to program the micro:bit. Unfortunately the [Mbed Online IDE has been retired](https://os.mbed.com/blog/entry/keil-studio-cloud-mbed-online-compiler/).

### Mbed Source Code and Versions Used

The Mbed repository for micro:bit is [https://github.com/lancaster-university/mbed-classic](https://github.com/lancaster-university/mbed-classic), this is a fork of Mbed OS 2 (classic) with changes and fixes needed for the micro:bit project. This is the version of Mbed used with the offline DAL toolchain, [Mbed Online Compiler](https://os.mbed.com/handbook/mbed-Compiler), and the [online editors on microbit.org](https://microbit.org/code).

micro:bit was based on the well-established Mbed 2.0 SDK, with which Mbed 5 is compatible. Work is ongoing to [bring the micro:bit runtime onto Mbed 5](https://github.com/lancaster-university/microbit-dal/issues/224).

## Nordic nRF5 SDK

The micro:bit <span class="v1">V1</span> Mbed abstraction for the Nordic chip and micro:bit <span class="v2">V2</span> CODAL abstraction are built on top of the [Nordic nRF5 SDK](https://www.nordicsemi.com/eng/Products/Bluetooth-low-energy/nRF5-SDK).

Crucially, this includes Nordic's [Soft Device 110](https://www.nordicsemi.com/Software-and-Tools/Software/S110) <span class="v1">V1</span> / [Soft Device 113](https://www.nordicsemi.com/Software-and-tools/Software/S113) <span class="v2">V2</span>, a binary object that gets included into any hex file for the micro:bit that manages control of the radio to allow the micro:bit to use the industry standard Bluetooth Low Energy protocols.

The SoftDevice runs on the same MCU as the user's code, and when using the BLE APIs that the micro:bit runtime uses, calls are made into SoftDevice. SoftDevice also occupies the highest priority interrupts, so that user code can be pre-empted by SoftDevice when this is required for the radio to function properly.

<span class="v1">V1</span> only. Micro:bit programs use SoftDevice S110 by default, which only allows the device to be a [GAP Peripheral](http://bluetooth-developer.blogspot.co.uk/2016/07/microbit-and-bluetooth-roles.html). It is possible to use [Soft Device S130](https://www.nordicsemi.com/Software-and-tools/Software/S130) with the micro:bit by compiling offline with Mbed, though that is beyond the scope of this documentation.
