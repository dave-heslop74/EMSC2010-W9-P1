# EMSC2010 – Week 9 Practical 1: Numerical Modelling

This repository contains the template Jupyter notebooks for **Week 9 Practical 1** of *EMSC2010: Data Science for Earth System Scientists* at the Australian National University.

The session introduces **numerical modelling** through the finite difference method applied to heat diffusion in soil. Students build a working 1D soil temperature model from scratch, explore how physical parameters affect model behaviour, and investigate the concept of numerical stability before extending the model to a time-varying surface boundary condition.

---

## Notebooks

### Notebook 1 – Soil Temperature Model (`NB1`)

Students implement a one-dimensional finite difference model to simulate how heat diffuses downward through a column of soil after the surface is set to a fixed temperature. The temperature of each soil layer is updated at each time step using the heat diffusion equation:

$$T_i^{\text{new}} = T_i + \kappa \frac{\Delta t}{(\Delta z)^2} \left(T_{i+1} - 2T_i + T_{i-1}\right)$$

where $\kappa$ is the thermal diffusivity of the soil, $\Delta t$ is the time step, and $\Delta z$ is the layer thickness.

The notebook covers:

- Setting up the soil column with initial and boundary conditions
- Running the time-stepping loop and recording model output
- Plotting temperature profiles at different time steps to observe the warming front propagating downward to equilibrium
- Plotting the temperature time series of an individual layer
- **Experiments:** comparing how thermal diffusivity differs between dry soil, rock-bearing soil, and wet clay, and exploring the effect of reversing the temperature gradient
- **Numerical stability:** understanding why the time step and layer thickness must satisfy $\Delta t \leq \frac{(\Delta z)^2}{2\kappa}$, and the computational cost implications of resolving finer spatial detail

**Key concepts:** Finite difference method, heat diffusion, initial and boundary conditions, thermal diffusivity, numerical stability

**Libraries:** `numpy`, `matplotlib`

---

### Notebook 2 – Soil Temperature Model with a Daily Surface Cycle (`NB2`)

Building directly on NB1, students modify the model to simulate a realistic scenario: a soil column driven by a sinusoidally varying surface temperature that follows a 24-hour daily cycle:

$$T_{\text{surface}}(t) = T_{\text{mean}} + A \sin\left(\frac{2\pi t}{P}\right)$$

where $T_{\text{mean}}$ = 15°C, amplitude $A$ = 10°C, and period $P$ = 86400 s (one day). Students update the model parameters (50 layers of 5 cm, 10-minute time step, 20-day run) and adapt the time-stepping loop to apply the oscillating boundary condition at each step.

The notebook explores how warming pulses penetrate the soil during the day but are damped and delayed with depth — and how the soil column requires several cycles to "forget" its initial conditions and settle into a true periodic equilibrium.

A **solution notebook** is also provided for reference.

**Key concepts:** Sinusoidal boundary conditions, damping and phase lag with depth, transient vs periodic equilibrium, model spin-up

**Libraries:** `numpy`, `matplotlib`

---

## Getting Started

This is a **template repository**. To begin working on the notebooks:

1. Click **"Use this template"** at the top of this page to create a copy of the repository in your own GitHub account.
2. Open any notebook from your copy of the repository and click the **"Open in Colab"** badge at the top of the notebook to launch it in Google Colab.
3. Before submitting, replace the `uXXXXXXX` placeholder in the filename with your ANU student UID.

---

## Repository Structure

```
EMSC2010-W9-P1/
├── EMSC2010_W9_P1_NB1_uXXXXXXX.ipynb            # Soil temperature model (fixed surface)
├── EMSC2010_W9_P1_NB2_uXXXXXXX.ipynb            # Soil temperature model (daily cycle)
├── EMSC2010_W9_P1_NB2_uXXXXXXX_solution.ipynb   # NB2 solution for reference
├── LICENSE
└── README.md
```

---

## Course Information

| | |
|---|---|
| **Course** | EMSC2010 – Data Science for Earth System Scientists |
| **Institution** | Australian National University (ANU) |
| **Week** | 9 |
| **Session** | Practical 1 |
| **Topic** | Numerical Modelling |

---

## License

This repository is released under the [MIT License](LICENSE).
