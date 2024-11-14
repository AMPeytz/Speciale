# Dynamic Portfolio Choice Models with Transaction Costs - Masters Thesis in Economics.

### General Overview
This repo contains files for my masters thesis in economics,
which focus on Dynamic Portfolio Choice Models, in the presence of transaction costs.
These models are solved using dynamic programming methods. We use constrained non linear optimization, quadrature and monte carlo methods, gaussian process regression and a problem specific sampling scheme.
This repo contains files regarding the thesis written in LaTeX, and my coding project, in Python.
<br>
This thesis, is greatly inspired by the work of Simon Scheidegger (2023); Peter Schober, Julian Valentin and Dirk Pflüger (2020); and Yongyang Cai, Kenneth Judd and Rong Xu (2013).

---

## Folder Structure

Below is a breakdown of the main folders in the repository and their contents:

- **`Python/`**: Contains the main source code for the project, including scripts and modules.
- **`Speciale dokumentet/`**: This folder contains the LaTeX project. Including local packages (KU-frontpage), and figures from the Python project end up here aswell
- **`Notes from papers/`**: A small LaTeX project consisting of notes used. This is no longer comprehensive, see the thesis.
- **`Gammel kode/`**: Contains old code.

---

## Brief model description

We solve problems:

$$
v_{t} (\mathbf{x}_{t}, \theta_t) = \max_{c_t , \boldsymbol{\delta}^{+}_{t}, \boldsymbol{\delta}^{-}_{t} } \left\{ u(c_t) 
\Delta t + \beta \mathbb{E}_{t} \left[ 
\pi_{t+\Delta t}^{1-\gamma}
v_{t+\Delta t} (\mathbf{x}_{t+\Delta t }, \theta_{t + \Delta t }  ) 
\right] \right\} , \quad t < T 
$$

With Dynamics:

$$
b_{t} = 1 - \mathbf{1}^{\top} \cdot (\mathbf{x_t} - \boldsymbol{\delta}_t - \psi( \boldsymbol{\delta}^{+}_{t}, \boldsymbol{\delta}^{-}_{t}  )) - c_t \Delta t
$$

$$
\pi_{t+\Delta t} = b_t R_f (\theta_t)  + (\mathbf{x}_t + \boldsymbol{\delta}_t)^{\top} \cdot \mathbf{R}(\theta_t) 
$$

$$
\mathbf{x}_{t+\Delta t} =  \frac{(\mathbf{x}_t + \boldsymbol{\delta}_t) \odot \mathbf{R}_t (\theta_t )}{ \pi_{t+\Delta t} }
$$

$$
W_{t+\Delta t} = \pi_{t+\Delta t} W_t
$$

Terminal value function:

$$
v_T (\mathbf{x}_T , \theta_T ) = u ( (1 - \psi(\mathbf{x}_T)) \cdot (1-R_f (\theta_T)) )\cdot \Delta t \cdot (1-\beta)^{-1} 
$$

Subject to constraints:

$$
\boldsymbol{\delta}_t \geq - \mathbf{x}_t 
$$

$$
b_t \geq 0 
$$

$$
\mathbf{1}^{\top} \mathbf{x}_t \leq 1 
$$

---

## Computational Requirements

To run the code effectively, consider the following requirements:



- **Hardware**: Code is writting for use on MacOS. Other systems might need some tweaks or other packages.
- **Software**: Code is written in Python 3.11.9.
- **Dependencies**: In order to run the code, the following packages are required:
  - Numpy
  - Torch
  - Gpytorch
  - Cyipopt 
    - **Note**: This package may be difficult to install. See package specifications.
  - Scipy
  - Tasmanian 
    - **Note**: This package may be difficult to install. See package specifications.
  - Chaospy
  - Matplotlib
  - Logging
  - Joblib
  - Os
  - Multiprocessing
  - Random
  - Scienceplots
  - Itertools

---

