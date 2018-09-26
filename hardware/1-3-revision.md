---
layout: page
order:
title: Previous micro:bit revision
heading: Previous micro:bit revision
description: Image of front and back of micro:bit with individual accelerometer and magnetometer
permalink: /hardware/previous-revision/
ref: 1-3
lang: en
assigned-to: markw
review-with: jonnya
---

# Overview

This page details the hardware details of the previous micro:bit revision, showing the layout of the individual accelerometer and magnetometer components.

![img](/docs/hardware/assets/microbit-overview.png)



## Accelerometer

The accelerometer is a separate chip that provides 3-axis sensing.
It also includes some on board gesture detection (such as fall detection) in hardware,
and additional gesture sensing (e.g. logo-up, logo-down, shake) via software algorithms.
It is connected to the application processor via the I2C bus.

| item          | details
| ---           | ---
| Model         | [Freescale MMA8653FC](http://www.nxp.com/products/sensors/accelerometers/3-axis-accelerometers/2g-4g-8g-low-g-10-bit-digital-accelerometer:MMA8653FC)
| Features      | 3 axis, 2/4/8g ranges
| Resolution    | 10 bits (0..1023)
| Max output data rate | 800Hz
| On board gestures | 'freefall'
| Other gestures | Other gestures are implemented by software algorithms in the runtime.


## Magnetometer

The magnetometer is a separate chip that provides magnetic field strength sensing.
A software algorithm in the standard runtime uses the on board accelerometer
to turn these readings into a board orientation independent compass reading.
The compass must be calibrated before use, and the calibration process is automatically
initiated by the runtime software.
This device is connected to the application processor via the I2C bus.

| item          | details
| ---           | ---
| Model         | [Freescale MAG3110](http://www.nxp.com/products/sensors/magnetometers/sample-data-sets-for-inertial-and-magnetic-sensors/high-accuracy-3d-magnetometer:MAG3110)
| Max update rate | 80Hz
| Full Scale range | 1000uT
| Sensitivity | 0.10uT
