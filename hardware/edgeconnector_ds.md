---
layout: page
order:
title: Edge Connector Data Sheet
heading: Edge Connector Data Sheet
description: A detailed data sheet all about the pins and signals of the edge connector.
permalink: /hardware/edgeconnector_ds/
ref: hardware
lang: en
assigned-to: davidw
review-with: jonnya
---


# Overview

The edge connector on the micro:bit board brings out all the key signals and circuits
that you would need in order to build attachments to the micro:bit. 5 of the pads are
large rings with 4mm through plated holes suitable for attaching standard banana plugs,
or for clipping crocodile clips to. 3 of these are connected to GPIO pins that are
also capable of analog, PWM and touch sensing. The 3V and GND rings are useful for
providing a small amount of power to external circuits, or (carefully) back powering
the micro:bit from an external power supply.

The smaller strips spaced at 1.27mm on the edge connector have additional signals,
some of which are used by the micro:bit, and others that are free for you to use.
There are a number of external PCB connectors for purchase with an 80w 1.27mm pitch
that can be used to easily access these extra pins. For these narrow pins,
they are only connected on the front of the device, the narrow pins on the back
are unconnected.


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
|          | 40      | P0.20    | P0.20 | P12 | **GPIO**, ACCESS, (PWM), (UART)                   | I      | i12Kd          |
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
| startup   | the startup conditions when the micro:bit boots: Input or Output
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

6. The source file for [the pinout table](./pinmap.csv) is held in CSV format.
You can load this into a spreadsheet and sort and filter it in any way that
makes sense to you. There is also a [zipped Python script](./csv2md.zip) in this folder 
that you can download to re-generate the markdown table version of the pinmap
used on this page, from the .csv file.


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
onboard accelerometer and magnetometer devices. It is strongly suggested
that you avoid using these pins for any function other than I2C.

It is possible to disable the DAL services that use these pins as the I2C bus,
but the accelerometer and magnetometer device will still be connected
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
can use the GND and 3V rings, are detailed here: [psu](./powersupply)


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

NOTE 3: The pin marked 'reserved for accessibility' is not presently
used, and may be used as a general purpose input/output pin.
It may be used in future releases of the software runtime, to enable
and disable an on-board accessibility mode.

NOTE 4: The BBC suggest in the safety guide, that the maximum current
you can draw from the whole edge connector at any one time is
90mA. This is set based on the 30mA budget for on board peripherals,
and the fact that the on board regulator of the KL26 when powered
from USB is rated at a maximum of 120mA.
