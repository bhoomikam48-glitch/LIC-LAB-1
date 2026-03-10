# Common Source Amplifier Configurations

# a) Source Degenerated Common Source Amplifier.

# AIM: 
 Design of PMOS active load configuration in tsmc018lib using LTspice.

# Circuit:
<img width="1280" height="708" alt="image" src="https://github.com/user-attachments/assets/cb65f43c-62d7-44e1-a1e0-03ac5f73d0c0" />


Given data: VDD=2V  P<=1.5mW  Vov=0.25V  Vth=0.36V  CL=1pF  Ln=Lp=180nm .

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

   * NMOS Transistor:** 

   * power verification:

     Let ID = 200 µA

     P = VDD*ID

     Power = 2*200 µA = 0.4mW which is <= 1.5mW.
    Thus power is verified.

     Given,
     VRS = 0.2V VOV = 0.25V
     We know that,
     VRS = IDRS , 0.2/200µ = RS , RS = 1kΩ.

     Also,

     Vout = VDD/2 + 0.2
     Vout =1+0.2 = 1.2V.

     * To find Vgs :
       VOV = 0.25V Vth=0.36V 
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


    The Drain -current equation is given by,
   
   
       
     
     

     

   
 
