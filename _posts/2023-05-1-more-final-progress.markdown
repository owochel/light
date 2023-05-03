---
label: assignments
layout: post
title: "more final progress"
date: 2023-05-01 15:50:58 -0500
categories: jekyll update
---

I cross into problems with Attiny85 memory limit. Even if I use a smaller resolution like 8 resulting in a 25-int-long level table, the Attiny85 is still be too small to store all the values.

I found a way around that. The curve is only being used on the top lamp which dims in the course of 30 min. And because the curve is only being calculated based on time -- which is a stable factor in comparison to a reading of a sensor -- I could calculate the level on the fly.

Here's the final code that's being uploaded to the Attiny. You will see that the value are mapped on the course of 30 mins and the value of the analogWrite are being calculated every time the loop comes back to the spot.

```
int lightTop=0;
int lightBot=1;

void setup() {
  // set  the transistor pin as output:
  pinMode(lightBot, OUTPUT);
  pinMode(lightTop, OUTPUT);
  digitalWrite(lightBot, HIGH);
}

void loop() {
  long currentTime = millis();
  if(currentTime<1800001){
  // Do something while waiting for 30 minutes
    int index = map(currentTime, 0, 1800000, 255, 0);  // map the time to an index in the range of 0 to 255
    float scalingFactor = (256 * log10(2)) / (log10(256));
    analogWrite(lightTop, pow(2, index / scalingFactor) - 1);
  }else{
    analogWrite(lightTop, LOW);
  }

}
```

Here's a video of this initial trail. This is a 10 min time lapse.

<iframe width="900" height="500"
  src="
https://user-images.githubusercontent.com/51350490/235798392-c0b212e6-0e5a-461b-9d0a-508440b5f019.mp4">
</iframe>

However, programming the attiny has not been smooth. I don't know what could be causing this, but a couple of other people are also crossing into problems where the console will complain:

```
avrdude: ser_recv(): programmer is not responding
```

I ended up using Chumou's computer to upload the code. And this problem has been blocking me too long so that I've decided to go with a portoboard instead of the cut PCB.

Another calculation that I didn't plan but should have is the current consumption. Each bulb we bought drain 0.2 Amps, the power supply we used output 2000 milliamps. So luckily, we are way above the value.

Here's a video of this soldered circuit trail (also with 2 bulbs). This is the time lapse to the point the light turns off.

<iframe width="900" height="500"
  src="
https://user-images.githubusercontent.com/51350490/236008609-9b2b09e4-b816-4a60-827e-11f9876f2aa1.mp4
">
</iframe>

Fabrication Stuff:
Leia did some test for the plywood bending!

<iframe width="640" height="1137.8"
  src="
https://user-images.githubusercontent.com/51350490/235799788-68f65712-7cb4-412c-825e-9a75976743b5.mp4">
</iframe>

This bend is the final design we decided to go with. Leia also sand and oiled the wooden frame.

After the wood parts are done. We designed the acrylic parts based on the wood frame since the bends are not perfectly 90 degree, and we want the acrylic to fully cover the plywood edge. We traced the frame on physical papers and traced the physical sketch in Illustrator for laser cutter.

Here's the the general design. Later we added ear holes to make it easier to put the bulb in.

![The screenshot of the Illustrator file.]({{ site.asseturl }}/\_final/acrylic.png)

On the traced file, it is pretty visible that the bend is not a perfect bend once we traced it.

In the original plan, we wanted a shade/diffusor edge on the top. In the process, we noticed that the diffusor isn't really diffusing as much as the wall is. The bulb is shining directly on the wall to shape the scallop. However, we still like the acrylic as a visual indicator of a lamp. Therefore, we went for the acrylic bending route.

![The screenshot of the Illustrator file.]({{ site.asseturl }}/\_final/bend.png)

From there, we basically cut the acrylic piece. Noticed that the wood bend shrunk more over night, so that our acrylic pieces doesn't really fit exactly. Assembled everything, including the circuit. Attached the protoboard on the lamp body. Sand down the edges of the acrylic.

Here's a final photo of the lamp against the wall:
![The screenshot of the Illustrator file.]({{ site.asseturl }}/\_final/final.png)

There are too many things we learned in the process. Here's compilation of them.

- Taking measurement in the right space is very helpful and important
- Splitting tasks and delegating is very helpful
- With circuit design, PCB should have been the last step.
- Bending plywood is both easier than harder than we anticipated
  - The process is very simple, but doing the math is hard
  - Doing the curved edge requires a better calculation of the radius
  - The wood shrinks and shrinks unevenly after bending (could be from the glue).
- Switch attachment and other parts attachment could have comes before designing the wood structure
- Designing for non-precise parts are way harder and still results in non-flush-fit
  - We did the measurements, then trace on paper, then trace in Illustrator. It worked, but it's not a flush fit.
- Sides of acrylic matters when it comes to satin acrylic
- Next time doing acrylic bending, we should have a mold made for the form.
