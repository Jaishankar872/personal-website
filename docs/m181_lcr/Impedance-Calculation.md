---
title: Impedance Calculation
---
## Basic Term
### Complex Impedance
![Image title](assets/Imp_concept11.png){ width="200" }

- Polar form: $\displaystyle\vec{Z} = Z \angle\theta$   
- Cartesian form: $Z = R + jX$

where,

  - $\vec{Z}$ → impedance vector in Polar Form
  - $Z$ → magnitude of the impedance
  - $\theta$ → phase angle
  - $R$ → Resistance (Real part)  
  - $X$ → Impedance (Imaginary part)

### Polar → Cartesian form
- Resistance: $R = |Z| \cdot \cos \theta$
- Reactance: $X = |Z| \cdot \sin \theta$

### Cartesian → Polar form
- $Z = \sqrt{R^2 + X^2}$
- $\angle \theta = \tan^{-1}\left(\frac{X}{R}\right)$

## Typical equations for LCR meters
> Reference links:  
> 1. [LCR meter basic measurement principles](https://www.hioki.com/in-en/learning/usage/lcr-meters_1.html)  
> 2. [Typical equations for LCR meters](https://www.hioki.com/in-en/learning/usage/lcr-meters_2.html)

- Measurement from the current $I$ flowing and the voltage $V$ across the target’s terminals.
- LCR meters measure not only the ratio of current and voltage RMS values, but also the phase difference between current and voltage waveforms.

$\vec{Z} = \displaystyle\frac{|V| \angle \theta_V}{|I| \angle \theta_I} = \frac{|V|}{|I|} \angle (\theta_V - \theta_I) = |Z| \angle\theta$

### Reactance
- Capacitive Reactance: $X_C = \frac{1}{2\pi fC}$
- Inductive Reactance: $X_L = 2\pi fL$

> Reference: [Complex Impedance from Wikipedia](https://en.wikipedia.org/wiki/Electrical_impedance#Complex_impedance)

### Equivalent circuit mode
<figure markdown="span">
  ![Image title](assets/Imp_concept2.jpg){ width="250" }
</figure>

## Calibration
Calibration involves Open and short correction

**Working on it, I will add soon...**