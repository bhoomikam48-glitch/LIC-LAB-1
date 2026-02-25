# LIC-LAB-1
# Experiment-1 Analysis of CS amplifier using 180nm technology
# Aim:
Design cs ampifier using nmosfet in tsmc 180nm using vdd=2V , P<=1.5mW,capacitor = 1.5pF
# Theory:
The Common Source (CS) amplifier is one of the most widely used MOSFET amplifier configurations. In this circuit, the source terminal is common to both the input and the output, typically connected to ground. The input signal is applied between the gate and source (VGS), and the output is taken from the drain terminal.
# Principle of Operation

When a small AC signal is applied at the gate:

A change in gate-to-source voltage (VGS) causes a change in drain current (ID).

The varying drain current produces a voltage drop across the drain resistor (RD).

This results in a varying output voltage at the drain.

If the input voltage increases, the drain current increases, causing a larger voltage drop across RD, which reduces the drain voltage. Therefore, the output voltage decreases when the input increases.

 This produces a 180° phase shift between input and output.

 Voltage Gain
 
The small-signal voltage gain of a CS amplifier is given by:

Av​=−gm​RD​
* **gm** = Transconductance of the MOSFET.
* **Rd** = Drain resistance.
  
  The negative sign indicates phase inversion.

  # Operating Region

For proper amplification, the MOSFET must operate in the saturation region, where:

 ID​=1/2​kn​(VGS​−VT​)^2
 
This ensures linear amplification of small signals.

# Characteristics

* **High input impedance**

* **Moderate output impedance**

* **High voltage gain**

* **180° phase reversal**

* **Suitable for voltage amplification**

 # Applications

* **Audio amplifiers**

* **Signal amplification stages**

* **Analog integrated circuits**

* **First stage of multistage amplifiers**

  # Design of the circuit:

 # Circuit 1: CS Amplifier with Resistor Load

<img width="1456" height="817" alt="image" src="https://github.com/user-attachments/assets/73495578-c838-463b-8893-a2b683cbc099" />

1) DC OPERATING POINT:

The DC operating point (also called the Q-point – Quiescent Point) of a Common Source (CS) amplifier is the steady-state voltage and current values of the MOSFET when no AC input signal is applied.

Condition for Proper Biasing:

For a CS amplifier, the MOSFET must satisfy:


 VDS​>VGS​−VT
 
 ​
i.e.  1>0.9-0.36,  where VT is given VT=O.36V

This ensures operation in the saturation region, which is required for amplification.

# Calculation

1)Assuming ID =200µA which satisfy P<=1.5mW (P=V*I ; 2×200×10^−6 ; 400µW<=1.5mW)

2)We know VDD-ID*RD=VDS

2-200×10−6×RD=1

therefore,  RD=5K ohms

3)Kn′=μnCox

Kn′= 230×10^−6 A/V^2 ,
 where μn = 273.809×10^-6 and Cox = εox / tox .

Cox  = Oxide capacitance per unit area (F/m²)  
εox  = Permittivity of oxide material  
tox  = Oxide thickness (m)  

Since,

εox = ε0 × εr

Therefore,

Cox = (ε0 × εr) / tox
Cox =(8.854 ×10^-12  × 3.9)/4.1 × 10^-9


4)VGS​=VG​−VS​=0.9−0=0.9V
ID​=​K′*W/L​(Vov​)^2 
W=1.07×10−6m

 # DC analysis:
 
![WhatsApp Image 2026-02-23 at 18 40 21](https://github.com/user-attachments/assets/ceda3a26-b3a8-4c4e-97c2-613687585cb8)

From this simulation Vout=1.23,Vin=0.9v and Id=153µA the load line equation is given by Vout=VDD-Id*RD. The calculated value does not match with simulated one so we will change the width to maintain the length at 180nm and obtain desired current value.

## Length-Width vs Drain Current (Id)

| Length (nm) | Width (µm) | Id (µA) |
|-------------|------------|---------|
| 180       |  1.07        |  153  |
| 180       |    1.10     | 157   |
| 180       |    1.20     | 167   |
| 180       |   1.40      |  189  |
| 180       |   1.51      |  200  |

To check the mosfet is in saturation region Vds=Vd-Vs ;1-0=1V ; VDS = VDD / 2 ;VDS = 2 / 2 =1V

since Vds>Vov

It is in saturation region.The Q point is 1V,200µA

<img width="838" height="606" alt="image" src="https://github.com/user-attachments/assets/3bf71ba4-a4f0-4be3-bf0a-70e7709d3661" />
<img width="666" height="628" alt="image" src="https://github.com/user-attachments/assets/fb1aac47-675e-4705-a062-dc3ceb8ce10a" />



 # Transfer Analysis

<img width="1915" height="428" alt="image" src="https://github.com/user-attachments/assets/016e7173-8fde-4152-8d14-c692c1ebff8e" />


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

Transient analysis in a Common Source (CS) amplifier studies how the circuit responds to time-varying signals, especially during switching (turn-on / turn-off) or sudden changes in input.

<img width="1908" height="417" alt="image" src="https://github.com/user-attachments/assets/06a524ee-5a95-4da1-b600-5d842738384a" />

<img width="1911" height="433" alt="image" src="https://github.com/user-attachments/assets/0e84cdde-9c46-4adf-94f6-0239faafcedf" />

<img width="1918" height="872" alt="image" src="https://github.com/user-attachments/assets/a7046e57-0c17-4d81-b383-057779817bc7" />


From graph,

The output waveform is 180° phase shifted with respect to the input.

When Vin increases, Vout decreases.

When Vin decreases, Vout increases.

This confirms proper operation of a Common Source amplifier, which always produces phase inversion.

* **input** :

  Minimum peak: 0.969V
  Maximum peak: 1.026V

  * **output** :

  Minimum peak: 0.890V
  Maximum peak: 0.909V
  

*Av​=ΔVin/​ΔVout

*Av=1.026 - 0.969/ 0.909 - 0.890 = 3 

*Gain(dB) = 20log10(Av)=9.54dB​​​

*gm= 2Id / Vov=7.407×10^−4 S

*Av=gm×RD

*Av=7.407×10^−4×5×10^3=3.7

*Gain(dB) = 20log10(Av)=11.364db

Simulated gain = 9.54db
Therotical gain: 11.364db.


 # AC Analysis(without capacitor):

<img width="1918" height="422" alt="image" src="https://github.com/user-attachments/assets/bea0bb2a-c9fa-4a26-96fe-12571b7f5036" />


* **Av=9.4-3=6.4dB**

* **Cutoff frequency=41.88GHz**

* **Bandwidth=41.88GHz**

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
Cutoff frequency ≈ 41.88 GHz
At this frequency, gain reduces by 3 dB
After this point, gain decreases rapidly
This indicates:
 High-frequency roll-off
 4. Bandwidth
Bandwidth ≈ 41.88 GHz
Since there is no capacitor, the response remains flat until high frequency.
Only high-frequency limitation is visible.

# AC Analysis(with capacitor):
<img width="1363" height="762" alt="image" src="https://github.com/user-attachments/assets/b470ad44-1030-49e2-9701-7e077be1d88f" />
<img width="1910" height="421" alt="image" src="https://github.com/user-attachments/assets/2c6306e1-e989-4ca2-b8cd-69bb1b20156f" />


* **C=1pF**

* **Av=9.4-3=6.4dB**

* **Bandwidth=36.300MHz**

  The graph shows Gain (dB) vs Frequency.
  
The mid-band gain is 9.43 (≈ 6.4 dB).
The gain remains almost constant at low and mid frequencies.
Due to the added capacitor (C = 1pF), the gain starts decreasing at a much lower frequency.
The bandwidth is 36.300 MHz, which is significantly reduced compared to the case without capacitor.

Adding the capacitor reduces the bandwidth and causes earlier high-frequency roll-off, while the mid-band gain remains approximately the same.

## 10. Comparison Table

| Parameter      | Theoretical | Simulated |
|---------------|------------|-----------|
| Gain (V/V)    | 3 .7      |   3     |
| Gain (dB)     | 11.36 dB    | 9.54 dB    |
| ID            | 200 µA     | 153 µA  |
| W             | 1.07 µm    | 1.51 µm   |

# Procedure:
1.create the Circuit
Open LTspice and start a new schematic. Save the file in a suitable folder with an appropriate name.

2️. Place Required Components
Insert the necessary components into the schematic:
NMOS transistor (180 nm model)
DC voltage source for power supply
AC voltage source for input
Resistor
Ground terminal (mandatory)
Connect the circuit properly according to the required configuration.

3️. Assign Component Values
Set the values for each element:
DC supply voltage
AC input signal (amplitude and frequency)
Resistor value
Ensure correct MOSFET model is selected and connected (Drain, Gate, Source properly wired)

4️. Set Up Simulation Commands
Open the simulation settings and add:
DC operating point analysis to find the bias conditions
AC analysis to obtain gain and frequency response
Transient analysis to observe time-domain output waveform
Enter the required parameters for each type of analysis.

5️. Run the Simulation
Click the Run button to execute the simulation.
Observe the waveform window for:
DC operating values
Gain plot versus frequency
Output waveform versus time

6️. Analyze the Results
From the results:
Verify MOSFET operating region using VGS, VDS, and ID.
Determine voltage gain from AC plot.
Identify cutoff frequency and bandwidth.
Confirm amplification from transient waveform.

# Inference:

From the DC, AC, transfer, and transient analyses of the NMOS amplifier, the following conclusions are obtained:

1️. DC Analysis:
The MOSFET is properly biased and operates in the required region (saturation region). The Q-point is stable, confirming correct biasing of the amplifier.

2️. Transfer Characteristics:
The transfer curve shows a negative slope, indicating that the output decreases as the input increases. This confirms that the circuit behaves as an inverting amplifier.

3️.AC Analysis:
The amplifier provides a constant mid-band gain (around 9.43 or 6.4 dB). The gain decreases after the cutoff frequency, determining the bandwidth.
When a capacitor is added, the bandwidth reduces due to increased high-frequency roll-off.

4️. Transient Analysis:
The output waveform is amplified and inverted compared to the input signal, confirming proper amplification action.

 Overall Inference:
The designed NMOS amplifier operates correctly in saturation region, provides voltage amplification with negative gain, and exhibits proper frequency response characteristics. The presence of capacitance significantly affects the bandwidth while keeping mid-band gain nearly constant.





