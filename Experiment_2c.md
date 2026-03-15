# Experiment 2 c) : Diode-Connected Common-Source Amplifier with Source Degeneration.

# AIM : Design of an NMOS Diode-Connected with a PMOS active load using 180nm technology in LTspice.

# CIRCUIT:


<img width="1237" height="783" alt="Image" src="https://github.com/user-attachments/assets/f9014c71-0ced-4a30-b158-65f39dece774" />


* A diode-connected NMOS with PMOS active load is a common configuration in CMOS analog circuits used for bias generation, current mirroring, and amplifier stages. In this circuit, one NMOS transistor is diode-connected (its gate and drain are shorted), while another NMOS acts as the amplifying device. A PMOS transistor is used as an active load connected to the supply voltage.

* This structure provides stable biasing, higher gain, and efficient use of silicon area, making it widely used in analog VLSI design.
  

  | Transistor | Type | Function                   |
| ---------- | ---- | -------------------------- |
| M1         | NMOS | Diode-connected transistor |
| M2         | NMOS | Amplifying transistor      |
| M3         | PMOS | Active load                |


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


