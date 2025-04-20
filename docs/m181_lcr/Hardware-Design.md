---
title: Hardware Design
---
## Core Concept
- A fixed sine wave voltage to DUT via series resistor and then measure the voltage drop(V), current(I) flow and VI phase difference to calculate the complex impedance.
- With formula Inductance(L), Capacitance (C) and Resistance(R) of DUT can be derived from this complex impedance.
> Dissipation factor(D), Equivalent Series Resistance(ESR) also can calculated.

<figure markdown="span">
  ![Image title](assets/HW_concept4.png){ width="400" }
  <figcaption>Cor Concept</figcaption>
</figure>

<figure markdown="span">
  ![Image title](assets/HW_concept1.png){ width="400" }
  <figcaption>Implemented Method</figcaption>
</figure>

## Capability
  Manufacturer(JYETech) mentioned specification

<figure markdown="span">
  ![Image title](assets/HW_Specs1.png){ width="400" }
</figure>
>Image source [link](https://jyetech.com/m181-lcr-meter/)

## Design files
- Schematics file @ [link](https://jyetech.com/wp-content/uploads/Schematic_M181.pdf)
- Assembly Guide @ [link](https://jyetech.com/wp-content/uploads/M181_AssemblyGuide.pdf)

## Block-wise Explanation
### Power Tree
1. USB Input voltage 5V
2. Charge pump TPS60403 IC generate dual voltage +/- 5V
3. LDO to generate 3.3V

### Signal Generator (DAC)
 To generate sine wave with fixed frequency DAC is required. This MCU doesn't have inbuilt DAC

> Detailed explain found at [link](https://www.tek.com/en/blog/tutorial-digital-analog-conversion-r-2r-dac).

* R-2R Ladder (DAC) form with digital pin. 
* 8-bit Resolution by 8-pin.
* DAC connect to Voltage follower (U4C).
* Next Two RC Low pass filter ($F_c=723Hz$) connected
* Here output tapped for AFC(Automatic Factor Correction) which is connected to ADC of MCU.
* Further RC High pass filter ($F_c=312Hz$) which also block DC & again voltage follower (U4D) to provide output.

### Trans-impedance amplifier
The fundamental idea in this technique is to convert the current ($I_X$) through DUT into voltage ($V_O$).
$$
V_O = I_X * R_F
$$

### Kelvin (4-wire) measurement
* Dedicate 2-wire to measure the voltage across DUT.
* Here a switch used to toggle between voltage and current measurement.

<figure markdown="span">
  ![Image title](assets/HW_concept31.png){ width="400" }
</figure>
>Image source [link](https://www.allaboutcircuits.com/textbook/direct-current/chpt-8/kelvin-resistance-measurement/)

[**Open Point**] - Calibration need to preformed to compensate the probe error.

### Amplifier Section
- Instrument amplifier(U2A, U2C, U2D) with fixed gain of 5.25
- Non-Inverting amplifier with gain 100 and also adds offset voltage (-1.77V) will be connected to ADC of MCU
- Both Amplitude via Gain selection(voltage divider) and High pass filter(DC block)
- Via GS pin, the Gain selected between pass with unity gain and attenuate in $\frac{1}{101}$ factor.

## Miscellaneous Section
1. I2C 128x64 resolution SSD1306 display.
2. Three push button for user input / control.
3. SWD signal are terminated J3 Header.
4. UART signal are connected to CH340N USB serial.