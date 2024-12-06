# Time Evolution of a Nonlinear Dynamical System

This repository contains a Python implementation of a nonlinear dynamical system described by a set of nine coupled ordinary differential equations (ODEs). The equations model the dynamics of certain physical systems, including hydrodynamic or convective instabilities. The system is characterized by a reduced Rayleigh number \( r \), a geometry parameter \( a \), and a coupling constant \( \sigma \).

---

## Dynamics

The system of ODEs is as follows:

\[
\begin{aligned}
\dot{C}_1 &= -\sigma b_1 C_1 - C_2 C_4 + b_4 C_4^2 + b_3 C_3 C_5 - \sigma b_2 C_7, \\
\dot{C}_2 &= -\sigma C_2 + C_1 C_4 - C_2 C_5 + C_4 C_5 - \frac{\sigma}{2} C_9, \\
\dot{C}_3 &= -\sigma b_1 C_3 + C_2 C_4 - b_4 C_4^2 - b_3 C_1 C_5 + \sigma b_2 C_8, \\
\dot{C}_4 &= -\sigma C_4 - C_2 C_3 - C_2 C_5 + C_4 C_5 + \frac{\sigma}{2} C_9, \\
\dot{C}_5 &= -\sigma b_5 C_5 + \frac{1}{2} C_2^2 - \frac{1}{2} C_4^2, \\
\dot{C}_6 &= -b_6 C_6 + C_2 C_9 - C_4 C_9, \\
\dot{C}_7 &= -b_1 C_7 - r C_1 + 2 C_5 C_8 - C_4 C_9, \\
\dot{C}_8 &= -b_1 C_8 + r C_3 - 2 C_5 C_7 + C_2 C_9, \\
\dot{C}_9 &= -C_9 - r C_2 + r C_4 - 2 C_2 C_6 + 2 C_4 C_6 + C_4 C_7 - C_2 C_8.
\end{aligned}
\]

Where:
- \( C_1, C_2, \dots, C_9 \): State variables of the system.
- \( r = \frac{R}{R_c} \): Reduced Rayleigh number.
- \( \sigma \): Coupling constant.
- \( a \): Parameter describing the geometry of the square cell.

The constants \( b_1, b_2, \dots, b_6 \) depend on the geometry parameter \( a \) and are defined as:
\[
\begin{aligned}
b_1 &= \frac{4 (1 + a^2)}{1 + 2 a^2}, \quad 
b_2 = \frac{1 + 2 a^2}{2 (1 + a^2)}, \quad 
b_3 = \frac{2 (1 - a^2)}{1 + a^2}, \\
b_4 &= \frac{a^2}{1 + a^2}, \quad 
b_5 = \frac{8 a^2}{1 + 2 a^2}, \quad 
b_6 = \frac{4}{1 + 2 a^2}.
\end{aligned}
\]

---

## Features

### 1. Numerical Integration
The code uses the **Euler method** for time evolution of the coupled ODEs. It evolves the state variables over a specified time range with a timestep \( dt \).

### 2. Initial Conditions
The system is initialized with the following state:
\[
C(t=0) = [0.1, 0, 0.1, 0, 0, 0, 0, 0, 0.1]
\]

### 3. Configurable Parameters
You can adjust:
- **Geometry parameter**: \( a = 1/2 \) (default).
- **Coupling constant**: \( \sigma = 0.5 \) (default).
- **Reduced Rayleigh number**: \( r = 14.1 \) (default).
- **Timestep**: \( dt = 0.01 \) (default).
- **Simulation time**: \( T = 100 \) (default).

### 4. Output
- The simulation generates and **saves the time series** of all state variables as `time_series.csv`.
- **Plots** include:
  - Time series of state variables from \( t = 1 \) to \( t = 100 \).
  - Phase plot of \( C_6 \) vs \( C_7 \) from \( t = 1 \) to \( t = 100 \).

---

## How to Use

### Running the Simulation
1. Clone the repository and navigate to the project directory.
2. Run the Python script:
   ```bash
   python dynamics.py
