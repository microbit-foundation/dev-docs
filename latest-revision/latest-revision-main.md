---
layout: page
title: Guidance on using the latest micro:bit revision
heading: micro:bit V2
description: Details of the V2.0 micro:bit revision
permalink: /latest-revision/
ref: latest-revision
lang: en
---
## Overview

* TOC
{:toc}

The [**latest revision**](./announcement/) of the BBC micro:bit is designed to be completely familiar to anyone who has used the original device. It’s the same size, shape, looks very similar, and works in the same way. Every programme that could run on a micro:bit version 1 can be re-built to run on the latest revision.

The editors will support both versions simultaneously for features common to both boards,for example the motion sensor, LEDs, buttons etc.

The latest revision builds upon the current micro:bit experience by refining the board and adding widely requested sound making and sensing capabilities.

Amongst the micro:bit features, ‘sound’ is in a unique position of being already present in the editors, but not on the board, so it is already familiar to teachers, yet the speaker and microphone on the board are transformative in the kinds of applications people can build.

### Features

- On board speaker
- MEMs Microphone with LED indicator
- Touch sensitive logo
- Built-in sleep/off mode that means the board can be powered-down with batteries connected
- Discrete regulator that can supply up to 190mA of current to external accessories

### Refinements

- Notched edge connector. To make it easier to connect things like crocodile clips and conductive thread
- Power LED indicator. In addition to the USB activity indicator, a power LED shows whether the micro:bit is powered on or off
- Gold plated antenna. To easily identify the radio/Bluetooth component

### Hardware specification

Detailed breakdown on our [V2 hardware page](../hardware/)

- Target MCU, Nordic Semiconductor nRF52833 (64MHz Cortex-M4F, 512kB Flash, 128kB RAM)
- Interface MCU: NXP KL27, 256kB Flash (128kB reserved for future enhancement), 32kB RAM
- Motion sensor: ST LSM303
- MEMS microphone: Knowles SPU0410LR5H-QB-7 MEMS
- Power consumption 300mA (up to 190mA for accessories)

### Hardware block diagram

![V2 block](/docs/hardware/assets/v2-block.svg)

## Guides

These pages provide further guidance on the updates for different audiences.

### [Guidance for editor developers](./editors/)

### [Guidance for accessory makers](./accessories/)

### [Guidance for content producers](./content/)

## Comparison

### Feature comparison

![Table of features](/docs/latest-revision/assets/comparison-table.png)

### Front

![Comparison front](/docs/latest-revision/assets/comparison-front.png)

### Back

![Comparison back](/docs/latest-revision/assets/comparison-back.png)

## Universal Editors & Universal Hex Files

In an effort to ensure the greatest degree of continuity for teachers, users will not need to select which version of the device they have before using MakeCode or the Python Editor. Instead, the editors will support a new format called “universal hex” which can run on both micro:bit V1 and micro:bit V2 (more below)

This means that you can use MakeCode or the online Python Editor as you always have, to use all of the features that are common to both version of the BBC micro:bit: Display, buttons, motion sensing, gestures like shake, light sensing, and even the Music blocks.

## How do I use the new features?

The **speaker** works in the same way you would expect when you connect up your headphones or an external speaker to the micro:bit. By default, the sound output will be on both the speaker and Edge connector.
The **microphone** will have an additional set of blocks in MakeCode and objects in MicroPython to use, so that you can monitor and respond to sound.
The **logo touch** is implemented in the same way as touching a pin on the edge connector and will have equivalent blocks in MakeCode and objects in MicroPython to use. Note that Logo touch is capacitive touch by default and the edge pins are resistive.

To access the features of the latest revision only (eg. to output sound only on the speaker and not the edge connector), you will need to add additional code to your programs. This ensures that the default editor experience continues to work for everyone, regardless of the board revision.

Features that are common to all board variants will work in the same way they always have. For example, you will be able to use the same blocks in MakeCode to use the accelerometer on any board revision.

### Makecode
You can use the latest board revision in the live micro:bit editor [https://makecode.microbit.org](https://makecode.microbit.org) alongside the current revision. 

#### Using the new features in MakeCode

The Microphone and Logo touch features can be found in the Input menu

The Speaker features can be found in the Music menu

The Capacative/Resistive touch mode can be found in the Pins menu

### Python

You can use the latest board revision and APIs in the Python editor:

 [https://python.microbit.org/](https://python.microbit.org/)

 If you want to use a specific or custom build of MicroPython you can do this in [Mu](https://codewith.mu/).

 1. Drag and drop the MicroPython binary on to the `MICROBIT` drive
 2. Open the **Files** tab in Mu and copy `main.py` from the Files on your computer to the Files on your micro:bit

![Copy main.py](/docs/latest-revision/assets/copy-main-py-mu.gif){: width="600"}

#### Using the new features in Python

We are currently working on updates to MicroPython documentation, but you can find Python APIs by searching via the REPL for example:

```Python
import microbit
dir(microbit)
```
### Python APIs

| API                                        | Usage        |
|--------------------------------------------|--------------|
| play sound expression (giggle, happy, hello, mysterious, sad, slide, soaring, spring, twinkle, yawn) | `audio.play("hello")`|
| Choose music/pitch output pin | `music.play(music.JUMP_UP, pin=microbit.pin_speaker, wait=True)` |          
| Stop music on pin             | `music.stop(pin=microbit.pin_speaker)` |
| Set the volume 0-255          | `microbit.set_volume(128)` |
| Get current sound loud/quiet  |`microbit.microphone.current_sound()` |
| Check current sound == loud/quiet | `microbit.microphone.current_sound() == microbit.microphone.LOUD` |
| Check if a loud/quiet sound occurred since the last call to was_sound() | `microbit.microphone.was_sound(microbit.microphone.LOUD)` |
| Get history of sounds since last call to get_sounds() | `microbit.microphone.get_sounds()` |
| Set threshold for sound 0-255 | `microbit.microphone.set_threshold(microbit.microphone.LOUD, 128)` |
| Get current sound level in range 0-255 | `microbit.microphone.sound_level()` |
| Logo is touched | `microbit.pin_logo.is_touched()` |

## Universal Hex Format

The editors and apps are compatible with and will let you download and flash a file to any micro:bit revision. This is called a  **Universal Hex** file. A clear indication that you are working with this format is that a compiled .hex file will be ~1.8Mb as opposed to ~700Kb in size.

More information about this is available on our [hex format](../software/hex-format/#universal-hex-files) page

The Foundation has written a javascript library and [Universal Hex Creator](../software/universal-hex-creator) to generate these files - you do not need to re-implement any file generation.

### Bluetooth BLE

A hex file that enables all micro:bit Bluetooth services is available to use for testing BLE. [Download the updated version of the BLE all services hex](/docs/latest-revision/assets/bluetooth-services.hex)

## Will my saved hex files work with the new board?

Yes, however you will need to update the files by dragging and dropping them into the software editor in which they were created.

If you attempt to use an old .hex file without updating it, the micro:bit will display a compatibility error eg. `:( 529`

![Compatibility error](/docs/software/assets/compat-error.gif)

## How do I get a device to test?

If you haven’t already received a device, but would like one in order to test/develop an accessory or editor please contact us at [support@microbit.org](mailto:support@microbit.org?subject=Request%20for%20the%20latest%20micro%3Abit&body=Name%3A%0D%0A%0D%0AAddress%3A%0D%0A%0D%0AContact%20number%3A)

## How do I update the firmware for the latest micro:bit?
The latest micro:bit will ship with the latest DAPLink firmware at version 0255. If you have been testing the latest board or need to re-flash the firmware, it is linked here, but you can also find details about this on our [DAPLink](../software/daplink-interface/) page.

[Download 0255 firmware for V2](https://cdn.sanity.io/files/ajwvhvgo/production/2cfe581e01f533513276485375adec3f00153af5.hex?dl){: .btn.sm-btn download}

## How do I find out more about the hardware and software updates?

Our [DAL, Devices and Editors mailing list](http://eepurl.com/dyRx-v) provides up to date information about the any technical changes regarding the micro:bit.

## How do I feed back or raise issues?

Any questions or issues should be reported via [micro:bit support](https://support.microbit.org/support/tickets/new).

You can also report issues on the relevant Github Repositories.
