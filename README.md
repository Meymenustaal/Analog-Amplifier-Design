# 📐 Analog Circuit Design: 4-Stage Cascaded BJT Amplifier

## 📌 Project Overview
This project involves the design and LTSpice simulation of a highly stable 4-stage cascaded BJT voltage amplifier. The primary objective is to optimize inter-stage impedance matching using common-emitter and emitter-follower topologies to achieve a targeted voltage gain of 200x. The analysis incorporates real-world semiconductor non-idealities, loading effects, and the Early Effect.

## ⚙️ Circuit Architecture and Functions
The system operates on a 12V DC supply to prevent signal clipping and consists of four functional stages:
* **Stage 1 (Q1 - 2N3904):** Common Emitter. Provides the primary voltage gain ($A_{v1} \approx -17.67$). An emitter resistor ($R_8 = 214\,\Omega$) introduces negative feedback for thermal stability.
* **Stage 2 (Q2 - 2N3904):** Emitter Follower (Buffer). Provides no voltage gain ($A_{v2} \approx 0.99$) but ensures perfect impedance matching between stages 1 and 3 due to its high input and low output impedance.
* **Stage 3 (Q3 - 2N3904):** Common Emitter. Acts as the secondary voltage gain stage ($A_{v3} \approx -12.44$).
* **Stage 4 (Q4 - 2N3904):** Emitter Follower. Functions as the output driver (buffer) to maximize power transfer to the load.
* **Output Protection (D1):** A parallel diode acting as a clipper to prevent the signal from dropping below critical negative levels. 

## 🧠 Theoretical vs. Simulation Analysis (Early Effect)
A critical evaluation was conducted between ideal paper calculations and the LTSpice semiconductor model:
* **Theoretical Gain:** Calculated as **236.9** using cascade modeling.
* **Simulated Gain:** Measured as **200.5** during transient (.tran) analysis (1mV, 1kHz input).

**Deviation Analysis:** The ~15% discrepancy is attributed to the **Early Effect**. While theoretical models assume infinite transistor output impedance ($r_o$), the LTSpice 2N3904 model accounts for finite output resistance. This internal resistance runs parallel to the 4.7kΩ collector loads, reducing the effective equivalent resistance and accurately lowering the overall gain.

## 📋 Semiconductor Baseline
Design parameters are strictly based on the ON Semiconductor 2N3904 datasheet:
* $V_{CE}$ (Max): 40V
* $I_C$ (Max): 200mA
* DC Current Gain ($\beta$): Assumed 300 for worst-case modeling.
* $V_{BE}$: 0.7V constant voltage model for DC analysis.

## 📷 Media

**LTSpice Circuit Schematic**
<img width="883" height="359" alt="image" src="https://github.com/user-attachments/assets/20f94c65-bbc4-44af-a340-282c6cdf1c2f" />


**Transient Analysis: Input vs. Output Voltage Waveform (Gain ≈ 200x)**
<img width="1109" height="499" alt="image" src="https://github.com/user-attachments/assets/1886ed22-46f1-4c65-b993-3b538c28b273" />

