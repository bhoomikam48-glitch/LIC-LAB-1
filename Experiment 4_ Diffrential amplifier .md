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


* Modes of Operation

###  Differential Mode


V_{id} = V_{in1} - V_{in2}


Gain for differential input:


Av  = $$ V_{pp,out}/{V_{ind} $$


This is the desired mode of operation.



Common Mode


$$ V_{icm} = {V_{in1}} + V_{{in2}}/{2} $$ 


Ideally:


A_{cm} = 0


In practice, small nonzero gain exists due to:

- Finite tail resistance
- Mismatch
- Channel length modulation



Common Mode Rejection Ratio (CMRR):


CMRR = {A_d} / {A_{cm}


In dB:


CMRR_{dB} = 20 \log \left(\frac{A_d}{A_{cm}}\right)
