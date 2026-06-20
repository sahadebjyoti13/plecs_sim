# Efficiency vs Volume Trade-off in Boost PFC Design for Electric Scooters

MATLAB-based framework for the design and optimization of a **500 kHz Boost Power Factor Correction (PFC) converter** for electric scooter charging applications.

The project investigates the trade-off between **efficiency**, **inductor volume**, and **magnetic stress** by optimizing the boost inductor design over the complete operating range.

---

## Specifications

* **Topology:** CCM Boost PFC
* **Input:** 230 V RMS, 50 Hz AC
* **Rectified Input Range:** 10 – 325 V
* **Output Voltage:** 400 V ± 0.5%
* **Output Power:** 240 W – 1.2 kW
* **Switching Frequency:** 500 kHz
* **Switch Technology:** GaN (LMG3411R070)
* **Magnetic Core:** Ferrite EE Core
* **Winding:** Litz Wire

---

## Features

* Multi-Objective Genetic Algorithm (MOGA) using `gamultiobj`
* Pareto optimization of:

  * **Total inductor loss** (Core + Copper)
  * **Core volume**
* High-frequency ferrite core loss modeling using:

  * Improved Generalized Steinmetz Equation (**iGSE**)
* Physical design constraints:

  * Core saturation ((B_{max} \le B_{sat}))
  * Window fill factor
  * Current density limit
  * Air-gap manufacturability
* Automated Pareto knee-point extraction
* Stress-index based design exploration:

[
\text{Stress Index} = L \cdot I_{pk} \cdot I_{rms}
]

* Stress maps generated over:

  * Input voltage ((V_{in}))
  * Output power ((P_o))
  * Ripple ratio ((\Delta I_L/I_o))

---

## Example Optimal Design

For a **230 V AC → 400 V DC**, **1.2 kW**, **500 kHz** Boost PFC:

| Parameter    | Value     |
| ------------ | --------- |
| Ripple Ratio | 46.1 %    |
| Inductance   | 33.98 µH  |
| Turns        | 19        |
| Core Area    | 58.63 mm² |
| Air Gap      | 0.74 mm   |
| Core Volume  | 6.28 cm³  |
| Total Loss   | 0.35 W    |

---

## Repository Structure

* `pfc.m` – Main optimization script
* `pfc_objectives.m` – Objective functions (loss & volume)
* `pfc_constraints.m` – Physical and magnetic constraints
* `pareto_results.mat` – Pareto-optimal solutions

---

## Engineering Assumptions

* High-strand-count Litz wire
* Practical winding fill factor: (k_w = 0.3)
* AC resistance correction factor: 1.35 @ 500 kHz
* Ferrite core loss modeled using iGSE:

[
P_v = k f^{\alpha} B^{\beta}
]

with coefficients corresponding to high-frequency power ferrites (e.g., TDK N87/N97, Ferroxcube 3F4).

---

## References

1. R. W. Erickson and D. Maksimovic, *Fundamentals of Power Electronics*, 2nd Ed., Springer, 2001.

2. N. Mohan, T. Undeland and W. Robbins, *Power Electronics: Converters, Applications and Design*, Wiley.

3. V. Ramanarayanan, *Power Electronics Course Notes*, IISc Bangalore.

4. TDK Ferrite Core Datasheets (N87 / N97 materials).

---

**Author:** Debjyoti Saha
B.Tech, Electrical Engineering
Indian Institute of Engineering Science and Technology (IIEST), Shibpur
