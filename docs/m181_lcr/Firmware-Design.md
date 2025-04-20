---
title: Software Frontend Driver
---

## Software Flow Diagram

<figure markdown="span">
  ![Image title](assets/SW_concept1.png){ width="700" }
</figure>

## Signal Generator (DAC)

The signal generator uses an R-2R ladder DAC connected to digital pins PB0 to PB7. Key features include:

- 8-bit resolution, providing 256 steps.
- A circular buffer for sine wave data, applied via interrupts.

### Timer 1

Timer 1 is responsible for generating the sine wave through digital pins PB0 to PB7.  
**Timer Specifications:**

- **Prescaler:** 2  
- **Interval:** $\frac{1}{frequency} \times \frac{1}{100}$  

## Voltage & Current Measurement

### Pin Description

#### VI - PA7 Pin
| Measure  | VI   |
|----------|------|
| Voltage  | LOW  |
| Current  | HIGH |

#### GS - PA6 Pin
- **LOW:** <TBA>  
- **HIGH:** Gain is unity  

#### ADC - PA0, PA1 Pins
- **PA0:** Voltage and current measurement.  
- **PA1:** Automatic Factor Correction (AFC).  

### Measurement Mode Handling

- Four possible modes are configured using the VI and GS pins.  
- To ensure accurate measurements, the mode is set with a time gap before measurement.  
- A total of 8 modes are cycled via Timer 2 interrupts.

#### Timer 2

Timer 2 toggles the VI measurement switch.  
**Timer Specifications:**
- **Prescaler:** 72000  
- **Interval:** 250ms  

> **Community Support:** [ADC Timer Implementation](https://community.platformio.org/t/in-stm32f103-how-to-create-two-timer-interrupt-running-without-disturb-each-other/43870/2)

## ADC Configuration

The ADC operates in dual mode for PA0 (ADC0) and PA1 (ADC1). Key features include:

- Timer 3 triggers ADC sampling via TRGO.  
- Direct Memory Access (DMA) is used to offload CPU load.  
- DMA overflow interrupts transfer ADC sample data to specific arrays.

### Timer 3

Timer 3 triggers ADC measurements.  
**Timer Specifications:**
- **Prescaler:** 8  
- **Interval:** $\frac{1}{sampling frequency}$  

## Display

The SSD1306 display (128x64 resolution) is connected via I2C using PA4 (SCL) and PA3 (SDA).  

### Implementation

- PA3 and PA4 do not natively support I2C on this MCU. A software (bit-banging) I2C interface is implemented by modifying the [tobajer/i2cbitbang library](https://github.com/tobajer/i2cbitbang).  
- The display is controlled using a modified library, [4ilo/ssd1306-stm32HAL](https://github.com/4ilo/ssd1306-stm32HAL), which is a fork of [afiskon/stm32-ssd1306](https://github.com/afiskon/stm32-ssd1306).  

> **Community Support:** [Display with Non-Standard I2C Pins](https://community.platformio.org/t/ssd1306-display-is-not-working-on-bluepill-board-stm32f103/43752/10)

## Miscellaneous Section

### User Buttons

- **PB13:** Hold  
- **PB14:** Serial/Parallel (S/P) mode  
- **PB15:** RCL mode