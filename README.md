# Comparative-CMOS-Technology-Scaling-Study-using-Silvaco-TCAD
Comparative TCAD analysis of planar NMOS devices across 180 nm, 90 nm, 45 nm, and 22 nm technology nodes using Silvaco ATLAS, focusing on Id–VGS characteristics and CMOS scaling trends


# TCAD Analysis of CMOS Scaling: 180nm to 22nm 🔬

[![Simulation: Silvaco ATLAS](https://img.shields.io/badge/Simulation-Silvaco%20ATLAS-blue)](https://www.silvaco.com/)
[![Tech: CMOS Scaling](https://img.shields.io/badge/Technology-CMOS%20Scaling-orange)](#)

## 📌 1. Project Overview
This project presents a comparative **TCAD-based analysis** of planar NMOS transistors across four technology nodes: **180nm, 90nm, 45nm, and 22nm**. Using **Silvaco ATLAS**, we analyze how scaling affects electrostatic control, threshold voltage ($V_t$), and subthreshold leakage.



### Key Objectives:
* Validate MOSFET scaling theory through physics-based simulation.
* Extract electrical parameters ($V_t, SS, I_{on}, I_{off}$).
* Visualize electron concentration and surface confinement.

---

## 🛠️ 2. Simulation Environment
* **Tool:** Silvaco ATLAS (2D Device Simulation)
* **Conditions:** $V_{DS} = 1V$, $V_{GS}$ Sweep ($0-1V$), Temp = $300K$.
* **Scaling Strategy:** Proportional reduction of channel length ($L_g$) and oxide thickness ($t_{ox}$).

---

## 📊 3. Extracted Electrical Parameters
The following data was extracted from the simulated $I_d–V_{GS}$ characteristics:

| Node | $V_t$ (V) | SS (mV/dec) | $I_{on}$ (A) | $I_{off}$ (A) |
| :--- | :---: | :---: | :---: | :---: |
| **180 nm** | ~0.203 | ~95 | $1.1 \times 10^{-4}$ | $9.9 \times 10^{-10}$ |
| **90 nm** | ~0.250 | ~117 | $6.1 \times 10^{-4}$ | $1.4 \times 10^{-9}$ |
| **45 nm** | ~0.338 | ~79 | $3.2 \times 10^{-4}$ | $6.2 \times 10^{-12}$ |
| **22 nm** | **~0.192** | **~48** | Bias-limited | $2.3 \times 10^{-17}$ |



---

## 🔍 4. Discussion & Trends
* **Electrostatic Control:** Scaling to 22nm significantly improves the Subthreshold Slope (**48 mV/dec**), indicating superior gate control.
* **Charge Confinement:** Electron concentration plots reveal a transition from bulk-dominated conduction in 180nm to **strong surface confinement** in 22nm.
* **Leakage:** Leakage current ($I_{off}$) shows sensitivity to $V_t$ tuning and DIBL as we enter the nanometer regime.

---

## 🔮 5. Future Work
* Transition to **FinFET** and **Gate-All-Around (GAA)** architectures.
* Inclusion of **Short-Channel Effects (SCE)** like DIBL and velocity saturation.

---

## 🧠 6. Conclusion
This simulation validates that while scaling improves drive current and density, maintaining electrostatic control requires aggressive $t_{ox}$ scaling and doping profile optimization, as demonstrated by the superior performance of the 22nm node.
