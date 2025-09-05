# 🚀 CubeSat Power System Simulation

This project simulates the **CubeSat Electrical Power System (EPS)** in **CircuitJS**.  
The goal is to model how a CubeSat manages power during **sunlight** and **eclipse** cycles, focusing on **battery charging/discharging**, **solar input**, and **load behavior**.

---

## 📌 Problem Statement

A CubeSat orbits Earth and experiences:

- 🌞 **Sunlight Phase (60 min):** Solar panels supply power to electronics and charge the battery.  
- 🌑 **Eclipse Phase (30 min):** No solar input; the battery discharges to keep the system alive.  

The simulation should demonstrate how **battery voltage, current, and charge evolve** over multiple orbital cycles.

---

## 🎯 Objectives

- Calculate **solar input**, **battery behavior**, and **load requirements**.  
- Build the CubeSat EPS circuit in **CircuitJS**.  
- Simulate **charge/discharge cycles** of the battery.  
- Troubleshoot CircuitJS limitations and apply workarounds.

---

## 📚 Resources

- [Perplexity Research](https://www.perplexity.ai/search/1-create-the-power-bus-battery-3ibTwQCeSNWhAU1CQkboBg)  
- [ChatGPT Discussion 1](https://chatgpt.com/share/68baead2-6dcc-8011-a4df-5c1401fee842)  
- [ChatGPT Discussion 2](https://chatgpt.com/share/68baebf5-8a54-8011-be25-c734e30d009a)  
- [YouTube Tutorial](https://youtu.be/cKx952NsPjc?si=RzU6_CjePzXv0DqZ)  

---

## ⚡ Circuit Description

### 🔹 Input Source
- DC/AC voltage source.  
- Ammeter placed after source to measure current input.  

### 🔹 Resistors
- `0.1 Ω` → battery ESR  
- `0.01 Ω` → solar input ESR  

### 🔹 Signal Generator
- Waveform generator (`11.1 mHz`) to simulate orbital sunlight/eclipse cycles.  

### 🔹 Current Source Branches (PWL Approximation)
**Branch 1**  
- `27 Ω` resistor + AC voltage source (10 V, configurable frequency/duty).  

**Branch 2**  
- `18 Ω` resistor + AC voltage source (10 V, configurable frequency/duty).  

---

## 🛠️ Problems Faced & Solutions

1. **Missing Features in CircuitJS**  
   - ❌ PWL current source not available.  
   - ✅ Used pulse voltage + series resistor to approximate solar input.  

2. **Switching Control Signals**  
   - ❌ Incorrect ON/OFF timing of loads.  
   - ✅ Step-by-step simulation with scopes; tuned duty cycle until aligned.  

3. **Bad Connections**  
   - ❌ Simulator flagged “bad connections.”  
   - ✅ Added proper ground nodes and corrected resistor placement.  

---

## 🚧 Failures & Fixes

1. **Current Source Limitation**  
   - ❌ Only DC current supported.  
   - ✅ Replaced with **pulse voltage + resistor** for sunlight/eclipse profile.  

2. **Incorrect ESR Placement**  
   - ❌ ESR resistors initially in wrong branches.  
   - ✅ Moved `0.1 Ω` → battery path, `0.01 Ω` → solar path.  

3. **Unrealistic Resistance Values**  
   - ❌ Used `1 kΩ`, leading to negligible currents.  
   - ✅ Updated to realistic: `0.1 Ω` and `10 Ω`.  

---

## 🔍 Troubleshooting Approach

- Isolate **battery**, **solar input**, and **load** subcircuits.  
- Document **expected vs actual waveforms**.  
- Use **scopes + labeled nodes** for debugging.  
- Explore CircuitJS docs/forums for advanced simulation methods.  

---

 

Many concepts were new, but this process improved my understanding 

---
