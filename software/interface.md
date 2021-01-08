---
layout: page
order:
title: DAPLink and the USB Interface
heading: DAPLink and the USB interface
description: the DAPLink software running on the USB interface chip for the micro:bit provides the drag and drop programming and debugging features that make the micro:bit so easy to use.
permalink: /software/daplink-interface/
ref: software
lang: en
---

## Target and Interface MCUs

The micro:bit presents itself as a USB disk when it is connected over USB, and can be programmed through this interface without the need to install any drivers. This makes it easier to use as a beginner. Furthermore, no matter what code you run on your micro:bit, or how you manage to crash the device, you can always still put a new program on using the USB connection.This is made possible by having a separate 'interface chip' or 'interface MCU' on the micro:bit dedicated to USB connections, programming and debugging.

The **Interface MCU** is a **Freescale KL27** <span class="v2">V2</span> or **Freescale KL26** <span class="v1"> V1</span>.

The chip that developers' code runs on, and that all the peripherals are connected to is called the 'target MCU'. See the [Hardware](/hardware) page and the schematic for more details about how these two devices are connected.

The **Target MCU** is a **Nordic Semiconductor nRF52833** <span class="v2">V2</span> or **Nordic Semiconductor nRF51822** <span class="v1">V1</span>.

<img src="/docs/software/assets/Interface.svg" alt="DAPlink interface" style="background:#eeeeff; padding:20px;">

The target and interface MCUs are connected by two interfaces:

- Serial Wire Debug (SWD) for programming the target MCU.

- UART for sending messages between the two devices. In practice, the UART from the target MCU is passed through directly to the PC over USB.

### Reference design

On the [reference design](/hardware/reference-design) the interface circuit is clearly separated from the main micro:bit circuits so that you can do the following things:

- Build a board without the interface circuitry and use another debugger to program that over SWD.

- Build a board with *just* the interface circuitry and use that to flash other hardware that you have built that might be too small to contain its own interface chip.


## DAPLink software

This interface chip is running software from [Arm Mbed](https://os.mbed.com/) called [DAPLink](https://github.com/ARMmbed/DAPLink).

This software provides four USB endpoints that have specific purposes:

- MSC - USB mass storage device for drag-and-drop programming of the target MCU's flash memory.

- CDC - serial pass-through from the target MCU to the PC. This is how messages get from the code you write onto the PC.

- HID - CMSIS-DAP compliant debug channel - this is useful if you want to use advanced debuggers like GDB or Keil to understand what's happening (or not happening!) on your micro:bit.

- WebUSB - facilitates communicating with the device via a WebUSB capable browser.

The DAPLink software and interface chip are part of the [Arm Mbed HDK](https://os.mbed.com/handbook/mbed-HDK)

The micro:bit currently ships with DAPLink bootloader at version 0255 and interface at version 0255.

This table shows the device revision and which DAPLink Bootloader and interface it shipped with:

| Board revision | Bootloader | Interface | Download
| -------------- | ---------- | --------- | --------
| 1.3            | 0234       | 0234      | [0234](/docs/software/assets/DAPLink-factory-release/0234_kl26z_microbit_0x8000.hex){: .btn.sm-btn download}
| 1.3b           | 0234       | 0241      | [0241](/docs/software/assets/DAPLink-factory-release/0241_kl26z_microbit_0x8000.hex){: .btn.sm-btn download}
| 1.5            | 0243       | 0249      | [0249](/docs/software/assets/DAPLink-factory-release/0249_kl26z_microbit_0x8000.hex){: .btn.sm-btn download}
| 2.0            | 0255       | 0255      | [0255](/docs/software/assets/DAPLink-factory-release/0255_kl27z_microbit_0x8000.hex){: .btn.sm-btn download}

This table shows the latest DAPLink release for each board version that has been fully tested by the Foundation:

| Board revision | Bootloader | Interface | Download
| -------------- | ---------- | --------- | --------
| 1.*            | 02**       | 0253      | [0253](/docs/software/assets/DAPLink-factory-release/0253_kl26z_microbit_0x8000.hex){: .btn.sm-btn download}
| 2.*            | 0255       | 0255      | [0255](/docs/software/assets/DAPLink-factory-release/0255_kl27z_microbit_0x8000.hex){: .btn.sm-btn download}


### The DAPLink boot loader

It is possible to update the version of DAPLink running on your micro:bit. This is done using the DAPLink bootloader. This means that in fact, DAPLink is built twice for the micro:bit.

1. `bootloader mode` is used to for updating the main interface firmware. In this mode, the drive name is `MAINTENANCE` and hex files dropped onto the disk are written into the KL27 <span class="v2">V2</span> or KL26 <span class="v1">V1</span> flash. These files MUST contain an image of DAPLink or equivalent.
2. `interface mode` is used to target the nRF52833 <span class="v2">V2</span> or nRF51822 <span class="v1">V1</span>. In this mode, the drive name is `MICROBIT` and the hex files dropped onto the micro:bit are written to the flash of the target MCU.

There are detailed instructions for how to [update the firmware version on the micro:bit website](https://microbit.org/get-started/user-guide/firmware/).

**You should never update your micro:bit with firmware from untrusted sources, as these could damage your micro:bit, or make it impossible to re-flash**

## Files on the MICROBIT drive

The flash file system presented on the micro:bit drive is entirely virtual. It is not backed by real memory, and this is why the drive ejects itself after new files are written. When a file is dropped onto the MICROBIT drive, instead of being written into flash memory (like a normal USB memory stick), it is streamed to the target MCU.

The following virtual files exist on the file-system:

- `DETAILS.TXT`: This file tells you about the build of DAPLink currently installed on the interface chip. In later versions of DAPLink it also includes more diagnostic information.

- `MICROBIT.HTM`: This is a link to [microbit.org](https://microbit.org) to help you get started.

After flashing occurs, there might also be a `FAIL.TXT` file, that gives a cause for failure.

The file [error.c](https://github.com/mbedmicro/DAPLink/blob/master/source/daplink/error.c) in the DAPLink source can help in diagnosing what these errors mean.

There is also a full list of [micro:bit error codes](https://support.microbit.org/en/support/solutions/articles/19000016969-micro-bit-error-codes) in our Knowledgebase.

## UART connection

Due to the number of pins on the Nordic Semiconductor chip, only the uart TX and RX lines are connected between the interface MCU and the target MCU. This means that there is no hardware flow control possible. This means that at higher serial speeds (baud rates above 9600), the micro:bit may drop characters being sent to it.

## HID and CMSIS-DAP

The HID endpoint is for a CMSIS-DAP channel. This can most easily be used [with pyOCD](https://github.com/mbedmicro/pyOCD), an open source python library for programming and debugging Arm Cortex-M microcontrollers using CMSIS-DAP

## WebUSB

The [WebUSB API](https://developers.google.com/web/updates/2016/03/access-usb-devices-on-the-web) facilitates communicating with USB devices from the Browser.

It has been supported in DAPLink since version **0243**, so if you have an older micro:bit, you will need to [update the DAPLink firmware](https://microbit.org/get-started/user-guide/firmware/).

The API is currently available in [Chrome based browsers](https://caniuse.com/#feat=webusb) (Android, Chrome OS, Linux, macOS and Windows) and is supported in the MakeCode Editor and the Python Editor. This enables you to flash your micro:bit straight from the browser without the need to save the .hex file first, and use serial communication between the micro:bit and the editor.

## Updating the DAPLink full image

<div class="alert alert-danger">Please note - there is almost no situation in the normal use of the micro:bit where this step will be necessary. We have documented it here in the interests of making the the micro:bit more friendly to developers who want to experiment with the code on the KL27. If your micro:bit enumerates in MAINTENANCE or MICROBIT mode you should never need to perform these steps</div>

**Please only use use these steps if you are familiar with USB bootloaders and command line tools. You should never need to perform these to update a micro:bit.**

You can also flash a full DAPLink image to the <span class="v2">V2</span> device using the KL27 internal bootloader. This will update both interface and bootloader.

[Download latest full DAPLink image](/docs/software/assets/DAPLink-factory-release/full_firmware_image_crc.bin){: .btn.sm-btn download}

You will need to register for and download the [**Bootloader Host Application (blhost)**](https://www.nxp.com/design/software/development-software/mcuxpresso-software-and-tools-/mcuboot-mcu-bootloader-for-nxp-microcontrollers:MCUBOOT?&tab=Design_Tools_Tab) from NXP. IN the /bin folder you will find executables for your operating system.

### Enter bootloader mode

To enter this mode we need to ground TP1 during board power up, this is the BOOTMODE pin in the KL27. To do that, connect with a wire (or something like a paper-clip) TP1 red circle) with any ground point (black square) as you insert the USB cable into the device.

![TP1](/docs/software/assets/TP1.png){: width: 300px}

### Bootloader CLI tool

Run the bootloader tool on your OS. These instructions relate to the CLI, but the GUI settings would be broadly similar.

Usage info:

```
blhost --help
```

Flash KL27 bin file:

```
blhost -u 0x15a2,0x0073 flash-erase-all 0
blhost -u 0x15a2,0x0073 write-memory 0x0 kl27_file.bin
```

Read KL27 flash contents into `kl27_flash_dump.bin` file:

```
blhost -u 0x15a2,0x0073 read-memory 0x0 0x40000 kl27_flash_dump.bin
```
