# Idea
The goal of this project is to make a very cheap wifi repeater in a 1 button device to connect places in your house without good internet access.

The project is very simple, we only have to create a 3D printed well-looking case for the device and a simple electric circuit to power up an ESP-01 through 127v AC current as cheap as possible.

---

# How will we approach this?
The first thing to do is create a 127v AC to 3.3v DC converter, the most efficient way to do this is to use a transformer, the bad part of this is that there are not transformers available in all the mexican internet.

![](https://image.made-in-china.com/202f0j10EpuGeUCsOgcv/Efd-Type-Transformer-for-Cell-Phone-Charging-.jpg)

Another solution is to use 5v phone chargers that already include a 127v AC to 5v DC converter, but this will not be professional, and if you want a good charger that doesn't brake in less than a week, you will have to invert at least 2 dollars per charger and also we will have to reduce those 5v to 3.3v through a regulator.

![](https://http2.mlstatic.com/D_NQ_NP_816043-MLM31998925487_082019-O.jpg)