---
layout: page
order:
title: makecode.microbit.org
heading: makecode.microbit.org
description: Information about the MakeCode editor for the BBC micro:bit
permalink: /software/makecode/
ref: makecode
lang: en
---

## Overview

[Microsoft MakeCode for micro:bit](https://makecode.microbit.org) is a free, open source platform for creating projects with the BBC micro:bit.

Connect colour-coded blocks that relate to hardware features and Computer Science fundamentals and switch between blocks, JavaScript and MakeCode Python views. A device simulator shows you what will happen on the physical device before you download your program.

## Source

The source code for MakeCode for micro:bit target can be found at [github.com/Microsoft/pxt-microbit](https://github.com/Microsoft/pxt-microbit)

This target depends on several other repositories:

- <https://github.com/Microsoft/pxt> the PXT framework
- <https://github.com/Microsoft/pxt-common-packages> common APIs across various MakeCode editors
- <https://github.com/lancaster-university/microbit> basic wrapper around the DAL
- <https://github.com/lancaster-university/microbit-dal> the micro:bit DAL

## Compiler

 MakeCode uses a built-in compiler to translate a project into a .hex file when you select **Download**.

This has the advantage of not requiring an internet connection in order to code the micro:bit. Once the browser editor at [makecode.microbit.org](https://makecode.microbit.org) loads, it is cached on your computer.

The MakeCode editors contain a copy of the micro:bit runtime [the DAL/CODAL](/software/runtime) which the blocks and javascript APIs reference.

When you press **Download** the compiler converts the code into a machine readable [hex file format](/software/hex-format).

When this .hex file is flashed onto the MICROBIT drive, the KL26/7 interface processor on the micro:bit copies it into the flash memory inside the nRF application processor and the code runs.

## Other Features

MakeCode supports two-way conversion of code, so you can write code as blocks and see what the generated code looks like in Javascript/MakeCode Python. You can also write Javascript/MakeCode Python code, and if possible, MakeCode will convert this back into blocks automatically.

MakeCode also allows you to [write your own block types](https://makecode.com/extensions) and [publish them as Extensions](https://makecode.microbit.org/extensions).

## App

An app is available for [Windows 10](https://www.microsoft.com/en-gb/p/makecode-for-micro-bit/9pjc7sv48lcx?rtc=1&activetab=pivot:overviewtab)

## Offline

 An [offline version of the MakeCode editor](https://makecode.microbit.org/offline) is available for use in situations where there is limited or no internet connectivity.

## Documentation

- [MakeCode for micro:bit reference](https://makecode.microbit.org/reference) provides information and examples on using the blocks
- [MakeCode Technical Docs](https://makecode.com/docs) for general development

## Extension authoring

The editor has built in support for [Github authoring](https://makecode.com/blog/github-packages). There is a written guide on [Creating Extensions](https://makecode.com/extensions/getting-started) within the reference documentation and a [video tutorial on YouTube](https://www.youtube.com/watch?v=ztrm4XehfGo&list=PLMMBk9hE-SepwjCAK7cY-jvq6KeQKda8x)

## Tutorial authoring

Users can [publish their own tutorials](https://makecode.com/writing-docs/user-tutorials) for simple, guided steps on using MakeCode. Tutorials also support third party extensions.

## Community

There are a variety of ways to get involved and interact:

- Join the [micro:bit developer community on Slack](../../community/)
- Raise a [MakeCode issue or feature request](https://github.com/Microsoft/pxt-microbit/issues)
- Ask the MakeCode development team on [MakeCode forum for micro:bit](https://forum.makecode.com/c/microbit/11)
- Help [Translate MakeCode](https://makecode.com/translate) into your own language.
