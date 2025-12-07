# Discrete Logic RGB LED Controller (PWM)

![3D PCB Render](Hardware/3D%20Render/3D_PCB.png)

## Project Overview
This project is a **Voltage Controlled Current Source (VCCS)** implementation that controls the brightness of an RGB LED using **Pulse Width Modulation (PWM)**. 

Unlike standard microcontroller-based solutions (Arduino/ESP32), this project was built entirely using **discrete logic gates (74xx series)** to demonstrate a fundamental understanding of digital timing, state machines, and signal propagation.

## Key Features
* **Clock Generation:** RC Oscillator using Schmitt Trigger (74HC14).
* **PWM Generation:** Logic-based duty cycle creation (25%, 50%, 75%) using D-Flip Flops (74HC74) and AND gates (74HC08).
* **Signal Multiplexing:** 4-to-1 Multiplexer (74LS153) to select brightness levels.
* **Power Stage:** MOSFET (2N7000) driver acting as a switch for the LED load.
* **Debouncing:** Hardware switch debouncing using RC networks and Schmitt Triggers.

## Technical Specifications
| Component | Function |
| :--- | :--- |
| **74HC14** | Hex Inverting Schmitt Trigger (Oscillator & Debounce) |
| **74HC74** | Dual D-Flip Flop (Frequency Division) |
| **74HC08** | Quad 2-Input AND Gate (Logic Mixing) |
| **74LS153**| Dual 4-input Multiplexer (Signal Selection) |
| **2N7000** | N-Channel MOSFET (Output Driver) |

## How It Works
1.  **Clock Source:** The **74HC14** creates a square wave clock signal.
2.  **Frequency Division:** The **74HC74** divides the clock frequency to create timing references.
3.  **Duty Cycle Logic:** By combining the divided clocks using logic gates, specific duty cycles (25%, 75%) are synthesized.
4.  **Selection:** The **Multiplexer** selects the desired waveform based on user switch inputs.
5.  **Output:** The **MOSFET** drives the LED with the selected PWM signal, effectively controlling average current and brightness.

## Simulation Results
The circuit was simulated to verify timing and duty cycles.
*(See `/Simulation` folder for full waveform graphs)*

## Tools Used
* **Schematic Capture:** Altium
* **Simulation:** Falstad CircuitJS
* **PCB Design:** EasyEDA

## Future Improvements
* Implement **45-degree trace routing** on the PCB to minimize acid traps.
* Add a **Ground Plane** for better noise immunity.

---

*Project by Harshil Byggari*

