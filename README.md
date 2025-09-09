# Bandgap-Reference-Circuit
This repository presents the design and verification of a **CMOS Bandgap Voltage Reference (BGR)** using **Cadence Virtuoso**.  
The BGR provides a **stable reference voltage 1.27V** by combining **CTAT** (Complementary-to-Absolute-Temperature) and **PTAT** (Proportional-to-Absolute-Temperature) behaviors, making it robust against **temperature** and **process variations**.  

<img width="927" height="753" alt="image" src="https://github.com/user-attachments/assets/0570dd21-4dd4-42f1-8621-295a9e150d59" />


<img width="1467" height="727" alt="image" src="https://github.com/user-attachments/assets/b02f6862-d702-4ce2-9ff6-3d2ef357eb87" />

## Objective
To design a **low-variation voltage reference source** for use in analog/mixed-signal ICs such as ADCs, DACs, regulators, PLLs, and sensor interfaces.  

## Design Approach
### For OTA (Operational Transconductance Amplifier):
- Required Gain: **40 dB**  
- Reference Current: **100 µA**  
- Overdrive Voltages: **900, 600, 300 mV**
<img width="1019" height="795" alt="image" src="https://github.com/user-attachments/assets/4f77b2af-0c3e-4839-9360-f4e2a760d2fc" />

### For BGR Core:
- **CTAT Generation:** Base-emitter voltage (V<sub>BE</sub>) of PNP BJTs as shown below
  <img width="1280" height="519" alt="image" src="https://github.com/user-attachments/assets/ee1e31bc-361a-4751-9718-12e880322ce4" />
 
- **PTAT Generation:** ΔV<sub>BE</sub> across matched BJTs scaled by resistor as shown below
  <img width="1280" height="529" alt="image" src="https://github.com/user-attachments/assets/9fc348cf-4556-4e41-bc01-d65262410d49" />

  To match the other input node of opamp to this voltage it must must be mapped to 794mV. But the
voltage of the diode in the PTAT branch is 728mV. So, we put a resistor in between to follow up
this voltage. We find the voltage difference is 65.3 mV and current through this branch is 355 uA
so the resistance is 180Ω. As shwon in the below diagram.
<img width="618" height="477" alt="image" src="https://github.com/user-attachments/assets/f18cfa08-4862-42cf-b421-01efe0542bcf" />

- **Summation:** Weighted addition of CTAT + PTAT to achieve 1.27 V  

