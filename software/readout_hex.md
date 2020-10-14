---
layout: page
order:
title: Reading out .hex files
heading: Reading out .hex files
description: A method to read out the .hex file on the micro:bit
permalink: /software/readout_hex/
ref: software
lang: en
assigned-to: markw
review-with: jonnya
---


## Overview

There may be occasions when you want to take a look at the programming that is running on the micro:bit or if you have misplaced the original program.

## uBitTool

[uBitTool](https://www.embeddedlog.com/ubittool/) is a command line and GUI application to interface with the micro:bit.

This tool has a range of features:

- Read the micro:bit flash contents
- Extract user Python code from the micro:bit flash
- Flash the micro:bit
- Compare the contents of the micro:bit flash against a local hex file

You can download the [latest release of the uBitTool GUI Editor](https://github.com/carlosperate/ubittool/releases/) from the GitHub repository and there are [Instructions to read out the contents of a hex file](https://www.embeddedlog.com/ubittool/usage.html) on the website


## py-ocd

This method reads out the .hex file on the micro:bit to a file in your working directory.

In order to complete this task you will require some additional tools and libraries:

  - Linux/Mac OS
  - Python 2 (pyOCD is not supported in Python3)
  - [GNU Project Debugger](https://www.gnu.org/software/gdb/) included as part of [ArmDeveloper GNU Embedded Toolchain](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads) [How to Install](https://gnu-mcu-eclipse.github.io/toolchain/arm/install/)
  - [pyOCD Python library](https://github.com/mbedmicro/pyOCD)

The method described here has been tested on Mac OS  using [Homebrew as a package manager](https://brew.sh/), but should work on Linux. Additional steps are linked to, but it is outside the scope of this article to go through setup.

## Procedure

1. Attach micro:bit via USB
2. Open two terminal windows/tabs
3. In the first terminal start a GDB server by running ```pyocd-gdbserver --persist -t nrf51 -bh -r```
4. In the second terminal window/tab run ```arm-none-eabi-gdb``` to open gdb
5. In the same terminal run ```target remote :3333``` to connect to the GDB server
6. Now run ```dump ihex memory out.hex 0x000 0x3E800``` to write 'out.hex' to your working directory


