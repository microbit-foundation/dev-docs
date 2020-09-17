---
layout: page
title: Guidance on using the latest micro:bit revision
heading: micro:bit v2
description: Details of the 2.0 micro:bit revision
permalink: /latest-revision/
ref: latest-revision
lang: en
---
## Overview

{% include alert-info.html content="Any issues raised in the period prior to public announcement should be reported in **private**. This means you should double check before posting anything on GitHub.<br><br>

There's lots of opportunity for collaboration on the software sides, and the software work has lots of partners covering issues in different areas - so please raise **software and documentation** issues in our [microbit-issues GitHub repository](https://github.com/microbit-foundation/microbit-issues) If you'd like to raise issues privately, you're welcome to contact [micro:bit support.](mailto:support@microbit.org?subject=Software%20issue)<br><br>

For **hardware** issues, of which we hope there are precious few, please contact The Foundation directly via [micro:bit support](mailto:support@microbit.org?subject=Hardware%20issue) so we can track and triage appropriately." %}

* TOC
{:toc}

The **latest revision** of the BBC micro:bit is designed to be completely familiar to anyone who has used the original device. It’s the same size, shape, looks very similar, and works in the same way. Every programme that could run on a micro:bit version 1 can be re-built to run on the latest revision.  The editors will support both versions simultaneously for features common to both boards.

The latest revision builds upon the current micro:bit experience by refining the board and adding widely requested sound making and sensing capabilities.

Amongst the micro:bit features, ‘sound’ is in a unique position of being already present in the editors, but not on the board, so it is already familiar to teachers, yet the speaker and microphone on the board are transformative in the kinds of applications people can build.


### Features

- On board speaker
- MEMs Microphone with LED indicator
- Touch sensitive logo 
- Built-in sleep/off mode that means the board can be powered-down with batteries connected
- Discrete regulator that can supply up to 200mA of current to external accessories


### Refinements

- Notched edge connector. To make it easier to connect things like crocodile clips and conductive thread
- Power LED indicator. In addition to the USB activity indicator, a power LED shows whether the micro:bit is powered on or off
- Gold plated antenna. To easily identify the radio/Bluetooth component


## Hardware specification

Detailed breakdown on our [v2 hardware page](../hardware/)

- Target MCU, Nordic Semiconductor nRF52833 (64MHz Cortex-M4F, 512kB Flash, 128kB RAM)
- Interface MCU: NXP KL27Z, 256kB Flash (128kB reserved for future enhancement), 32kB RAM
- Motion sensor: ST LSM303
- MEMS microphone: Knowles SPU0410LR5H-QB-7 MEMS
- Power consumption 300mA (up to 200mA for accessories)


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

In an effort to ensure the greatest degree of continuity for teachers, users will not need to select which version of the device they have before using MakeCode or the Python Editor. Instead, the editors will suport a new format called “universal hex” which can run on both micro:bit V1 and micro:bit V2 (more below)

This means that you can use MakeCode or the online Python Editor as you always have, to use all of the features that are common to both version of the BBC micro:bit: Display, buttons, motion sensing, gestures like shake, light sensing, and even the Music blocks.


## Feature availability

| **Feature**      | **CODAL** | **MakeCode** | **MakeCode Sim.** | **MicroPython** |
| ---------------- | --------- | ------------ | ----------------- | --------------- |
| Microphone       | ✅         | ✅            | 🛑               | ✅               |
| Speaker          | ✅         | ✅            | 🛑               | ✅               |
| Logo touch       | ✅         | ✅            | 🛑               | ✅               |
| Power Management | ✅         | 🛑            | 🛑               | 🛑               |

## How do I use the new features?

The **speaker** works in the same way you would expect when you connect up your headphones or an external speaker to the micro:bit. By default, the sound output will be on both the speaker and Edge connector. 
The **microphone** has an additional set of blocks in MakeCode and objects in MicroPython to use, so that you can monitor and record sound. 
The **logo touch** is implemented in the same way as touching a pin on the edge connector and will have equivalent blocks in MakeCode and objects in MicroPython to use.

To access the features of the latest revision only (eg. to output sound only on the speaker and not the edge connector), you will need to add additional code to your programs. This ensures that the default editor experience continues to work for everyone, regardless of the board revision.

Features that are common to all board variants will work in the same way they always have. For example, you will be able to use the same blocks in MakeCode to use the acceleromater on any board revision.


### Makecode
You can use the latest board revision in the beta editor [https://makecode.microbit.org/stable](https://makecode.microbit.org/stable)

**Using the new features in MakeCode**


An extension has been developed to include the microphone and logo touch features currently available. [https://github.com/frumplecoin/demo-extension](https://github.com/frumplecoin/demo-extension) ← *Please do not share any links to this extension or make any public statements about this that could link it to micro:bit*


1. Open [https://makecode.microbit.org/stable](https://makecode.microbit.org/stable)
2. Select Advanced > Add Extension and paste [https://github.com/frumplecoin/demo-extension](https://github.com/frumplecoin/demo-extension) into the search box. 
3. Click on the extension to add it to the toolbox.

**v2 MakeCode APIs**
The Microphone and Logo touch features can be found in the Input menu

- On loud/quiet sound `input.onSound(SoundType.Loud)`
- On Logo pressed `input.onLogoPressed`
- On logo released `input.onLogoReleased`
- Logo is pressed `input.logoIsPressed`
- soundlevel  `input.soundLevel` returns the current soundlevel
- Set loud/quiet sound threshold to 0-255 `input.setSoundThreshold(SoundType.Loud, 128)`

The Speaker features can be found int the music menu

- volume `music.volume` returns the current volume
- on-board speaker enable true/false `music.setOnBoardSpeakerEnable(false)`

### Python
You can use the latest board revision in the Python beta editor:
 https://python-editor-next-release-review.microbit.org/
 
**Using the new features in the Python Editor**

**v2 Python APIs**

- `music.play(music.JUMP_UP, pin=microbit.pin_speaker, wait=True)` - Choose where to output sound (works with pitch, too)
- `music.stop(pin=microbit.pin_speaker)`
- `microbit.microphone.current_sound()`
- `microbit.microphone.current_sound() == microbit.microphone.LOUD` - also `microbit.microphone.QUIET`
- `microbit.microphone.was_sound(microbit.microphone.LOUD)` - If a sound occured since you last checked
- `microbit.microphone.get_sounds()` - history of sounds since last call to get_sounds() - nice way to count claps
- `microbit.pin_logo.is_touched()`  Normal pin object with only is_touched() to avoid confusion.


## Universal Hex Format

The editors and apps are compatible with and will let you download and flash a file to any micro:bit revision. This is called a  **Universal Hex** file. A clear indication that you are working with this format is that a compiled .hex file will be ~1.8Mb as opposed to ~700Kb in size.

More information about this is available on our [hex format](../software/hex-format/#universal-hex-files) page

The Foundation has written a javascript library to generate these files - you do not need to re-implement any file generation. This is currently in a private GitHub repository but access can be granted by request.


### Bluetooth BLE 
A hex file that enables all micro:bit Bluetooth services is available to use for testing BLE. [Download the updated version of the BLE all services hex](/docs/latest-revision/assets/bluetooth-services.hex)


## Will my saved hex files work with the new board?

Yes, however you will need to update the files by dragging and dropping them into the software editor in which they were created.

If you attempt to use an old .Hex file without updating it, the micro:bit will display a compatibility error eg. `:( E029`

![Compatibility error](/docs/software/assets/compat-error.gif)


## How do I get a device to test?

If you haven’t already received a device, but would like one in order to test/develop an accessory or editor please contact us at [support@microbit.org](mailto:support@microbit.org?subject=Request%20for%20the%20latest%20micro%3Abit&body=Name%3A%0D%0A%0D%0AAddress%3A%0D%0A%0D%0AContact%20number%3A)


## How do I find out more about the hardware and software updates?

Our [DAL, Devices and Editors mailing list](http://eepurl.com/dyRx-v) provides up to date information about the any technical changes regarding the micro:bit.  Until the latest revision of the micro:bit is public, we will email you with key updates..


## How do I feed back or raise issues?

Any issues raised in the period prior to public announcement should be reported in **private**. This means you should double check before posting anything on GitHub.

**Software** issues can be raised in our [microbit-issues GitHub repository](https://github.com/microbit-foundation/microbit-issues) or via [micro:bit support](mailto:support@microbit.org?subject=Software%20issue).
**Hardware** questions or issues should be reported via [micro:bit support](mailto:support@microbit.org?subject=Hardware%20issue).