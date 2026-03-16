# Experiment 2 c) : Diode-Connected Common-Source Amplifier with Source Degeneration.

# AIM : Design of an NMOS Diode-Connected with a PMOS active load using 180nm technology in LTspice.

# CIRCUIT:


<img width="1237" height="783" alt="Image" src="https://github.com/user-attachments/assets/f9014c71-0ced-4a30-b158-65f39dece774" />


* A diode-connected NMOS with PMOS active load is a common configuration in CMOS analog circuits used for bias generation, current mirroring, and amplifier stages. In this circuit, one NMOS transistor is diode-connected (its gate and drain are shorted), while another NMOS acts as the amplifying device. A PMOS transistor is used as an active load connected to the supply voltage.

* This structure provides stable biasing, higher gain, and efficient use of silicon area, making it widely used in analog VLSI design.
  

  | Transistor |  Type |    Function                 |


|  M1         |  NMOS |  Diode-connected transistor |

|  M2         |  NMOS |  Amplifying transistor      |

|  M3         |  PMOS |  Active load                |


Connections

M1 (NMOS): Gate connected to drain → diode-connected.

M2 (NMOS): Gate receives input signal.

M3 (PMOS): Connected to supply VDD and acts as an active load.

Output is taken at the drain node between NMOS and PMOS.




Given data: 

| Parameter | Symbol | Value |
| :--- | :--- | :--- |
| Supply Voltage | $V_{DD}$ | 2.0 V |
| Target Drain Current | $I_D$ | $200\text{ }\mu\text{A}$ |
| Power Consumption | $P_{cons}$ |  $\leq 1.5\text{mW}$) |
| Overdrive Voltage | $V_{OV}$ | 0.25 V |
| Load Capacitance | $C_L$ | 1.0 pF |
| Technology Node | $L$ | 180 nm (TSMC 0.18um) |
| Threshold Voltage | $Vthn$ | 0.36V (NMOS) |
| Threshold Voltage | $Vthp$ | 0.39V (PMOS) |




# DC Analysis:

* Design calculation:

  
Power verification:

Let ID = 200 µA

P = VDD * ID = 2 * 200 µA = 0.4mW.


Verification: 0.4mW <= 1.5mW (Constraint satisfied).


Also,

Vout = VDD/2

Vout = 2/2

Vout = 1 = 1V




 # For M3 Transistor:


 VG3 = VD3 = VS1

 VGS3 = VG3 = VOV + VTH
 
   VG3  = 0.25 + 0.36 
      
   VG3   = 0.61V


   VS3 = 0 ,  VD3 = VS1 = 0.61V



  * For M3 to be SATURATION,

VGS3 >= VTH

0.61 V >= 0.36 V

and VDS3 >= VOV

VDS3= 0.60 V ( From simulation)

Hence, 0.60 >= 0.25

Therefore both the conditions are satisfied.

Therefore M3 is operating in SATURATION region.




# For M1 Transistor :


VGS1 = VOV + VTH

VGS1 = 0.25 + 0.36

VGS1 = 0.61V

VG1 = VS1 + VGS1

VG1 = 0.61 + O.61

VG1 = 1.22V

* For M1 to be SATURATION,

VGS1 >= VTH

0.61 V >= 0.36 V

and VDS1 >= VOV

VDS1 = VOUT - VS1

VDS1 = 1 - 0.61

VDS1 = 0.39V

Therefore , VDS1 >= VOV.

0.39 >= 0.25

Therefore both the conditions are satisfied.

Therefore M1 is operating in SATURATION region.





# For M2 Transistor :(PMOS)


VSG2 = VOV + |VTH|

VSG2 = 0.25 + 0.39

VSG2 = 0.64 V

VSG2 = VS2 - VG2

0.64 = 2 - VG2

VG2 = 1.36V

VSD2 = VDD - VOUT

VSD2 = 2 - 1

VSD2 = 1



* For M2 to be SATURATION,

  
VSG2 >= VTH

0.64 V >= 0.39 V

and VSD2 >= VOV

Therefore , VSD2 >= VOV.

1 >= 0.25

Therefore both the conditions are satisfied.

Therefore M2 is operating in SATURATION region.






# For M1 and M3 Transistor :

The Drain -current equation is given by,

ID = (1/2) μn Cox (W/L) (VOV)²

Kn′=μnCox

From Datasheet,

Kn′= 230×10^−6 A/V^2 , where μn = 273.809×10^-6 and Cox = εox / tox .

Cox = Oxide capacitance per unit area (F/m²)

εox = Permittivity of oxide material

tox = Oxide thickness (m)

Since,

εox = ε0 × εr

Therefore,

Cox = (ε0 × εr) / tox , Cox =(8.854 ×10^-12 × 3.9)/4.1 × 10^-9

Cox = 8.42 × 10⁻³ F/m²

By rearranging, ID = (1/2) μn Cox (W/L) (VOV)²

W = 5 µm , for ID= 200µA.






# For M2 Transistor:

The Drain -current equation is given by,

ID = (1/2) μp Cox (W/L) (VOV)²

Kp′=μpCox

From Datasheet,

Kp′= 0.974×10^−6 A/V^2 , where μp = 115.689 cm²/Vs and Cox = εox / tox .

Cox = Oxide capacitance per unit area (F/m²)

εox = Permittivity of oxide material

tox = Oxide thickness (m)

Since,

εox = ε0 × εr

Therefore,

Cox = (ε0 × εr) / tox , Cox =(8.854 ×10^-12 × 3.9)/4.1 × 10^-9

Cox = 8.42 × 10⁻³ F/m²

By rearranging, ID = (1/2) μn Cox (W/L) (VOV)²

W = 11.8 µm , for ID= 200µA.



<img width="1801" height="723" alt="Image" src="https://github.com/user-attachments/assets/b0502367-d663-447b-b329-4ab43aa1b893" />



With these calculated width , we get ID=70µA , VOUT=0.90V.


Taking the ratio of the current i.e. = 200 / 70 = 2.85 (assumed current ID = 200 , simulated ID = 70).

Wn = 5 * 2.85 = 14.25 µm , Wp = 11.8 *2.85 = 33.63µm , taking reference as 14.25 µm , 33.63 µm start increasing or

decreasing the width values to get ID = 200 µA , VOUT = 1.0V





<img width="1882" height="795" alt="Image" src="https://github.com/user-attachments/assets/51349fd9-ce94-4527-af8e-bbe98ec782bb" />




* Final Width values : Wn = 14.7µm (for M1) , Wn = 14µm (for M3) , Wp = 35µm (for PMOS).

* After tuning width values we get ID=200µA , VOUT=1.0V which matches with theoretical and simulated analysis.



### Design Evolution: MOSFET Sizing Comparison

| Component | Initial Width ($W$) | Final Width ($W$) | 
| :--- | :--- | :--- |
| **$M_1$ (Input)** | 5.0 µm | 14.7 µm | 
| **$M_3$ (Degeneration)** | 5.0 µm | 14.0 µm |
| **$M_2$ (Active Load)** | 11.8 µm | 35.0 µm | 
| **Drain Current ($I_D$)** | 70 µA | 200 µA | 




# Transfer Analysis : (DC Sweep)



<img width="1918" height="890" alt="Image" src="https://github.com/user-attachments/assets/2ca0702a-56c9-4890-a4a9-694461127bd1" />


* Breakdown of the VTC Curve
  

 Region 1: 
 
* Cut-off ($V_{in} < \approx 0.8V$)The input transistor $M_1$ is in the cut-off region (it is essentially "OFF").Because there is no current flowing through the circuit, there is no voltage drop across the PMOS load ($M_2$). Consequently, $V_{out}$ remains pulled up to the supply voltage ($V_{DD} = 2.0V$).



Region 2: 

* Active/Saturation Region ($\approx 0.9V < V_{in} < 1.4V$)This is the linear amplification region. As $V_{in}$ increases, $M_1$ turns on and begins conducting.The slope of this curve represents the voltage gain ($A_v = \frac{\Delta V_{out}}{\Delta V_{in}}$). Your plot shows a nice, steep decline here.The source degeneration ($M_3$) keeps this transition smooth and linear, rather than a sharp, hard switch.




Region 3:

* Saturation/Triode of Load ($\approx V_{in} > 1.4V$)Once $V_{in}$ passes roughly 1.4V, the output voltage levels off at approximately 0.65V.At this point, the NMOS stack is pulling as hard as it can, and the PMOS load is likely entering the triode region or hitting the voltage headroom limit of the stack. The circuit is now "saturated" at its low-level output voltage.



### DC Sweep Analysis (Transfer Characteristics)

| Region | Input Voltage ($V_{in}$) Range | Behavior | Circuit State |
| :--- | :--- | :--- | :--- |
| **Cut-off** | $0.0V - 0.8V$ | $V_{out} \approx V_{DD}$ | $M_1$ is OFF; Load is open. |
| **Transition/Linear** | $0.9V - 1.4V$ | $V_{out}$ drops sharply | High gain ($A_v$) region. |
| **Saturation/Triode** | $1.4V - 2.0V$ | $V_{out} \approx 0.65V$ | $M_1$ is pulling current hard. |







# Transient Analysis:


Transient analysis in a Common Source (CS) amplifier studies how the circuit responds to time-varying signals, especially during switching (turn-on / turn-off) or sudden changes in input.




input waveform:


<img width="1918" height="852" alt="Image" src="https://github.com/user-attachments/assets/187a7f2f-b51f-4668-a7a6-176347339cc0" />






output waveform:



<img width="1918" height="887" alt="Image" src="https://github.com/user-attachments/assets/69618c2a-448f-4819-aeab-de2b94b9296e" />





* Input Waveform ($V_{in}$):

Maximum ($V_{in,max}$): $1.229\text{V}$

Minimum ($V_{in,min}$): $1.210\text{V}$

Peak-to-Peak ($V_{pp,in}$): $1.229\text{V} - 1.210\text{V} = 0.019\text{V}$





* Output Waveform ($V_{out}$):

Maximum ($V_{out,max}$): $\approx 1.261\text{V}$

Minimum ($V_{out,min}$): $\approx 906.73\text{mV}$

Peak-to-Peak ($V_{pp,out}$): $1.26\text{V} - 906.80\text{mV} = 0.35\text{V}$


Phase: Note that the output is 180° out of phase with the input (when $V_{in}$ goes up, $V_{out}$ goes down), which is characteristic of a Common-Source based amplifier.





* Voltage Gain ($A_v$) Calculation

The magnitude of the voltage gain is defined as:


$$|A_v| = \frac{V_{pp,out}}{V_{pp,in}}$$


Substituting the observed values:

$$|A_v| = \frac{\text{0.35V}}{0.019\text{V}} = 18.42\text{ V/V}$$


In decibels (dB):

$$A_v(dB) = 20 \log_{10}(31) \approx 25.30\text{ dB}$$




### Transient Analysis Performance

| Metric | Measured Value |
| :--- | :--- |
| **Input Amplitude ($V_{in,pp}$)** | 0.019V |
| **Output Amplitude ($V_{out,pp}$)** | 0.35V |
| **Voltage Gain ($A_v$)** | 18.42 V/V |
| **Gain (dB)** | 25.30 dB |
| **Phase Shift** | 180° |



* Theoretical gain:


$$
A_v = \frac{-g_{m1} r_{o2}}{1 + \frac{g_{m1}}{g_{m3}}}
$$

  gm1 = gm3 = (2ID / VOV)
  
   gm = (2 × 200×10⁻⁶) / 0.25
  
 gm = 1.6 × 10⁻³ S


ro2 = 1 / (λ ID)

ro2 = 1 / (0.1 × 200×10⁻⁶)

ro2 = 50 kΩ




$$
A_v = \frac{-  1.6 × 10⁻³  50 kΩ }}{1 + \frac{1.6 × 10⁻³}}{1.6 × 10⁻³}}
$$


A_v = -40 V/V.


* In decibels (dB):

$$A_v(dB) = 20 \log_{10}(40) \approx 32.04\text{ dB}$$



### Theoretical vs. Practical Gain Comparison

| Metric | Theoretical Value | Practical Value (Sim) |
| :--- | :--- | :--- | :--- |
| **Gain ($A_v$)** | 40.0 V/V | 18.4 V/V | 
| **Gain (dB)** | 32.04 dB | 25.30 dB | 



* The difference  between Theoretical vs. Practical Gain occurs due to:


* Finite Output Resistance ($r_o$):
  
 Theoretical formulas often assume the transistor is a perfect current source (infinite output resistance). 
 
 In reality, the finite $r_o$ of the transistors (due to channel length modulation) shunts your output signal,
 
 effectively reducing the gain.



Source Degeneration Accuracy:

The actual resistance of $1/g_{m3}$ is not perfectly linear. 

The interaction between the input stage and the degeneration transistor in a real simulation is more complex 

than the simple $1/g_{m3}$ term used in basic theory.





# AC Analysis:


# Frequency Response Analysis:

The AC analysis was performed across a frequency range of 0.1 HZ to 100GHZ.The frequency response demonstrates the bandwidth limits imposed by parasitic capacitances in the 180nm CMOS process.




<img width="1918" height="853" alt="Image" src="https://github.com/user-attachments/assets/10e66d43-3944-485c-96e7-76e12a6f18e7" />







Bandwidth is measured at: Av(mid) − 3 dB = 25.30 − 3 = 22.3 dB fH (upper cutoff frequency) ≈ 341.57 MHz.

fL (lower cutoff frequency) ≈ 0 Hz


Therefore: Bandwidth (BW) ≈ 341.57 MHz.



* Unity gain bandwidth:


  
<img width="1918" height="858" alt="Image" src="https://github.com/user-attachments/assets/c8ec7d55-7da3-42b9-bb49-7f96bdb02246" />




From AC analysis plot At frequency ≈ 7.04GHz

Magnitude ≈ 16.05mdB at 0 dB

Therefore, UGB ≈ 7.04GHz.



$$A_{v,linear} = 10^{\left( \frac{25.30}{20} \right)}$$


$$A_{v,linear} = \approx \mathbf{18.40 \text{ V/V}}$$


The UGB is the product of the Gain ($A_{v,linear}$) and the Bandwidth ($BW$):


$$UGB = 18.40 \times 341.57 \text{ MHz}$$


$$UGB \approx \mathbf{6.28 \text{ GHz}}$$




From simulation analysis: UGB ≈ 7.04GHz

From Gain–Bandwidth product: UGB ≈ 6.28GHz

Thus Gain bandwidth product , practically and theoretically are verified and validated.




# Conclusion:

* A diode-connected NMOS combined with another NMOS transistor and a PMOS active load forms an efficient biasing and amplification structure in CMOS analog circuits.
  
* The diode-connected device establishes a stable current reference, while the PMOS active load provides high resistance and improved voltage gain, making the circuit suitable for high-performance analog VLSI systems.











# Comparative Analysis of Degeneration Techniques

| Metric | Exp 2A: Resistor Load | Exp 2B: NMOS Current Source | Exp 2C: Diode-Connected NMOS |
| :--- | :--- | :--- | :--- |
| **Degeneration Type** | Passive Resistor (Rs = 1000 Ω) | Active NMOS Current Source | Diode-Connected NMOS |
| **Drain Current (Id)** | ≈ 200 µA | ≈ 200 µA | ≈ 200 µA |
| **Power Consumption** | ≈ 0.4 mW | ≈ 0.4 mW | ≈ 0.4 mW |
| **Theoretical Gain** | 23.74 dB | 10.65  dB | 32.04 dB |
| **Simulated Gain (Transient)** | 21.02 dB | dB | 27.97 dB |
| **Simulated Gain (AC / Midband)** | **18.02 dB dB** | **dB** | **9 dB** |
| **Bandwidth (fH)** | **212.875 MHz** | **** | **500 MHz** |
| **Linearity** | Good (Passive source degeneration improves linearity) | Excellent (Current source improves bias stability) | Moderate–Good (Nonlinearity due to diode connection) |
| **Stability** | Moderate | High | High |
| **Primary Trade-off** | High gain but limited bandwidth | Very low gain but high stability | Very high bandwidth but reduced practical AC gain |

---

# Inference

1. **Resistor Load Configuration (Exp 2A)**  
   - Provides **high midband gain (28.4 dB)** close to theoretical value.  
   - Bandwidth is limited to **37.66 MHz**, restricting high-frequency applications.  
   - Passive degeneration improves **linearity** but reduces **frequency response**.

2. **NMOS Current Source Configuration (Exp 2B)**  
   - Shows **very low gain (~3.53 dB)** due to the **high output resistance of the NMOS current source**.  
   - Bandwidth improves to **184.56 MHz**.  
   - Provides **excellent bias stability and improved operating point control**.

3. **Diode-Connected NMOS Configuration (Exp 2C)**  
   - Achieves the **highest theoretical gain (32.04 dB)**.  
   - Provides the **largest bandwidth (500 MHz)** among all configurations.  
   - However, the **practical AC midband gain drops to ~9 dB** due to the nonlinear resistance introduced by the diode connection.

---

# Conclusion

From the comparison of the three degeneration techniques:

- **Resistor degeneration** provides the **best practical midband gain**, making it suitable for **low-frequency amplifier designs**.
- **NMOS current source degeneration** offers **excellent bias stability and improved bandwidth**, but suffers from **very low gain**.
- **Diode-connected NMOS degeneration** provides the **highest bandwidth and stable operating point**, making it suitable for **high-frequency analog applications**, though with reduced practical gain.

Thus, the selection of degeneration technique depends on the design goal:

- **High Gain → Resistor Load**
- **High Stability → NMOS Current Source**
- **High Bandwidth → Diode-Connected NMOS**

---

# Advantages Comparison

## Resistor Degeneration
- Simple circuit implementation
- Predictable linear performance
- Higher practical midband gain

## NMOS Current Source Degeneration
- Improved bias stability
- Higher bandwidth than resistor degeneration
- Less sensitive to supply variations

## Diode-Connected NMOS Degeneration
- Self-biasing capability
- Highest bandwidth among the three configurations
- Compact implementation for integrated circuits
- Stable operating point|
