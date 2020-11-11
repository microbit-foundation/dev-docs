---
layout: page
title: Universal Hex Creator
heading: Universal Hex Creator
description: Create a Universal Hex file
permalink: /software/universal-hex-creator/
ref: universal-hex-tool
lang: en
assigned-to: markw
review-with: carlospa
---

The Universal Hex Creator lets you combine a hex file created for a micro:bit V1 device and a hex file created for a V2 device, resulting in a Universal Hex format that is compatible with all revisions of the micro:bit.

DAPLink will process the Universal Hex and only write data to the relevant board revision; V1 or V2. More information is available on our [Hex format](../hex-format) page and the [Javascript/Typescript libary](https://github.com/microbit-foundation/microbit-universal-hex) on which the Universal Hex Creator tool is based.

{% include uhex-tool.html %}