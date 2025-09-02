---
layout: page
order:
title: micro:bit software
heading: The micro:bit software ecosystem
description: There are a huge range of software platforms and tools that make the micro:bit work as well as it does. This page outlines what they are and redirects you to more detailed explanations of the different projects.
permalink: /software/
ref: software
lang: en
---

## Overview
{:.no_toc}

* TOC
{:toc}

Software for the micro:bit consists of two main groups:
1. software that runs on your computer (host), for example the browser editor

2. software that runs on the micro:bit (target)

Typically, a program is written on the host computer and then transferred to the micro:bit over USB.

There are actually two chips on the micro:bit, one that is running the **DAPlink** software entirely to facilitate the flashing (KL26<span class="v1">V1</span>/KL27<span class="v2">V2</span>) and one that actually runs the user's code (nRF51<span class="v1">V1</span>/nRF52<span class="v2">V2</span>).

![Software flow]({{ "/docs/software/assets/software-program.svg" | relative_url }})


## High level programming languages

The 'high level' programming languages for the micro:bit break down into two broad categories

- Compiled languages: your program is compiled to Arm assembler or some other kind of bytecode before being copied onto the micro:bit.

- Interpreted Languages: both your script and an interpreter for it are copied onto the micro:bit. Because the interpreter is on the micro:bit itself, these languages typically also allow you to program the micro:bit 'live' over USB by typing commands.

### Compiled languages

*C/C++, while certainly compiled, is not considered a high-level language in this context*

In order to ensure that the micro:bit online code editors could scale to support millions of deployed boards, Microsoft built [MakeCode](https://makecode.microbit.org), an in-browser-compiler written in TypeScript.

This process further explained in the [MakeCode software page]({{ "/software/makecode" | relative_url }}) page.

In-browser-compilers do not compile the whole of the software stack, just the user's script. Function calls and low level functions are handled by the micro:bit runtime. A pre-compiled runtime image is included in the browser and concatenated with the compiled script before being presented for download.

### Interpreted languages

In the [official micro:bit editors](https://microbit.org/code), only Python is interpreted. This is done by the use of the MicroPython interpreter.

The details of this are documented in the [MicroPython]({{ "/software/micropython" | relative_url }}) page.

There is also a [port of the Javascript interpreter Espruino](http://www.espruino.com/MicroBit) that runs on the micro:bit.

## Coding environments and IDEs

There are a huge number of possible coding environments that you can use to program the micro:bit.

Among the most popular are the official ones listed at http://microbit.org/code as well as the offline Mu editor.

Here's a non-exhaustive list of possible code editors for use with the micro:bit: *please add any you know about that are not here*

- [MakeCode](https://makecode.microbit.org)

- [Python](https://python.microbit.org)

- [App Inventor](http://iot.appinventor.mit.edu/#/microbit/microbitintro)

- [Arduino IDE (C++)](https://learn.adafruit.com/use-micro-bit-with-arduino/overview)

- [Art:bit](https://kidscodejeunesse.org/artbit)

- [Bitty Software Applications](https://bittysoftware.blogspot.com/p/applications.html)

- [CodeMao](https://codemao.cn/)

- [https://wood.codemao.cn/?editor_mode=1](https://wood.codemao.cn/?editor_mode=1)

- [Edublocks (Python with blocks)](https://app.edublocks.org/#MicroBit)

- [GNAT (Ada)](https://github.com/AdaCore/Ada_Drivers_Library/tree/master/examples/MicroBit)

- [Kittenblock](https://www.kittenbot.cc/pages/software)

- [Kodu](https://www.kodugamelab.com/resources/#microbit)

- [MATLAB & Simulink](https://uk.mathworks.com/academia/courseware/microbit.html)

- [Mbed Online Compiler](https://os.mbed.com/platforms/Microbit/)

- [mBlock 5](https://www.makeblock.com/software/mblock5)

- [MicroBlocks (beta)](http://microblocks.fun/)

- [Mind+](http://mindplus.cc/)

- [Mu offline Python editor](http://codewith.mu/)

- [PyCharm (with MicroPython plugin, can also flash to micro:bit)](https://plugins.jetbrains.com/plugin/9777-micropython)

- [Thonny (You will need to change the interpreter in Tools > Options > Interpreter)](https://thonny.org/)

- [Vittascience (with blocks & python programming, simulator and many electronic modules)](https://vittascience.com/microbit/)

## From coding environment to micro:bit

Each of the coding environments generates a special file called a .hex file, which contains code for your micro:bit, written in a format it can understand.

The micro:bit code is updated by dragging a .hex file onto the MICROBIT drive that appears on your computer, when you plug in the micro:bit. It looks just like a USB memory stick to your computer (the flash drive is actually emulated by the [DAPLink]({{ "/software/daplink-interface" | relative_url }}) software)

It is also possible to 'flash' code to your micro:bit by using a mobile app, and using the [Bluetooth]({{ "/bluetooth/" | relative_url }}) communications interface from your mobile phone.

Read more about [bluetooth apps]({{ "/bluetooth/apps-and-examples" | relative_url }}).

### micro:bit Low Level (C/C++) Software Stack

When you write an application for your micro:bit, other pieces of software are joined together with your application to make up the final .hex file that is flashed. This code consists of various lower level software components, such as:

- [DAL/CODAL]({{ "/software/runtime/" | relative_url }}) (sometimes called the runtime), written in C++ by Lancaster University. The DAL abstracts the facilities of the micro:bit into a common set of functions that can be used by all coding languages. The high level block functions in MakeCode map almost directly onto equivalent C/C++ calls in the runtime. MicroPython requires less use of the DAL.

- [Arm Mbed]({{ "/sofrware/runtime/" | relative_url }}) The Arm Mbed SDK  provides standardised drivers for MCU peripherals and abstracts most of the low level hardware details of different MCUs, meaning that micro:bit software can be easily run on other hardware. This includes an abstraction for BLE, the Mbed BLE api.

- [Nordic nRF5 SDK]({{ "/software/runtime/#nordic-nrf5-sdk" | relative_url }}) Mbed itself builds on top of the Nordic nRF5 SDK, the component provided by Nordic to assist programmers in using their hardware.

- [MicroPython interpreter]({{ "/software/micropython" | relative_url }}) If you are using Python, then the whole MicroPython language interpreter is joined to your application to make up the .hex file. MicroPython on the micro:bit uses Mbed underneath, though MicroPython also runs on a wide range of other hardware platforms.
