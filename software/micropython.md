---
layout: page
order:
title: Python on the micro:bit
heading: Micro Python
description: Micro Python is one of the offline editors available for use with the micro:bit
permalink: /software/micropython/
ref: software
lang: en
assigned-to: davidw
review-with: nicholast
---


# Overview

MicroPython is a version of the popular Python programming language for
devices like the micro:bit. It's free software: creating, maintaining and
documenting MicroPython is the work of an international team of
volunteers.

There are four ways to use MicroPython on the micro:bit.

1. Use the browser based editor on the microbit.org website (the original editor at microbit.co.uk still exists but is very out of date).
2. Use the beginner friendly editor called Mu (it works on Windows, Mac OSX,
Linux and Raspberry Pi).
3. If you're on a ChromeBook use the MicroPython application found on the Google
Play store.
4. Use your regular editor to create Python files and a suite of command line
tools to interact with the device (for advanced users only).

# Getting Started

MicroPython on the micro:bit is easy.

If you want a no-install experience, start with the
[browser based editor](http://python.microbit.org/)

It's perfect if you don't have control over the setup of your computer (for
example, you're in a classroom you don't normally teach in, or have a shared
laptop). Alternatively, download a zipped up version of the editor and
launch it from your local file system. This is still something experimental,
so if you have any issues with it please [report issues](https://github.com/bbcmicrobit/PythonEditor/issues). If you'd like to try that, please use this file:

* [Python 'web' editor for offline use, v0.1](/software/assets/python-editor-mbf0.1.zip)

Write code in the web editor, press the `Download` button and drag the
resulting `.hex` file onto your micro:bit.

Use the "Snippets" button to easily re-use common blocks of code in your own
program. This saves on typing! If you're not running the editor from your local
file system, use the "Share" button to create a link to retrieve your code. Let
others see your work by sharing the link on social media. A blocks based
interface and micro:bit emulator are coming soon!

The most powerful yet easy to use editor is [Mu](http://codewith.mu/). It comes
as a pre-built package: just download it and run!

Mu has lots of powerful features: easily flash your code onto the device at the
touch of a button, move files to and from the device, code quality checks, code
completion, call tips and the facility to connect to the device for
live interactive coding (the famous REPL - it's like talking in code to your
micro:bit because it **R**eads [your code], **E**valuates [it], **P**rints [any results]
and **L**oops [back for the next instruction]). If you have a choice of editor,
choose this one.

The ChromeBook based editor is a version of the browser based editor but with
the addition of a REPL similar to Mu's for live interactive coding.

Those of you who already have a favourite code editor can continue to use it in
conjunction with command line tools like
[uflash](https://uflash.readthedocs.io/en/latest/) and
[microfs](https://microfs.readthedocs.io/en/latest/). These tools are for
experienced users only.

Finally, there are great [tutorials](https://microbit-micropython.readthedocs.io/en/latest/tutorials/introduction.html) for MicroPython on the micro:bit.
They are free for you to use, re-use, adapt, adopt, enhance and share to your
own needs.

# What is MicroPython?

MicroPython is just as easy to learn as the other programming languages but
differs from them in several important respects:

1. MicroPython is a complete reimplementation of Python 3. This includes advanced features not found in any of the other languages: basic data types (strings,
integers, floating point numbers, booleans), data structures (lists, dictionaries, sets), classes, exception handling, generators and list comprehensions.
2. MicroPython runs entirely on the micro:bit itself - no need for a compiler.
3. MicroPython (like Python) is a dynamic language so it's possible to work with the device interactively: enter Python code and see the device immediately respond in live coding sessions using the REPL feature.
4. MicroPython comes with lots of exclusive features: a powerful music programming language, a speech synthesiser, built-in images and music, a local file system and a large range of ways to connect to attached devices: I2C, NeoPixel, SPI and UART.

The Bluetooth stack is not enabled inside MicroPython because of memory
constraints. However MicroPython uses the Bluetooth radio hardware with its own
simple yet powerful `radio` module. The protocol for the `radio` module is a
lot more beginner friendly than Bluetooth yet allows users to create efficient
yet effective wireless networks of micro:bit devices. Conceptually it works in
the same way as walkie-talkies: anyone broadcasting on a certain channel can be
heard by anyone listening on the same channel (and there are a large selection
of channels to tune into). That's it!

Finally, and perhaps most importantly, by learning MicroPython you're learning
how to use Python - one of the world's most popular professional programming
languages. You inadvertantly use Python *every day* when you use YouTube,
Google, Facebook, Instagram, DropBox and a plethora of other online services.
These skills are valuable: Python programmers are in demand.

## The MicroPython Software

MicroPython is itself written in C++. The MicroPython "runtime" is built using
a set of offline tools. The output from this build process is a `.hex` file
containing the complete MicroPython language. The editors described above
combine this file with your code to generate the file you copy onto the device.

You can flash just the runtime .hex file onto any micro:bit by simply making
sure the editor based code is empty.

When MicroPython is loaded to the micro:bit in this way, it obviously doesn't
have a user program associated with it. But, you can connect to your micro:bit
over the USB Serial port using a terminal program (or inside the Mu editor
press the REPL button to do the same). You can then have a live conversation
with MicroPython; for example if you type `display.show("Hello")`, the moment
that you press `RETURN` the message `"hello"` will scroll on the screen.

More interesting still, if the .hex file you copied onto the device *does*
contain some of your code, it's still possible to connect with the REPL and
interact with your program. This is very useful for debugging purposes.


## Adding a User Application to MicroPython

Both the web hosted and the offline editor (Mu) have a copy of this MicroPython
.hex file inside them, as a plain text file.

When you write your Python application, both the web hosted editor and the
offline editor Mu create a modified .hex file for you to copy to the micro:bit.
This modified file contains 3 things

1. An identical copy of the base MicroPython .hex code file;
2. A small header which marks a region as a MicroPython script (followed by the
length of the script in bytes);
3. A verbatim copy of your Python program, complete with comments and any
spaces.

As a result, Mu and the `uflash` command are able to retrieve your Python code
from .hex files (even if you forgot to save your source code).

When you flash (i.e. copy) a .hex file into the micro:bit it reboots.
MicroPython looks for your script in a special memory address. If it finds a
script it'll attempt to run it. Your program will run all the while there is
something to do, so it will keep going all the while your program loops around,
or until an error occurs (at which time the program will stop and scroll a
helpful error message on the device).


## Is MicroPython Compiled or Interpreted? It's Both!

Compilation is when code is turned into instructions the computer understands.
As a result, these instructions are evaluated very quickly. Interpretation is
when code is run by another (interpreting) program instead of directly on the
computer. Interpretation has the advantage of flexibility: it's possible to
interact with the interpreter while your program is running and change things.
This is, in fact, what you're doing when you live-code using the REPL. However,
due to the interpretation process interpreted code is slower than compiled
code.

MicroPython uses a combination of compilation and interpretation techniques
to run your program. Here's how:

When MicroPython sees a script it parses each line of the script. The end
result is a set of in-memory tokens grouped in such a way that they represent
how your program works. This is called the *parse tree*.

The parse tree is compiled into a terse set of instructions called Python
*bytecode*. Bytecode instructions are like CPU assembly language instructions,
but they are targeted for a *virtual machine*, not for a real piece of computer
hardware.

The Python bytecode is given to the Python virtual machine to run and so your
program is executed.

All of the above happens in the blink of an eye.

The Python virtual machine built into MicroPython is itself compiled from C++
code. It reads Python bytecodes and interprets them one at a time,
calling into lower level C++ functions to make each one perform
it's unique purpose. By using a bytecode interpreter, MicroPython
implements a virtual machine with it's own virtual instruction set.
It is virtual, because these instructions are not "baked in" to the
hardware, but they are implemented in software. This is what allows
MicroPython to be easily 'ported' onto different computer systems
with different processors.

# Links

## Code Editors and Tools

The BBC micro:bit website hosts a [very old version](https://www.microbit.co.uk/app/#create:xyelfe) of the browser based Python code editor.

A new [Python in Education](http://pyedu.io/) website will contain lots of
[micro:bit related resources](http://pythonineducation.org/en/microbit/) and
an online editor as well as general Python in education related resources - all
of which will be released under an open license so you'll be free to use, adapt
and share them.

You can [download Mu](http://codewith.mu/) from its website and also get
involved with [its development](https://github.com/mu-editor/). In addition,
the browser based editor is [open source and community maintained](https://github.com/bbcmicrobit/PythonEditor).

A couple of Python modules provide code and command line commands for
[flashing your micro:bit](https://uflash.readthedocs.io/en/latest/) and
[interacting with the filesystem](https://microfs.readthedocs.io/en/latest/).

## Community Contributions

Many people in the international Python community have contributed free-to-use
resources via the [MicroPython / BBC micro:bit World Tour](https://microworldtour.github.io/).

[Online python simulator](https://create.withcode.uk/)

## Documentation

Tutorials and API documentation for developers can be
[found here](https://microbit-micropython.readthedocs.io/en/latest/).


## Logging an Issue with the Development Team

[Show open issues](https://github.com/bbcmicrobit/micropython/issues)

[Log a new issue](https://github.com/bbcmicrobit/micropython/issues/new)

[Ask a question on the mailing list](https://mail.python.org/mailman/listinfo/microbit) (you must be a member of the mailing list before you can post to it).

## Source Code

[MicroPython on the micro:bit source code](https://github.com/bbcmicrobit/micropython)

[Documentation source code](https://github.com/bbcmicrobit/micropython/tree/master/docs).

[MicroPython source code](https://github.com/micropython/micropython).

[Browser based editor](https://github.com/bbcmicrobit/PythonEditor)

[Mu source code](https://github.com/mu-editor)

[uFlash](https://github.com/ntoll/uflash)

[microfs](https://github.com/ntoll/microfs)

## Other Links

All development is covered by the Python Software Foundation's
[code of conduct](https://www.python.org/psf/codeofconduct/).

The [Python Software Foundation](https://www.python.org/psf-landing/)
represents, supports and coordinates the wider Python community.

Learn how to [embed assembly language](http://docs.micropython.org/en/latest/pyboard/pyboard/tutorial/assembler.html) in
your Python scripts (this feature is enabled for MicroPython on the micro:bit).

Lots of MicroPython / BBC micro:bit videos can be found on [this YouTube playlist](https://www.youtube.com/playlist?list=PLzCYc445IVNQimtxAlPpaFMtvv8qKSncK).

The Python Software Foundation's description of their involvement in the project can be found in [this blog post](https://pyfound.blogspot.co.uk/2016/03/a-million-children.html).

One of the contributors to the project [gave a keynote address](https://www.youtube.com/watch?v=JVaF6uZuSIU) to the 2016 European Python Programming conference (EuroPython).

A [CAS Chat](https://www.youtube.com/watch?v=zEqQq8K89Y4) about the micro:bit and MicroPython gives an interesting perspective of the wider project.

[CAS.TV micropython demo](https://www.youtube.com/watch?v=hUIObK3MHL8)   media offset 23:53
