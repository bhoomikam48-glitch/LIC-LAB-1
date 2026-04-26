# Experiment 5 -  Opamp circuit Design and Analysis 



<img width="962" height="417" alt="image" src="https://github.com/user-attachments/assets/f0c759d3-c1ee-4879-b091-360a50eac5b9" />


## a) Non inverting amplifier   b)  Voltage Follower




### Part a) - Non inverting amplifier  



# 1. Theory and Working Principle:


* A Non-Inverting Amplifier is an operational amplifier circuit configuration where the input signal is applied to the non-inverting (+) terminal. This results in an output signal that is in phase with the input.


* The circuit uses negative feedback by feeding a portion of the output voltage back to the inverting (-) terminal through a voltage divider network ($R_f$ and $R_1$).


* Because of the "virtual short" concept in ideal Op-Amps, the voltage at the inverting terminal ($V_-$) tracks the voltage at the non-inverting terminal ($V_+$), ensuring $V_- = V_{in}$.



<img width="1506" height="847" alt="image" src="https://github.com/user-attachments/assets/af4089f0-758f-460b-ac88-76c11463fefb" />



## 2. Design Specifications


* Op-Amp: $\mu A741$
  
* Supply Voltages ($V_{CC} / V_{EE}$): $\pm 12V$
 
* Input Signal ($V_{in}$): Sine wave, $4.5V$ peak, $500Hz$ frequency
  
* Feedback Resistor ($R_f$): $5k\Omega$
  
* Input Resistor ($R_1$): $1k\Omega$




## Design Calculations
The gain is determined by the formula:
Gain (Av) = 1 + (Rf / R1)

Given Av = 6v/v
- Rf = 5k Ohm
- R1 = 1k Ohm
- Vin = 4.5V (Peak)

Calculation:
- Av = 1 + (5000 / 1000) = 6
- Theoretical Vout = 6 * 4.5V = 27V




<img width="1918" height="877" alt="image" src="https://github.com/user-attachments/assets/ae78ff83-20b8-4fa9-8bc8-22d4909d0037" />





### Simulation Results (Transient Analysis)
The transient simulation shows the circuit operating at a gain of 6. 
- **Input:** 4.5V Peak Sine Wave.
- **Output:** Saturates at ~11.8V.



### The output is clipped because the required swing (27V) exceeds the power supply rails (+/- 12V). 

This demonstrates the 'Saturation Region' of the uA741 Op-Amp. To observe a full sine wave output, the input should be kept below 2V.






# Ac analysis :


<img width="1918" height="892" alt="image" src="https://github.com/user-attachments/assets/b6ef530c-ae57-4fa0-b2a1-9de94e02b510" />






The AC simulation was performed from 1Hz to 100GHz to determine the frequency limitations of the circuit.

| Parameter | Value |
| :--- | :--- |
| **Mid-band Gain** | 15.56 dB (Linear Gain $\approx$ 6) |
| **Bandwidth (-3dB frequency)** | $\approx$ 166 kHz |
| **Gain-Bandwidth Product (GBWP)** | 1 MHz |
| **Phase at Mid-band** | 0° (In-phase) |


* A linear gain ($A_v$) of $6$.$$

Gain\text{ (dB)} = 20 \log_{10}(6) \approx 15.56\text{ dB}$$  This perfectly matches your simulation result.


* The Bandwidth (BW) is defined as the frequency range where the gain remains within $3\text{ dB}$ of its maximum value (the $-3\text{ dB}$ point).
  
   $15.56 - 3 = 12.56\text{ dB}$

    Bandwidth is approximately 165kHz



* Gain-Bandwidth Product (GBWP)
  
The GBWP is a constant for an Op-Amp that describes the trade-off between gain and speed.

$$GBWP = 6 \times 166,667 \approx 1,000,000\text{ Hz} = 1\text{ MHz}$$
  


**Observations:**
- The gain remains constant until approximately 100 kHz.
- The high-frequency roll-off is characteristic of the uA741 internal compensation capacitor.
- The Gain-Bandwidth Product remains consistent with the manufacturer's datasheet (1 MHz).




### Conclusion:


The circuit was designed with a closed-loop gain of 6 ($15.56\text{ dB}$), established by a $5k\Omega$ feedback resistor and a $1k\Omega$ input resistor.


* Transient Behavior: The simulation highlighted the "Clipping" phenomenon. While the mathematical output should have been $27\text{V}$, the physical limits of the $\mu A741$ (powered at $\pm 12\text{V}$) restricted the output to approximately $11.8\text{V}$.


* Frequency Response: The AC analysis confirmed a $1\text{ MHz}$ Gain-Bandwidth Product (GBWP). The circuit maintains stable gain up to roughly $166\text{ kHz}$, after which the internal compensation of the Op-Amp causes the gain to roll off.


* Phase Integrity: As a non-inverting configuration, the input and output remain perfectly in phase ($0^\circ$ shift) within the operating bandwidth.




## Applications


* Sensor Pre-amplification: Scaling up small millivolt signals from sensors to a range readable by ADCs.

* Audio Buffering: Providing high input impedance to prevent loading of the previous circuit stage while increasing signal strength.

* Signal Conditioning: Used in instrumentation where the signal must maintain its original polarity.





