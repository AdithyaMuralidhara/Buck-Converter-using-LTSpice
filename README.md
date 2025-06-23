# Buck Converter Simulation in LTSpice (Automotive 12V to 5V)

This repository demonstrates the simulation of a **Buck Converter** (DC-DC step-down converter) using **LTSpice**, specifically designed for **automotive applications** to convert 12V to 5V efficiently. It includes circuit design, parameter calculations, and LTSpice simulation setup.

---

## Theoretical Background

The **Buck Converter** operates by switching a transistor ON and OFF at high frequencies, storing energy in an inductor, and smoothing the output with a capacitor.

Values Considered:

- **V<sub>in</sub> = 12V**  -> Input Voltage to converter

- **V<sub>out</sub> = 5V**  -> Desired output required across load

- **f = 25 kHz** -> Switching frequency

- **R = 5Ω** -> Load Resistor

## Formulas used

- D = V<sub>in</sub> / V<sub>out</sub>

- I<sub>load</sub> = V<sub>out</sub> / R

- ΔI ≈ 20% − 40% of I<sub>load</sub>

- ΔV ≤ 1% - 2% of V<sub>out</sub>

- L = ((V<sub>in</sub> - V<sub>out</sub>) × D) / (f × ΔI)

- C = ΔI / (8 × f × ΔV)

## Calculations: 

D = 5 / 12 = 0.416 = **41.6%**

I<sub>load</sub> = 5 / 5 = **1A**

ΔI = 0.3 × 1 = **0.3A**

L = ((12 - 5) × 0.416 ) / (25 × 10<sup>3</sup> × 0.3) = **388.7 μH** 

ΔV = 0.01 × 5 = **0.05V**

C = 0.3 / (8 × 25 × 10<sup>3</sup> × 0.05) = **30 μF**


---

## Final Design Values

| Parameter         | Value          |
|------------------|----------------|
| Input Voltage     | 12 V           |
| Output Voltage    | 5 V            |
| Duty Cycle (k)    | 0.416          |
| Switching Frequency | 25 kHz       |
| Inductor          | 388.7 µH       |
| Capacitor  | 30 µF         |
| Load Resistance   | 5 Ω            |
| Peak-to-Peak Inductor Ripple | 0.3 A |
| Output Ripple Voltage | 50 mV     |


## Components Used

| Component         | Part/Value     | Purpose                                 |
|------------------|----------------|-----------------------------------------|
| Voltage Source    | 12V DC         | Input power supply                      |
| MOSFET            | IRF740L        | High-speed switching element            |
| Diode             | 1N5819         | Schottky diode for freewheeling         |
| Inductor          | 388.7 µH         | Energy storage component                |
| Capacitor         | 30 µF          | Output voltage ripple filtering         |
| Load              | 5 Ω            | Represents typical automotive load      |
| PWM Control       | PULSE Source   | Generates gate pulses for the MOSFET    |


## LTSpice Setup

Simulation Parameters:

```spice
.param D=0.416
.param Ts=40u
.tran 5ms
```
---

## Circuit and Ouput Waveform

![Screenshot 2025-06-18 131752](https://github.com/user-attachments/assets/c12a2e34-401b-4cd4-8930-fc8dcbe5c758)
