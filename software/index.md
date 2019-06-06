---
layout: page
order:
title: micro:bit Software
heading: the micro:bit Software Ecosystem
description: There are a huge range of software platforms and tools that make the micro:bit work as well as it does. This page outlines what they are and redirects you to more detailed explanations of the different projects.
permalink: /software/
ref: software
lang: en
assigned-to: jonnya/davidw
review-with: jonnya
---

# Overview
{:.no_toc}

* TOC
{:toc}

Software for the micro:bit consists of two main groups:
1. software that runs on your main computer (the 'host' computer, left hand side in the diagram)
2. software that runs on the micro:bit (the 'target' computer, right hand side in the diagram)

Typically, a program is written on the host computer and then transferred to
the micro:bit over USB. There are actually two chips on the
micro:bit, one that is running software entirely to facilitate the flashing (the KL26Z) and one that actually runs the user's code (the nRF51822).

![Software flow](/docs/software/assets/overview.png)


# High Level Programming Languages

The 'high level' programming languages for the micro:bit break down into
two broad categories

* Compiled languages: your program is compiled to ARM assembler or some other kind of bytecode before being copied onto the micro:bit.
* Interpreted Languages: both your script and an interpreter for it are copied onto the micro:bit. Because the interpreter is on the micro:bit itself, these languages typically also allow you to program the micro:bit 'live' over USB by typing commands.

## Compiled Languages

*C/C++, while certainly compiled, is not considered a high-level language in this context*

In order to ensure that the micro:bit online code editors could scale to support 1M deployed boards, Microsoft built [Makecode, an in-browser-compiler](https://makecode.microbit.org), written in TypeScript.

This process is explained in full in the [In browser compiler](/software/in_browser_compiler) page, and in fantastic detail at [TouchDevelop in 208 bits](https://www.touchdevelop.com/docs/touch-develop-in-208-bits).

These in-browser-compilers do not compile the whole of the software stack,
but just the user's script. Function calls and low level functions are
handled by the micro:bit runtime and mbed. A pre-compiled runtime image is
included in the browser and concatenated with the compiled script before
being presented for download.

## Interpreted Languages

In the official micro:bit editors at microbit.co.uk, only Python is interpreted. This is done by the use of the MicroPython interpreter.

The details of this are documented in the [MicroPython](/software/micropython) page.

There is also a [port of the Javascript interpreter Espruino](http://www.espruino.com/MicroBit) that runs on the micro:bit.

# Coding environments and IDEs

There are a huge number of possible coding environments that you can use
to program the micro:bit.

Among the most popular are the official ones listed at http://microbit.org/code as well as the offline Mu editor.

Here's a non-exhaustive list of possible code editors for use with the micro:bit. *please add any you know about that are not here*

* [Javascript Blocks(powered by Makecode)](https://makecode.microbit.org)
* [Python](https://python.microbit.org)
* [mbed Online Compiler](http://developer.mbed.org/platforms/Microbit)
* [Mu offline Python editor](http://codewith.mu/)
* [PyCharm (with MicroPython plugin, can also flash to micro:bit)](https://plugins.jetbrains.com/plugin/9777-micropython)
* [Edublocks (Python with blocks)](https://app.edublocks.org/#MicroBit)


# From Coding Environment to micro:bit

Each of the coding environments generates a special file called a .hex file, which
contains code for your micro:bit, written in a format it can understand.

The micro:bit code is updated by dragging a .hex file onto the MICROBIT drive
that appears on your computer, when you plug in the micro:bit. It looks just like a
USB memory stick to your computer (the flash drive is actually emulated
  by the [DAPLink](/software/daplink-interface) software)

It is also possible to 'flash' code to your micro:bit by using a mobile app,
and using the Bluetooth communications interface from your mobile phone.

You can read more about [bluetooth flashing](/bluetooth/profile) or
[bluetooth apps](/bluetooth/apps-and-examples) by following these links.


# micro:bit Low Level (C/C++) Software Stack

When you write an application for your micro:bit, other pieces of software are
joined together with your application to make up the final .hex file that is
flashed. This code consists of various lower level software components, such as:

* [the micro:bit Runtime](./runtime-mbed/) (sometimes called the device abstraction layer), written in C++ by Lancaster University. The DAL abstracts the
facilities of the micro:bit into a common set of functions that can be used
by all coding languages, though some languages, like Python, make less use of the DAL than Makecode, where the high level block functions map almost directly onto equivalent C/C++ calls in the runtime

* [ARM mbed](./runtime-mbed/#arm-mbed) The runtime builds on top of the ARM mbed SDK, which provides standardised drivers for MCU peripherals and abstracts most of the low level hardware details of different MCUs, meaning that micro:bit software can be easily run on other hardware. This
includes an abstraction for BLE, the mbed BLE api.

* [Nordic nRF51-SDK](./runtime-mbed/#nordic-nrf51-sdk) mbed itself builds on top of the
Nordic nRF51-SDK, the component provided by Nordic to assist programmers in using their hardware.

* [MicroPython interpreter](./micropython) If you are using Python, then the whole MicroPython language interpreter is joined to your application to make up the .hex file. MicroPython on the micro:bit uses mbed underneath, though MicroPython also runs on a wide range of other hardware platforms.
