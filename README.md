# Idea
The goal of this project is to make a very cheap wifi repeater in a 1 button device to connect places in your house without good internet access.

The project is very simple, we only have to create a 3D printed well-looking case for the device and a simple electric circuit to power up an ESP-01 through 127v AC current as cheap as possible.

---

# How will we approach this?
The first thing to do is create a 127v AC to 3.3v DC converter, the most efficient way to do this is to use a transformer, the bad part of this is that there are not transformers available in all the mexican internet.

![](https://image.made-in-china.com/202f0j10EpuGeUCsOgcv/Efd-Type-Transformer-for-Cell-Phone-Charging-.jpg)

Another solution is to use 5v phone chargers that already include a 127v AC to 5v DC converter, but this will not be professional, and if you want a good charger that doesn't brake in less than a week, you will have to invert at least 2 dollars per charger and also we will have to reduce those 5v to 3.3v through a regulator.

![](https://http2.mlstatic.com/D_NQ_NP_816043-MLM31998925487_082019-O.jpg)

For all those reasons I think the best way to approach this is by creating a capacitive power supply, it will be cheap, it does not require many components and it will provide a 3.3v output, the disadvantages of this type of power supply is that they are much more dangerous than transformer power supplies, but since we will have the whole circuit in a closed package with no access to users, we should be fine, the second downside is that these transformerless power supplies can only work on low-power circuits, but since we are using an ESP-01 we only have to deal in the worst case with 200mah, so if our power supply can provide 200mah then we have no problem.

![](https://1.bp.blogspot.com/-5waie95tRaA/XP8lu3Ch-BI/AAAAAAAAB9E/hQiLJMz4JCUK3InRqlkK_I2ieNCABVHKQCLcBGAs/s1600/luz%2Bnocturna%2Bautomatica%2Bcon%2Bfunete%2Bcapacitiva.JPG)

---
# Building the circuit

To create our capacitive power supply we must use as its name says a capacitor that will limit the current that flows in the circuit, then we will have to transform that reduced AC current into a stable DC current, we will do this thanks to 4 diodes and an electrolytic capacitor to stabilize that current, in parallel with the capacitor we will use a zener diode to limit and maintain a stable voltage and then we could use a 3.3v ams1117 regulator with some capacitors or another zener diode and capacitors to keep it cheap.

Our ESP-01 consume 80mah in average (or at least this is what the datasheet says) I have an ESP-32 with a small LED which in fact consume much more than an ESP-01 and I got 90mah readings if my ESP-32 is working as a wifi server.
![](https://github.com/PaoloReyes254/ESP-01-LOW-COST-WIFI-REPEATER/blob/main/assets/Readings.jpg)
but as we said a 200mah power supply must be enouugh for all our requirements. To accomplish this we must calculate something called capacitive reactance which will give us the impedance that our capacitor produce in ohms and then with ohm's law we should be able to calculate the maximum current that our circuit will produce.

The formula to calculate capacitive reactance is:

![](https://github.com/PaoloReyes254/ESP-01-LOW-COST-WIFI-REPEATER/blob/main/assets/CapacitiveReactance.PNG)

As I live in Mexico we have 127v 60hz AC current and to get the capacitive reactance we need the capacity of the capacitor and the frequency of the country, but as I don't know which is the capacitance to get 200mah output, I can solve for the resistance that will be the capacitive reactance in ohm's law, such as follow:

![](https://github.com/PaoloReyes254/ESP-01-LOW-COST-WIFI-REPEATER/blob/main/assets/Resistance.PNG)

If we replace with our data we get:

![](https://github.com/PaoloReyes254/ESP-01-LOW-COST-WIFI-REPEATER/blob/main/assets/CapacitiveReactanceValue.PNG)