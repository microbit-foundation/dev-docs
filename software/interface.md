---
layout: page
order:
title: DAPLink and the USB Interface
heading: DAPLink and the USB interface
description: The DAPLink software running on the USB interface chip for the micro:bit provides the drag and drop programming and debugging features that make the micro:bit so easy to use.
permalink: /software/daplink-interface/
ref: software
lang: en
---

## Target and Interface MCUs

The micro:bit presents itself as a USB disk when it is connected over USB, and can be programmed through this drive without the need to install any drivers. This makes it easier to use as a beginner. Furthermore, no matter what code you run on your micro:bit, or how you manage to crash the device, you can always still put a new program on using the USB connection.This is made possible by having a separate 'interface chip' or 'interface MCU' on the micro:bit dedicated to USB connections, programming and debugging.

The **Interface MCU** is a **Nordic nRF52833/nRF52820** <span class="v2">V2.2x</span>, **Freescale KL27** <span class="v2">V2.00</span>, or **Freescale KL26** <span class="v1">V1</span>.

The chip that developers' code runs on, and that all the peripherals are connected to is called the 'target MCU'. See the [Hardware](/hardware) page and the schematic for more details about how these two devices are connected.

The **Target MCU** is a **Nordic Semiconductor nRF52833** <span class="v2">V2</span> or **Nordic Semiconductor nRF51822** <span class="v1">V1</span>.

![v2 interface](/docs/software/assets/v2-interface.png)

The target and interface MCUs are connected by these interfaces:

- Serial Wire Debug (SWD) for programming the target MCU.

- UART for sending messages between the two devices. In practice, the UART from the target MCU is passed through directly to the PC over USB.

- <span class="v2">V2</span> I2C using a custom [protocol](/software/spec-i2c-protocol/).

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

This table shows the device revision and which DAPLink Bootloader and Interface it shipped with:

| Board revision | Bootloader | Interface | Download
| -------------- | ---------- | --------- | --------
| 1.3            | 0234       | 0234      | [0234](/docs/software/assets/DAPLink-factory-release/0234_kl26z_microbit_0x8000.hex){: .btn.sm-btn .download}
| 1.3b           | 0234       | 0241      | [0241](/docs/software/assets/DAPLink-factory-release/0241_kl26z_microbit_0x8000.hex){: .btn.sm-btn .download}
| 1.5            | 0243       | 0249      | [0249](/docs/software/assets/DAPLink-factory-release/0249_kl26z_microbit_0x8000.hex){: .btn.sm-btn .download}
| 2.00           | 0255       | 0255      | [0255](/docs/software/assets/DAPLink-factory-release/0255_kl27z_microbit_0x8000.hex){: .btn.sm-btn .download}
| 2.20           | 0256       | 0256      | [0256](/docs/software/assets/DAPLink-factory-release/0256_nrf52820_microbit_if_crc_5dd23001a7_gcc.hex){: .btn.sm-btn .download}
| 2.21           | 0257       | 0257      | [0257](/docs/software/assets/DAPLink-factory-release/0257_nrf52820_microbit_if_crc_c782a5ba90_gcc.hex){: .btn.sm-btn .download}

This table shows the latest DAPLink release for each board version that has been fully tested by the Foundation:

| Board revision | Bootloader | Interface | Download
| -------------- | ---------- | --------- | --------
| 1.*            | 02**       | 0253      | [0253](/docs/software/assets/DAPLink-factory-release/0253_kl26z_microbit_0x8000.hex){: .btn.sm-btn .download}
| 2.00           | 0255       | 0255      | [0255](/docs/software/assets/DAPLink-factory-release/0255_kl27z_microbit_0x8000.hex){: .btn.sm-btn .download}
| 2.2*           | 0257       | 0257      | [0257](/docs/software/assets/DAPLink-factory-release/0257_nrf52820_microbit_if_crc_c782a5ba90_gcc.hex){: .btn.sm-btn .download}

### Beta releases

#### DAPLink 0258-beta3

This DAPLink beta release for <span class="v2">V2.00</span> and <span class="v2">V2.2*</span> has the following improvements:

- 🚀 Faster flashing! Drag & drop a hex file into the `MICROBIT` drive can be up to 25% faster 
- 🚦 Fixed issue where orange LED next to the USB connector sometimes didn't flash when programming the micro:bit via WebUSB 
- 📋 V2.00 also has stability improvements for data logging (this improvement is already present in the V2.2* factory release)


| Board revision | Interface  | Download
| -------------- | ---------- | --------
| 2.00           | 0258-beta3 | [0258-beta3 for V2.00](/docs/software/assets/daplink-beta-releases/0258-beta3_kl27z_microbit_if_crc_0004198_gcc.hex){: .btn.sm-btn .download}
| 2.2*           | 0258-beta3 | [0258-beta3 for V2.2*](/docs/software/assets/daplink-beta-releases/0258-beta3_nrf52820_microbit_if_crc_0004198_gcc.hex){: .btn.sm-btn .download}

Instructions showing how to identify your micro:bit and how to update the DAPLink firmware can be found in the [microbit.org firmware page](https://microbit.org/get-started/user-guide/firmware/).

Once the firmware is updated, you can confirm it's running this beta version if the `DETAILS.TXT` file contains this line:
```
Build ID: v0258-beta3-g0004198b (gcc)
```

If you find any issues with this beta release, please report it via [Support](https://support.microbit.org/support/tickets/new), or via this [GitHub Issue tracker](https://github.com/microbit-foundation/DAPLink/issues).

And, most importantly, **thank you for testing!**

### The DAPLink bootloader

It is possible to update the version of DAPLink running on your micro:bit. This is done using the DAPLink bootloader. This means that in fact, DAPLink is built twice for the micro:bit.

1. `bootloader mode` is used to for updating the interface firmware. In this mode, the drive name is `MAINTENANCE` and hex files dropped onto the disk are written into the interface MCU flash. These files MUST contain an image of DAPLink or equivalent.
2. `interface mode` is used to flash the target MCU. In this mode, the drive name is `MICROBIT`.

There are detailed instructions for how to [update the firmware version on the micro:bit website](https://microbit.org/get-started/user-guide/firmware/).

**You should never update your micro:bit with firmware from untrusted sources, as these could damage your micro:bit, or make it impossible to re-flash**

## Files on the MICROBIT drive

The flash file system presented on the micro:bit drive is entirely virtual. It is not backed by real memory, and this is why the drive ejects itself after new files are written. When a file is dropped onto the MICROBIT drive, instead of being written into storage memory (like a normal USB memory stick), it is streamed to the target MCU.

The following virtual files exist on the file-system:

- `DETAILS.TXT`: This file tells you about the build of DAPLink currently installed on the interface chip. In later versions of DAPLink it also includes more diagnostic information.

- `MICROBIT.HTM`: This is a link to [microbit.org](https://microbit.org) to help you get started.

- `MY_DATA.HTM` : This is a [data logging](https://microbit.org/get-started/user-guide/data-logging/) file and might not be always present in the MICROBIT drive.

After flashing occurs, there might also be a `FAIL.TXT` file, that gives a cause for failure.

The file [error.c](https://github.com/mbedmicro/DAPLink/blob/master/source/daplink/error.c) in the DAPLink source can help in diagnosing what these errors mean.

There is also a full list of [micro:bit error codes](https://support.microbit.org/en/support/solutions/articles/19000016969-micro-bit-error-codes) in our Knowledgebase.

An `ASSERT.TXT` file might also appear, this indicates a minor error might have occurred, but DAPLink was able to recover and work as expected.

## UART connection

Due to the number of pins on the Nordic Semiconductor chip, only the uart TX and RX lines are connected between the interface MCU and the target MCU. This means that there is no hardware flow control possible. This means that at higher serial speeds (baud rates above 9600), the micro:bit may drop characters being sent to it.

## HID and CMSIS-DAP

The HID endpoint is for a CMSIS-DAP channel. This can most easily be used [with pyOCD](https://github.com/mbedmicro/pyOCD), an open source python library for programming and debugging Arm Cortex-M microcontrollers using CMSIS-DAP

## WebUSB

The [WebUSB API](https://developers.google.com/web/updates/2016/03/access-usb-devices-on-the-web) facilitates communicating with USB devices from the Browser.

It has been supported in DAPLink since version **0247**, so if you have an older micro:bit, you will need to [update the DAPLink firmware](https://microbit.org/get-started/user-guide/firmware/).

The API is currently available in [Chrome based browsers](https://caniuse.com/#feat=webusb) (Android, Chrome OS, Linux, macOS and Windows) and is supported in the MakeCode Editor and the Python Editor. This enables you to flash your micro:bit straight from the browser without the need to save the .hex file first, and use serial communication between the micro:bit and the editor.

## Updating the DAPLink full image (V2.00 only)

<div class="alert alert-danger">Please note - there is almost no situation in the normal use of the micro:bit where this step will be necessary. We have documented it here in the interests of making the the micro:bit more friendly to developers who want to experiment with the code on the <span class="v2">V2.00</span> KL27 interface MCU. If your micro:bit enumerates in MAINTENANCE or MICROBIT mode you should never need to perform these steps.</div>

**Please only use use these steps if you are familiar with USB bootloaders and command line tools. You should never need to perform these to update a micro:bit.**

You can also flash a full DAPLink image to the <span class="v2">V2</span> device using the KL27 internal bootloader. This will update both interface and bootloader.

[Download latest full DAPLink image](/docs/software/assets/DAPLink-factory-release/kl27z_bl_0255_if_0255_microbit_full_image.bin){: .btn.sm-btn download}

You will need to register for and download the [**Bootloader Host Application (blhost)**](https://www.nxp.com/design/software/development-software/mcuxpresso-software-and-tools-/mcuboot-mcu-bootloader-for-nxp-microcontrollers:MCUBOOT?&tab=Design_Tools_Tab) from NXP. In the `/bin` folder you will find executables for your operating system.

<div class="alert alert-warning">Please ensure the nRF52 flash has been erased before erasing/flashing the KL27 flash. Programmes running on the nRF52 can affect the KL27 internal boot process and stop the kinetis bootloader from running. You can flash an <a href="/docs/software/assets/erase-flash.hex">erase-flash.hex</a> file to erase the nRF52.</div>

### Enter bootloader mode

To enter this mode we need to ground TP1 during board power up, this is the BOOTMODE pin in the KL27. To do that, connect with a wire (or something like a paper-clip) from TP1 (the red circle) with any ground point (any black square) as you insert the USB cable into the device.

![TP1](/docs/software/assets/TP1.png){: width: 300px}

### Bootloader CLI tool

Run the bootloader tool on your OS. These instructions relate to the CLI, but the GUI settings would be broadly similar.

Usage info:

```
blhost --help
```

The DAPLink software enables flash protection for the bootloader flash area, so we need to use erase command that also unsecures the flash:

```
blhost -u 0x15a2,0x0073 flash-erase-all-unsecure
```

Then unplug the micro:bit from the computer and plug it again, the KL27 should automatically enter the kinetis bootloader. To flash the bin file:

```
blhost -u 0x15a2,0x0073 write-memory 0x0 kl27_file.bin
```

To read KL27 flash contents into `kl27_flash_dump.bin` file:

```
blhost -u 0x15a2,0x0073 read-memory 0x0 0x40000 kl27_flash_dump.bin
```
