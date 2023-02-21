---
layout: post
title: "12v controller"
date: 2023-02-08 16:32:58 -0500
categories: jekyll update
---

We are making a 12v controller that allows you to manipulate 12v bulbs.
I'm using the [itp labs for FQP30N06L MOSFET](https://itp.nyu.edu/physcomp/labs/motors-and-transistors/using-a-transistor-to-control-high-current-loads-with-an-arduino/) for the circuit.

The potentiometer readings is never stable. While it is not noticeable when the bulb is bright, I found it flickers when the pot is tunned down close to off. I added a tiny resistor at the output to reduce the voltage, so it won't turn on the bulb when it is close to zero.

The code can be found [here]({{ site.codeurl}}\_12v/12v/12v.ino ).

For the bulb input, I used a audio jack port I found from the junk shelf. The port has two plugs that is easy to attach/remove. To reduce the chances of damage and shorts happening behind the soldering points, I also added a backing and four feet for the board.

![This the picture of the board.]({{ site.asseturl }}/\_12v/side.jpg)

See video for demo

<iframe width="360" height="640"
  src="https://user-images.githubusercontent.com/51350490/220451484-515fa4e7-223d-464e-8f79-75b00d273631.mp4">
</iframe>

NOTE from after class:
The resistor ended up becoming a huge problem. It altered the current went through the bulb that results in malfunctions for all the other bulbs other than the corn cob. Lesson learned: do not alter the circuit if you don't know what you are doing.

Also, Tom told me that the GND and Volt pins on the MOSFET are too close together. Even if the soldering points are not touching, the current running through the points might short the circuit.
