# 4-Bit CMOS Accumulator — Post-Layout Power & Timing Analysis

## Overview
This repository presents the transistor-level design and verification of a 4-bit CMOS accumulator implemented using a bit-sliced architecture. The design was validated through full schematic and post-layout simulations, with emphasis on realistic power, timing, and voltage-scaling behavior.

All results are obtained from post-layout extracted views, reflecting real parasitic effects rather than idealized logic-level assumptions.

---

## Architecture
- Bit-sliced implementation using four identical 1-bit accumulator cells  
- Ripple-carry accumulation path  
- Shared clock and reset distribution across all slices  
- Carry propagation identified as the dominant critical path  

---

## Design & Verification Flow
1. Transistor-level schematic design of a 1-bit accumulator  
2. Hierarchical integration into a 4-bit top-level accumulator  
3. Custom layout with abutment-based bit-slice connectivity  
4. Complete **DRC-clean** and **LVS-matched** physical verification  
5. Post-layout simulations for:
   - Functional correctness  
   - Dynamic and static power characterization  
   - Timing and setup-time margin analysis  

---

## Power Analysis
Post-layout power measurements were performed across frequency and supply-voltage variations.

### VDD = 1.1 V
- Frequency range: 600 MHz – 1 GHz  
- Dynamic power slope: **0.0396 µW/MHz**  
- Static power: **44.56 µW**  

### Voltage Scaling (1.1 V → 0.9 V)
- Dynamic power reduction: **~60.6%**  
- Static power reduction: **~10.6%**  
- Observed reduction exceeds ideal V² scaling due to reduced short-circuit current, parasitic effects, and altered switching behavior in post-layout simulations  

---

## Timing Analysis
- Critical path spans full carry propagation from **Q0 → Q3**  
- Worst-case transitions occur during accumulator rollovers (**7→8** and **15→0**)  
- Minimum passing clock period: **380 ps**  
- Setup-time failure observed at **370 ps**, confirming a 10 ps margin to failure  

---

## Tools Used
- **Cadence Virtuoso** — Schematic capture and custom layout  
- **DRC / LVS** — Physical verification  
- **Post-layout transient simulations** — Power and timing analysis  

---

## Repository Structure
.
├── docs/ # Detailed analysis and report
├── schematics/ # Transistor-level schematics
├── layout/ # Custom layout and extracted views
├── simulations/ # Testbenches and simulation setups
├── results/ # Power plots and timing waveforms
└── README.md

yaml
Copy code

---

## Key Takeaways
- Dynamic power increases with bit-width due to higher effective switching capacitance  
- Post-layout parasitics significantly influence real power behavior  
- Carry-chain delay dominates accumulator timing performance  
- Voltage scaling provides substantial dynamic power savings with limited static power reduction  

---

## Notes
This project emphasizes **physical-design realism** over abstract modeling. All results are derived from post-layout extracted simulations and represent real CMOS implementation constraints.
