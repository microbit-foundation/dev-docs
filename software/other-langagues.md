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

# Submissions
To add a new language to the page, [edit the page on  Github](http://github.com/microbit-foundation/dev-docs/edit/master/software/other-languages.md). For a language to be accepted it's implementation must be complete enough to display a heart on the display!

Please format the addition using this template:

## Language Name

[Project homepage](https://example.com)

[Example](https://example.com)

### micro:bit heart

`
    example code to show a heart on the display
`



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
