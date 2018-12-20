---
layout: page
order:
title: Edge Connector
heading: Edge Connector
description: The edge connector provides a set of pads and pins to allow interfacing to other circuits and components.
permalink: /hardware/edgeconnector/
ref: hardware
lang: en
---


# Overview

The edge connector on the micro:bit is used to connect to external circuits and components.

There are 25 strips/pins including 5 rings for using with 4mm banana plugs or crocodile clips. 3 of these rings are for general purpose input and output (GPIO), and two are connected to the micro:bit power supply.

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

There is a good [mechanical data-sheet](http://resources.coolcomponents.co.uk/CONNECTORS/10156.pdf) for the right angle PCB edge connector available from Cool Components.



## Edge Connector Data-Sheet

[Technical Data sheet](../edgeconnector_ds/)

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

## Can You Find a Better Connector?

There are a number of suppliers of edge connector for the micro:bit, in various forms,
such as a right angle through-hole, a stand-up through-hole and a stand-up surface
mount. There are a wide range of connector manufacturers that sell thousands of
different types of connectors.

There are also some nice ideas that have surfaced in the community such as using just
the right size of countersunk or cheese-head bolt, or even 3D printed inserts.

Can you help to find or design a better connection solution to the micro:bit
edge connector? Share your designs and discoveries with us!

<div class="container">
     <h2>
      <span>Third Party Connectors</span>
      <a href="http://github.com/microbit-foundation/dev-docs/edit/master/hardware/edgeconnector.md" class="btn btn-info" role="button">Add your connector to our list</a>
    </h2>
</div>

<div class="container-fluid">
	<div class="row">
		<div class="col-md-12">
			<div class="col-md-6">
				<h3>Supplier</h3>
			</div>
			<div class="col-md-6">
				<h3>Product</h3>
			</div>
		<div class="col-md-12">
			<div class="col-md-6">
        <a href="http://www.dgyuliang.net"><img src="/docs/hardware/assets/cylconn-logo.png" alt="cylconn-logo" style="width: 50%;"></a>
			</div>
			<div class="col-md-6">
        <p> <a href="http://www.dgyuliang.net/d/file/Produtcs/Customized%20Connector/MICRO%20BIT%20Connector/84a0fe06b4296135d64139b5b4297ef3.pdf">Cylconn 90 degree connector</a></p>
        <p> <a href="http://www.dgyuliang.net/d/file/Produtcs/Customized%20Connector/MICRO%20BIT%20Connector/0d43030af84ade6fc3f00e242079c055.pdf">Cylconn 180 degree connector</a></p>
			</div>
		</div>
	</div>
</div>
