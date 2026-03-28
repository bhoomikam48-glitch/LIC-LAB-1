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



$$W = 11.235 \times 10^{-6}\text{ m} = \mathbf{11.235\text{ \mu m}}$$



### Operating point:


<img width="1185" height="752" alt="image" src="https://github.com/user-attachments/assets/e14aa54a-74ef-44ec-945b-31bf8265c761" />




| Stage | Width ($W$) |

| **Theoretical** | 11.23 µm | 

| **Final (Simulated)** | 19.90 µm | 

**Observation:** The increase in width from 11.23 µm to 19.90 µm was necessary to maintain the tail current of 0.833mA while keeping the transistors  in the saturation region .





Parameter, Hand Calculated, LTspice Simulated

Tail Current (ISS​), 0.833 mA,  0.833 mA

"Drain Current (ID1,2​)",0.4165 mA, 0.4165 mA

Node Voltage Vp​,−0.700 V,  −0.700479 V

Output CM Voltage Vout​,0.000 V,  0.00036 V


The DC operating point is successfully fixed. 

Both $M1$ and $M2$ are operating in the saturation region, providing a stable baseline for subsequent Transient and AC analysis.



