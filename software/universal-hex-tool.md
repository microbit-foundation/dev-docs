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

DAPLink will process the Universal Hex and only write data to the relevant board revision; V1 or V2. More information is available on our [Hex format](../hex-format), the [Javascript/Typescript libary](https://github.com/microbit-foundation/microbit-universal-hex) on which the Universal Hex Creator tool is based and the associated [Universal Hex specification](https://github.com/microbit-foundation/spec-universal-hex).

To support [cross-device compatibility](../hex-format/#cross-device-compatibility), we have created a [standalone error hex](/docs/software/assets/stand-alone-error-v1.hex) that can be combined with a V2 only hex in this tool to produce a Hex that will work on a V2 board, but error if used on a V1.

[Download standalone error hex](/docs/software/assets/stand-alone-error-v1.hex){: .btn.sm-btn download}

{% include uhex-tool.html %}