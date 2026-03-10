# Common Source Amplifier Configurations

# a) Source Degenerated Common Source Amplifier.

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





# Transfer analysis:



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

<img width="1918" height="857" alt="image" src="https://github.com/user-attachments/assets/37794d61-942f-4573-911e-0d812e8c69ea" />


output waveform:

<img width="1918" height="843" alt="image" src="https://github.com/user-attachments/assets/3eaf8306-7d32-49c7-9ed9-3cebde7d9a70" />


 

     

   
 
