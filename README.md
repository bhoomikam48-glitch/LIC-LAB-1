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








