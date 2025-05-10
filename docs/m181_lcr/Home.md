---
title: Introduction
---

This document provides an overview of the [M181 LCR Meter](https://github.com/Jaishankar872/LCR_Meter_Proto_M181) GitHub repository.

   Goal is to develop only the Firmware for M181 LCR Meter made by JyeTech. Hope to provide understanding in basics of LCR Meter.

## Hardware - M181 LCR Meter 
- Official product page link [here](https://jyetech.com/m181-lcr-meter/)
- I have purchased from Banggood, buying link is [here](https://www.banggood.in/Jyetech-M181-LCR-Meter-18101K-DIY-Kit-100Hz-1KHz-Test-Frequency-High-precision-Small-Value-Inductance-Resistance-and-Capacitance-Measurement-Module-reviews-p2017117.html)

## Setup for programming
- Programmer → Raspberry pi debug probe (**modified)
- Interface  → SWD
- IDE        → PlatformIO
- Framework  → STM32Cube

**Note**: Still this firmware under development.
## Tasks to be completed
- [x] Zero Padding function (ADC offset)
- [ ] Auto calibration option
- [ ] Improve the phase difference calculation
- [ ] Fix issue in missing to capture the button press input
- [ ] Correct the current waveform crop issue in auto gain selection. 
- [ ] Add option for Parallel calculation ($C_p$,$L_p$) 

## Context

Explore the following sections for detailed information:

* [Hardware Description](/m181_lcr/Hardware-Design/)  
  Learn about the hardware design and components of the M181 LCR Meter.

* [Frontend Driver](/m181_lcr/Firmware-Design/)  
  Understand the firmware design and driver implementation.

* [Signal Processing](/m181_lcr/Signal-Processing)  
  Dive into the signal processing techniques used in the system.

* [Impedance Calculation](/m181_lcr/Impedance-Calculation)  
  Discover the methods for calculating impedance with the M181 LCR Meter.

## Credits
* [JYETech](https://jyetech.com/m181-lcr-meter/)
* [Maximilian Gerhardt](https://github.com/maxgerhardt)