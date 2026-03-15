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



