# Solar Differential Rotation Analysis
**PHYS 146 – University of Alberta**  
**Author:** Rudmila Samuad Eka  
**Date:** April 2024

---

## Overview

This project analyzes the **differential rotation of the Sun** by tracking sunspot positions over time using observational data from NASA's Solar Dynamics Observatory (SDO).

Unlike solid bodies, the Sun is composed of gaseous plasma — meaning it does not rotate uniformly. Rotation is fastest at the equator (~24 days per rotation) and slowest near the poles (~35 days). This project confirms this phenomenon quantitatively by fitting a sinusoidal model to real tracked sunspot data.

---

## Research Question

> Does the Sun's rotation period vary with latitude, and if so, by how much?

---

## Data

- **Source:** NASA Solar Dynamics Observatory (SDO) — HMI Intensitygram (orange filter)
- **Collection method:** Online Tracker software applied to SDO video footage; Heliocentric Cartesian coordinate system established with Sun's center at (0, 0)
- **4 sunspots tracked** across two latitude bands:

| Sunspot | Location | Observation Dates | # Observations |
|---------|----------|-------------------|----------------|
| 1 | Near equator | 14 Jan – 23 Jan 2023 | 11 |
| 2 | Near north pole | 01 Mar – 11 Mar 2023 | 11 |
| 3 | Near equator | 15 Jul – 25 Jul 2023 | 11 |
| 4 | Near north pole | 11 Jan – 20 Jan 2023 | 10 |

---

## Methods

### 1. Coordinate Framework
A Heliocentric Cartesian coordinate system (x, y) was established centered on the Sun. Solar radius calibrated to **R = 696,340 km**.

### 2. Latitude Calculation
Heliographic latitude θ calculated for each sunspot using:

$$\sin\theta = \frac{\bar{y}}{R}$$

where $\bar{y}$ is the average vertical position across all observations.

### 3. Theoretical Model
Sunspot horizontal position as a function of time modeled as:

$$x(t) = R\cos\theta\sin(\omega t + \phi)$$

### 4. Curve Fitting
Angular velocity ω and phase φ fitted to observed x(t) data using `scipy.optimize.curve_fit`. Uncertainties extracted from the covariance matrix.

### 5. Period Calculation
Rotation period calculated from best-fit angular velocity:

$$T = \frac{2\pi}{\omega}$$

---

## Results

| Sunspot | Location | θ (°) | ω (rad/day) | T (days) |
|---------|----------|--------|-------------|----------|
| 1 | Near equator | -10.60 | 0.250 ± 0.010 | **25 ± 1** |
| 2 | Near north pole | 38.03 | 0.200 ± 0.010 | **31 ± 2** |
| 3 | Near equator | 5.68 | 0.247 ± 0.010 | **25 ± 0.1** |
| 4 | Near north pole | 27.00 | 0.220 ± 0.010 | **29 ± 1** |

**Theoretical values:** ~24 days (equator) · ~35 days (poles)

### Key Finding
Results confirm solar differential rotation — equatorial sunspots complete a full rotation ~25% faster than polar sunspots, consistent with theoretical predictions and established solar physics literature.

---

## Repository Structure

```
solar-differential-rotation/
│
├── notebooks/
│   └── solar_differential_rotation.ipynb   # Full analysis notebook
├── report/
│   └── lab_report_solar rotation(final).pdf              # Final lab report (April 2024)
│   └── lab_report_solar rotation(midterm).pdf            # Final lab report (March 2024)
├── presentation/
│   └── SOlar Rotation Presentation                       # Presentation (April 2024)
└── README.md
```

---

## How to Run

```bash
# Clone the repo
git clone https://github.com/RudmilaS/solar-differential-rotation.git

# Install dependencies
pip install numpy pandas matplotlib scipy jupyter

# Launch notebook
jupyter notebook notebooks/solar_differential_rotation.ipynb
```

---

## Tools Used

| Tool | Purpose |
|------|---------|
| `NumPy` | Array operations, trigonometric calculations |
| `pandas` | Data structuring |
| `Matplotlib` | Visualization of fits and differential rotation trends |
| `SciPy` | Curve fitting, uncertainty extraction |
| `Jupyter Notebook` | Interactive analysis and documentation |

---

## References

1. NASA. *Solar Rotation Varies by Latitude.* 2013. https://www.nasa.gov/image-article/solar-rotation-varies-by-latitude/
2. Obridko & Badalyan (2019). Solar Corona as Indicator of Differential Rotation. *Cosmic Research*, 57, 407–412.
3. Stenflo, J.O. (1989). Differential rotation of the sun's magnetic field pattern. *A&A*, 210, 403–409.
4. Jha, B.K. et al. Measurements of Solar Differential Rotation Using the Kodaikanal Sunspot Data. *Solar Physics.*

---

*University of Alberta · Mathematical Physics · Science Co-op Program*
