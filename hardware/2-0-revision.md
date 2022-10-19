---
layout: hardware
order:
title: 2.0 micro:bit revision
heading: Hardware
description: Details of the 2.0 micro:bit revision
permalink: /hardware/2-0-revision/
ref: hardware
lang: en
---

## Overview

{:notoc}

* TOC
{:toc}

![Board overview 2.0](/docs/hardware/assets/microbit-overview-2.png)

## Hardware block diagram

![2.0 block](/docs/hardware/assets/v2-block.svg)

## Getting Started With the micro:bit Hardware

The micro:bit is a Single Board Computer (SBC) that contains an application processor with a variety of on-chip peripherals. Other peripherals are connected to this chip.

An interface processor is connected to the application processor and manages communications via the USB interface, including the drag-and-drop code flashing process. The interface processor does not connect to any of the micro:bit peripherals.

Two key pieces of information to help understand the internals of the micro:bit are:

- The [schematics](../schematic), which shows the detailed component data and connectivity of the device.

- The [reference design](../reference-design), which is a complete module design of a compatible micro:bit, and is designed to be a starting point for anyone interested in understanding the micro:bit or designing their own variant.

## Hardware Description

### nRF52 Application Processor

The nRF52 application processor is where user programs run.
A single, complete application including user code, runtime code and Bluetooth stack is loaded and run directly from on-chip flash memory.
All user accessible GPIO pins are provided by this processor.
There is an on-board 2.4GHz radio peripheral used to provide Bluetooth and custom radio capabilities via an off-chip aerial.

| item          | details
| ---           | ---
| Model         | [Nordic nRF52833](https://www.nordicsemi.com/Products/Low-power-short-range-wireless/nRF52833)
| Core variant  | [Arm Cortex-M4 32 bit processor with FPU](https://developer.arm.com/ip-products/processors/cortex-m/cortex-m4)
| Flash ROM     | 512KB
| RAM           | 128KB
| Speed         | 64MHz
| Debug         | [SWD](https://infocenter.nordicsemi.com/index.jsp?topic=%2Fps_nrf52833%2Fdif.html), [J-Link/OB](https://www.segger.com/products/debug-probes/j-link/models/j-link-lite/j-link-lite-cortex-m/)
| More Info     | [Software](../../software), [NRF52 datasheet](https://infocenter.nordicsemi.com/index.jsp?topic=%2Fstruct_nrf52%2Fstruct%2Fnrf52833.html&cp=3_1)

### Bluetooth Wireless Communication

The on-board 2.4GHz supports Bluetooth communications via the [Nordic S113 SoftDevice](https://www.nordicsemi.com/Software-and-Tools/Software/S113), which provides a fully qualified Bluetooth low energy stack.
This allows the micro:bit to communicate with a wide range of Bluetooth devices, including smartphones and tablets.

| item          | details
| ---           | ---
| Stack         | Bluetooth 5.1 with Bluetooth Low Energy(BLE)
| Band          | 2.4GHz ISM (Industrial, Scientific and Medical) 2.4GHz..2.41GHz
| Channels      | 50 2MHz channels, only 40 used (0 to 39), 3 advertising channels (37,38,39)
| Sensitivity   | -93dBm in Bluetooth low energy mode
| Tx Power      | -40dBm to 4dBm
| Role          | [GAP Peripheral & GAP Central](https://bluetooth-developer.blogspot.com/2016/07/microbit-and-bluetooth-roles.html)
| Congestion avoidance | Adaptive Frequency Hopping
| Profiles      | [BBC micro:bit profile](https://lancaster-university.github.io/microbit-docs/ble/profile/)
| More Info     | [Bluetooth](../../bluetooth)

### Low level radio communications

The on-board 2.4GHz transceiver supports a number of other radio communications standards, on which we build the microbit-radio protocol
This protocol provides a very simple small-packet broadcast radio interface between other devices that support it, such as other micro:bit devices.
The 'radio' interface that appears in a number of the languages on the micro:bit is built on top of this protocol.
Additionally, the micro:bit runtime software adds a 'group code' to each data payload, allowing for simple user managed device addressing and filtering to take place.

| item          | details
| ---           | ---
| Protocol      | [Micro:bit Radio](https://lancaster-university.github.io/microbit-docs/ubit/radio)
| Freq band     | 2.4GHz
| Channel rate  | 1Mbps or 2Mbps
| Encryption    | None
| Channels      | 80 (0..80)
| Group codes   | 255
| Tx power      | Eight user configurable settings from 0(-30dbm) to 7 (+4dbm)
| Payload size  | 32 (standard) 255 (if reconfigured)
| More Info     | [Micro:bit Radio](https://lancaster-university.github.io/microbit-docs/ubit/radio)

### Buttons

The two buttons on the front of the micro:bit, and the one button on the back, are tact momentary push-to-make buttons. The back button is connected to the KL27 interface processor and to the NRF52 processor for system reset purposes. This means that the application will reset regardless of if it is powered from USB or from battery.

Front buttons A and B can be programmed in the user application for any purpose.
A and B are debounced by software, which also includes short press, long press, and 'both A+B' press detection. Buttons operate in a typical inverted electrical mode, where a pull-up resistor ensures a logical '1' when the button is released, and a logical '0' when the button is pressed.
Both A and B buttons are connected to GPIO pins that are also accessible on the micro:bit edge connector.

| item          | details
| ---           | ---
| Type          | 2 tactile user buttons, 1 tactile system button
| Debounce      | (A & B) software debounced, 54ms period
| Pullup        | (A & B) external 4K7, (System) 10K

### Display

The display is a 5x5 array of LEDs.
It is connected to the micro:bit as a 5x5 matrix.
Runtime software repeatedly refreshes this matrix at a high speed, such that it is within the user persistence of vision range, and no flicker is detected.
This LED matrix is also used to sense ambient light, by repeatedly switching some of the LED drive pins into inputs and sampling the voltage decay time, which is roughly proportional to ambient light levels.

| item          | details
| ---           | ---
| Type          | miniature surface mount red LED
| Physical structure | 5x5 matrix
| Electrical structure | 5x5
| Intensity control | Software controlled up to 255 steps
| Sensing | ambient light estimation via software algorithm
| Sensing Range | TBC, 10 levels from off to full on
| Colour sensitivity | red centric, red is 700nm

### Motion sensor

The micro:bit has a combined accelerometer and magnetometer chip that provides 3-axis sensing and magnetic field strength sensing.
It also includes some on-board gesture detection (such as fall detection) in hardware, and additional gesture sensing (e.g. logo-up, logo-down, shake) via software algorithms.
A software algorithm in the standard runtime uses the on-board accelerometer to turn readings into a board orientation independent compass reading.
The compass must be calibrated before use, and the calibration process is automatically initiated by the runtime software.
This device is connected to the application processor via the I2C bus.

The micro:bit has a footprint for two different motion sensors: one made by ST (the LSM303AGR) and one by NXP (FXOS8700CQ). The micro:bit DAL supports both of these sensors, detecting them at runtime. Only one sensor will ever be placed.

| item          | details
| ---           | ---
| Model         | [LSM303AGR](https://www.st.com/en/mems-and-sensors/lsm303agr.html)
| Features      | 3 magnetic field and 3 acceleration axes , 2/4/8/16g ranges
| Resolution    | 8/10/12 bits
| On board gestures | 'freefall'
| Other gestures | Other gestures are implemented by software algorithms in the runtime.

### Temperature sensing

The NRF52 application processor has an on-board core temperature sensor.
This is exposed via the standard runtime software, and provides an estimate of ambient
temperature.

| item          | details
| ---           | ---
| Type          | on-core NRF52
| Sensing range | -40C .. 105C
| Resolution    | 0.25C steps
| Accuracy      | +/-5C (uncalibrated)
| More Info     | [DAL Thermometer](https://lancaster-university.github.io/microbit-docs/ubit/thermometer/)

### Speaker

In addition to outputting sound via PWM on the pins, the micro:bit has a PCB mounted magnetic speaker to which sound output is mirrored.

| item          | details
| ---           | ---
| Type          | JIANGSU HUANENG MLT-8530
| SPL           | 80dB @ 5V, 10cm
| Self-resonant frequency | 2700Hz
| More Info     | [Datasheet](https://datasheet.lcsc.com/szlcsc/1811151451_Jiangsu-Huaneng-Elec-MLT-8530_C94599.pdf)

### Microphone

An on-board MEMs microphone provides a sound input to the micro:bit and a built in LED indicator on the front of the board shows the user when this is powered.

The microphone has an external bias circuit of 33K:1K (power to ground) and is AC-coupled to the microphone input pin.

| item          | details
| ---           | ---
| Type          | Knowles SPU0410LR5H-QB-7 MEMS
| Sensitivity   | -38dB ±3dB @ 94dB SPL
| SNR           | 63dB
| AOP           | 118db SPL
| Frequency range | 100Hz ~ 80kHz
| Polar pattern | Omnidirectional
| More Info     | [Datsheet](https://www.knowles.com/docs/default-source/model-downloads/spu0410lr5h-qb-revh32421a731dff6ddbb37cff0000940c19.pdf?Status=Master&sfvrsn=cebd77b1_4)

### General Purpose Input/Output Pins

The edge connector brings out many of the GPIO circuits of the application processor. Some of these circuits are shared with other functions of the micro:bit, but many of these extra circuits can be re-allocated to general purpose use if some software features are turned off.

| item          | details
| ---           | ---
| Rings         | 3 large IO rings and two large power rings, 4mm plug and crocodile clip compatible
| GPIO features | 19 assignable GPIO pins
||        2 are dedicated to the external I2C interface
||        6 are used for display or light sensing feature
||        2 are used for on-board button detection
||        1 is reserved for an accessibility interface
||        19 may be assigned as digital input or digital output
||        19 may be assigned for up to 3 simultaneous PWM channels
||        19 may be assigned for 1 serial transmit and 1 serial receive channel
||        6 may be assigned as analog input pins
||        3 may be assigned to an optional SPI communications interface
||        3 may be assigned for up to 3 simultaneous touch sensing inputs
|ADC resolution | 10 bit (0..1023)
| Edge Connector| [Edge connector](/hardware/edgeconnector/)
| Pitch | 1.27mm, 80 way double sided.
| Pads| 5 pads, with 4mm holes

### Power supply

Power to the micro:bit may be provided via 5V on the USB connector, or via a 3V battery plugged into the JST connector. It is also possible (with care) to power the micro:bit from the 3V /GND rings on the edge connector. The 3V /GND rings at the bottom can be used to supply power to external circuits. The board uses an LDO specified up to 300mA, with thermal cut-out for short circuit protection.

| item          | details
| ---           | ---
| Operating range | 1.8V .. 3.6V
| Operating current (USB and battery)   | 300mA max
| On-board Peripherals budget | 90mA
| Battery connector | JST S2B-PH-SM4-TB
| Max current provided via edge connector | 190mA
| More Info | [Power supply](../powersupply)

### Interface

The interface chip handles the USB connection, and is used for flashing new code to the micro:bit, sending and receiving serial data back and forth to your main computer.

| item          | details
| ---           | ---
| Model         | [MKL27Z256VFM4](https://www.nxp.com/part/MKL27Z256VFM4#/)
| Core variant: | [Arm Cortex-M0+](https://www.arm.com/products/processors/cortex-m/cortex-m0plus.php)
| Flash ROM     | 256KB (128kB reserved for non-volatile storage)
| RAM           | 16KB
| Speed         | 48MHz
| Debug capabilities | [SWD](https://infocenter.nordicsemi.com/index.jsp?topic=%2Fstruct_nrf52%2Fstruct%2Fnrf52820.html)
| More Info | [DAPLink](/software/daplink-interface/), [KL27 reference manual (behind login)](https://www.nxp.com/webapp/Download?colCode=KL27P64M48SF6RM) [KL27 datasheet](https://www.nxp.com/docs/en/data-sheet/KL27P64M48SF6.pdf)

### USB communications

The micro:bit has an on-board USB communications stack, that is built into the firmware of the interface chip. This stack provides the ability to drag and drop files onto the
MICROBIT drive in order to load code into the application processor. It also allows serial data to be streamed to and from the micro:bit application processor over USB to an external host computer, and supports the CMSIS-DAP specification for host debugging of application programs.

| item          | details
| ---           | ---
| Connector     | USB micro, MCR-B-S-RA-SMT-CS5-TR
| USB version   | 2.0 Full Speed device
| Speed         | 12Mbit/sec
| USB classes supported | [Mass Storage Class (MSC)](https://en.wikipedia.org/wiki/USB_mass_storage_device_class)
|    | [Communications Device Class (CDC)](https://en.wikipedia.org/wiki/USB_communications_device_class)
|    | [CMSIS-DAP HID & WinUSB](https://arm-software.github.io/CMSIS_5/DAP/html/index.html)
|    | [WebUSB CMSIS-DAP HID](https://wicg.github.io/webusb/)
| More Info | [DAPLink](/software/daplink-interface/)

### Debugging

The interface processor can be used with special host tools to debug code that is running on the application processor. It connects to the application processor via  2-pin Serial Wire Debug (SWD). The interface processor code can also be debugged via its internal SWD software debug interface, for example to load initial bootloader code into this processor at manufacturing time, or to recover a lost bootloader.

| item          | details
| ---           | ---
| Protocol      | Serial Wire Debug (SWD)
| Options       | DAPLink (CMSIS-DAP)
|               | JLink/OB (via different firmware)

### Mechanical

We have some [nice 2D and 3D CAD drawings and models of the micro:bit](https://github.com/microbit-foundation/microbit-reference-design) including all the important dimensions. These models can be used as a basis for generating really nice marketing and project images of the micro:bit, but also as a basis for accurate manufacture of attachments e.g. via 3D printing.

| item          | details
| ---           | ---
| Dimensions    | 51.60mm(w) 42.00mm(h) 11.65mm(d), button depth to board 4.55mm, speaker depth to board 3.00mm, JST connector to board 5.50mm
| Weight        | TBC

## Further information

- [BBC Technical Specifications](http://www.bbc.co.uk/mediacentre/mediapacks/microbit/specs)

- [I2C specification (behind login)](https://www.nxp.com/webapp/Download?colCode=UM10204&location=null)

- [SPI 'specification'](https://en.wikipedia.org/wiki/Serial_Peripheral_Interface_Bus)

- [Fritzing diagram, contributed by Kok Ho Huen](/docs/hardware/assets/Microbit.fzpz.zip)
