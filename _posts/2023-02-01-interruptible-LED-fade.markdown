---
layout: post
title: "Interruptible LED fade"
date: 2023-02-01 16:32:58 -0500
categories: jekyll update
---

Create a fading LED attached to a micro-controller. Your LED should be interruptible by either a pushbutton, analog input, or serial input. Your fade speed and fade curve are yours to determine. Don’t use programmable LEDs for this, keep it simple and use a single-channel source. Either fade an LED directly from your micro-controller, or use a DC source.

<iframe width="360" height="640"
  src="
https://user-images.githubusercontent.com/51350490/220447883-8ba788b7-cb66-48ec-864e-6b2e3052b02d.mp4">
</iframe>

In this assignment, I used both the simple linear curve and the exponential curve for the fade. The LED on the top of the video is the exponential curve fade and the bottom is the simple linear curve fade. As the video shows, the two types of fades are different.
The button on the top (brown) gradually turns the lights on, and the bottom turns the lights off. When both buttons are pressed at the same time, the bulbs show a loop where the two bulbs flash with the fade on to off and back to on.

[The code for the circuit view on github.]({{ site.codeurl}}\_PWM/fade/fade.ino )

![This the picture of the circuit.]({{ site.asseturl }}/\_PWM/circuit.jpg)
