# Dynamic Portfolio Choice Models with Transaction Costs - Masters Thesis in Economics.

### General Overview
This repository contains files for my masters thesis in economics,
which focuses on Dynamic Portfolio Choice Models, in the presence of transaction costs.
These models are solved using dynamic programming methods. We use constrained non linear optimization, quadrature and monte carlo methods, gaussian process regression and a problem specific sampling scheme.
<br>
<br>
The thesis was written in LaTeX, and be compiled using the main.tex file.
The computational scheme was written in python, using a stack of libraries noted below.
<br>
<br>
This thesis is greatly inspired by the work of Simon Scheidegger (2023); Peter Schober, Julian Valentin and Dirk Pflüger (2020); and Yongyang Cai, Kenneth Judd and Rong Xu (2013). Further references and be found in the thesis document.

---

## Folder Structure

Below is a breakdown of the main folders in the repository and their contents:

- **`Python/`**: Contains the main source code for the project, including scripts and modules.
- **`Speciale dokumentet/`**: This folder contains the LaTeX project. Including local packages (KU-frontpage), and figures from the Python project end up here aswell
- **`Notes from papers/`**: A small LaTeX project consisting of notes used. This is no longer comprehensive, see the thesis.
- **`Gammel kode/`**: Contains old code.

---

## Brief model description

We solve problem(s):

$$
v_{t} (\mathbf{x_t}, \theta_t) = \max_{c_t , \boldsymbol{\delta_{t}^{+}}, \boldsymbol{\delta_{t}^{-}} }{ u(c_t) \Delta t + \beta \mathbb{E}_{t} \Big[ \pi _{t+\Delta t} ^{1-\gamma} v _{t+\Delta t}  \mathbf{x} _{t+ \Delta t} \Big]}
$$

With Dynamics:

$$
b_t = 1 - \mathbf{1} \cdot \Big( \mathbf{x_t} - \boldsymbol{\delta_t} - \psi \Big( \boldsymbol{\delta_{t}^{+}}, \boldsymbol{\delta_{t}^{-}}  \Big) \Big) - c_t \Delta t
$$

$$
\pi_{t+\Delta t} = b_t R_f (\theta_t)  + (\mathbf{x}_t + \boldsymbol{\delta}_t)^{\top} \cdot \mathbf{R}(\theta_t) 
$$

$$
\mathbf{x_{t+\Delta t}} =  \frac{(\mathbf{x_t} + \boldsymbol{\delta_t}) \odot \mathbf{R_t} (\theta_t )}{ \pi_{t+\Delta t} }
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



- **Hardware**: Code is writting for use on MacOS. Other systems might need some tweaks or other packages. This project was run on a Macbook Pro 2023 laptop, with the Apple M3 chip.
- **Software**: Code is written in Python 3.11.9.
- **Dependencies**: In order to run the code, the following packages are required:
  - Numpy
  - Torch
  - Gpytorch
  - Cyipopt 
  - Scipy
  - Tasmanian 
    - **Note**: Installation of this package is bothersome. See Tasmanian repository and installation guide.
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

