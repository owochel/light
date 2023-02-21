## Addressable LED Candle

This project asks us to uses an arduino and [NeoPixel jewel](https://www.adafruit.com/product/2226) to create a candle.
I chose to use a Nano 33 BLE and a photocell to accomplish a torch that "borrows" light.

The borrowing parts were straightforward enough. I am able to program the turning on process pretty fast.
I spend some time trying to think of ways I can turn the torch off because the photocell won't be able to read a difference in light changes when the NeoPixel is on.
As Ijon suggested, there are lots of sensors in BLE that could come in handy. I ended up using the accelerometer in the BLE to program a state-change.
The code can be found [here](https://github.com/owochel/light/blob/main/candle/candle.ino).

The limitation of this project is that it requires some tuning in every environment. The changes in environmental lights and/or lending light sources requires a different threshold value in the code.

See the video below.

<iframe width="640" height="360"
  src="https://user-images.githubusercontent.com/51350490/220415147-8cc454b8-c854-4994-9675-4594c63cf6cb.mp4">
</iframe>
