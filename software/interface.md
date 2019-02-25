---
layout: page
order:
title: DAPLink and the USB Interface
heading: DAPlink and the USB interface
description: the DAPLink software running on the USB interface chip for the micro:bit provides the drag and drop programming and debugging features that make the micro:bit so easy to use.
permalink: /software/daplink-interface/
ref: software
lang: en
---

# Target and Interface MCUs

One of the coolest features of the micro:bit is the way that it presents itself as a USB disk when it is connected over USB, and can be programmed through this interface without the need to install any drivers. Furthermore, no matter what code you run on your micro:bit, or how you manage to crash the device, you can always still put a new program on using the USB connection.

This is made possible by having a separate 'interface chip' or 'interface MCU' on the micro:bit dedicated to USB connections, programming and debugging. On the micro:bit, that chip is a **Freescale KL26Z**. The chip that developers' code runs on, and that all the peripherals are connected to (the nRF51822) is called the 'target MCU'. See the [Hardware](/hardware) page and the schematic for more details about how these two devices are connected.

<img src="/docs/software/assets/Interface.svg" alt="DAPlink interface" style="background:#eeeeff; padding:20px;">

The target and interface MCUs are connected by two interfaces:

* Serial Wire Debug (SWD) for programming the target MCU
* UART for sending messages between the two devices. In practice, the UART from the target MCU is passed through directly to the PC over USB.

## Reference Design

On the [reference design](/hardware/reference-design) the interface circuit is clearly separated from the main micro:bit circuits so that you can do the following things:

* Build a board without the interface circuitry and use another debugger to program that over SWD
* Build a board with *just* the interface circuitry and use that to flash other hardware that you have built that might be too small to contain its own interface chip.


# DAPLink software


This interface chip is running software from ARM mbed called `DAPLink`.

The source is [available on GitHub](https://github.com/mbedmicro/DAPLink)

This software provides three USB endpoints that have specific purposes:

* MSC - USB mass storage device for drag-and-drop programming of the target MCU's flash memory.
* CDC - serial passthrough from the target MCU to the PC. This is how messages get from the code you write onto the PC
* HID - CMSIS-DAP compliant debug channel - this is useful if you want to use advanced debuggers like GDB or Keil to understand what's happening (or not happening!) on your micro:bit


The DAPLink software and interface chip are part of the [ARM mbed HDK](https://developer.mbed.org/handbook/mbed-HDK)
and the [mbed Enabled program](https://www.mbed.com/en/about-mbed/mbed-enabled/)

The micro:bit currently ships with DAPLink bootloader at version 0243 and [interface at version 0249](https://github.com/ARMmbed/DAPLink/releases/tag/v0249).

The following versions of the device have previously been shipped with the following DAPLink versions

 - v1.3: bl:0234 if:0234
 - v1.3B: bl:0234 if:0241 (built by Farnell for micro:bit commercial sales)
 - v1.5: bl:0243 if:0249

## The DAPLink Boot Loader

It is possible to update the version of DAPLink running on your micro:bit. This is done using the DAPLink bootloader. This means that in fact, DAPLink is built twice for the micro:bit.

* Firstly `bootloader mode`: to target the KL26Z in 'bootloader mode', used for updating the main interface firmware. In this mode, the drive name is `MAINTENANCE` and hex files dropped onto the disk are written into the KL26 flash. These files MUST contain an image of DAPLink or equivalent.
* Secondly in `interface mode` to target the nRF51822. In this mode the disk is called `MICROBIT` and the hex files dropped onto the micro:bit are written to the flash of the target MCU.


## Updating Your Version of DAPLink

There are detailed instructions for how to [update the firmware version on the micro:bit website](https://microbit.org/guide/firmware/).

**You should never update your micro:bit with firmware from untrusted sources, as these could damage your micro:bit, or make it impossible to re-flash**

## Files on the MICROBIT Drive

The flash file system presented on the micro:bit drive is entirely virtual. It is not backed by real memory, and this is why the drive ejects itself after new files are written. When a file is dropped onto the MICROBIT drive, instead of being written into flash memory (like a normal USB memory stick), it is streamed to the target MCU.

The following virtual files exist on the file-system
* `DETAILS.TXT`: This file tells you about the build of DAPLink currently installed on the interface chip. In later versions of DAPLink it also includes more diagnostic information
* `MICROBIT.HTM`: This is a link to [microbit.org](https://microbit.org) to help you get started.

After flashing occurs, there might also be a `FAIL.TXT` file, that gives a cause for failure.

The file [error.c](https://github.com/mbedmicro/DAPLink/blob/master/source/daplink/error.c) in the DAPLink source can help in diagnosing what these errors mean.

# UART Connection

Due to the number of pins on the nRF51822, only the uart TX and RX lines are connected between the interface MCU and the target MCU. This means that there is no hardware flow control possible. This means that at higher serial speeds (baud rates above 9600), the micro:bit may drop characters being sent to it.

# HID and CMSIS-DAP

The HID endpoint is for a CMSIS-DAP channel. This can most easily be used [with pyOCD](https://github.com/mbedmicro/pyOCD), an open source python library for programming and debugging ARM Cortex-M microcontrollers using CMSIS-DAP
