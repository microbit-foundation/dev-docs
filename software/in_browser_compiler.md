---
layout: page
order:
title: In Browser Compilers
heading: In Browser Compilers
description: The in-browser compilers allow you to compile code even when not connected to the internet.
permalink: /software/in_browser_compiler/
ref: software
lang: en
assigned-to: davidw
review-with: jonnya
---


# Overview

There are a number of different code editors for the micro:bit.
Of the available editors, Blocks, Touch Develop and Code Kindgoms and PXT have an
in-browser compiler. This means that when you hit the 'compile' button
to translate your code into a language supported by the micro:bit, all of the
hard work takes place inside your web browser.

MicroPython has an online web editor version, but it doesn't use an in-browser compiler.
You can also use MicroPython offline by installing the Mu editor on your computer.

The in-browser build process is useful, because you are not dependent
on an internet connection in order to code and innovate with your
micro:bit - once you have the web page open and the editor is cached
on your computer, you can work independently of internet access.

By being web based, these editors allow you to write code for the
micro:bit without needing to install any special software on your
computer, which is especially important if working in a previously
unused classroom, or on a public computer.

PXT will be the foundations official editor, and this can be found at
[PXT editor](http://pxt.microbit.org). It is currently released as a beta
version.


# How it Works

![img](/docs/software/assets/browser-build-pipeline.png)

The above diagram shows an example of how blocks code is converted into a
.hex file that can be loaded onto your micro:bit

1a. Edit your script; this is automatically saved inside the web browser cache on your
computer.

1b. Press the COMPILE button, and this blocks script is first
converted into touch develop code (for the microbit.co.uk editors) or javascript.
The in-browser-compiler then converts it into ARM machine code instructions.

1c. The ARM machine code instructions are 'linked' with the Lancaster University
runtime code [The DAL](/software/runtime-mbed) and converted into an Intel-HEX file
format. This is done by ensuring that the in-browser-compiler knows the entry points
of key functions that it needs to be able to call out into.

2. You accept the download of the .hex file, which is stored in the filing system
on your computer.

3. Drag and drop the .hex file onto the MICROBIT drive, and the interface
processor on the micro:bit copies it into the flash memory inside the application
processor. Your code now runs.

Because code is compiled in-browser, the compiler needs to have a copy of
the runtime/DAL code in order to create a complete distributable package.
There is a pre-compiled copy of the runtime (DAL+mbed) that gets loaded
when you first load the editor.


# Other Features

PXT supports two-way conversion of code, so you can write code in the visual blocks and
see what the generated code looks like. You can also write code, and if
possible, PXT will convert this back into blocks automatically.

Because PXT uses the same underlying format as Touch Develop, it means
that you can import scripts written in Touch Develop, Blocks and Code
Kingdoms, and they will be converted into PXT visual blocks.

PXT also allows you to write your own block types and publish them
as packages, read about it here: [PXT Packages](https://www.pxt.io/packages)

Touch Develop has a built in ARM assembler - it is possible to write
ARM assembly language directly in your code, and this will be included
in the final binary image. The NeoPixel library is an example
of where the Touch Develop assembler has been used to good effect
[TD NeoPixel Library](http://www.microbit.co.uk/taxtmq). The timing
requirements for driving NeoPixels are very critical, and this ARM
assembly code controls the GPIO pin of the micro:bit very quickly
within the necessary timing restrictions.

The Python web editor does not use the in-browser compiler. It only
sits inside the frame of the website, but it gains access to the
save and import functionality for saving and loading scripts
to local files, and to and from a cloud store.

Read more about how MicroPython works: [MicroPython on micro:bit](./micropython)


# Contributions

The PXT editor is open source. You can log issues with the dev team here:
[PXT issues](https://github.com/Microsoft/pxt-microbit/issues/new)

Why not take part, and add your own features to the PXT editor?
Here is the source code for the whole site:

[PXT source code](https://github.com/Microsoft/pxt-microbit)


# Links

[The Microsoft Offering](https://www.microsoft.com/en-us/research/project/the-bbc-microbit-and-microsoft/)

[Touch Develop](https://github.com/Microsoft/microbit-touchdevelop)

[Design of the in-browser compiler](https://www.touchdevelop.com/docs/touch-develop-in-208-bits)

[PXT](https://github.com/Microsoft/pxt-microbit)

[TypeScript](https://github.com/Microsoft/TypeScript)
