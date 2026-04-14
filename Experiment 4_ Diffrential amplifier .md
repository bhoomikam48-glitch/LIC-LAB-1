## Experiment - 04  Diffrential amplifier analysis:


# Circuit - 01 

# MOS Differential Pair with Tail Current Source


# Aim: 

**To design and analyze a MOS Differential Amplifier for the following specifications:**

- Supply Voltage: VDD = 0.9 V  
- VSS = -0.9 V  
- Input Common Mode Voltage (VICM) = 0 V  
- Output Common Mode Voltage (VOCM) = 0 V  
- Channel Length (L) = 360 nm  
- Power Constraint: P ≤ 1.5 mW


# Theory:


* The differential amplifier is a fundamental building block of analog integrated circuits, forming the input stage of almost all operational amplifiers (op-amps).

* Its core function is to amplify the difference between two input signals while rejecting signals that are common to both inputs (noise, supply ripples).



    V_{out} = (V_{in1} - V_{in2}



  It is the core stage of:

 - Operational Amplifiers (Op-Amps)
 - Comparators
 - Instrumentation Amplifiers
 - Mixers
 - ADC front-end circuits.


##  Basic Operation

A MOS Differential Amplifier typically consists of:

- Two matched NMOS transistors (M1, M2)
- A constant tail current source (ISS)
- Load (Resistor or Active Load)

### Working Principle:

When:


V_{in1} = V_{in2}


- Current splits equally
- I_{D1} = I_{D2} = ISS/2
- Outputs are equal

When:


V_{in1} > V_{in2}


- M1 draws more current
- M2 draws less current
- Output voltages shift in opposite directions

Thus, the circuit converts differential voltage into differential output voltage.


### Modes of Operation

###  Differential Mode


V_{id} = V_{in1} - V_{in2}


Gain for differential input:


Av  = $$ V_{pp,out}/{V_{ind} $$


This is the desired mode of operation.



### Common Mode


$$ V_{icm} = {V_{in1}} + V_{{in2}}/{2} $$ 


Ideally:


A_{cm} = 0


In practice, small nonzero gain exists due to:

- Finite tail resistance
- Mismatch
- Channel length modulation




### Common Mode Rejection Ratio (CMRR):


$$ CMRR = A_d / A_ cm $$


In dB:


CMRR_dB = 20 log A_d / A_cm





# Circuit :


<img width="1397" height="822" alt="image" src="https://github.com/user-attachments/assets/4c70f114-573f-4237-82c5-a528ec60c389" />




### * DC ANALYSIS:


SpecificationsTechnology Channel Length ($L$): $360\text{ nm}$

Supply Voltage ($V_{DD}$): $0.9\text{V}$

Negative Supply ($V_{SS}$): $-0.9\text{V}$

Total Voltage Swing ($V_{total}$): $1.8\text{V}$ ($0.9\text{V} - (-0.9\text{V})$

Power Dissipation Limit ($P$): $\le 1.5\text{mW}$ (Using $1.5\text{mW}$ for design)$

Required Input Common Mode ($V_{inCM}$): $0\text{V}$

Target Output Common Mode ($V_{outCM}$): $0\text{V}$

Common Source Node Voltage ($V_p$): $-0.7\text{V}$

Process Parameter ($\mu_n C_{ox}$): $2.305 \times 10^{-4}\text{ A/V}^2$

Threshold Voltage ($V_T$): $0.36\text{V}$


** Design calculations:


Determine Tail Current ($I_{SS}$)


To satisfy the power constraint:



$$I_{SS} \le \frac{P_{limit}}{V_{total}} = \frac{1.5\text{ mW}}{1.8\text{ V}} \approx 0.833\text{ mA}$$


$I_{SS} = \mathbf{0.833\text{ mA}}$




For a balanced common-mode input:


$$I_{D1} = I_{D2} = \frac{I_{SS}}{2} = \frac{0.833\text{ mA}}{2} = \mathbf{0.4165\text{ mA}}$$




Drain Load Resistors ($R_D$):



To fix the output common-mode voltage ($V_{out}$) at $0\text{V}$:


$$V_{out} = V_{DD} - I_D R_D$$$$0\text{V} = 0.9\text{V} - (0.4165\text{mA} \times R_D)$$


$$R_D = \frac{0.9\text{V}}{0.4165\text{mA}} \approx \mathbf{2.163\text{ k}\Omega}$$



Transistor Operating Point ($M_1, M_2$):


Given $V_{inCM} = V_G = 0\text{V}$ and $V_p = V_S = -0.7\text{V}$:



$$V_{GS} = V_G - V_S = 0 - (-0.7) = \mathbf{0.7\text{ V}}$$


$$V_{OV} \text{ (Overdrive Voltage)} = V_{GS} - V_T = 0.7 - 0.36 = \mathbf{0.34\text{ V}}$$


$$V_{DS} = V_{out} - V_S = 0 - (-0.7) = \mathbf{0.7\text{ V}}$$



Condition for Saturation: 


$V_{DS} > V_{OV}$ $\rightarrow$ $0.7\text{V} > 0.34\text{V}$ (Confirmed: Saturation region)



Transistor Sizing (Width Calculation)

Using the drain current equation to solve for $W$:



$$I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{OV})^2$$




$$W = \frac{2 \times I_D \times L}{\mu_n C_{ox} \times (V_{OV})^2}$$


$$W = \frac{2 \times 0.4165 \times 10^{-3} \times 360 \times 10^{-9}}{2.305 \times 10^{-4} \times (0.34)^2}$$



$$W = 11.235 \times 10^{-6}\text{ m} = \mathbf{11.235\text{ \µm}}$$



### Operating point:


<img width="1185" height="752" alt="image" src="https://github.com/user-attachments/assets/e14aa54a-74ef-44ec-945b-31bf8265c761" />






| Stage | Width ($W$) |


| **Theoretical** | 11.23 µm | 


| **Final (Simulated)** | 19.90 µm | 


**Observation:** The increase in width from 11.23 µm to 19.90 µm was necessary to maintain the tail current of 0.833mA while keeping the transistors  in the saturation region .





Parameter| Hand Calculated | LTspice Simulated


Tail Current | (ISS​)| 0.833 mA | 0.833 mA


"Drain Current | (ID1,2​)"| 0.4165 mA | 0.4165 mA


Node Voltage | Vp​,−0.700 V, |  −0.700479 V


Output CM Voltage Vout | ​,0.000 V, |  0.00036 V



The DC operating point is successfully fixed. 


Both $M1$ and $M2$ are operating in the saturation region, providing a stable baseline for subsequent Transient and AC analysis.



### Input Common Mode Range (ICMR)

ICMR defines the range of input voltage over which:

- Transistors remain in saturation
- 
- Circuit behaves linearly



Limited by:

- Tail transistor saturation
  
- Input transistor saturation
  
- Supply rails



* A. Minimum Input Common-Mode ($V_{ICM,min}$)

 The lower limit is reached when the tail current source ($I_{SS}$) is at the edge of triode. 
 
 For the tail current source to stay in saturation, the voltage at node $V_p$ must be at least $V_{DS,sat}$ of the
 current source.



 * B. Maximum Input Common-Mode ($V_{ICM,max}$)

   
   The upper limit is reached when the differential pair ($M_1, M_2$) enters the triode region.
   
    This happens when $V_{GD} = V_{th}$.


   ## Common-Mode Range Analysis

Based on the DC operating point ($V_p = -0.7V$, $V_{GS} = 0.7V$), the allowable common-mode ranges were calculated 

to ensure all transistors remain in the saturation region.


### ICMR (Input Common-Mode Range)


- **Minimum:**
  
   $V_{ICM,min} = V_p + V_{th} 
  
    $V_{ICM,min} = -0.7 + 0.36 
  
   $V_{ICM,min}  =  -0.34V 


  
- **Maximum:**


  $V_{ICM,max} = V_{out} + V_{th} 

  $V_{ICM,max} =  0 + 0.36

  $V_{ICM,max} = 0.36V$ 
  





### Output Common-Mode Range (OCMR) Analysis

 The OCMR defines the allowable swing at the output nodes ($V_{out1}, V_{out2}$) while keeping $M_1$ and $M_2$ in 
 
 saturation.


A. Maximum Output Voltage ($V_{OCM,max}$)The maximum output is limited by the supply voltage $V_{DD}$.


B. Minimum Output Voltage ($V_{OCM,min}$)The minimum output is reached when $M_1$ (or $M_2$) enters the triode 

region ($V_{DS} = V_{GS} - V_{th}$).



### OCMR (Output Common-Mode Range)

- **Minimum:**


  $V_{OCM,min} = V_{oCM} - V_{th}

  $V_{OCM,min} =  0 - 0.36

  $V_{OCM,min} = -0.36V$

  
- **Maximum:**

 $V_{OCM,max} = V_{DD} = 0.9V$



 Metric | Minimum Value | Maximum Value |

  
Input Common-Mode  (ICMR) | −0.34V | +0.36V |


Output Common-Mode (OCMR) | −0.36V | +0.90V |




Linear Differential Input Region Analysis

The linear region of a differential amplifier is the range of the differential input voltage 

($V_{id} = V_{in1} - V_{in2}$) over which both transistors $M_1$ and $M_2$ remain in the saturation region and 

contribute to the output.




For a MOS differential pair, the maximum differential input voltage ($V_{id,max}$) before the entire tail current

($I_{SS}$) is steered into a single transistor is defined by the overdrive voltage 

($V_{OV}$):$$V_{id,max} = \sqrt{2} \cdot V_{OV}$$




Gate-Source Voltage ($V_{GS}$): $0.7\text{V}

$Threshold Voltage ($V_T$): $0.36\text{V}

$Overdrive Voltage ($V_{OV}$): $V_{GS} - V_T = 0.7\text{V} - 0.36\text{V} = \mathbf{0.34\text{V}}$



Calculation:$$V_{id,max} = \sqrt{2} \cdot 0.34\text{V} \approx \mathbf{0.48\text{V}}$$



* Linear Range 


($|V_{id}| < \sqrt{2}V_{OV}$)


Both $M_1$ and $M_2$ are ON and operating in saturation. 


The output voltage is a linear function of the differential input.


Saturation/Clipping ($|V_{id}| > \sqrt{2}V_{OV}$):

One transistor carries the full tail current ($I_{SS} = 0.833\text{mA}$), while the other transistor turns OFF 

($I_D = 0$). The output voltage clips at its maximum or minimum level, leading to severe distortion.




$$
|v_{id}| \leq \sqrt{2} V_{OV}
$$

$$- \sqrt{2} V_{OV} \leq v_{id} \leq \sqrt{2} V_{OV}$$

$$   Final range :  -0.48 \leq v_{id} \leq 0.48$$




### Summary of Operation

| Input Condition | Circuit State | Output Behavior |

| :--- | :--- | :--- |

| $|V_{id}| < 0.48V$ | $M1$ and $M2$ both ON | Linear Amplification |


| $|V_{id}| > 0.48V$ | Current Steering (One transistor OFF) | Non-linear / Output Clipping |



### Linear region analysis:

($|V_{id}| < \sqrt{2}V_{OV}$)

  $|V_{id}| < 0.48V$

   $300mv < 0.48V$

<img width="1132" height="762" alt="image" src="https://github.com/user-attachments/assets/682e91cf-e6b8-4f7e-b3f1-5fe31031c9d2" />


<img width="1919" height="846" alt="Screenshot 2026-03-29 063921" src="https://github.com/user-attachments/assets/9f07ef0f-8bdd-49ab-93fa-40af80622cdd" />



##  Transient Analysis: Linear Region Behavior


- **Input 1:** SINE(0 150m 1k)
  
- **Input 2:** SINE(0 -150m 1k)
  
- **Condition Check:** $V_{id} (300mV) < \sqrt{2}V_{OV} (480mV)$


### Results and Observations

The simulation waveforms  demonstrate:

1. **Phase Relationship:** The two outputs ($V_{out1}$ and $V_{out2}$) are exactly $180^\circ$ out of phase, confirming standard differential operation.
   
3. **Signal Integrity:** The output sinusoids maintain a pure shape without clipping, verifying that the circuit is operating within the calculated linear region.

5. **Common-Mode Stability:** The source node ($V_p$) remains stable, allowing the differential pair to steer current effectively.

**Conclusion:** The transient simulation validates the theoretical linear range calculations. The amplifier provides consistent gain for inputs up to approximately 480mV.







##  Transient Analysis: Non-Linear (Clipping) Behavior

### Simulation Setup

To observe the limits of amplification, the differential input ($V_{id}$) was increased to **600mV**, which exceeds the theoretical linear limit of **480mV**.

- **Input Signals:** SINE(0 300m 1k) and SINE(0 -300m 1k)
- 
- **Constraint Check:** $V_{id} (600mV) > \sqrt{2}V_{OV} (480mV)$


<img width="1918" height="867" alt="image" src="https://github.com/user-attachments/assets/57836bd7-9c22-42df-95b6-df03c82b9317" />


### Results and Interpretation
The waveforms in this test exhibit clear **non-linear distortion**:

1. **Output Flattening:** The output signals ($V_{out1}$ and $V_{out2}$) show significant flattening at the peaks. This occurs because the differential pair is fully steering the tail current ($I_{SS}$) into one branch, leaving the other branch with insufficient current to maintain a linear output.
   
3. **Gain Compression:** As $V_{id}$ increases beyond the linear threshold, the incremental gain decreases, leading to the observed compression in the output swing.
   
5. **Region of Operation:** At the signal peaks, the transistors are no longer operating in the constant-current saturation region required for linear amplification.
   

**Conclusion:** This simulation confirms the theoretical boundary of $\sqrt{2}V_{OV}$. For high-fidelity applications, the input must be maintained below 480mV to avoid the distortion observed in this analysis.




### Small Signal Gain Analysis ($A_v$):

For a MOS differential amplifier with a resistive load ($R_D$), the differential voltage gain is defined as the ratio of the change in output voltage to the 

change in differential input voltage ($V_{id}$).


<img width="1918" height="846" alt="image" src="https://github.com/user-attachments/assets/20486a86-0815-4f61-9f59-46faa72dc3f0" />


### 1. Theoretical Calculation:

 The theoretical gain for a single-ended output is given by:
 
 When channel length modulation is considered, the single-ended voltage gain formula becomes $$ A_v = -g_m (R_D \parallel r_o)$$
 
 Calculate Transistor Output Resistance ($r_o$)
 
 The output resistance is inversely proportional to the channel length modulation coefficient ($\lambda$) and the drain current($I_D$) 
 
 $\lambda$: $0.1\text{ V}^{-1}$ 
 
 (Given)$I_D$: $0.4165\text{ mA}$
 
 Calculation:
 
 $$r_o = \frac{1}{\lambda \cdot I_D}= \frac{1}{0.1 \cdot 0.4165 \times 10^{-3}} \approx \mathbf{24.01\text{ k}\Omega}$$
 
 Effective Load Resistance ($R_{L,eff}$)  The effective load is the parallel combination of the drain resistor ($R_D$) and the transistor's output resistance ($r_o$):$R_D$: $2.16\text{ k}\Omega$
 
 $$R_{L,eff} = R_D \parallel r_o = \frac{2.16\text{k} \cdot 24.01\text{k}}{2.16\text{k} + 24.01\text{k}} \approx \mathbf{1.98\text{ k}\Omega}$$

 
  $$|A_v| = g_m \cdot R_{L,eff} = 2.45\text{ mS} \cdot 1.98\text{ k}\Omega \approx \mathbf{4.85\text{ V/V}}$$

* In decibels (dB):

$$A_v(dB) = 20 \log_{10}(4.85) \approx 13.71\text{ dB}$$

 
### 2. Simulated Gain (From Waveforms)Based on the transient simulation results:


Peak Input Voltage ($V_{in,peak}$): $150\text{ mV}$


Peak Output Voltage ($V_{out,peak}$): From the waveform V(out1)  or V(out2)  the peak is $600\text{ mV}$.


 Simulated Gain: $A_{v(sim)}$ = $\frac{V_{out,peak}}{V_{in,peak}}$ = $\frac{600\text{ mV}}{150\text{ mV}}$ = $\mathbf{4\text{ V/V}}$

 * In decibels (dB):

$$A_v(dB) = 20 \log_{10}(4.00) \approx 12.04\text{ dB}$$


* The voltage gain of the differential amplifier was evaluated both theoretically and through transient simulation.

| Metric | Value |

| :--- |  :--- |

| **Transconductance ($g_m$)** | 2.45 mS |

| **Theoretical Gain ($A_v$)** | 4.85 V/V | 13.71 dB |

| **Simulated Gain ($A_{v,sim}$)** | 4.0 V/V | 12.04 dB |


The remaining difference is likely due to the more complex sub-threshold and body effect parameters present in the `tsmc018.lib` BSIM models used in LTspice.



# AC Analysis & Frequency Response:

The AC analysis was performed to determine the high-frequency performance of the differential amplifier when loaded with a 10pF capacitor.



<img width="1363" height="830" alt="image" src="https://github.com/user-attachments/assets/daf695e3-92ae-4a35-8723-3c630d3fdcf1" />



<img width="1918" height="843" alt="image" src="https://github.com/user-attachments/assets/4f13c0f5-460b-4645-9ea4-ffd574d0271c" />




Midband gain: 15.96 dB = 24.06 V/V.

Bandwidth is measured at: Av(mid) − 3 dB = 15.96 − 3 = 12.96 dB

fH (upper cutoff frequency) ≈ 8.05 MHz 

fL (lower cutoff frequency) ≈ 0 Hz

Therefore: Bandwidth (BW) ≈ 8.05 MHz.

* 3dB Bandwidth (BW):

Theoretical Check:

$$f_{3dB} = \frac{1}{2\pi \cdot R_D \cdot C_L} = \frac{1}{2\pi \cdot 2.16\text{k}\Omega \cdot 10\text{pF}} \approx \mathbf{7.37\text{ MHz}}$$



Unity gain Bandwidth:



<img width="1918" height="855" alt="image" src="https://github.com/user-attachments/assets/a4fa5b97-f640-4032-ba33-187f3251ecaa" />



From AC analysis plot At frequency ≈ 48.85 MHz

Magnitude ≈ -6.52mdB at 0 dB

Therefore, UGB ≈ 48.85 MHz


$$A_{v,linear} = 10^{\left( \frac{15.96}{20} \right)}$$


$$A_{v,linear} = \approx \mathbf{6.28 \text{ V/V}}$$


The GBP is the product of the Gain ($A_{v,linear}$) and the Bandwidth ($BW$):


$$UGB = 6.28 \times 8.05 \text{ MHz}$$


$$UGB \approx \mathbf{50.55 \text{ MHz}}$$


### Simulation Results Summary

| Parameter | Value |

| :--- | :--- |

| **Mid-band Gain** | 15.96 dB (6.28 V/V) |

| **3dB Bandwidth (BW)** | 8.05 MHz |

| **Unity Gain Bandwidth (UGB)** | 48.85 MHz |

| **Gain Bandwidth Product (GBP)** | 50.55 MHz |



# Overall Inference:

The experiment successfully demonstrates the design and performance trade-offs of a MOSFET Differential Amplifier in $180\text{nm}$ technology.

By fixing the tail current at $0.833\text{mA}$, we achieved a stable operating point that meets the power constraint of $\le 1.5\text{mW}$.

The transition from a theoretical width ($11.23\mu\text{m}$) to a simulated width ($19.90\mu\text{m}$) highlights the impact of non-ideal process parameters like channel length modulation. 

Furthermore, the AC analysis confirms that the high-frequency performance is dominated by the output pole created by the $R_D C_L$ network, providing a gain of 

$15.96\text{dB}$ and a bandwidth of $8.05\text{MHz}$.




## Overall Conclusion

The design and analysis of the MOS Differential Amplifier (Circuit 1) were completed successfully. The following key objectives were met:

1. **DC Biasing:** The operating point was successfully fixed at $V_p = -0.7V$ and $V_{out} = 0V$, ensuring both transistors remain in the saturation region for maximum signal swing.
   
2. **Linearity:** Transient analysis confirmed a linear input range of approximately 480mV. Inputs exceeding this value resulted in noticeable current steering and output clipping.
   
3. **Frequency Response:** With a $10pF$ load, the amplifier achieved a 3dB bandwidth of 8.05 MHz and a Unity Gain Bandwidth (UGB) of 48.85 MHz.



## Summary of Results

The following table summarizes the design specifications and the results obtained through LTspice simulation for the 180nm CMOS Differential Amplifier.

| Parameter | Theoretical / Target | Simulated Result | Observation |

| :--- | :--- | :--- | :--- |

| **Power Consumption** | ≤ 1.5 mW | 1.5 mW | Satisfies project requirement. |

| **Operating Point ($V_p$)** | -0.7 V | -0.7004 V | Stable biasing achieved. |

| **Voltage Gain** | 4.85 V/V | 4.0 V/V | Reduction due to finite output resistance ($r_o$). |

| **3dB Bandwidth** | 7.37 MHz | 8.05 MHz | Pole set by $R_D$ and 10pF load. |

| **Unity Gain BW (UGB)** | -- | 45.6 MHz | High-frequency limit of the amplifier. |

| **Linear $V_{id}$ Range** | ± 0.48 V | ± 0.48 V | Verified through transient analysis. |






## CIRCUIT - 02 

## CMOS Differential Amplifier with PMOS Active Load and NMOS Tail Current Source.


# Aim: 

**To design and analyze a MOS Differential Amplifier for the following specifications:**

- Supply Voltage: VDD = 0.9 V  
- VSS = -0.9 V  
- Input Common Mode Voltage (VICM) = 0 V  
- Output Common Mode Voltage (VOCM) = 0 V  
- Channel Length (L) = 360 nm  
- Power Constraint: P ≤ 1.5 mW



# Theory of Operation:

** The circuit is designed to amplify the difference between two input signals, $V_{in1}$ and $V_{in2}$, while rejecting the common-mode signal.Differential Pair ($M_1, M_2$): 
These NMOS transistors convert the differential input voltage into differential currents.

** Active Load ($M_3, M_4$): These PMOS transistors act as current sources. 
In this specific configuration (gates tied to a reference or ground), they provide high output impedance, which significantly increases the voltage gain compared to passive resistors.

** Current Tail ($M_5$): This NMOS transistor is biased in the saturation region to act as a constant current source $I_{SS}$, ensuring the total current $I_{D1} + I_{D2}$ remains constant




<img width="1463" height="837" alt="image" src="https://github.com/user-attachments/assets/53d2aa7f-66fd-4e75-ae4e-54700486e9ac" />




# DESIGN CALCULATIONS:


### * DC ANALYSIS:


SpecificationsTechnology Channel Length ($L$): $360\text{ nm}$

Supply Voltage ($V_{DD}$): $0.9\text{V}$

Negative Supply ($V_{SS}$): $-0.9\text{V}$

Total Voltage Swing ($V_{total}$): $1.8\text{V}$ ($0.9\text{V} - (-0.9\text{V})$

Power Dissipation Limit ($P$): $\le 1.5\text{mW}$ (Using $1.5\text{mW}$ for design)$

Required Input Common Mode ($V_{inCM}$): $0\text{V}$

Target Output Common Mode ($V_{outCM}$): $0\text{V}$

Common Source Node Voltage ($V_p$): $-0.7\text{V}$

Process Parameter ($\mu_n C_{ox}$): $2.305 \times 10^{-4}\text{ A/V}^2$

Threshold Voltage ($V_T$): $0.36\text{V}$


** Determine Tail Current ($I_{SS}$)


To satisfy the power constraint:



$$I_{SS} \le \frac{P_{limit}}{V_{total}} = \frac{1.5\text{ mW}}{1.8\text{ V}} \approx 0.833\text{ mA}$$


$I_{SS} = \mathbf{0.833\text{ mA}}$




For a balanced common-mode input:


$$I_{D1} = I_{D2} = \frac{I_{SS}}{2} = \frac{0.833\text{ mA}}{2} = \mathbf{0.4165\text{ mA}}$$




Transistor Operating Point ($M_1, M_2$):


Given $V_{inCM} = V_G = 0\text{V}$ and $V_p = V_S = -0.7\text{V}$:



$$V_{GS} = V_G - V_S = 0 - (-0.7) = \mathbf{0.7\text{ V}}$$


$$V_{OV} \text{ (Overdrive Voltage)} = V_{GS} - V_T = 0.7 - 0.36 = \mathbf{0.34\text{ V}}$$


$$V_{DS} = V_{out} - V_S = 0 - (-0.7) = \mathbf{0.7\text{ V}}$$



Condition for Saturation: 


$V_{DS} > V_{OV}$ $\rightarrow$ $0.7\text{V} > 0.34\text{V}$ (Confirmed: Saturation region)



Transistor Sizing (Width Calculation)

Using the drain current equation to solve for $W$:



$$I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{OV})^2$$




$$W = \frac{2 \times I_D \times L}{\mu_n C_{ox} \times (V_{OV})^2}$$


$$W = \frac{2 \times 0.4165 \times 10^{-3} \times 360 \times 10^{-9}}{2.305 \times 10^{-4} \times (0.34)^2}$$



$$W = 11.235 \times 10^{-6}\text{ m} = \mathbf{11.235\text{ \µm}}$$
