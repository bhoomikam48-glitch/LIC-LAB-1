# Experiment 7 - Integrator circuit 




<img width="960" height="1280" alt="WhatsApp Image 2026-04-25 at 17 17 00" src="https://github.com/user-attachments/assets/3cbfe67d-eb76-4d1d-a263-938a25772c76" />







# Part b) - Integrator circuit 



### 1. Principle


* The circuit operates as an Inverting Integrator.
  
* It uses a capacitor ($C_1$) in the feedback loop to store charge over time.
  
*  According to the virtual ground concept at the inverting terminal, the current through the input resistor ($I_{in} = V_{in} / R_1$) must pass through the capacitor.
  
*   This creates an output voltage proportional to the integral of the input signal.




### 2. Theory: The "Practical" Addition

* In an ideal integrator, the DC gain is infinite, which causes the output to "drift" and saturate at the supply rails due to small input offset voltages.

* The Role of $R_2$: By adding a feedback resistor ($R_2$) in parallel with $C_1$, we limit the DC gain to $A_{max} = -R_2/R_1$.

* Frequency Response: This creates a cutoff frequency ($f_a$).
 Above this frequency, the circuit acts as an integrator; below it, it acts as a simple inverting amplifier.


### 3. Resistor Design Calculations
  
* Given constraints: $f_a = 250$ Hz, $C_1 = 0.1\text{ μF}$, and $f_{in} = 1000$ Hz

* A. Input Resistor ($R_1$)

* Calculated using the break frequency where integration begins:

 $$R_1 = \frac{1}{2\pi f_a C_1} = \frac{1}{2\pi (250)(0.1 \times 10^{-6})} \approx \mathbf{6.4\text{ kΩ}}$$


* B. Feedback Resistor ($R_2$)

 To ensure the circuit remains stable and "practical," $R_2$ is typically chosen as $10 \times R_1$:


 $$R_2 = 10 \times 6.4\text{ kΩ} = \mathbf{64\text{ kΩ}} \text{ (Standard value: } \mathbf{68\text{ kΩ}}\text{)}$$



* C. Compensation Resistor ($R_3$)To minimize DC offset errors at the output:

 $$R_3 = R_1 \parallel R_2 \approx \mathbf{5.8\text{ kΩ}}$$








### 4. Mathematical Analysis at 1 kHz

   
  The transfer function for a practical integrator is:
  
  $$V_{out} \approx -\frac{1}{R_1 C_1} \int V_{in} \, dt$$
  
  For a sine wave input $V_{in} = V_p \sin(2\pi f t)$, the output amplitude is scaled by the factor:
  
  $$|A_v| = \frac{1}{2\pi f R_1 C_1}$$Substituting your values ($R_1 = 6.4\text{ kΩ}$, $C_1 = 0.1\text{ μF}$, $f = 1000\text{ Hz}$):
  
  $$|A_v| = \frac{1}{2\pi \cdot 1000 \cdot 6.4\text{k} \cdot 0.1\text{u}} \approx 0.25$$
  
  If your input peak $V_p = 1$V, the output peak will be approximately 0.25V.




| Component | Value | Purpose |
| :--- | :--- | :--- |
| **R1 (Input)** | 6.4 kΩ | Determines integration rate |
| **R2 (Feedback)**| 68 kΩ | Prevents DC saturation (Practical Integrator) |
| **C1** | 0.1 μF | Integrating capacitor |
| **R3 (Comp)** | 5.8 kΩ | Bias current compensation |









  <img width="1342" height="807" alt="image" src="https://github.com/user-attachments/assets/458ce195-312a-4b7f-aa2a-87d06728c308" />







  <img width="1902" height="892" alt="image" src="https://github.com/user-attachments/assets/e738ac75-2a11-4316-98c4-b6d87612ca08" />









 * Gain Magnitude ($|A_v|$):
  
  At 1 kHz, the reactance of the capacitor ($X_C \approx 1.59\text{ kΩ}$) is much smaller than $R_2$, so:
  
  $$|A_v| = \frac{1}{2\pi f R_1 C_1} = \frac{1}{2\pi (1000)(6.4\text{k})(0.1\text{u})} \approx \mathbf{0.25}$$

 This explains why your output wave is roughly 1/4th the height of your 1V input.




* Phase Analysis:
The output lags the input by $90^\circ$ (plus the $180^\circ$ inversion).

This transforms a Sine wave into a -Cosine wave, which is exactly what your simulation shows: the output peak aligns with the input zero-crossing.






| Parameter / Component | Value / Formula | Technical Function |
| :--- | :--- | :--- |
| **Circuit Type** | Practical Integrator | Mathematical integration with DC stability |
| **Input Frequency ($f_{in}$)** | $1000$ Hz | Operational frequency in the integration zone |
| **Lower Cutoff ($f_a$)** | $250$ Hz | Frequency where integration behavior begins |
| **Input Resistor ($R_1$)** | $6.4$ kΩ | Sets time constant; $R_1 = 1 / (2\pi f_a C_1)$ |
| **Feedback Resistor ($R_2$)** | $68$ kΩ | Limits DC gain to prevent Op-Amp saturation |
| **Feedback Capacitor ($C_1$)** | $0.1$ μF | Stores charge to perform the integral operation |
| **Comp. Resistor ($R_3$)** | $5.8$ kΩ | Minimizes DC offset ($R_1 \parallel R_2$) |
| **Gain at $1$ kHz ($A_v$)** | $\approx 0.25$ | Attenuation factor $|1 / (2\pi f R_1 C_1)|$ |
| **Phase Shift** | $90^\circ$ Lag | Shifts Sine input to Negative Cosine output |
| **Supply Voltage** | $\pm 13$V | Standard rails for uA741 stability |









Case 1: 

Square Wave InputTheory:

The integral of a constant is a linear ramp ($y = mx$).

Analysis: When the square wave is at $+1$V, the output decreases at a constant rate.

When at $-1$V, it increases at a constant rate.Result: The output becomes a Triangular Wave.




<img width="1910" height="910" alt="image" src="https://github.com/user-attachments/assets/8a69992d-9b7f-463c-b80d-42fb51b99b37" />





Case 2: 

Triangular Wave InputTheory: 

The integral of a linear ramp is a quadratic function ($y = x^2$).

Analysis: As the input voltage increases linearly, the rate of change of the output increases, creating a curved slope.

Result: The output becomes a Parabolic Wave



<img width="1916" height="911" alt="image" src="https://github.com/user-attachments/assets/9ec87f60-517f-4f3e-a92e-53543a46c8cb" />









| Input Waveform | Mathematical Operation | Expected Output Shape | Peak-to-Peak Analysis |
| :--- | :--- | :--- | :--- |
| **Sine Wave** | $\int \sin(\omega t) dt$ | Negative Cosine | $\approx 0.5$ Vp-p |
| **Square Wave** | $\int \text{constant } dt$ | Triangular Wave | $\approx 0.78$ Vp-p |
| **Triangular Wave** | $\int \text{linear } dt$ | Parabolic Wave | Smoothed curvature |







### Real-World Applications
1. **Function Generators:** Converting square waves to triangular/sawtooth waves.
2. **Dual-Slope ADCs:** High-precision measurement in digital multimeters.
3. **Control Systems:** Integral component in PID controllers for industrial automation.
4. **Analog Filters:** Removing high-frequency noise from sensor data.
