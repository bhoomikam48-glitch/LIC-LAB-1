# Experiment 6 - Adder Circuit Analysis 




<img width="1024" height="768" alt="image" src="https://github.com/user-attachments/assets/7fa7a3b1-a24a-4464-96e3-8ac26f0d43f0" />





To design the circuit for part (b), we need to implement the transfer function:$$y_2(t) = 2x_2(t) + 6x_3(t)$$

Since both coefficients are positive, a Non-Inverting Summing Amplifier is the ideal choice.





1. Principle & Theory
  
  
* The non-inverting summer works in two stages:

  
   Voltage Division (Input Stage): The input voltages $x_2$ and $x_3$ are combined at the non-inverting terminal ($+$) through a resistive network.

   This creates a voltage $V_p$ based on the principle of superposition

  * Non-Inverting Gain (Amplification Stage): The Op-Amp then amplifies $V_p$ by a gain factor determined by the feedback resistors $R_f$ and $R_g$
 




### General Formula:

The output voltage for a two-input non-inverting summer is:

$$V_{out} = \left( 1 + \frac{R_f}{R_g} \right) \left[ \frac{x_2 \cdot R_6 + x_3 \cdot R_5}{R_5 + R_6} \right]$$



* Resistor Design & Analysis

 To get $y_2(t) = 2x_2(t) + 6x_3(t)$, we need to solve for the resistor values. Let's set a standard value for $R_g$ as 10 kΩ.


 Step A: 
 
 Ratio of InputsThe ratio of the coefficients is $6 / 2 = 3$.
 
 In the weighted average at the non-inverting terminal, the influence of the voltage is inversely proportional to its series resistance.
 
 Let $R_5 = 30\text{ kΩ}$ (connected to $x_2$)Let $R_6 = 10\text{ kΩ}$ (connected to $x_3$)


 the voltage at the non-inverting pin ($V_p$) becomes:$$V_p = \frac{x_2(10\text{k}) + x_3(30\text{k})}{30\text{k} + 10\text{k}} = 0.25x_2 + 0.75x_3$$



 Step B: Required Gain
 
 
 Now we compare our current expression to the target:
 
 Target: $2x_2 + 6x_3$
 
 Current: $0.25x_2 + 0.75x_3$


 To turn $0.25$ into $2$ (or $0.75$ into $6$), we need a gain ($A_v$) of 8.
 
 $$A_v = 1 + \frac{R_f}{R_g} = 8$$$$\frac{R_f}{10\text{k}} = 7 \implies R_f = 70\text{ kΩ}$$





 Verification
 
 Plugging the values back into the equation:
 
 $$V_{out} = \left( 1 + \frac{70\text{k}}{10\text{k}} \right) \left[ \frac{x_2(10\text{k}) + x_3(30\text{k})}{10\text{k} + 30\text{k}} \right]$$$$V_{out} = (8) \left[ \frac{10\text{k}}{40\text{k}}x_2 + \frac{30\text{k}}{40\text{k}}x_3 \right]$$$$V_{out} = 8(0.25x_2 + 0.75x_3) = \mathbf{2x_2 + 6x_3}$$


signal source for $x_2(t)$ is set to the sine wave $-0.5 \sin(2000\pi t)$ and $x_3(t)$ is a constant $+1$V DC source  



$$y_2(t) = 2x_2(t) + 6x_3(t)$$


$$y_2(t) = 2 \left[ -0.5 \sin(2000\pi t) \right] + 6 \left[ 1 \right]$$



$$y_2(t) = 6 - \sin(2000\pi t) \text{ Volts}$$





<img width="1535" height="780" alt="image" src="https://github.com/user-attachments/assets/397d4527-1c67-43f7-b451-6fffe7411703" />



<img width="1872" height="917" alt="image" src="https://github.com/user-attachments/assets/f5750915-263a-4751-8b09-378ff90ef01d" />




The resulting signal $y_2(t)$ consists of two parts:

DC Offset (6V): The output is shifted upwards by 6V due to the constant $+1$V input at $x_3$ being amplified by a factor of 6.

AC Component (Sine Wave): A sine wave with a peak amplitude of 1V and a frequency of 1000 Hz ($2000\pi = 2\pi f \implies f = 1000$).

Note that the negative sign indicates a $180^\circ$ phase shift relative to a standard sine wave.



In a simulation,  a sine wave oscillating between a maximum of 7V ($6 + 1$) and a minimum of 5V ($6 - 1$).


*** “The simulated output waveform matches the theoretical output of  confirming correct resistor design.” ***




# Applications:


* Instrumentation and Signal Conditioning

* Mathematical Computation (Analog Computers)

* Level Shifting and DC Offsetting

* Digital-to-Analog Converters (DAC)

* Audio Mixing Consoles
