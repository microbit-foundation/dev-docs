---
layout: page
order:
title: Edge Connector and Pinout
heading: Edge Connector & micro:bit pinout
description: The edge connector provides a set of pads and pins to allow interfacing to other circuits and components.
tags: micro:bit pinout, edge connector
permalink: /hardware/edgeconnector/
ref: hardware
lang: en
---

# Overview
{:notoc}

* TOC
{:toc}

The edge connector on the micro:bit is used to connect to external circuits and components.

There are 25 strips/pins including 5 rings for using with 4mm banana plugs or crocodile clips. 3 of these rings are for general purpose input and output (GPIO) and are
also capable of analog, PWM and touch sensing, and two are connected to the micro:bit power supply.

The smaller strips spaced at 1.27mm on the edge connector have additional signals,
some of which are used by the micro:bit, and others that are free for you to use.
There are a number of external PCB connectors for purchase with an 80w 1.27mm pitch
that can be used to easily access these extra pins.

Only the pins on the front are connected to signals. The back rings are connected to the
front rings, but the back small strips are unconnected.


## Edge Connector Pins

![edge connector](/docs/hardware/assets/edge_connector.svg)

Also checkout [microbit.pinout.xyz](https://microbit.pinout.xyz) for more information.

## Pins and Signals

This table shows various data about each of the pins on the micro:bit edge connector.

| m:b ring | mod     | schem    | MCU   | s/w | functions                                         | dir    | pull?          |
| -------- | ---     | -----    | ---   | --- | ---------                                         | ---    | -----          |
|          | 21      | COL1R    | P0.04 | P3  | (GPIO), (ANALOG), **LEDCOL(1)**, (PWM), (UART)    | O      | --             |
|          |         | PAD1     |       | P0  | }                                                 |        |                |
|          |         | PAD1     |       | P0  | }                                                 |        |                |
| 0        | 18      | PAD1     | P0.03 | P0  | } **GPIO**, ANALOG, TOUCH, PWM, UART              | I      | e10Mu, i12Kd   |
|          |         | PAD1     |       | P0  | }                                                 |        |                |
|          | 22      | COL2R    | P0.05 | P4  | (GPIO), (ANALOG), **LEDCOL(2)**, (PWM), (UART)    | O      | --             |
|          | 37      | BTN_A    | P0.17 | P5  | (GPIO), **BUTTON(A)**, (PWM), (UART)              | I      | e10Ku, i12Kd?  |
|          | 30      | COL9R    | P0.12 | P6  | (GPIO), **LEDCOL(9)**, (PWM), (UART)              | O      | --             |
|          | 29      | COL8R    | P0.11 | P7  | (GPIO), **LEDCOL(8)**, (PWM), (UART)              | O      | --             |
|          |         | PAD2     |       | P1  | }                                                 |        |                |
|          |         | PAD2     |       | P1  | }                                                 |        |                |
| 1        | 19      | PAD2     | P0.02 | P1  | } **GPIO**, ANALOG, TOUCH, PWM, UART              | I      | e10Mu, i12Kd   |
|          |         | PAD2     |       | P1  | }                                                 |        |                |
|          | 38      | P0.18    | P0.18 | P8  | **GPIO**, PWM, UART                               | I      | i12Kd          |
|          | 28      | COL7R    | P0.10 | P9  | (GPIO), **LEDCOL(7)**, (PWM), (UART)              | O      | --             |
|          | 23      | COL3R    | P0.06 | P10 | (GPIO), **LEDCOL(3)**, (ANALOG), (PWM), (UART)    | O      | --             |
|          | 9       | BTN_B    | P0.26 | P11 | (GPIO), **BUTTON(B)**, (PWM), (UART)              | I      | e10Ku, i12Kd?  |
|          | 40      | P0.20    | P0.20 | P12 | (GPIO),**ACCESSIBILITY**, (PWM), (UART)                   | I      | i12Kd          |
|          |         | PAD3     |       | P2  | }                                                 |        |                |
|          |         | PAD3     |       | P2  | }                                                 |        |                |
| 2        | 20      | PAD3     | P0.01 | P2  | } **GPIO**, ANALOG, TOUCH, PWM, UART              | I      | e10Mu, i12Kd   |
|          |         | PAD3     |       | P2  | }                                                 |        |                |
|          | 6       | SCK      | P0.23 | P13 | **GPIO**, SPI(SCLK), PWM, UART                    | I      | i12Kd          |
|          | 5       | MISO     | P0.22 | P14 | **GPIO**, SPI(MISO), PWM, UART                    | I      | i12Kd          |
|          | 4       | MOSI     | P0.21 | P15 | **GPIO**, SPI(MOSI), PWM, UART                    | I      | i12Kd          |
|          | 34      | P0.16    | P0.16 | P16 | **GPIO**, PWM, UART                               | I      | i12Kd          |
|          |         | +V_TGT   |       |     | PSU(V_TGT)                                        |        | --             |
|          |         | +V_TGT   |       |     | }                                                 |        | --             |
|          |         | +V_TGT   |       |     | }                                                 |        | --             |
| 3V       |         | +V_TGT   |       |     | } PSU(V_TGT)                                      |        | --             |
|          |         | +V_TGT   |       |     | }                                                 |        | --             |
|          |         | +V_TGT   |       |     | PSU(V_TGT)                                        |        | --             |
|          | 17      | SCL      | P0.00 | P19 | (GPIO), **I2C(SCL)**, (PWM), (UART)               | O      | e4k7u          |
|          | 16      | SDA      | P0.30 | P20 | (GPIO), **I2C(SDA)**, (PWM), (UART)               | I      | e4k7u          |
|          |         | GND      |       |     | PSU(GND)                                          |        | --             |
|          |         | GND      |       |     | }                                                 |        | --             |
|          |         | GND      |       |     | }                                                 |        | --             |
| GND      |         | GND      |       |     | } PSU(GND)                                        |        | --             |
|          |         | GND      |       |     | }                                                 |        | --             |
|          |         | GND      |       |     | PSU(GND)                                          |        | --             |



| column    | purpose
| ---       | ---
| m:b ring  | the micro:bit basic interface (the 5 rings on the front)
| mod       | the pin number on the module:bit
| schem     | the symbol name in the micro:bit schematics
| MCU       | the actual pin name of the nRF51822 MCU chip
| s/w       | the name that is used in the DAL runtime software
| functions | all possible functions, **BOLD** for default. brackets indicate use with caution
| dir       | the startup conditions (direction) when the micro:bit boots: Input or Output
| pull?     | pull up or down resistors. e10Mu means an external 10Mohm pullup, i12Kd means an internal 12K pull down.


Notes

1. RINGs for 0, 1, 2, 3V and GND are also connected to the respective reverse
side rings on the edge connector.

2. The 3V and GND rings have guard strips either side of the big rings,
to avoid any degradation of device performance due to slipping crocodile
clip connections. Care should be taken on rings 0, 1 and 2 to avoid
shorting crocodile clips against adjacent pins, which could cause
some slight interference with the pattern currently displayed on
the LED matrix, or introduce some innaccuracies in the light sensing
readings.

3. The DAL DynamicPWM driver (and the underlying nrF51 timer peripherals)
dictate that PWM can only be active on 3 pins simultaneously.
Any attempt to allocate a 4th pin for PWM use, will disable one of the
existing PWM pins.

4. Digital input pins are by default configured with internal
pull down resistors when the pins are configured by the DAL.

5. Functions in brackets should be used with caution, as other features
of the device may become unstable, degraded or non operational, if their
normal use is not disabled in the software first.

6. The source file for [the pinout table](/docs/hardware/pinmap.csv) is held in CSV format.
You can load this into a spreadsheet and sort and filter it in any way that
makes sense to you. There is also a [zipped Python script](/docs/hardware/csv2md.zip) in this folder
that you can download to re-generate the markdown table version of the pinmap
used on this page, from the .csv file.

7. The pin marked 'ACCESSIBILITY' is used to enable/disable an on-board
accessibility mode, and should not be used for anything else (even though it
can be used as a GPIO for testing). Future versions of the official micro:bit
editors may remove the ability to write to this pin.


## Uncoupling Default Functionality

Pins that are marked with brackets around functions, require the default
functionality for that pin to be disabled, before other functions can
be used.

pins: P3, P4, P6, P7, P9, P10

These pins are coupled to the LED matrix display, and also it's associated
ambient light sensing mode. To disable the display driver feature (which
will automatically disable the light sensing feature) call the DAL
function `display.enable(false)`. To turn the display driver back on again
later, call the DAL function `display.enable(true)`.

Note also that the LED 3x9 matrix connects LEDs with associated resistors across
these pins, so you should take that into account when designing circuits to use these
pins for other purposes.


pins: P5, P11

These pins are assigned to the two on-board buttons. In their default
setup with all the standard high level languages, there is a global
uBit instance containing: `uBit.buttonA`, `uBit.buttonB` and `uBit.buttonAB`.

Buttons are hooked into the system timer in their constructor for
regular debouncing. However, if you want to completely remove
this feature and use the physical pins for other purposes,
you can `delete uBit.buttonA`, it will call the C++ destructor
and de-register the button instance from the system timer, effectively
disabling all DAL activity with that pin. It is then possible
to use a `MicroBitPin` instance around the physical pin name to
control it directly without interference from the DAL.

Be aware though, that there are 10K external pullup resistors
fitted to the micro:bit board.


pins: P19, P20

These pins are allocated to the I2C bus, which is used by both the
onboard motion sensor. It is strongly suggested
that you avoid using these pins for any function other than I2C.

It is possible to disable the DAL services that use these pins as the I2C bus,
but the motion sensor device will still be connected
to the bus, and may try to interpret the signals as data payloads,
which could create some undesirable side effects on the SDA and interrupt
pins. There are 4K7 pullups fitted to both pins on the board, so the
best use for these two signals is to add other I2C devices.

The main reason you might choose to use these pins for other purposes would
be if you were designing your own micro:bit variant without any
I2C devices, and then it would free up two more pins for other
purposes.


## Power Supply Capabilities

The power supply capabilities and parameters, which better define how you
can use the GND and 3V rings, are detailed here: [psu](/hardware/powersupply)


## GPIO Capabilities

These key GPIO parameters are transcribed directly from Section 6, 7 and 8 of the nRF51822 Datasheet,
and provided here as a handy reference.

| KEY    | Description                                        | section | Min      | Max     |
| ---    | -------------------------------------------------- | ------- | ----     | ----    |
| VOL    | Voltage Output Low                                 |  8.23   | VSS      | 0.3V    |
| VOH    | Voltage Output High                                |  8.23   | VDD-0.3  | VDD     |
| VIL    | Input voltage for logic low                        |  8.23   | VSS      | 0.3*VDD |
| VIH    | Input voltage for logic high                       |  8.23   | 0.7*VDD  | VDD     |
| xxx    | Max source current from IO pin                     |  8.23   | --       | 5mA     |
| xxx    | Max sink current into IO pin                       |  8.23   | --       | 5mA     |
| VIO    | Tolerable pin voltages for IO pin                  |  6      | -0.3V    | VDD+0.3 |
| xxx    | Pin impedance when an input                        |  ?      | TBD      |         |
| VDD(o) | Operating voltage range (LDO)                      |  7      | 1.8V     | 3.6V    |
| VDD(a) | Absolute voltage range                             |  6      | -0.3V    | +3.9V   |
| VSS    | Ground reference                                   |  6      | 0V       | 0V      |
| RPU    | Pull up resistance                                 |  8.23   | 11K      | 16K     |
| RPD    | Pull down resistance                               |  8.23   | 11K      | 16K     |


NOTE 1: The maximum number of pins configured as high-drive (5mA)
at any one time is 3 pins.

NOTE 2: A common way that the maximum pin voltages can be exceeded, is
to attach an inductive load such as a speaker, motor, or piezo sounder
directly to the pin. These devices often have significant back-EMF
when energised, and will generate voltages that exceed the maximum
specifications of the GPIO pins, and may cause premature device failure.

NOTE 3: The pin marked 'ACCESSIBILITY' is used to enable/disable an on-board
accessibility mode, and should not be used for anything else (even though it
can be used as a GPIO for testing). Future versions of the official micro:bit
editors may remove the ability to write to this pin.

NOTE 4: The BBC suggest in the safety guide, that the maximum current
you can draw from the whole edge connector at any one time is
90mA. This is set based on the 30mA budget for on board peripherals,
and the fact that the on board regulator of the KL26 when powered
from USB is rated at a maximum of 120mA.


## PCB Connector

The PCB connector is an 80 way * 1.27mm pitch double sided connector.

You can buy this connector from a number of sources.

At a pinch, it is also possible to use an old PCI edge connector from a PC motherboard,
as the pitch is the same (but it is slightly wider).

There is a good [mechanical data-sheet](http://resources.coolcomponents.co.uk/CONNECTORS/10156.pdf) for the right angle PCB edge connector available from Cool Components.

## Can You Find a Better Connector?

There are a number of suppliers of edge connector for the micro:bit, in various forms,
such as a right angle through-hole, a stand-up through-hole and a stand-up surface
mount. There are a wide range of connector manufacturers that sell thousands of
different types of connectors.

There are also some nice ideas that have surfaced in the community such as using just
the right size of countersunk or cheese-head bolt, or even 3D printed inserts.

Can you help to find or design a better connection solution to the micro:bit
edge connector? Share your designs and discoveries with us!

## Third Party Connnectors
[Add your connector to our list](http://github.com/microbit-foundation/dev-docs/edit/master/hardware/edgeconnector.md){: .btn.btn-info}

| Supplier | Product 
| -------- | -------
|[Cyclonn](http://www.dgyuliang.net)| [Cylconn 90 degree connector](http://www.dgyuliang.net/d/file/Produtcs/Customized%20Connector/MICRO%20BIT%20Connector/84a0fe06b4296135d64139b5b4297ef3.pdf), [Cylconn 180 degree connector](http://www.dgyuliang.net/d/file/Produtcs/Customized%20Connector/MICRO%20BIT%20Connector/0d43030af84ade6fc3f00e242079c055.pdf)


## Further information

[micro:bit schematics](../schematic)

[micro:bit CAD resources (Kitronik)](https://www.kitronik.co.uk/blog/bbc-microbit-cad-resources/)

[Edge connector CAD resources (Proto-Pic)](https://www.proto-pic.co.uk/micro-bit-resources.html)

[Eagle libraries for the micro:bit edge connector](https://github.com/proto-pic/micro-bit-eagle-libraries)

[KiCad component and footprint library](https://github.com/anthonykirby/kicad_microbit_connector)

[2D CAD drawing](https://www.kitronik.co.uk/pdf/bbc_microbit_mechanical_datasheet_V2.pdf)
This drawing has all the key micro:bit dimensions, including the pin spacing of the
various pins of the edge connector on the micro:bit board.

[STP file](https://www.kitronik.co.uk/zip/Microbit_STEP.zip) This file is a 3D CAD
file for use with [3D modelling software](http://3d-viewers.com/step-viewer.html).

[STL file](https://www.kitronik.co.uk/zip/Microbit_STL.zip) This file can be used
with 3D printers.

[SAT file](https://www.kitronik.co.uk/zip/Microbit_SAT.zip) This file can be used
with [ACIS Modeller](http://www.spatial.com/products/3d-acis-modeling).