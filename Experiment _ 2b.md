# Experiment 2 b) : Cascode Amplifier

# AIM :  Design of an NMOS cascode stage with a PMOS active load using 180nm technology in LTspice.

# CIRCUIT:


<img width="1085" height="832" alt="image" src="https://github.com/user-attachments/assets/47ac7ce2-b62a-4afc-a04b-28355c51c25a" />



Given data: VDD=2V , P<=1.5mW , Vov=0.25V , Vthn=0.36V , Vthp=0.39V , CL=1pF , Ln=Lp=180nm .



In this configuration:

* M1 (Driver): Acts as the standard common-source transconductor, converting your input voltage ($V_{in}$) to a current.

* M3 (Current Source): Replaces the source-degeneration resistor, acting as a high-impedance tail current source to set the bias current.

* M2 (PMOS Load): Remains as your Active Load.


Extremely High Output Resistance ($R_{out}$)

In a simple common-source stage, the output resistance is roughly $r_{o1} \parallel r_{o2}$.

In a cascode, the output resistance is boosted to approximately $g_{m1} \cdot r_{o1} \cdot r_{o3}$.

Benefit: Since Gain $\approx g_m \cdot R_{out}$, 

this boost in $R_{out}$ leads to a significantly higher voltage gain without needing to increase the size of the transistors.



# DC ANALYSIS:

* Design calculations:


 power verification:

 Let ID = 200 µA

 P = VDD*ID

 Power = 2*200 µA = 0.4mW which is <= 1.5mW.

 Thus power is verified.

 Also,
 Vout = VDD/2 + VS1
 
 Vout = VDD/2 + 0.3

 Vout =1+0.3 = 1.3V.

 
  
