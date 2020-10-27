---
layout: page
heading: Making accessories for the micro:bit
description: Information on making accessories and peripherals for the  micro:bit
permalink: /accessories/making-accessories/
lang: en
---

## Accessory list

A [list of available accessories](https://microbit.org/buy/accessories/) is maintained on the micro:bit website.

[submit an accessory](https://form.jotformeu.com/83453273451355){: .btn.sm-btn}

## Using the Edge Connector

The micro:bit card edge connector, commonly referred to as the 'edge connector' or the 'pins' makes accessory design easy.

Many micro:bit accessories are designed to use an edge connector socket, so it is simple to plug in and remove the board.

There are limitations to the current that can be drawn from the micro:bit, and accessories must be designed carefully to ensure they do not damage the micro:bit, or that the micro:bit cannot damage them.

### V2 revision

The edge connector on the <span class="V2">V2</span> board revision is backwards compatible with the <span class="v1">v1</span> edge connector, but has additional dedicated pins.

- Details of the [edge connector and pinout](/hardware/edgeconnector)
- Details about [powering things from the board](/hardware/powersupply)

## Battery Pads

There are two rounded rectangular pads on the back of the micro:bit. These allow you to connect a battery holder via a mechanism other than the JST connector.

![Picture of the two rounded rectangular pads](/docs/accessories/assets/making-accessories-d7c25.png)

The upper pad is 0V or GND and the lower pad is 3V.

### V2 revision

In the <span class="v2">V2</span> board revision, the 3V rounded rectangular pad is connected to the 3V ring on the edge connector.

- If you make an accessory that uses the rounded rectangular pads, it must be protected from reverse charging when the board is powered by USB, battery or edge connector.
- You can now source power from the rounded rectangular pads if you are making an accessory, as they are consistent with the power architecture of the edge connector.

Due to the addition of a speaker, current accessories that use the rounded rectangular pads to power the micro:bit will no longer fit.


