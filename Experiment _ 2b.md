# Experiment 2 b) : Cascode Amplifier

# AIM :  Design of an NMOS cascode stage with a PMOS active load using 180nm technology in LTspice.

# CIRCUIT:


<img width="1085" height="832" alt="image" src="https://github.com/user-attachments/assets/47ac7ce2-b62a-4afc-a04b-28355c51c25a" />


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


 Power verification:

 Let ID = 200 µA

  $$P = V_{DD} \times I_D = 2\text{V} \times 200\mu\text{A} = 0.4\text{mW}$$

  Verification: $0.4\text{mW} \leq 1.5\text{mW}$ (Constraint satisfied).




  Also,
 
  Vout = VDD/2 
 
  Vout = 2/2

  Vout = 1 = 1V










 # For M3 Transistor:




​
  VGS3 = VOV + VTH 
  
  VGS3  =   0.25 + 0.36
  
  VGS3  = 0.61V
	


	

	
	​

 Assume , VS1 = 0.3V 

 




 VDS3 = VS1 = 0.3V ( VS3 = 0)

 






 

* For M3 to be SATURATION,


 



  VGS3 >= VTH

  



  0.61 V >= 0.36 V
  



  and VDS3 >= VOV
  



 VDS = 0.3 V 
 



 Hence, 0.3 >= 0.25
 



 Therefore both the conditions are satisfied. 

 



 Therefore M3 is operating in SATURATION region.
	












 




 # For M1 Transistor :
   

   VGS3 = VOV + VTH 
   
  
   VGS3  =   0.25 + 0.36
   
  
   VGS3  = 0.61V
   




  VG1 = VS1 + VGS1
  
 
  VG1 = 0.3 + O.61
  

  VG1 = 0.91V
  







 * For M1 to be SATURATION,
   

  VGS1 >= VTH
  

  0.91 V >= 0.36 V
  



  and VDS1 >= VOV
  


  VDS1 = VOUT - VS1
  

  VDS1 = 1 - 0.3
  


  VDS1 = 0.7V
  



  Therefore , VDS1  >= VOV.
  

  
   0.7 >= 0.25 
   

  
 Therefore both the conditions are satisfied. 
 



 Therefore M1 is operating in SATURATION region.
 
	







#  For M2 Transistor :(PMOS)
  

  
 
 VSG2 = VOV + |VTH| 
 

 
  VSG2    = 0.25 + 0.39 
  

   
   VSG2   = 0.64 V
   




  VSG2 = VS2 - VG2
  


  0.64  =  2 - VG2



   VG2 = 1.36V





   VSD2 = VDD - VOUT 
   

   
   VSD2   = 2 - 1 
   

	
   VSD2 = 1
   




  * For M2 to be SATURATION,
   
   

  VSG2 >= VTH
  



  1.36 V >= 0.39 V
  


  and VSD2 >= VOV
  



  Therefore , VSD2 >= VOV.
  

  
   1 >= 0.25 
   


  
 Therefore both the conditions are satisfied.
 



 Therefore M2 is operating in SATURATION region.

 

# For M1 and M3 Transistor :


 * The Drain -current equation is given by,

 
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


W = 5 µm ,  for  ID= 200µA
    


# For M2 Transistor:


* The Drain -current equation is given by,

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

W = 11.8 µm ,  for ID= 200µA


<img width="1860" height="851" alt="Image" src="https://github.com/user-attachments/assets/4a56d35e-2242-4ca8-a475-c8b9abb1e88c" />


With these calculated width , we get ID=63.5µA , VOUT=1.46V

Taking the ratio of the current i.e. = 200 / 63.5 = 3.14 (assumed current ID = 200 , simulated ID = 63.5).


Wn = 5 * 3.14 = 15.7 µm , Wp = 11.8 * 3.14 = 37.05µm , taking reference as 15.7 µm , 37.05µm start increasing or

decreasing the width values to get ID = 200 µA , VOUT = 1.0V



<img width="1756" height="845" alt="Image" src="https://github.com/user-attachments/assets/6db05518-0583-4a34-8442-4a9f1ea95488" />


* Final Width values : Wn = 18.5µm (for M1) ,   Wn = 16.6µm (for M3) ,   Wp = 34.6µm (for PMOS).

* After tuning width values we get  ID=200µA , VOUT=1.0V which matches with theoretical and simulated analysis.

### Comparison of Initial vs. Final Design Parameters

| Parameter | Symbol | Initial Design | Final Optimized Design |
| :--- | :--- | :--- | :--- |
| **Drain Current** | $I_D$ | $63.5\text{ }\mu\text{A}$ | **$200\text{ }\mu\text{A}$** |
| **M1 Width (Input)** | $W_{n1}$ | $5\text{ }\mu\text{m}$ | **$18.5\text{ }\mu\text{m}$** |
| **M3 Width (Tail)** | $W_{n3}$ | $5\text{ }\mu\text{m}$ | **$16.6\text{ }\mu\text{m}$** |
| **M4 Width (PMOS)** | $W_{p}$ | $11.8\text{ }\mu\text{m}$ | **$34.6\text{ }\mu\text{m}$** |
| **Channel Length** | $L$ | $180\text{ }\text{nm}$ | $180\text{ }\text{nm}$ |



# Transfer Analysis : (DC Sweep)


<img width="1918" height="855" alt="Image" src="https://github.com/user-attachments/assets/e99cc4d4-4abc-46cd-91f1-633cdb31bac2" />




DC Sweep Analysis (Voltage Transfer Characteristics)


The DC sweep plot reveals three distinct regions of operation for the cascode amplifier:

* Cut-off Region ($V_{in} < V_{thn}$):

When $V_{in}$ is below the threshold voltage (approx. $0.36\text{V}$), the input transistor $M_1$ is OFF.No current flows through the branch. The PMOS load pulls $V_{out}$ up to $V_{DD}$ ($2\text{V}$).


* Saturation (High Gain Region):

As $V_{in}$ increases beyond $V_{thn}$, the transistors enter the saturation region.This is the steep linear portion of the blue curve (centered around $V_{in} \approx 0.9\text{V}$).In this region, the amplifier provides maximum gain. Small changes in $V_{in}$ result in large swings in $V_{out}$.

* Triode/Linear Region:

As $V_{in}$ continues to increase (above $1.1\text{V}$), $V_{out}$ drops so low that the NMOS transistors enter the triode region.The output flattens out at the "lower rail," which is the sum of the $V_{DS,sat}$ of the bottom transistors.



### DC Sweep Analysis Summary (VTC)

| Input Voltage ($V_{in}$) | Output Voltage ($V_{out}$) | Region of Operation | Status |
| :--- | :--- | :--- | :--- |
| 0.0 V to 0.4 V | ~ 2.0 V | Cut-off | Output at VDD |
| 0.6 V | ~ 1.9 V | Transition | M1 starts conducting |
| **0.91 V (Bias)** | **~ 1.1 V** | **Saturation** | **Active Gain Region** |
| 1.0 V | ~ 0.7 V | High Swing | Approaching Triode |
| 1.2 V to 2.0 V | ~ 0.4 V | Triode / Saturation | Output Clipping (Low) |




# Transient Analysis:


Transient analysis in a Common Source (CS) amplifier studies how the circuit responds to time-varying signals, especially during switching (turn-on / turn-off) or sudden changes in input.




