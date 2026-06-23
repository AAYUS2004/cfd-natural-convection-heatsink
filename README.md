# CFD Thermal Analysis of a Natural-Convection Heat Sink

**ANSYS Fluent 2026 R1 | SolidWorks 2026 | Student Portfolio Project**

---

## Problem Statement

Analyse the buoyancy-driven heat transfer from a copper finned heat sink exposed to ambient air under natural convection, without any forced airflow. The goal was to determine the peak temperature, thermal resistance, and effective heat transfer coefficient using CFD simulation.

---

## Geometry

- Cylindrical copper heat sink with 6 straight rectangular fins
- Base diameter: 120 mm | Fin height: 100 mm | Fin thickness: 5 mm
- Modelled in SolidWorks 2026, imported into ANSYS DesignModeler

---

## Methodology

- Enclosure created around heat sink (0.15 m lateral, 0.25 m above, 0.10 m below)
- Boolean subtraction to extract fluid domain
- Heat sink surface set as heat flux wall (500 W/m²)
- Pressure inlet (bottom) + Pressure outlet (top) — open domain approximation
- Boussinesq buoyancy model with gravity enabled
- Laminar flow — justified by pre-simulation Rayleigh number Ra = 5.04 × 10⁶ (laminar threshold: 10⁹)
- Mesh: 505,425 elements with inflation layers on heat sink walls
- Solver: SIMPLE, second-order upwind, converged within 500 iterations

---

## Key Results

| Parameter | Value |
|---|---|
| Peak Base Temperature | 500 K (227°C) |
| Ambient Temperature | 300 K (27°C) |
| Thermal Resistance | 3.00 K/W |
| Effective Heat Transfer Coefficient | 2.50 W/m²K |
| Max Air Velocity | 0.706 mm/s |
| Rayleigh Number | 5.04 × 10⁶ |

---

## Results Preview

<img width="792" height="352" alt="temperature_contour_isometric png" src="https://github.com/user-attachments/assets/4cc67b40-3dd3-4288-b9bc-b41ea15d12a1" />

*Static temperature contour — peak 500 K (227°C) at heat sink base, ambient 300 K in far field*

---

## Analytical Comparison

Churchill–Chu correlation for a vertical flat plate used as an order-of-magnitude consistency check *(not a direct validation — correlation is for smooth flat plates, not finned arrays)*:

- Nu = 25.0
- h = 8.45 W/m²K

Both simulation and analytical values fall within the accepted natural convection range of **2–25 W/m²K** ✓

---

## Known Limitations

- **No formal mesh independence study** — ANSYS Student licence (512K element cap) constrained this; result should be treated as converged, not Richardson-extrapolated
- **Radiation not modelled** — estimated contribution ~1% for polished copper (ε = 0.05) at T_max = 500 K, considered negligible
- **Boussinesq approximation borderline** at βΔT = 0.5 — ideal gas law would be more accurate for ΔT = 200 K
- **Enclosure side walls set as adiabatic** — constrains lateral air entrainment compared to a fully open environment; likely cause of lower-than-scale-estimate air velocity
- **Churchill–Chu used as consistency check only** — not a validated correlation for finned geometry

---

## Tools Used

| Tool | Purpose |
|---|---|
| SolidWorks 2026 | CAD modelling |
| ANSYS Fluent 2026 R1 | CFD simulation |
| ANSYS Mechanical | Meshing |

---

## Key Learning Outcomes

- Full CFD workflow: CAD → Geometry → Mesh → Solver → Post-processing
- Natural convection physics: Rayleigh number, Boussinesq approximation, buoyancy-driven flow
- Thermal analysis: heat flux BCs, thermal resistance, effective h calculation
- Analytical cross-validation using Churchill–Chu correlation
- Honest documentation of limitations — a core engineering practice

---

## About

3rd-year B.Tech Mechanical Engineering student | Delhi Skill and Entrepreneurship University

Self-learning portfolio project — not a research publication.

*Feedback and suggestions welcome via Issues.*
