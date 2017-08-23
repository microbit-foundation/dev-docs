---
layout: page
order:
title: Edge Connecgtor
heading: Edge Connector
description: The edge connector provides a set of pads and pins to allow interfacing to other circuits and components.
permalink: /hardware/edgeconnector/
ref: hardware
lang: en
assigned-to: davidw
review-with: jonnya
---


# Overview

The edge connector on the micro:bit is used to connect to external circuits and components.

It has 5 rings for using with 4mm banana plugs or crocodile clips. 3 of these are for
general purpose input and output, and two are connected to the micro:bit power supply.

The small strips in between are also connected to various signals, and with the right connector
you can get access to quite a few different signals.

Only the pins on the front are connected to signals. The back rings are connected to the
front rings, but the back small strips are unconnected.


## Edge Connector Pins

![edge connector](/docs/hardware/assets/edge_connector.svg)


## PCB Connector

The PCB connector is an 80 way * 1.27mm pitch double sided connector.

You can buy this connector from a number of sources.

At a pinch, it is also possible to use an old PCI edge connector from a PC motherboard,
as the pitch is the same (but it is slightly wider).

There is a good mechanical data-sheet for the right angle PCB edge connector
[here](http://resources.coolcomponents.co.uk/CONNECTORS/10156.pdf)


## Edge Connector Data-Sheet

[Technical Data sheet](../edgeconnector_ds/)

[micro:bit CAD resources](https://www.kitronik.co.uk/blog/bbc-microbit-cad-resources/)

[2D CAD drawing](https://www.kitronik.co.uk/pdf/bbc_microbit_mechanical_datasheet_V2.pdf)
This drawing has all the key micro:bit dimensions, including the pin spacing of the
various pins of the edge connector on the micro:bit board.

[STP file](https://www.kitronik.co.uk/zip/Microbit_STEP.zip) This file is a 3D CAD
file for use with 3D modelling software.

[STL file](https://www.kitronik.co.uk/zip/Microbit_STL.zip) This file can be used
with 3D printers.

[SAT file](https://www.kitronik.co.uk/zip/Microbit_SAT.zip) This file can be used
with ACIS modeller.


## Can You Find a Better Connector?

There are a number of suppliers of edge connector for the micro:bit, in various forms,
such as a right angle through-hole, a stand-up through-hole and a stand-up surface
mount. There are a wide range of connector manufacturers that sell thousands of
different types of connectors.

There are also some nice ideas that have surfaced in the community such as using just
the right size of countersunk or cheese-head bolt, or even 3D printed inserts.

Can you help to find or design a better connection solution to the micro:bit
edge connector? Share your designs and discoveries with us!


# Links

[STP viewers](http://3d-viewers.com/step-viewer.html)

[ACIS Modeller](http://www.spatial.com/products/3d-acis-modeling)
