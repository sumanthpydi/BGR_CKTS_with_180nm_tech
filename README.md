# Current-Mirror Bandgap Reference – SCL 180 nm

Schematic design and simulation of a self-biased, current-mirror based bandgap voltage reference in the SCL 180 nm process (`ts018_scl_prim`), using Cadence Virtuoso (ADE L) and Spectre.

**Report:** [`BGR_Current_Mirror_SCL180nm_Report.pdf`](BGR_Current_Mirror_SCL180nm_Report.pdf)

## Circuit
- PMOS/NMOS current mirror (`pmos_33` / `nmos_33`, W/L = 20 µm / 5 µm) forcing equal branch currents
- Vertical PNPs (`vpnp33_10`) with area ratio n = 2
- I = V<sub>T</sub> ln(n) / R<sub>0</sub>, and V<sub>ref</sub> = V<sub>BE3</sub> + (R<sub>2</sub>/R<sub>0</sub>) V<sub>T</sub> ln(n)
- VDD = 3.3 V

## Simulations
1. CTAT: V<sub>BE</sub> of a single PNP at 5 µA versus temperature
2. PTAT: ΔV<sub>BE</sub> = V<sub>T</sub> ln 2 with ideal current sources
3. Self-biased PTAT core with current mirror
4. Complete BGR, with a parametric sweep of R<sub>2</sub> for minimum temperature drift

## Results (−40 °C to 125 °C)
| Parameter | Value |
|---|---|
| CTAT slope | −1.72 mV/°C (theory −1.70 mV/K) |
| ΔV<sub>BE</sub> slope (n = 2) | 59.4 µV/°C (theory 59.7 µV/K) |
| R<sub>0</sub> / R<sub>2</sub> | 2.8 kΩ / ≈ 68.2 kΩ |
| V<sub>ref</sub> | ≈ 1.14 V |
| ΔV<sub>ref</sub> | 13.34 mV |
| Temperature coefficient | ≈ 71 ppm/°C |

## Next steps
- Supply sweep (simple vs cascode mirror)
- Start-up circuit and power-up transient
- Op-amp based BGR, corners and Monte Carlo
- Layout and post-layout simulation

## Reference
Based on the lecture series on bandgap reference circuits by Hafeez K. T.; theory from B. Razavi, *Design of Analog CMOS Integrated Circuits*, Ch. 12.
