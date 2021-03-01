---
layout: page
order:
title: Schematics
heading: Schematics
description: micro:bit Circuit Schematics
permalink: /hardware/schematic/
ref: hardware
lang: en
assigned-to: markw
review-with: jonnya
---

## Overview

This page discusses the micro:bit schematic and Bill of Materials (BOM), which shows the electrical connections of the micro:bit and the components used in it.

The schematic is available from the BBC's [micro:bit hardware repository](https://github.com/bbcmicrobit/hardware)

If you're looking to make something of your own based on the micro:bit, you might prefer to use our ['Reference Design'](/hardware/reference-design/) which is based on a radio module and has space on the layout for you to add your own components.

## Schematics

- [V1.3](https://github.com/bbcmicrobit/hardware/blob/master/V1.3B/SCH_BBC-Microbit_V1.3B.pdf)
- [V1.5](https://github.com/bbcmicrobit/hardware/blob/master/V1.5/SCH_BBC-Microbit_V1.5.PDF)
- [V2 TBC](#)

## V2 pinmap

Whilst we work on the publication of the schematic for the latest revision, here is the pinmap and allocation of the nRF52833

| GPIO on nRF52833 | Allocation          | KL27 Landing                             | Edge Connector name |
| ---------------- | ------------------- | ---------------------------------------- | ------------------- |
| P0.00            | SPKR1               | KL27_DAC                                 |                     |
| P1.05            | COL4                | N                                        | P6                  |
| P0.02            | RING0               | N                                        | P0                  |
| P0.03            | RING1               | N                                        | P1                  |
| P0.04            | RING2               | N                                        | P2                  |
| P0.05            | MIC_IN              | N                                        |                     |
| P0.06            | UART_INTERNAL_RX    | P17 (LPUART1_RX)                         |                     |
| P1.08            | UART_INTERNAL_TX    | P25 (LPUART1_TX)                         |                     |
| P0.08            | I2C_INT_SCL         | P22 (I2C1_SCL)                           |                     |
| P0.10            | GPIO1               | N                                        | P8                  |
| P0.09            | GPIO2               | N                                        | P9                  |
| P0.11            | COL2                | N                                        | P7                  |
| P1.02            | GPIO3               | N                                        | P16                 |
| P0.19            | ROW5                | N                                        |                     |
| P0.14            | BTN_A               | N                                        | P5                  |
| P0.23            | BTN_B               | N                                        | P11                 |
| P1.04            | FACE_TOUCH          | N                                        |                     |
| P0.16            | I2C_INT_SDA         | P23 (I2C1_SDA)                           |                     |
| P0.17            | SCK_EXTERNAL        | N                                        | P13                 |
| P0.01            | MISO_EXTERNAL       | N                                        | P14                 |
| P0.13            | MOSI_EXTERNAL       | N                                        | P15                 |
| P0.20            | RUN_MIC             | N                                        |                     |
| P0.21            | ROW1                | N                                        |                     |
| P0.22            | ROW2                | N                                        |                     |
| P0.15            | ROW3                | N                                        |                     |
| P0.24            | ROW4                | N                                        |                     |
| P0.25            | COMBINED_SENSOR_INT | P11 SENSOR_nINT                          |                     |
| P0.26            | I2C_EXT_SCL         | N                                        | P19                 |
| P1.00            | I2C_EXT_SDA         | N                                        | P20                 |
| P0.12            | GPIO4               | N                                        | P12                 |
| P0.28            | COL1                | N                                        | P4                  |
| P0.31            | COL3                | N                                        | P3                  |
| P0.30            | COL5                | N                                        | P10                 |

## Key Features

Below, we've extracted some useful details about the hardware that anyone implementing software for the micro:bit, interfacing to it, or designing an add-on board for it should find useful.

### LEDS

The LED matrix is physically laid out as a 5x5. On the <span class="v2">V2</span> board this is implemented as a 5x5 matrix, but in the <span class="v1">V1</span>, this is implemented as a scanned matrix of 9x3 (i.e. 9 columns by 3 rows). Row 2 Col 8, and Row 2 Col 9 are not used.

The LED matrix is driven via a high-speed multiplex generated by application processor software.
This software also uses the LED Row and Col pins to implement the light sensing feature, as such you may see a difference in sensitivity between board revisions.
Some of the Columns appear on the edge connector, so if you want to use extra GPIO pins, you have to disable the display in software.

### Interface

The Interface sheet shows the KL26<span class="v1">V1</span>/KL27<span class="v2">V2</span> processor, which is an NXP microcontroller with an Arm processor, that implements the USB protocol for the USB connector. This provides a method for loading code onto the application processor, using a drag and drop interface.

The USB protocol handler on this processor implements a Mass Storage Class device in order to offer the drag and drop code load interface. It also provides a Connected Device Class that allows a serial port interface to be used across the USB.

The interface processor also contains an on-board regulator that steps down the USB voltage to 3.3V suitable for powering the rest of the micro:bit, and you can draw 120mA<span class="v1">V1</span>/300mA<span class="v2">V2</span> from this processor regulator. A TVS device is fitted to suppress ESD spikes and out of range voltages that could be present on the USB connector.

This processor does not have any connection to the GPIO pins on the micro:bit.

### Sensors

There is one combined motion sensor IC on the micro:bit, that contains an accelerometer and a magnetometer. The accelerometer measures acceleration in 3 axes, and the magnetometer can be used as a compass, as well as a magnetic field detector.

The device is connected to the application processor [I2C bus](../i2c/), and for the <span class="v1">V1</span> revision this [I2C bus is also shared](../i2c-shared/) to two pins on the edge connector. I2C pull-up resistors are pre-fitted on the board.

In <span class="v2">V2</span> there is a combined open drain, active low, interrupt signal (`COMBINED_SENSOR_INT`) to the application processor for the motion sensors and the KL27. Any device can asset this signal and the application processor has to query the individual devices to locate the origin.

The magnetometer can generate one processor interrupt for the application processor, and the accelerometer can generate two different processor interrupts in <span class="v1">V1</span> or just one in <span class="v2">V2</span>.

Note, the physical orientation of this IC is important for binary compatibility with the driver code in the application processor, which assumes a particular physical orientation in its calculations.

### Power Supply

Power to the micro:bit can be provided by 3 sources: The USB, the battery connector, and the 3V pad on the edge connector.

For USB powering, the KL26 interface processor has an on-board regulator that brings the external USB voltage into the correct range for the micro:bit board.

A low-Vf diode (in this case about 0.23V max) is used to switch between sources. The diode prevents back-powering of any source from any other source.

Care should be taken if powering the micro:bit from the 3V pad on the edge connector, as the trace from that pad is connected directly to the ICs on the board. Please check the datasheets for the appropriate ICs for their maximum tolerable voltages.

### Application Processor

The main application processor runs both the runtime code and user code, as a single binary image.

Code is loaded into this processor via the interface processor.

Communications via USB serial is done via the interface processor.

All GPIO pins on the [edge connector](../edgeconnector/) are serviced by this application processor.

All [bluetooth](../../bluetooth) features are provided by a SoftDevice stack loaded into this processor.

The nRF52<span class="v2">V2</span> features additional NFC functionality on P0.09(NFC1) and P0.10(NFC2) that is disabled by default, but can be configured using the [nRF5SDK](https://www.nordicsemi.com/Software-and-Tools/Software/nRF5-SDK).

### Edge Connector

The edge connector is the main interface to external components attached to the micro:bit.

This interface has a range of digital, analog, touch, PWM, and serial communications interfaces.

10Mohm weak pull-up resistors are fitted on P0 P1 P2 and logo<span class="v2">V2</span> for use in touch sensing mode, where they provide a weak pull-up to the supply providing a default high input and the user touching the GND pad pulls the pin down towards 0V, providing a low input. When in non touch modes, these pads have stronger internal pull-downs enabled in the software, so that the default input state when not connected is 'low'.

Guard pins are provided both sides of the 3V and GND pads, so that shorting by crocodile clips does not degrade the features of the device by causing spurious inputs.

Both the front and the back of each of the 5 round ring pads are electrically connected.

A number of pins have alternate assigned functions for use by the micro:bit, many of these can be disabled in software to gain more general purpose IO pins.

The <span class="v2">V2</span> board revision has a notched edge connector to make it easier to connect crocodile clips and wire etc. This does not affect compatibility with peripherals with edge connector sockets.

### Dimensions

The specific dimensions of the board are:

- 51.60mm(w) 42.00mm(h) 11.65mm(d)
- JST connector to board 5.50mm
- button depth to board 4.55mm
- <span class="v2">V2</span> speaker depth to board 3.00mm

The following image of the <span class="V2">V2</span> revision is taken from the [micro:bit V2 assembly diagram](/docs/hardware/assets/Microbit_V2_Assembly.pdf) provided by Avid.

![micro:bit assembly front](/docs/hardware/assets/microbit-v2-assembly-front.png)

The rear view of the device has been adapted to highlight the test points and describe their purpose.

![micro:bit assembly back](/docs/hardware/assets/microbit-v2-assembly-back.png)

### Exposed Test Points
Test Point | Use case
---------- | ---------
TP1 | U5 Bootmode - used for debugging U5 - KL27Z
TP7 | UDC+ of USB
TP8 | UDC- of USB
TP17 | Access to J2-Pin 1 Battery connector
TP19 | Access to VBUS line on J3 - USB Connector
TP20 | I2C_INT_SCL - access to U2 - nRF52
TP21 | I2C_INT_SDA - access to U2 - nRF52
TP9 | VREG - Lozenge test points
TP10 | GND - Lozenge test points
 
### Covered test points (Solder mask to be removed to access test point)
Test Point | Use case
---------- | ---------
TP11 | U2_SWDCLK - used to debug U2
TP12 | U2_SWDIO - used to debug U2
TP4 | U5_SWD_DIO - used for debugging U5 - KL27Z
TP3 | U5_SWD_TCLK - used for debugging U5 - KL27Z
TP2 | U5_IF_NRST - used for debugging U5 - KL27Z
TP6 | GND
TP18 | VBUS
TP5 | VREG - This is connected to TP9


## Further information

- [micro:bit V2 assembly diagram](/docs/hardware/assets/Microbit_V2_Assembly.pdf)

- [KL27 datasheet](https://www.nxp.com/docs/en/data-sheet/KL27P64M48SF6.pdf)

- [KL26 datasheet](http://www.nxp.com/webapp/search.partparamdetail.framework?PART_NUMBER=MKL26Z128VFM4)

- [nRF52833 datasheet](https://infocenter.nordicsemi.com/index.jsp?topic=%2Fstruct_nrf52%2Fstruct%2Fnrf52833.html&cp=3_1)

- [nRF51822 datasheet](https://www.nordicsemi.com/eng/Products/Bluetooth-low-energy/nRF51822)

- [LSM303AGR datasheet](https://www.st.com/resource/en/datasheet/lsm303agr.pdf)

- [FXOS8700 datasheet](https://www.nxp.com/docs/en/data-sheet/FXOS8700CQ.pdf)

- [MAG3110 datasheet](http://www.nxp.com/products/sensors/magnetometers/sample-data-sets-for-inertial-and-magnetic-sensors/high-accuracy-3d-magnetometer:MAG3110)

- [MMA8653FC datasheet](http://www.nxp.com/products/sensors/accelerometers/3-axis-accelerometers/2g-4g-8g-low-g-10-bit-digital-accelerometer:MMA8653FC)

- [PRT5xx datasheet](https://assets.nexperia.com/documents/data-sheet/PRTR5V0U2F_PRTR5V0U2K.pdf)

- [BAT60A datasheet](http://www.infineon.com/dgdl/Infineon-BAT60ASERIES-DS-v01_01-en.pdf?fileId=db3a304313d846880113def70c9304a9)

- [CON1 datasheet](https://uk.farnell.com/jst-japan-solderless-terminals/s2b-ph-sm4-tb-lf-sn/connector-header-smt-r-a-2mm-2way/dp/9492615)

- [SWD Interface](http://www.arm.com/products/system-ip/debug-trace/coresight-soc-components/serial-wire-debug.php)

- [USB Mass Storage Class](https://en.wikipedia.org/wiki/USB_mass_storage_device_class)

- [USB Communications Device Class](https://en.wikipedia.org/wiki/USB_communications_device_class)
