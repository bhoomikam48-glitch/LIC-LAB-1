# LIC LAB -2 

# Common Source Amplifier Configurations

#  Experiment a) :  Source Degenerated Common Source Amplifier.

# AIM: 
 Design of PMOS active load configuration in tsmc018lib using LTspice.

# Circuit:
<img width="1280" height="708" alt="image" src="https://github.com/user-attachments/assets/cb65f43c-62d7-44e1-a1e0-03ac5f73d0c0" />



Given data: VDD=2V , P<=1.5mW , Vov=0.25V , Vthn=0.36V , Vthp=0.39V , CL=1pF , Ln=Lp=180nm .


* DC ANALYSIS:

  Here ,
  * The PMOS transistor M1 is acting as the Active Load.
  In a standard amplifier, you might use a passive resistor (RD). Here, you’ve replaced it with a transistor (an "active" device).
  M1 is biased by the DC voltage source V3. This keeps M1 in the Saturation Region, where it acts like a constant current source.

 * The resistor R1  connected to the source of the NMOS M2 is the Source Degeneration element.
   "Degeneration": The term refers to Negative Feedback. As the input voltage (vin) increases, the current through M2 increases.

    The Benefit:
    * Linearity: It flattens the gain, making the output a more accurate (though smaller) reproduction of the input.
    * Stability: It makes the circuit less sensitive to variations in the transistor's manufacturing parameters (like VTH).
  

   # Design calculations:

   # NMOS Transistor: 

   * power verification:

     Let ID = 200 µA

     P = VDD*ID

     Power = 2*200 µA = 0.4mW which is <= 1.5mW.
     
     Thus power is verified.


     Given,
     VRS = 0.2V ,VOV = 0.25V
     
     We know that,
     
     VRS = IDRS , 0.2/200µ = RS , RS = 1kΩ.

     Also,

     Vout = VDD/2 + 0.2
     
     Vout =1+0.2 = 1.2V.


     * To find Vgs :
       VOV = 0.25V , Vth=0.36V
       
       VOV = Vgs-Vth
       
       Vgs = 0.25+0.36
       
       Vgs = 0.61V


      * Biasing voltage VB1 is obtained by,
        
        VB1 = VG1 = VGS + IDRS = 0.61 + 0.2 = 0.81V


       * Condition for saturation:
         
         VGS >= VTH
         0.61 >= 0.36
         
         and VDS >= VOV

        (VDD/2) >= VOV

        1 >= 0.25.

      Thus, it satisfies the condition of saturation for NMOS.



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

   Cox = (ε0 × εr) / tox ,  Cox =(8.854 ×10^-12 × 3.9)/4.1 × 10^-9
  
   Cox = 8.42 × 10⁻³ F/m²

    By rearranging,  ID = (1/2) μn Cox (W/L) (VOV)²
   
     w = 5 µm , ID= 200µA

       
     
  # PMOS transistor:

  Given: Vthp=0.39V  ,VOV=0.25V
 
   VOV = Vgs-|Vth|
       Vgs = 0.25+0.39
       Vgs = 0.64V
       
  Biasing voltage VB1 is obtained by,
 
 VB2 = VG2 = VS + VSG = VDD - VSG = 2- 0.64 = 1.36V


   * Condition for saturation:


       VSG >= VTH
          0.64 >= 0.36
          and VDS >= VOV


   (VDD/2) >= VOV
   
   1>=0.25

   
   Thus, it satisfies the condition of saturation for PMOS.




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


 By rearranging,  ID = (1/2) μn Cox (W/L) (VOV)²


 
  w = 11.8 µm , ID= 200µA  



  
      
 <img width="1167" height="685" alt="image" src="https://github.com/user-attachments/assets/46e7c177-9757-43c9-a511-0981ddd499ae" />






 With these calculated width , we get ID=76µA , VOUT=0.12V





 
 Taking the ratio of the current i.e. = 200 / 76 = 2.6  (assumed current ID = 200 , simulated ID = 76).




  Wn = 5 * 2.6 = 13 µm ,   Wp = 11.8 * 2.6 = 30.68µm , taking  reference as 13 µm ,  30.68µm start increasing the width values to get ID = 200 µA , VOUT = 1.2V


  




  **Final Width values :  Wn = 29.7µm  (for NMOS) ,  Wp = 35.7µm (for PMOS).**
   





  <img width="1082" height="587" alt="image" src="https://github.com/user-attachments/assets/a9557482-3998-491f-972f-244b2e768e92" />


  





  ID = 200µA , VOUT = 1.21V




  

  Thus simulated and theoretical values matched and verified.





# Transfer analysis: (DC Sweep) 



<img width="1918" height="856" alt="image" src="https://github.com/user-attachments/assets/0eba4912-fa76-4aa9-806d-e8888f737fe4" />

  



The graph shows three distinct regions of operation for your NMOS driver (M2):

### Regions of Operation
| Region | Input Range ($V_{in}$) | Output Behavior | MOSFET State ($M2$) |
| :--- | :--- | :--- | :--- |
| **Cut-off** | $0V$ to $\approx 0.5V$ | $V_{out} \approx V_{DD}$ (2V) | **OFF**: No current flows. |
| **Saturation** | $\approx 0.6V$ to $1.0V$ | High-Slope (Linear) | **ON**: Active amplification region. |
| **Triode** | $> 1.0V$ | $V_{out}$ flattens near $0V$ | **Deep ON**: Resistance is low; gain is lost. |

---
   


# Transient analysis:

Transient analysis in a Common Source (CS) amplifier studies how the circuit responds to time-varying signals, especially during switching (turn-on / turn-off) or sudden changes in input.


input waveform:

<img width="1918" height="852" alt="image" src="https://github.com/user-attachments/assets/a5a02434-f87e-4b09-9354-4aaa24416635" />


output waveform:

<img width="1915" height="848" alt="image" src="https://github.com/user-attachments/assets/f75b9656-405e-4ca4-b431-91e7fe196846" />



##  Transient Analysis Results

The transient simulation was performed with a $1kHz$ sinusoidal input signal .

### Waveform Observations
| Parameter | Input Waveform ($V_{in}$) | Output Waveform ($V_{out}$) |
| :--- | :--- | :--- |
| **Peak-to-Peak** | $\ 19.55mV$ | $\ 0.22V$ |
| **Phase Shift** | $0^\circ$ | $180^\circ$ |


### Gain Verification
The transient gain is calculated as the ratio of the output peak-to-peak voltage to the input peak-to-peak voltage:

$$A_{v(tran)} = \frac{V_{out(p-p)}}{V_{in(p-p)}}$$

Using values from the simulation plots:
* **$V_{in(p-p)} \ 809.91mV - 790.36mV = 19.55mV$**
* **$V_{out(p-p)} \ 1.49V - 1.27V = 0.22V$**

$$A_v = \frac{0.22V}{19.55mV} = 11.25 \text{ V/V}$$



  Av(dB) = 20 log(11.25) = 21.02dB



* The clean, undistorted sine wave confirms that the circuit is successfully biased in the **Saturation (Active) Region**.




* Theoretical gain:

  gm = 2ID / VOV
  
  gm = (2 × 200 × 10⁻⁶) / 0.25
 
  gm = 1.6 × 10⁻³ S
 

  ro = 1 / (λ ID)
 
  ro = 1 / (0.1 × 200 × 10⁻⁶)
 
  ro = 50 kΩ


  (ro1 || ro2) = 25 kΩ
 

  Av = - gm (ro1 || ro2) / (1 + gm RS) Av = - (1.6 × 10⁻³ × 25 × 10³) / (1 + 1.6 × 10⁻³ × 1 × 10³) Av = -40 / 2.6
 
  Av = -15.38 V/V


  Av(dB) = 20 log(15.38)
 
  Av(dB) = 23.74 dB


  ##  Gain Analysis: Theoretical vs. Practical

The amplifier was designed for a theoretical gain of **23.74 dB**. Upon simulation, the practical gain was measured at **21.02 dB**. This deviation is common in 180nm CMOS design due to second-order physical effects not captured in simplified manual calculations.

### Factors Contributing to Gain Loss

| Factor | Description | Impact on Gain |
| :--- | :--- | :--- |
| **Body Effect** | Source degeneration raises $V_{SB} > 0$, increasing $V_{th}$. | Reduces $g_m$ (transconductance). |
| **Channel Length Modulation** | Finite output resistance ($r_o$) of the MOSFETs. | Shunts the load, reducing total resistance. |
| **Non-Ideal Transistors** | Manual models assume ideal current sources. | Actual devices have parasitic effects in `tsmc018.lib`. |




 # AC Analysis:

 ##  Frequency Response Analysis:

The AC analysis was performed across a frequency range of $0.1Hz$ to $100GHz$. The frequency response demonstrates the bandwidth limits imposed by parasitic capacitances in the 180nm CMOS process.

<img width="1918" height="852" alt="image" src="https://github.com/user-attachments/assets/f54cc4d4-8c48-4ab4-b999-293e55482b97" />


Bandwidth is measured at: Av(mid) − 3 dB = 21.02 − 3
= 18.02 dB fH (upper cutoff frequency) ≈ 212.875 MHz
fL (lower cutoff frequency) ≈ 0 Hz

Therefore: Bandwidth (BW) ≈ 212.875 MHz.

Unity gain Bandwidth:


<img width="1917" height="853" alt="image" src="https://github.com/user-attachments/assets/4d750859-f6f2-4383-a1b3-9cf5e9eea1ab" />



From AC analysis plot At frequency ≈ 3.00 GHz

Magnitude ≈ 5.70mdB at 0 dB

Therefore, UGB ≈ 3.00 GHz

UGB ≈ Av(midband) × Bandwidth ( Theoretical Gain ≈ 15.384 dB)

Av ≈ 15.384 * 212.875 MHz
Now, UGB = Av × Bandwidth
UGB = 15.384 × 212.87 MHz
UGB ≈ 3.2 GHz

* From simulation analysis: UGB ≈ 3.00 GHz
  
* From Gain–Bandwidth product: UGB ≈ 3.2 GHz


* Thus Gain bandwidth product , practically and theoretically are verified and validated.
  
* The value 3 and 3.2 are very close .


# Conclusion:
 
 The design successfully balances gain and linearity.
 
 The Active Load provides high-impedance gain, while the Source Degeneration ensures stability and a broader linear operating range.
 
 The experiment demonstrates that for high-performance analog design, second-order effects like body-biasing and output impedance are essential considerations for  accurate performance prediction.
 
