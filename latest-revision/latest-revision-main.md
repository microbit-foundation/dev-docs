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

{% include alert-info.html content="Any issues raised in the period prior to public announcement should be reported in **private**. <br><br> This means you should double check before posting anything on GitHub." %}
- **Software** issues can be raised in the relevant private GitHub repositories or via [micro:bit support](mailto:support@microbit.org?subject=Software%20issue)

- **Hardware** issues **must** be reported via [micro:bit support](mailto:support@microbit.org?subject=Hardware%20issue).

The **latest revision** of the BBC micro:bit, builds upon the current micro:bit experience by refining the board and adding widely requested sound sensing capabilities.

**Features**

- Microphone and LED indicator
- Speaker
- Logo touch

**Refinements**

- Notched edge connector. To make it easier to connect things like crocodile clips and conductive thread
- Power LED indicator. In addition to the USB activity indicator, a power LED shows whether the micro:bit is powered on or off
- Copper plated antenna. To easily identify the radio/Bluetooth component


## Guides

- [Guidance for editor developers](./editors/)

- [Guidance for accessory makers](./accessories/)

- [Guidance for content producers](./content/)


## Comparison

### Feature comparison
![Table of features](/docs/latest-revision/assets/comparison-table.png)

### Front
![Comparison front](/docs/latest-revision/comparison-front.png)

### Back
![Comparison back](/docs/latest-revision/comparison-back.png)

## How do I use the new features?

The **speaker** works in the same way you would expect when you connect up your headphones or an external speaker to the micro:bit. By default, the sound output will be on both the speaker and Edge connector. 
The **microphone** has an additional set of blocks in MakeCode and objects in MicroPython to use, so that you can monitor and record sound. 
The **logo touch** is implemented in the same way as touching a pin on the edge connector and will have equivalent blocks in MakeCode and objects in MicroPython to use.

To access the features of the latest revision only (eg. to output sound only on the speaker and not the edge connector), you will need to add additional code to your programs. This ensures that the default editor experience continues to work for everyone, regardless of the board revision.


## Using the latest micro:bit revision with the micro:bit editors

The editors and apps are compatible with and will let you download and flash a file to any micro:bit revision. This is called a  **Universal Hex** file. A clear indication that you are working with this format is that a compiled .hex file will be ~1.8Mb as opposed to ~700Kb in size.

 Features that are common to all board variants will work in the same way they always have. For example, you will be able to use the same blocks in MakeCode to use the acceleromater on any board revision.

### Makecode
You can use the latest board revision in the [alpha editor](https://makecode.microbit.org/stable)

[https://makecode.microbit.org/stable](https://makecode.microbit.org/stable) 

### Python
You can use the latest board revision in the Python beta editor:

https://python-editor-next-release-review.microbit.org/

### Bluetooth BLE 
A hex file that enables all micro:bit Bluetooth services is available to use for testing BLE. [Download the updated version of the BLE all services hex](/docs/latest-revision/assets/bluetooth-services.hex)

## Will my saved hex files work with the new board?

Yes, however you will need to update the files by dragging and dropping them into the software editor in which they were created.

If you attempt to use an old .Hex file without updating it, the micro:bit will display a compatibility error eg. `:( E029`

![Compatibility error](/docs/software/assets/compat-error.gif/)

## How do I get a device to test?

If you haven’t already received a device, but would like one in order to test/develop an accessory or editor please contact us at [support@microbit.org](mailto:support@microbit.org?subject=Request%20for%20the%20latest%20micro%3Abit&body=Name%3A%0D%0A%0D%0AAddress%3A%0D%0A%0D%0AContact%20number%3A)


## How do I find out more about the hardware and software updates?

Our [DAL, Devices and Editors mailing list](http://eepurl.com/dyRx-v) provides up to date information about the any technical changes regarding the micro:bit. 

Questions are welcome via support or through [issues raised on this repository](https://github.com/microbit-foundation/dev-docs-private/issues)

