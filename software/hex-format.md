---
layout: page
order:
title: .HEX file format
heading: .HEX file format
description: What is the format of the .hex file created by the micro:bit editors?
permalink: /software/hex-format/
ref: software
lang: en
assigned-to: jonnya
review-with: davidw
---

The .hex file is in intel-hex format. You can learn more about that format <a href="https://en.wikipedia.org/wiki/Intel_HEX">here</a>. Intel hex consists of records of data, with the address in memory to store the data at the start. All data is hex-ascii encoded. All lines start with a : character. All lines end with a checksum byte that can be used to verify the integrity of the data.

A micro:bit .hex file usually starts writing data to the same fixed location in memory, so (at the moment at least) we would expect the first line of the file to start like this:

:020000040000FA

## Micropython

MicroPython builds take a firmware.hex image (the MicroPython pre-compiled image) and append your script to the end of it, in a fixed 8K region at a known address. When MicroPythons starts to run on the micro:bit, it looks for a signature at this fixed location, and uses that to determine whether to run the script, or drop directly to the REPL prompt.

<a href="https://github.com/bbcmicrobit/PythonEditor/blob/1df10c07a271d9597eac318aef2e5dc1259af24a/python-main.js#L68">This page</a> in the PythonEditor shows how this is done:
```javascript
    /*
    Turn a Python script into Intel HEX format to be concatenated at the
    end of the MicroPython firmware.hex.  A simple header is added to the
    script.
    - takes a Python script as a string
    - returns hexlified string, with newlines between lines
    */
    editor.hexlify = function(script) {
        function hexlify(ar) {
            var result = '';
            for (var i = 0; i < ar.length; ++i) {
                if (ar[i] < 16) {
                    result += '0';
                }
                result += ar[i].toString(16);
            }
            return result;
        }
        // add header, pad to multiple of 16 bytes
        data = new Uint8Array(4 + script.length + (16 - (4 + script.length) % 16));
        data[0] = 77; // 'M'
        data[1] = 80; // 'P'
        data[2] = script.length & 0xff;
        data[3] = (script.length >> 8) & 0xff;
        for (var i = 0; i < script.length; ++i) {
            data[4 + i] = script.charCodeAt(i);
        }
        // check data.length < 0x2000
        if(data.length > 8192) {
            throw new RangeError('Too long');
        }
        // convert to .hex format
        var addr = 0x3e000; // magic start address in flash
```

At address 0x3E000, you should see the MicroPython signature which is ASCII 'MP' followed by two bytes indicating the length of the script. These bytes are stored in little-endian format (low byte then high byte)

## TouchDevelop, Blocks and CodeKingdoms and PXT

All of these editors on the www.microbit.co.uk/app website, and also pxt.microbit.org have embedded meta-data inside the .hex file. This is a JSON encoded blob with various data about the script, and also the source code program. This may be compressed, and it is stored inside the flash memory of the micro:bit (but only if space is available in the flash memory). But it is always inside the .hex file. This embedded source code program ensures that when you drag and drop the .hex file onto the originating editor, it can recover the source program again.

This is documented in the pxt docs here: https://github.com/Microsoft/pxt/blob/437f53ca6311335c7f3f75a062ec1079b4e7806a/docs/source-embedding.md

## Links
[1] Intel Hex format: https://en.wikipedia.org/wiki/Intel_HEX

[2] MicroPython hexlify code: 

https://github.com/bbcmicrobit/PythonEditor/blob/1df10c07a271d9597eac318aef2e5dc1259af24a/python-main.js#L68

[3] embedded JSON format:

https://github.com/Microsoft/pxt/blob/437f53ca6311335c7f3f75a062ec1079b4e7806a/docs/source-embedding.md
