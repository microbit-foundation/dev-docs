---
title: Universal Hex creator
description: Create a Universal Hex file
slug: /firmware/universal-hex-creator/
---

The Universal Hex Creator lets you combine a hex file created for a micro:bit V1 device and a hex file created for a V2 device, resulting in a Universal Hex file that is compatible with all revisions of the micro:bit.

DAPLink will process the Universal Hex and only write data to the relevant board revision; V1 or V2. More information is available on our [Hex format](/firmware/hex-format/), the [Javascript/Typescript library](https://github.com/microbit-foundation/microbit-universal-hex) on which the Universal Hex Creator tool is based and the associated [Universal Hex specification](https://github.com/microbit-foundation/spec-universal-hex).

This complementary online tool can be used to split Universal Hex files into its individual Intel HEX components: [Universal Hex Splitter](https://microbit-foundation.github.io/microbit-universal-hex/examples/separate.html)

To support [cross-device compatibility](/firmware/hex-format/#cross-device-compatibility), we have created a [standalone error hex](https://github.com/microbit-foundation/incompatible-error-programme/releases/download/v1.0.0/error-programme-v1.hex) that can be combined with a V2 only hex in this tool to produce a Universal Hex that will work on a V2 board, and display a "not compatible" error if used on a V1.

<a href="https://github.com/microbit-foundation/incompatible-error-programme/releases/download/v1.0.0/error-programme-v1.hex" class="btn btn-cta" download>Download standalone error hex</a>

<iframe src="https://microbit-foundation.github.io/microbit-universal-hex/examples/webtool.html" title="Universal Hex creator tool" id="uhex-tool" style="border:0; width:100%; height:985px; margin-top:2rem"></iframe>
