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

  
