# Experiment 6 - Adder Circuit Analysis 




<img width="1024" height="768" alt="image" src="https://github.com/user-attachments/assets/7fa7a3b1-a24a-4464-96e3-8ac26f0d43f0" />










# Part b) - $$y_2(t) = 2x_2(t) + 6x_3(t)$$


To design the circuit for part (b), we need to implement the transfer function:$$y_2(t) = 2x_2(t) + 6x_3(t)$$


Since both coefficients are positive, a Non-Inverting Summing Amplifier is the ideal choice.





# 1. Principle & Theory
  
  
* The non-inverting summer works in two stages:

  
   Voltage Division (Input Stage): The input voltages $x_2$ and $x_3$ are combined at the non-inverting terminal ($+$) through a resistive network.

   This creates a voltage $V_p$ based on the principle of superposition

  * Non-Inverting Gain (Amplification Stage): The Op-Amp then amplifies $V_p$ by a gain factor determined by the feedback resistors $R_f$ and $R_g$
 




### General Formula:

The output voltage for a two-input non-inverting summer is:

$$V_{out} = \left( 1 + \frac{R_f}{R_g} \right) \left[ \frac{x_2 \cdot R_6 + x_3 \cdot R_5}{R_5 + R_6} \right]$$



* Resistor Design & Analysis

 To get $y_2(t) = 2x_2(t) + 6x_3(t)$, we need to solve for the resistor values. Let's set a standard value for $R_g$ as 10 kΩ.


* Step A: 
 
 Ratio of InputsThe ratio of the coefficients is $6 / 2 = 3$.
 
 In the weighted average at the non-inverting terminal, the influence of the voltage is inversely proportional to its series resistance.
 
 Let $R_5 = 30\text{ kΩ}$ (connected to $x_2$)Let $R_6 = 10\text{ kΩ}$ (connected to $x_3$)


 the voltage at the non-inverting pin ($V_p$) becomes:$$V_p = \frac{x_2(10\text{k}) + x_3(30\text{k})}{30\text{k} + 10\text{k}} = 0.25x_2 + 0.75x_3$$



* Step B: Required Gain
 
 
 Now we compare our current expression to the target:
 
 Target: $2x_2 + 6x_3$
 
 Current: $0.25x_2 + 0.75x_3$


 To turn $0.25$ into $2$ (or $0.75$ into $6$), we need a gain ($A_v$) of 8.
 
 $$A_v = 1 + \frac{R_f}{R_g} = 8$$$$\frac{R_f}{10\text{k}} = 7 \implies R_f = 70\text{ kΩ}$$





* Verification
 
 Plugging the values back into the equation:
 
 $$V_{out} = \left( 1 + \frac{70\text{k}}{10\text{k}} \right) \left[ \frac{x_2(10\text{k}) + x_3(30\text{k})}{10\text{k} + 30\text{k}} \right]$$$$V_{out} = (8) \left[ \frac{10\text{k}}{40\text{k}}x_2 + \frac{30\text{k}}{40\text{k}}x_3 \right]$$$$V_{out} = 8(0.25x_2 + 0.75x_3) = \mathbf{2x_2 + 6x_3}$$


signal source for $x_2(t)$ is set to the sine wave $-0.5 \sin(2000\pi t)$ and $x_3(t)$ is a constant $+1$V DC source  



$$y_2(t) = 2x_2(t) + 6x_3(t)$$


$$y_2(t) = 2 \left[ -0.5 \sin(2000\pi t) \right] + 6 \left[ 1 \right]$$



* $$y_2(t) = 6 - \sin(2000\pi t) \text{ Volts}$$





<img width="1535" height="780" alt="image" src="https://github.com/user-attachments/assets/397d4527-1c67-43f7-b451-6fffe7411703" />



<img width="1872" height="917" alt="image" src="https://github.com/user-attachments/assets/f5750915-263a-4751-8b09-378ff90ef01d" />




### The resulting signal $y_2(t)$ consists of two parts:

* DC Offset (6V): The output is shifted upwards by 6V due to the constant $+1$V input at $x_3$ being amplified by a factor of 6.

* AC Component (Sine Wave): A sine wave with a peak amplitude of 1V and a frequency of 1000 Hz ($2000\pi = 2\pi f \implies f = 1000$).

Note that the negative sign indicates a $180^\circ$ phase shift relative to a standard sine wave.



* In a simulation,  a sine wave oscillating between a maximum of 7V ($6 + 1$) and a minimum of 5V ($6 - 1$).


*** “The simulated output waveform matches the theoretical output of  confirming correct resistor design.” ***




# Applications:


* Instrumentation and Signal Conditioning

* Mathematical Computation (Analog Computers)

* Level Shifting and DC Offsetting

* Digital-to-Analog Converters (DAC)

* Audio Mixing Consoles










# Part d) - Averaging Circuit.


For part (d), the goal is to implement the averaging function:$$y_4(t) = \frac{x_1(t) + x_2(t) + x_3(t)}{3}$$This is a specific case of the non-inverting summing amplifier known as an Averaging Circuit.



# 1. Principle & Theory


The non-inverting averaging circuit works by exploiting the parallel combination of resistors at the non-inverting terminal. 

When multiple voltage sources are connected to the same node through equal resistors, the voltage at that node is the arithmetic mean (average) of the input voltages.


* The Voltage Divider Rule at the Non-Inverting Terminal ($V_p$):If $R_1 = R_2 = R_3 = R$, then by superposition:$$V_p = \frac{x_1 + x_2 + x_3}{3}$$


* The Gain Stage:
Since the target output $y_4(t)$ is exactly equal to this average, we need a circuit gain ($A_v$) of 1. This means the op-amp must act as a Voltage Follower (Buffer) for the averaged signal.





# 2. Resistor Design & Analysis
  
* Step A:

  Input Resistors ($R_1, R_2, R_3$)To ensure the node voltage is a true average, all input resistors must be identical.

  Design Choice: Let $R_1 = R_2 = R_3 = 30\text{ kΩ}$




* Step B:

Feedback Network ($R_f$ and $R_4$)

To achieve a gain of $A_v = 1$:

$$A_v = 1 + \frac{R_f}{R_4}$$For $A_v = 1$, the ratio $\frac{R_f}{R_4}$ must be 0.


$R_4 = 10\text{ kΩ}$ to ground. For this to work, the feedback resistor $R_f$ should be a short circuit (0 Ω).





Final Resistor Values (Non-Inverting Design)

Component	Value
R1	30kΩ
R2	30kΩ
R3	30kΩ
Rf	0Ω
Rg	10kΩ




# 3. Substitution & Waveform Analysis
  
  
 Using the given values:
 
* $x_1(t) = -1\text{V}$
 
  * $x_2(t) = -0.5 \sin(2000\pi t)$
 
 * $x_3(t) = +1\text{V}$





Substitute into the expression:

$$y_4(t) = \frac{-1 + (-0.5 \sin(2000\pi t)) + 1}{3}$$


$$y_4(t) = \frac{-0.5 \sin(2000\pi t)}{3}$$


$$y_4(t) \approx -0.166 \sin(2000\pi t) \text{ Volts}$$






<img width="1297" height="837" alt="image" src="https://github.com/user-attachments/assets/cb1509b8-5c2f-4828-b65a-bdaaa58b22c2" />






<img width="1891" height="917" alt="image" src="https://github.com/user-attachments/assets/1fe4e88a-67e1-45e9-9776-bafdbea333fd" />






<img width="1917" height="920" alt="image" src="https://github.com/user-attachments/assets/6ccf04be-3b5f-4998-b4db-b33423f554b7" />






# Simulation Observation:


The DC components ($-1\text{V}$ and $+1\text{V}$) cancel each other out.


The output will be a pure sine wave centered at 0V.The peak amplitude will be approximately 166 mV.


*** “The simulated output waveform matches the theoretical output of  confirming correct resistor design.” ***





# Applications:


Sensor Averaging: Combining readings from three identical sensors to reduce noise or errors from a single faulty sensor.

Signal Processing: Finding the "Common Mode" signal of three different lines.
