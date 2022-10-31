---
layout: page
order:
title: Other Programming Languages
heading: Other Programming Languages
description: Using other programming languages that support the BBC micro:bit
permalink: /software/other-languages/
ref: software
lang: en
---

## Overview

Aside from the officially supported editors: [MakeCode](https://makecode.microbit.org)  and [Python](https://python.microbit.org) there are a number of different languages that include support for the micro:bit.

This resource aims to compile a list of these programming languages with a link to the documentation, plus an example program.

## Submissions

To add a new language to the page, [edit the page on  Github](http://github.com/microbit-foundation/dev-docs/edit/master/software/other-languages.md). For a language to be accepted its implementation must be complete enough to display a heart on the display!

Please format the addition using this template:

## Language Name

[Project Homepage](https://example.com)

[Example](https://example.com)

### micro:bit heart

```
    example code to show a heart on the display
```

## Alternate Languages

## Ada

[Project Homepage](https://blog.adacore.com/ada-on-the-microbit)

[Example](https://github.com/AdaCore/Ada_Drivers_Library/tree/master/examples/MicroBit/text_scrolling)

### micro:bit heart

```ada
with MicroBit.Display;

procedure Main is
begin

   loop
      MicroBit.Display.Display ("<3");
   end loop;
end Main;
```

## Go (with TinyGo)

[Project Homepage](https://tinygo.org/)

[Playground](https://play.tinygo.org/) (select BBC micro:bit v1 from the drop-down)

[Documentation](https://tinygo.org/docs/reference/microcontrollers/machine/microbit/)

Examples:
  * [Microbit Blink](https://github.com/tinygo-org/tinygo-zoo/blob/master/microbit-blink/main.go)
  * [Microbit Pixel Buttons](https://github.com/tinygo-org/tinygo-zoo/blob/master/microbit-pixelbuttons/main.go)
  * [Microbit Accelerometer, Magnetometer, Temperature](https://github.com/tinygo-org/drivers/blob/release/examples/lsm303agr/main.go)

### micro:bit heart

```golang
package main

import (
	"image/color"
	"time"

	"tinygo.org/x/drivers/microbitmatrix"
)

func main() {
	display := microbitmatrix.New()
	display.Configure(
		microbitmatrix.Config{},
	)
	display.DisableAll()
	display.ClearDisplay()

	heart := [5][5]int8{
		{0, 1, 0, 1, 0},
		{1, 1, 1, 1, 1},
		{1, 1, 1, 1, 1},
		{0, 1, 1, 1, 0},
		{0, 0, 1, 0, 0},
	}

	c := color.RGBA{255, 255, 255, 0}

	for row := int16(0); row < 5; row++ {
		for col := int16(0); col < 5; col++ {
			if heart[row][col] == 1 {
				display.SetPixel(col, row, c)
			}
		}
	}

	for {
		// show heart forever
		display.Display()
		time.Sleep(10 * time.Millisecond)
	}
}
```

## Rust

[Project Homepage: _Discover Microcontrollers Using Rust_](https://docs.rust-embedded.org/discovery/microbit/)

Examples:
  * [LED Roulette](https://docs.rust-embedded.org/discovery/microbit/05-led-roulette/)
  * [UART: Send a Byte](https://docs.rust-embedded.org/discovery/microbit/07-uart/send-a-single-byte.html)
  * [LED Compass](https://docs.rust-embedded.org/discovery/microbit/09-led-compass/)

### micro:bit heart

```rust
#![deny(unsafe_code)]
#![no_main]
#![no_std]

use cortex_m_rt::entry;
use rtt_target::rtt_init_print;
use panic_rtt_target as _;
use microbit::{
    board::Board,
    display::blocking::Display,
    hal::{prelude::*, Timer},
};

#[entry]
fn main() -> ! {
    rtt_init_print!();

    let board = Board::take().unwrap();
    let mut timer = Timer::new(board.TIMER0);
    let mut display = Display::new(board.display_pins);
    let heart = [
        [0, 1, 0, 1, 0],
        [1, 1, 1, 1, 1],
        [1, 1, 1, 1, 1],
        [0, 1, 1, 1, 0],
        [0, 0, 1, 0, 0],
    ];

    loop {
        // Show heart for 1000ms
        display.show(&mut timer, heart, 1000);
        display.clear();
        timer.delay_ms(1000_u32);
    }
}
```
