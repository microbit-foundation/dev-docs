---
layout: page
order:
title: In Browser Compilers
heading: In Browser Compilers
description: The in-browser compilers allow you to compile code even when not connected to the internet.
permalink: /software/in_browser_compiler/
ref: software
lang: en
---


# Overview

There are a number of different code editors for the micro:bit.
Of the available editors; [MakeCode](https://makecode.microbit.org) and [Python](https://python.microbit.org) have an
in-browser compiler. This means that when you hit the **Download** button
to translate your code into a language supported by the micro:bit, all of the
hard work takes place inside your web browser.

You can also use MicroPython offline by installing the [Mu editor](https://codewith.mu) on your computer.

The in-browser build process is useful, because you are not dependent
on an internet connection in order to code and innovate with your
micro:bit - once you have the web page open and the editor is cached
on your computer, you can work independently of internet access.

By being web based, these editors allow you to write code for the
micro:bit without needing to install any special software on your
computer, which is especially important if working in a previously
unused classroom, or on a public computer.

# How it Works

![img](/docs/software/assets/browser-build-pipeline.png)

The above diagram shows an example of how blocks code is converted into a
.hex file that can be loaded onto your micro:bit

1a. Edit your script; this is automatically saved inside the web browser cache on your
computer.

1b. Press the **Download** button, and the script is first
converted into javascript. The in-browser-compiler then converts it into ARM machine code instructions.

1c. The ARM machine code instructions are 'linked' with the Lancaster University
runtime code, [the DAL](/software/runtime-mbed) and converted into an [Intel-HEX file
format](/software/hex-format.md). This is done by ensuring that the in-browser-compiler knows the entry points
of key functions that it needs to be able to call out into.

2. You accept the download of the .hex file, which is stored in the filing system
on your computer.

3. Download/Flash the .hex file onto the MICROBIT drive, and the interface
processor on the micro:bit copies it into the flash memory inside the application
processor. Your code now runs.

Because code is compiled in-browser, the compiler needs to have a copy of
the runtime/DAL code in order to create a complete distributable package.
There is a pre-compiled copy of the runtime (DAL+mbed) that gets loaded
when you first load the editor.


# Other Features

MakeCode supports two-way conversion of code, so you can write code as blocks and
see what the generated code looks like in Javascript. You can also write Javascript code, and if
possible, MakeCode will convert this back into blocks automatically.

Makecode also allows you to [write your own block types](https://makecode.com/extensions) and [publish them as Extensions](https://makecode.microbit.org/extensions).

The Python web editor does not use the in-browser compiler. It only
sits inside the frame of the website, but it gains access to the
save and import functionality for saving and loading scripts
to local files, and to and from a cloud store.

Read more about how MicroPython works: [MicroPython on micro:bit](/software/micropython)


# Contributions

The MakeCode editor is [open source](https://github.com/Microsoft/pxt-microbit), so you can develop your own feature and you can [log issues](https://github.com/Microsoft/PXT-microbit/issues/new) for the dev team to look into.

