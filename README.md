[<img src="https://www.raspberrypi.com/documentation/computers/images/4-model-b.jpg" style="width: 650px; height: auto;" alt="Raspberry Pi 4 Model B" title="Raspberry Pi 4 Model B">](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/)

# Beyond the Basics: Powering Your Raspberry Pi 4 Model B with the 40-Pin Header

While the Raspberry Pi 4 Model B offers convenient power options like USB-C and Power over Ethernet (PoE), this guide explores a more versatile approach: directly powering your Pi through its 40-pin header. This method is ideal for mobile electronics and robotics projects.

# Hardware Used In This Guide

- (1x) [Raspberry Pi 4 Model B](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/ "raspberrypi.com")
- (1x) [LM350 3 Amp Adjustable Voltage Regulator](https://www.digikey.com/en/products/detail/texas-instruments/LM350T-NOPB/8901 "digikey.com")
- (1x) [240 Ohm 1/4 Watt Resistor](https://www.digikey.com/en/products/detail/yageo/MFR-25FBF52-240R/9138101 "digikey.com")
- (1x) [820 Ohm 1/4 Watt Resistor](https://www.digikey.com/en/products/detail/yageo/MFR-25FBF52-820R/9138207 "digikey.com")
- (1x) [10 Microfarad Capacitor](https://www.sparkfun.com/products/523 "sparkfun.com")
- (1x) [100 Microfarad Capacitor](https://www.sparkfun.com/products/96 "sparkfun.com")
- (1x) [TO-220 Heatsink](https://www.sparkfun.com/products/121 "sparkfun.com")
- (1x) [Lectron Pro 7.4V 2000mAh 25C Lipo Battery with XT60 Connector](https://commonsenserc.com/product_info.php?cPath=37_213&products_id=7180 "commonsenserc.com")
- (1x) [XT60 Charging Adapter with Banana Plugs](https://commonsenserc.com/product_info.php?cPath=187&products_id=4741 "commonsenserc.com") or (1x) [XT60 Connectors - Male/Female Pair](https://www.sparkfun.com/products/10474 "sparkfun.com")

# Safety Disclaimer

**Always exercise caution when working with electronics.**

- **Risk of Electrical Shock:** Improper handling of electrical components can lead to serious injury or death.
- **Heat Dissipation:** Ensure that components, especially those generating heat (like voltage regulators), are adequately cooled to prevent overheating and potential fires.
- **Battery Safety:** Handle and charge batteries according to manufacturer's instructions. Avoid overcharging, over-discharging, or short-circuiting batteries.
- **Power Supply:** Use a reliable power supply suitable for your project. Avoid overloading circuits.

**It is recommended to seek guidance from experienced individuals or consult relevant safety standards before undertaking any electronics project.**

# Unlocking Flexibility: Setting the Output Voltage with Resistors

The LM350 3 Amp Adjustable Voltage Regulator offers the ability to fine-tune its output voltage to your specific needs. This is achieved using two external resistors, designated R1 and R2. The formula below lets you calculate the precise output voltage based on the chosen resistor values:

```
Output Voltage = 1.25 * (1 + R2 / R1)
```

In this guide, we'll be using a 240 ohm resistor for R1 and an 820 ohm resistor for R2. This specific combination delivers an output voltage around 5.52 volts, perfectly suitable for powering your Raspberry Pi 4 Model B.

Need to adjust the output voltage for a different application? No problem! Check out this [online resistor calculator](https://www.tmatlantic.com/encyclopedia/index.php?ELEMENT_ID=53993 "online resistor calculator") to explore various resistor combinations and their corresponding output voltages.

# Why 5.52 Volts? Understanding Our Target Voltage

According to the Raspberry Pi 4 Model B's [online datasheet](https://datasheets.raspberrypi.com/rpi4/raspberry-pi-4-datasheet.pdf "raspberrypi.com"), the ideal voltage range falls between 4.75 volts and 5.25 volts, with an absolute maximum of 6 volts. When using the recommended [Raspberry Pi 15 Watt USB-C Power Supply](https://www.raspberrypi.com/products/type-c-power-supply/ "raspberrypi.com") to power the Raspberry Pi 4 Model B we observed 5.18 volts on the Pi's 5 volt pins. Reviewing the Pi's [online hardware schematic](https://datasheets.raspberrypi.com/rpi4/raspberry-pi-4-reduced-schematics.pdf "raspberrypi.com") also shows us that the Pi's 5 volt pins are connected directly to the power supplied by the Pi's USB-C connector.

Here's where the LM350 3 Amp Adjustable Voltage Regulator comes into play. During our tests with this regulator set to 5.25 volts (the recommended upper limit), we observed a potential voltage drop of up to a third of a volt when the Pi was under load. To compensate for this potential drop and ensure the Pi receives a consistent voltage within its ideal range, we opted for a target output voltage of 5.52 volts with the LM350.

# Building the Power Supply Circuit

To build the power supply circuit successfully, we need to first identify each of the LM350 3 Amp Adjustable Voltage Regulator's pins.

<img src="https://www.jotrin.com/userfiles/images/techs/LM350%20IC.png" style="width: 650px; height: auto;" alt="LM350 3 Amp Adjustable Voltage Regulator" title="LM350 3 Amp Adjustable Voltage Regulator">

<img src="https://github.com/Theseus88/Powering-Your-Raspberry-Pi-4-Model-B-with-the-40-Pin-Header/blob/main/LM350%20circuit.svg" style="width: 445px; height: 210px;" alt="LM350 Power Supply Circuit" title="LM350 Power Supply Circuit">

# Bringing it to Life: Powering Your Pi with the Circuit

[<img src="https://commonsenserc.com/images/2S2000-25X_1000.jpg" style="width: 650px; height: auto;" alt="Lectron Pro 7.4V 2000mAh 25C Lipo Battery with XT60 Connector" title="Lectron Pro 7.4V 2000mAh 25C Lipo Battery with XT60 Connector">](https://commonsenserc.com/product_info.php?cPath=37_213&products_id=7180)

[<img src="https://commonsenserc.com/images/BP2XT60M_700.jpg" style="width: 650px; height: auto;" alt="XT60 Charging Adapter with Banana Plugs" title="XT60 Charging Adapter with Banana Plugs">](https://commonsenserc.com/product_info.php?cPath=187&products_id=4741)

[<img src="https://cdn.sparkfun.com/assets/parts/4/9/7/1/10474-02.jpg" style="width: 300px; height: auto;" alt="XT60 Connectors - Male/Female Pair" title="XT60 Connectors - Male/Female Pair">](https://www.sparkfun.com/products/10474)

<img src="https://www.raspberrypi.com/documentation/computers/images/GPIO-Pinout-Diagram-2.png" style="width: 650px; height: auto;" alt="GPIO and the 40-pin header" title="GPIO and the 40-pin header">

# Further Reading
- [Understandings LM350: A Comprehensive Guide to Adjustable Voltage Regulators](https://www.jotrin.com/technology/details/lm350-voltage-regulator "jotrin.com")
