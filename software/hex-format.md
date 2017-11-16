---
layout: page
order:
title: .HEX file format
heading: .HEX file format
description: What is the format of the .hex file created by the micro:bit editors?
permalink: /software/hex-format/
ref: hex-format
lang: en
assigned-to: jonnya
review-with: davidw
---

The .hex file is in intel-hex format. You can learn more about that format [here](https://en.wikipedia.org/wiki/Intel_HEX). Intel hex consists of records of data, with the address in memory to store the data at the start. All data is hex-ascii encoded. All lines start with a : character. All lines end with a checksum byte that can be used to verify the integrity of the data.

A micro:bit .hex file usually starts writing data to the same fixed location in memory, so (at the moment at least) we would expect the first line of the file to start like this:

:020000040000FA

## Micropython

MicroPython builds take a firmware.hex image (the MicroPython pre-compiled image) and appends your script to the end of it, in a fixed 8K region at a known address. When MicroPythons starts to run on the micro:bit, it looks for a signature at this fixed location, and uses that to determine whether to run the script, or drop directly to the REPL prompt.

[This page](https://github.com/bbcmicrobit/PythonEditor/blob/1df10c07a271d9597eac318aef2e5dc1259af24a/python-main.js#L68) in the PythonEditor shows how this is done:

At address 0x3E000, you should see the MicroPython signature which is ASCII 'MP' followed by two bytes indicating the length of the script. These bytes are stored in little-endian format (low byte then high byte)

## TouchDevelop, Blocks and CodeKingdoms and PXT

All of these editors on the www.microbit.co.uk/app website, and also pxt.microbit.org have embedded meta-data inside the .hex file. This is a JSON encoded blob with various data about the script, and also the source code program. This may be compressed, and it is stored inside the flash memory of the micro:bit (but only if space is available in the flash memory). But it is always inside the .hex file. This embedded source code program ensures that when you drag and drop the .hex file onto the originating editor, it can recover the source program again.

This is documented in the pxt docs here: https://github.com/Microsoft/pxt/blob/437f53ca6311335c7f3f75a062ec1079b4e7806a/docs/source-embedding.md

## Links

[1] Intel Hex format: <https://en.wikipedia.org/wiki/Intel_HEX>
[2] MicroPython hexlify code: <https://github.com/bbcmicrobit/PythonEditor/blob/1df10c07a271d9597eac318aef2e5dc1259af24a/python-main.js#L68>
[3] embedded JSON format: <https://github.com/Microsoft/pxt/blob/437f53ca6311335c7f3f75a062ec1079b4e7806a/docs/source-embedding.md>
