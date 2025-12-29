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

## 🔍 4.Results  &  Discussions


<img width="1280" height="727" alt="Image" src="https://github.com/user-attachments/assets/949fb41d-f0c8-451b-bdaf-3f5ef0d27f9c" />
<img width="549" height="122" alt="Image" src="https://github.com/user-attachments/assets/ad6cbd4c-d31b-4f41-a195-b8a524bc73c9" />




22 nm NMOS

The inversion charge is tightly confined at the surface, demonstrating near-ideal electrostatic control. This results in the lowest threshold voltage, steepest subthreshold slope, and best overall switching performance among all nodes.

---

<img width="1280" height="775" alt="Image" src="https://github.com/user-attachments/assets/b4a4b41a-d921-4bfb-bd2e-f89ed21ff003" />
<<img width="481" height="125" alt="Image" src="https://github.com/user-attachments/assets/ea4d773a-e7e2-4acc-a041-b2b5fe247e68" />

45 nm NMOS

Electrons are more strongly confined near the Si–SiO₂ interface, indicating improved gate-to-channel coupling. This leads to better subthreshold slope, reduced leakage, and enhanced drive current compared to larger nodes.


---



<img width="1280" height="784" alt="Image" src="https://github.com/user-attachments/assets/d0d774dc-5cbc-4968-a110-97f908fe74b1" />
<img width="391" height="121" alt="Image" src="https://github.com/user-attachments/assets/c61643f7-849c-44c9-a87a-4964559d560d" />




90 nm NMOS

Partial confinement of carriers near the surface is observed, though bulk conduction remains significant. This node represents a transition regime, where reduced channel length increases drain influence and leakage, degrading subthreshold behavior.


---

<img width="1280" height="761" alt="Image" src="https://github.com/user-attachments/assets/c4282c21-ae43-4e72-88a1-66757727f432" />
<img width="377" height="110" alt="Image" src="https://github.com/user-attachments/assets/33a017b7-ff19-43aa-b7c8-711673bf83c2" />





180 nm NMOS

The electron concentration spreads deep into the silicon bulk, indicating bulk-dominated conduction and weaker gate control. The long channel suppresses short-channel effects, but results in a higher subthreshold slope and lower drive current.

---


* **Electrostatic Control:** The Subthreshold Slope (SS) is the most critical indicator of a transistor's switching efficiency.The Physics: SS is mathematically governed by the capacitance ratio:$$SS \approx 60 \cdot \left(1 + \frac{C_{dep}}{C_{ox}}\right) \text{ mV/dec}$$Reasoning: In legacy nodes (180nm), the gate oxide is relatively thick, resulting in a lower $C_{ox}$. As we scale to 22nm, the oxide is aggressively thinned ($t_{ox} \approx 1.2\text{nm}$). This massive increase in $C_{ox}$ minimizes the impact of $C_{dep}$, driving the SS toward the theoretical limit of 60 mV/dec. Our 22nm simulation achieves ~48 mV/dec due to optimized doping and bias tuning.
* **Charge Confinement:** 180nm (Bulk-Dominated): Gate electric field lines are spread out. Carriers (electrons) are not tightly bound to the surface and can flow through the "bulk" of the silicon substrate.22nm (Surface-Dominated): The extremely high vertical electric field created by the ultra-thin $t_{ox}$ "pulls" the carriers into a very narrow, high-density inversion layer at the $Si–SiO_2$ interface.Impact: This Strong Surface Confinement prevents "punch-through"—where current flows deep in the substrate, bypassing gate control.
* **Leakage:** In the nanometer regime, the Drain acts as a "second gate," which is undesirable.The Reasoning: In the 22nm node, the Drain is physically so close to the Source that its electric field lowers the potential barrier at the Source junction. This is known as DIBL.Mitigation: The 22nm node utilizes Halo (Pocket) Doping to keep the off-state leakage ($I_{off}$) exceptionally low ($2.3 \times 10^{-17}\text{A}$).




---
Id–VGS Characteristics (Log & Linear)

Linear Scale:
<img width="1618" height="879" alt="image" src="https://github.com/user-attachments/assets/93d3d6a9-f9db-4b6b-a6ec-3512da365e06" />

In the linear Id–VGS plot, the drain current increases with gate voltage in the strong inversion region. Smaller nodes deliver higher drive current, following the order
22 nm > 45 nm > 90 nm > 180 nm, due to shorter channel lengths and improved gate coupling. The leftward shift of the curves confirms a reduction in threshold voltage with scaling.

---
Log Scale:
<img width="1588" height="863" alt="image" src="https://github.com/user-attachments/assets/70a1d4bd-39bc-4948-9565-75ae1c75b035" />

The log-scale Id–VGS curves show that as technology scales from 180 nm to 22 nm, the subthreshold slope becomes progressively steeper. This indicates stronger gate electrostatic control and earlier turn-on for smaller nodes. The 22 nm device exhibits the best subthreshold behavior, while the 180 nm device shows bulk-dominated conduction with a gentler slope.


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
