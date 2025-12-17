---
layout: page
order:
title: python.microbit.org
heading: python.microbit.org
description: Information about the micro:bit Python Editor
permalink: /software/python-editor/
ref: python-editor
lang: en
---

## Overview

The [Python Editor](https://python.microbit.org) is a free, open source, browser-based coding environment for creating [MicroPython]({{ "/software/micropython/" | relative_url }}) projects with the BBC micro:bit.

### Documentation

For using the editor:

- The [Reference](https://python.microbit.org/v/3/reference), [Ideas](https://python.microbit.org/v/3/ideas) and [API](https://python.microbit.org/v/3/api) tabs in the editor itself
- [User guide](https://microbit-micropython.readthedocs.io/en/latest/)
- [MicroPython reference](https://microbit-micropython.readthedocs.io/en/v2-docs/) provides information and examples on using the API

For developing the editor or understanding how it works:

- [GitHub](https://github.com/microbit-foundation/python-editor-v3)
- [Technical overview](https://github.com/microbit-foundation/python-editor-v3/blob/main/docs/tech-overview.md)

### Reusable software components

The [micro:bit MicroPython simulator](https://github.com/microbit-foundation/micropython-microbit-v2-simulator#readme) is a separate component that you can embed in your own software projects.

The [micro:bit connection](https://microbit-foundation.github.io/microbit-connection/) npm package is used to connect to and flash the micro:bit over WebUSB.

The MicroPython file system that stores the user's Python code can be manipulated with the [microbit-fs](https://microbit-foundation.github.io/microbit-fs/) npm package.

### Previous version

The micro:bit Python Editor (V2) is still available at [https://python.microbit.org/v/2](https://python.microbit.org/v/2) with source code at [https://github.com/bbcmicrobit/PythonEditor](https://github.com/bbcmicrobit/PythonEditor).

### Community

- Raise a [Python Editor issue or feature request](https://github.com/microbit-foundation/python-editor-v3/issues)
- Help [Translate the Python Editor](https://support.microbit.org/en/support/solutions/articles/19000106022-translating-the-python-editor) into your own language.
