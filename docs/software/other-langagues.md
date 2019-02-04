---
layout: page
order:
title: Other Programming Languages
heading: Other Programming Languages
description: Using other programming languages that support the BBC micro:bit
permalink: /software/other_languages/
ref: software
lang: en
---


# Overview

Aside from the officially supported editors: [Makecode](https://makecode.microbit.org) 
and [Python](https://python.microbit.org) there are a number of different 
languages that include support for the micro:bit.

This resource aims to compile a list of these programming languages with a link
to the documentation, plus an example program.

# Alternate Languages

## Ada

[Project homepage](https://blog.adacore.com/ada-on-the-microbit)

[Example](https://github.com/AdaCore/Ada_Drivers_Library/tree/master/examples/MicroBit/text_scrolling)

### micro:bit heart

```
with MicroBit.Display;

procedure Main is
begin

   loop
      MicroBit.Display.Display ("<3");
   end loop;
end Main;
```


# Contributions

This page can be edited in our [Github Repository](https://github.com/microbit-foundation/dev-docs/tree/master/software), with submission guidelines [found in our community issue tracker](https://github.com/microbit-foundation/microbit-community/issues/17).

