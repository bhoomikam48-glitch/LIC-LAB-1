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








# PART B) - Voltage Follower (Unity Gain Buffer)


1. Theory and Working Principle
  
* A Voltage Follower is an Op-Amp circuit where the output voltage is exactly equal to the input voltage ($V_{out} = V_{in}$). It is characterized by:

* Unity Gain: $A_v = 1$.

* High Input Impedance: It draws almost no current from the source, preventing "loading effects."

* Low Output Impedance: It can drive low-resistance loads (like your $360\Omega$ resistor) without the voltage dropping.


Working: 

The output is fed back directly to the inverting (-) terminal with $100\%$ feedback. 

Due to the virtual short between the terminals, $V_-$ must equal $V_+$. Since $V_-$ is connected directly to $V_{out}$ and $V_+$ is connected to $V_{in}$, then $V_{out} = V_{in}$.




### 2. Design Specifications:


* op-Amp: $\mu A741$
  
* Supply Voltages ($V_{CC} / V_{EE}$): $\pm 12V$

* Input Signal ($V_{in}$): Sine wave, $4.5V$ peak, $500Hz$ frequency.

* Load Resistor ($R_L$): $360\Omega$

* Feedback: Direct wire (Short circuit), which means $R_f = 0$ and $R_1 = \infty$.3.




3. Design Analysis
  
* The general formula for a non-inverting gain is $A_v = 1 + (R_f / R_1)$.

* In a voltage follower:


$$R_f = 0$ (short circuit)$R_1 = \infty$ (open circuit)Therefore, $A_v = 1 + (0 / \infty) = 1$$



# Transient analysis:


<img width="1918" height="912" alt="image" src="https://github.com/user-attachments/assets/aa0aefa4-83eb-466a-b592-0c1dda0cc56e" />



* Unity Gain Verification: Since $V_{peak(in)} = 4.5\text{V}$ and $V_{peak(out)} = 4.5\text{V}$, the voltage gain $A_v = \frac{V_{out}}{V_{in}} = 1$.


* Linear Operation: Because the required output ($4.5\text{V}$) is significantly lower than the supply rails ($\pm 12\text{V}$), the Op-Amp operates entirely

  within its linear region. This is why the output is a smooth, unclipped sine wave.


The transient simulation confirms the Unity Gain property of the buffer circuit.

- **Input Amplitude:** 4.5V Peak
- **Output Amplitude:** 4.5V Peak
- **Calculated Gain ($A_v$):** 1 (Unity)
- **Phase Shift:** 0°

**Observation:** The output waveform perfectly tracks the input waveform without any clipping or distortion. This occurs because the 4.5V output swing is well below the +/- 12V saturation limits of the uA741. This simulation demonstrates the circuit's ability to "follow" the input voltage while providing high input impedance and low output impedance.





### AC Analysis (Frequency Response)
The Frequency Response of the Voltage Follower demonstrates the maximum bandwidth achievable with the uA741 Op-Amp.


<img width="1917" height="882" alt="image" src="https://github.com/user-attachments/assets/fef5c1e0-8ef8-4424-aefc-f492ff220969" />


* Mid-band Gain

$0\text{ dB}$ corresponds to a linear gain of $1$ ($20 \log_{10}(1) = 0$). This confirms the unity gain property of the voltage follower.

* Bandwidth (Cut-off Frequency) :

The bandwidth is the frequency where the gain drops to $-3\text{ dB}$.

The gain crosses the $-3\text{ dB}$ threshold at $1\text{ MHz}$.


* Gain-Bandwidth Product (GBWP)

$$GBWP = Gain \times Bandwidth$$$$GBWP = 1 \times 1,000,000\text{ Hz} = 1\text{ MHz}$$


| Parameter | Value |
| :--- | :--- |
| **Mid-band Gain** | 0 dB (Linear Gain = 1) |
| **-3dB Bandwidth** |  1 MHz |
| **Gain-Bandwidth Product** | 1 MHz |
| **Phase at 180kHz** | -11.98° |

**Technical Inference:**
By setting the gain to unity, the circuit achieves the maximum possible bandwidth of the Op-Amp (equal to its GBWP). This makes the voltage follower an excellent choice for buffering high-frequency signals compared to high-gain amplifier stages.


### conclusion:

* Voltage Gain ($A_v$): Exactly 1 ($0\text{ dB}$). 

* The output waveform is a literal "mirror" of the input.

* Phase Shift: 0°. The input and output signals are perfectly synchronized in time.

* Bandwidth: Maximum possible for the device, reaching the $1\text{ MHz}$ limit of the $\mu A741$.

* Output Swing: Operating at $4.5\text{V}$ peak, the circuit remains entirely in the linear region, avoiding the clipping seen in high-gain configurations.



# Application


"The Voltage Follower acts as an electrical 'buffer.'

It provides no voltage magnification but provides significant current gain, ensuring that the input signal is delivered to the load without distortion or attenuation."
