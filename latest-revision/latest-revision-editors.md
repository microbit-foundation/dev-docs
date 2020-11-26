---
layout: page
title: Guidance on using the latest micro:bit revision
heading: micro:bit V2 - editors
description: Guidance on using the latest micro:bit revision, for editor developers
permalink: /latest-revision/editors/
ref: latest-revision-editors
lang: en
---

{% include alert-info.html content="This article is specifically for people who make editors for the micro:bit. Please also see our [general user information about the latest micro:bit revision](../)" %}

* TOC
{:toc}

Thanks for your continuing support of the micro:bit. There is a wonderful  breadth of [third party editors](https://microbit.org/code/#other-editors) available for the micro:bit that support different coding languages and learning scenarios. This article provides information to help you continue to support the 5 million existing micro:bits in the world and the latest board revision with the exciting new features of a speaker and microphone.

If you’d like to keep up to date with technical information about the device, please sign up to our [DAL, Devices and Editors mailing list](http://eepurl.com/dyRx-v) which provides information on hardware revisions, or key low-level software changes as early as possible.

----------

Please note that we do as much development as possible in the open, so if you’d like to be part of these processes you can join the relevant projects on GitHub:

- [Micro:bit Educational Foundation on GitHub](https://github.com/microbit-foundation)

- [microbit-dal](https://github.com/lancaster-university/microbit-dal)

- [CODAL](https://github.com/microbit-foundation/codal/)

- [microbit](https://github.com/lancaster-university/microbit)

- [MicroPython](https://github.com/bbcmicrobit/micropython)

- [MakeCode](https://github.com/Microsoft/pxt) for micro:bit [(pxt-microbit)](https://github.com/Microsoft/pxt-microbit)

Your tools are some of the most direct ways that users experience the micro:bit. We’ve done all we can to try and minimise the amount of work you will need to do in order to seamlessly support the new revision of the micro:bit and the old version in a single program.

## If you’re using the microbit DAL/Runtime

The most important change here is that the latest board revision runtime is based on [CODAL](https://lancaster-university.github.io/codal/) and no longer makes use of Arm Mbed.

| V2   | V1
| ---- | ---- 
|![Software Architectural Diagram V1](/docs/software/assets/software-overview-v2.svg) | ![Software Architectural Diagram V2](/docs/software/assets/software-overview.svg)

Mbed does not support the nRF52833 by default, though The Foundation does intend to publish a platform to enable this. The micro:bit editors do not use Mbed by default.

### Building CODAL

The [instructions for building CODAL](https://github.com/microbit-foundation/codal/blob/master/mb-build-instructions.md) are located in the micro:bit CODAL repository. The final link is TBC and may change.

## If you’re using MicroPython

Based on the current work in CODAL we've also worked with Damien George, the author of MicroPython, to build the changes into an updated release of MicroPython for the micro:bit.

The exisiting API has not changed. Scripts that use features that are common to all revisions will not be affected.

To support all revisions of the micro:bit, you will need to ensure you use the latest release of the MicroPython binary with your editor. The simplest way to do this is to flash a program created in the latest Python Editor which will contain the latest MicroPython build.

[https://python.microbit.org/](https://python.microbit.org/)

## If you’re using the micro:bit profile over BLE

The BLE Profile for the micro:bit has also been updated to ensure compatibility with both revisions of the board. We have published a binary that enables all BLE services available to the board and shows the connection status on the LED.

 [Download the updated version of the BLE all services hex](/docs/latest-revision/assets/bluetooth-services.hex)

The MakeCode Bluetooth package will  include all updates for the revised hardware and we will notify the DAL, Editors and Devices newsletter when this is available.

## Identifying which micro:bits you can support

If you write an editor that doesn’t have an online update mechanism, or is only periodically updated, we recommend that you use the board ID mechanism to list boards that your editor supports and notify users of any incompatibility issues. You can read the board ID as the first four characters of the device’s USB serial number.

### Table of board IDs

| micro:bit version | Board ID              |
| ----------------- | --------------------- |
| V1.3              | 9900                  |
| V1.5              | 9901                  |
| V2.0              | 9903 (reserved), 9904 |

For example, if you do not yet support the microphone on the latest board revision (board ID 9904), you can notify users of the compatibility issues within the editor, rather than failing silently and providing a program that does not work.

#### MicroPython

In the case of editors that use MicroPython, we propose the following approach which we introduced for the motion sensor update and believe still works.

If an unknown micro:bit version is detected, but that micro:bit already contains MicroPython at a newer version than the one the editor knows about use the serial port to flash just the python script to the [filesystem](https://bbcmicrobitmicropython.readthedocs.io/en/latest/filesystem.html)

This gives a teacher or facilitator who is unable to update their editors (for example due to IT restrictions), but who CAN update the base hex file on the micro:bit, the chance to quickly fix the problem while updating the editor in the background.

## Hex file compatibility

## Universal Hex files

The latest board revision introduces a superset of the Intel-Hex format that enables compatibility across processor variants. A Universal Hex is a file that contains the binary data for both micro:bit <span class="v1">V1</span> and micro:bit <span class="v2">V2</span>, in a format that the DAPLink can process to only write to memory the data relevant to its micro:bit board.

A **Universal Hex** hex file will work on a V1 or V2 board.
A clear indication that you are working with this format is that a compiled .hex file will be ~1.8Mb as opposed to ~700Kb in size.

We have developed a [Universal Hex Creator](../../software/universal-hex-creator) tool, to easily create a .hex file that will support all micro:bit variants.

This tool is based on a [Universal Hex JavaScript Library](https://github.com/microbit-foundation/microbit-universal-hex), written to implement the format and associated detailed [specification of the Universal Hex format](https://github.com/microbit-foundation/spec-universal-hex).

### Hex format compatibility

The Universal Hex format has been developed to ensure the best experience for users when moving between board variants. There may be cases where it is not possible to support both boards, for example an accessory that is designed only to target the V2 board variant. In these cases, to ensure the best user experience when flashing a hex file to any board variant, the file should always include an error message to signify board incompatibility to the user. If we do not do this, it results in a silent failure, which can be very confusing to users.

We have created a [standalone error hex](/docs/software/assets/stand-alone-error-v1.hex) that can be combined with a V2 only hex to produce a Hex that will work on a V2 board, but error if used on a V1.You can read more about how this works on the [Hex format](../../software/hex-format/) page.
