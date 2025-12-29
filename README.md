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
## 🛠️ 1. Repository Structure
├── src/
│   ├── 180nm_nmos.in     # Silvaco ATLAS structure for 180nm
│   ├── 90nm_nmos.in      # Silvaco ATLAS structure for 90nm
│   ├── 45nm_nmos.in      # Silvaco ATLAS structure for 45nm
│   └── 22nm_nmos.in      # Silvaco ATLAS structure for 22nm
├── results/
│   ├── id_vgs_plots/     # compiled plot
│   └── parameter_data.csv # Compiled extraction results
└── README.md

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
* **Electrostatic Control:** The Subthreshold Slope (SS) is the most critical indicator of a transistor's switching efficiency.The Physics: SS is mathematically governed by the capacitance ratio:$$SS \approx 60 \cdot \left(1 + \frac{C_{dep}}{C_{ox}}\right) \text{ mV/dec}$$Reasoning: In legacy nodes (180nm), the gate oxide is relatively thick, resulting in a lower $C_{ox}$. As we scale to 22nm, the oxide is aggressively thinned ($t_{ox} \approx 1.2\text{nm}$). This massive increase in $C_{ox}$ minimizes the impact of $C_{dep}$, driving the SS toward the theoretical limit of 60 mV/dec. Our 22nm simulation achieves ~48 mV/dec due to optimized doping and bias tuning.
* **Charge Confinement:** 180nm (Bulk-Dominated): Gate electric field lines are spread out. Carriers (electrons) are not tightly bound to the surface and can flow through the "bulk" of the silicon substrate.22nm (Surface-Dominated): The extremely high vertical electric field created by the ultra-thin $t_{ox}$ "pulls" the carriers into a very narrow, high-density inversion layer at the $Si–SiO_2$ interface.Impact: This Strong Surface Confinement prevents "punch-through"—where current flows deep in the substrate, bypassing gate control.
* **Leakage:** In the nanometer regime, the Drain acts as a "second gate," which is undesirable.The Reasoning: In the 22nm node, the Drain is physically so close to the Source that its electric field lowers the potential barrier at the Source junction. This is known as DIBL.Mitigation: The 22nm node utilizes Halo (Pocket) Doping to keep the off-state leakage ($I_{off}$) exceptionally low ($2.3 \times 10^{-17}\text{A}$).

---

## 🔮 5. Future Work
* Transition to **FinFET** and **Gate-All-Around (GAA)** architectures.
* Inclusion of **Short-Channel Effects (SCE)** like DIBL and velocity saturation.

---

## 🧠 6. Conclusion
This study confirms that as planar CMOS scales toward the 22nm regime, maintaining gate control becomes the primary challenge. The results validate that while drive current increases, careful engineering of doping and oxide thickness is required to manage the trade-offs between speed ($I_{on}$) and power consumption ($I_{off}$).

##Notes
All results are intended for academic and educational purposes
Absolute values may vary depending on process tuning and bias conditions
