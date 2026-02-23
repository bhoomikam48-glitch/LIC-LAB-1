# LIC-LAB-1
# Experiment-1 Analysis of CS amplifier using 180nm technology
# Aim:
Design cs ampifier using nmosfet in tsmc 180nm using vdd=2V , P<=1.5mW,capacitor = 1.5pF
# Theory:
A Common Source (CS) Amplifier is a fundamental MOSFET amplifier configuration widely used in analog circuit design. It provides voltage gain by using a transistor to amplify an input signal. The amplifier’s gain is determined by the transconductance of the MOSFET and the load resistance or active load. The CS amplifier is known for its high voltage gain and moderate input impedance, making it suitable for various signal processing applications.

In saturation region the current formula is given by ID=1/2knVov

 # Circuit 1: CS Amplifier with Resistor Load

![WhatsApp Image 2026-02-23 at 18 33 42](https://github.com/user-attachments/assets/516f17f8-6573-41ab-a86e-00784f11d65a)


# Calculation

1)Assuming ID =200µA which satisfy P<=1.5mW (P=V*I ; 2×200×10^−6 ; 400µW<=1.5mW)

2)We know VDD-ID*RD=VDS

2-200×10−6×RD=1

therefore RD=5K ohms

3)Kn′=μnCox

Kn′= 230×10^−6 A/V^2

4)VGS​=VG​−VS​=0.9−0=0.9V
ID​=​K′*W/L​(Vov​)^2 
W=1.07×10−6m

 # DC analysis:
 
![WhatsApp Image 2026-02-23 at 18 40 21](https://github.com/user-attachments/assets/ceda3a26-b3a8-4c4e-97c2-613687585cb8)

From this simulation Vout=1.23,Vin=0.9v and Id=153µA the load line equation is given by Vout=VDD-Id*RD. The calculated value does not match with simulated one so we will change the width to maintain the length at 180nm and obtain desired current value.

## Length-Width vs Drain Current (Id)

| Length (µm) | Width (µm) | Id (µA) |
|-------------|------------|---------|
| 1900        | 1500       | 10.92   |
| 1900        | 1650       | 15.92   |
| 1900        | 1700       | 17.89   |
| 1900        | 1750       | 22.57   |
| 1900        | 1750       | 25.20   |

To check the mosfet is in saturation region Vds=Vd-Vs ;1-0=1V

since Vds>Vov

It is in saturation region.The Q point is 1V,200µA

 # Transfer Analysis

![WhatsApp Image 2026-02-23 at 19 05 50](https://github.com/user-attachments/assets/c95bd877-443f-44c0-90ad-19a73f124e42) 

The curve is downward sloping.
As Vin increases, Vout decreases.
The relationship is almost linear in a certain region.
After a point, the curve becomes flat → indicating saturation.

# Interpretation:
Since the slope is negative, the circuit has
 * **Negative gain**
 * **Output is inverted with respect to input**
The flat region indicates the device is entering saturation region, where further increase in input does not significantly change output.
The mentioned Q-point (1V, 200µA) represents the DC operating point of the device.

# Transient Analysis:

<img width="1919" height="870" alt="image" src="https://github.com/user-attachments/assets/cd904cae-aeee-4734-ac5c-6f55d08703b5" />
From graph,

*Av​=ΔVin/​ΔVout

*Av=0.057/0.0186=3.06

*Gain(dB) = 20log10(Av)=9.714dB​​​

*gm= 2Id / Vov=7.49×10^−4 S

*Av=gm×RD

*Av=7.49×10^−4×5×10^3=3.74

*Gain(dB) = 20log10(Av)=11.36

 # AC Analysis(without capacitor):

<img width="1918" height="423" alt="image" src="https://github.com/user-attachments/assets/6499d784-5ed5-4850-85f6-8a162f719a37" />

* **Av=9.4-3=6.4dB**

* **Cutoff frequency=42.33GHz**

* **Bandwidth=42.33GHz**

# Interpretation of the Graph
 1. Nature of the Graph
X-axis → Frequency (Hz)
Y-axis → Gain (dB)
The curve is almost flat at low and mid frequencies
It drops sharply at higher frequencies
 2. Voltage Gain:
So the amplifier provides:
 Constant mid-band gain of about 9.43 (≈ 6.4 dB)
 3. Cutoff Frequency
Cutoff frequency ≈ 42.33 GHz
At this frequency, gain reduces by 3 dB
After this point, gain decreases rapidly
This indicates:
 High-frequency roll-off
 4. Bandwidth
Bandwidth ≈ 43.33 GHz
Since there is no capacitor, the response remains flat until high frequency.
Only high-frequency limitation is visible.
  




