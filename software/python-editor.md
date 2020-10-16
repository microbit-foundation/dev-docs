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

The [Python Editor](htps://python.microbit.org) is a free, browser based coding environment for creating [MicroPython](../micropython/) projects with the BBC micro:bit.

Use common snippets of code, add/remove files and modules, and upload/download .hex or .py files.

The Python editor is based upon the [Ace editor](http://ace.c9.io) and includes syntax highlighting, code folding and (semi) intelligent auto-indentation.

### Source

The upstream source code for the Python Editor can be found at [github.com/bbcmicrobit/PythonEditor](https://github.com/bbcmicrobit/PythonEditor)

The micro:bit target depends a closed source versioning repository that facilitates releases at `/v/`, for example the beta editor https://python.microbit.org/v/beta and previous releases.

### Offline

It is possible to use the Python Editor offline to generate, upload and download .hex or .py files. However, refreshing the browser resets the editor.

### Mu

[Mu](http://codewith.mu/) is a third party Python editor, that provides a downloadable, offline coding experience for the micro:bit and includes features such as datalogging and code debugging.

### Documentation

- [MicroPython reference](https://microbit-micropython.readthedocs.io/en/v1.0.1/) provides information and examples on using the blocks
- [Developer setup](https://github.com/bbcmicrobit/PythonEditor/blob/master/README.rst)
- [Filesystem](https://github.com/bbcmicrobit/PythonEditor/blob/master/docs/filesystem.md)
- [Translation strategy](https://github.com/bbcmicrobit/PythonEditor/blob/master/docs/translations.md)
- [Embedding the editor](https://github.com/bbcmicrobit/PythonEditor/blob/master/docs/embedEditor.md)
- [MakeCode Technical Docs](https://makecode.com/docs) for general development

### Community

There are a variety of ways to get involved and interact:

- Join the [micro:bit developer community on Slack](../../community/)
- Raise a [Python Editor issue or feature request](https://github.com/bbcmicrobit/PythonEditor/issues)
- Ask a question on the [MicroPython forum for micro:bit](https://forum.micropython.org/viewforum.php?f=17&sid=de047c3e944921889becbc00f02a918f)
- Help [Translate the Python Editor](https://support.microbit.org/en/support/solutions/articles/19000106022-translating-the-python-editor) into your own language.
