
# Solar Li-ion Battery Charger PCB

A fully designed PCB for solar-powered Li-ion battery charging with 
hardware protection — designed from scratch in KiCad.

---

## What this does

Takes input from a solar panel and safely charges a Li-ion battery 
with full hardware protection against overcharge, over-discharge, 
and short circuits. All protection logic is handled in hardware — 
no microcontroller involved.

---

## Why hardware protection matters

Li-ion batteries are dangerous if charged incorrectly — overcharging 
above 4.2V or discharging below 2.5V can cause permanent damage or 
fire. This design handles both in hardware, meaning protection is 
always active regardless of software state.

---

## How it works
1. **TP4056** manages the charging profile (constant current → constant voltage → cutoff at 4.2V)
2. **DW01A** monitors battery voltage using two internal comparators — cuts off at 4.28V (overcharge) and 2.5V (over-discharge)
3. **Dual NMOS** acts as a physical gate controlled by DW01A — disconnects battery when protection triggers

---

## Components

| Component | Role |
|---|---|
| TP4056 | Solar Li-ion charger IC |
| DW01A | Battery protection IC |
| Q1, Q2 (NMOS) | Physical disconnect switches |
| R1 (2.4kΩ) | Sets charging current to 500mA |
| R2 (10kΩ) | Disables temperature monitoring |
| R3, R4 (1kΩ) | LED current limiting resistors |
| D1 (RED LED) | Charging indicator |
| D2 (GREEN LED) | Charge complete indicator |
| C1 (100nF) | Input decoupling capacitor |
| R5 (0.1Ω) | Current sense resistor |

---
<img width="910" height="771" alt="image" src="https://github.com/user-attachments/assets/3495db37-01ae-47fc-b673-d9d77c9dcb75" />
<img width="1108" height="754" alt="image" src="https://github.com/user-attachments/assets/f28c8be0-194a-410e-b6f3-6341c354d66f" />

