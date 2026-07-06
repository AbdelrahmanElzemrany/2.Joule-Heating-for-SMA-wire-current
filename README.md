[Click here and press view raw to download and view the simulation video explaining the standalone process.](StandaloneJouleHeatingExplaination.mp4)

[Click here and press view raw to download and view the integrated control loop video.](TheFeedForwardControllerWithJouleheating.mp4)

# Joule-Heating-for-SMA-wire

An end-to-end electro-thermal modeling framework and feedforward control architecture to validate Joule heating dynamics in standalone and integrated Shape Memory Alloy (SMA) bending actuators. Built using Simulink, Simscape Multibody, and MATLAB.

This repository focuses explicitly on validating the thermodynamic subsystem and evaluating its integration with a feedforward control system utilizing lookup tables extracted via First-Order Reversal Curves (FORC). 
## 📝 Project Overview

While idealized models treat temperature as a direct input signal, real-world Shape Memory Alloy (SMA) actuators must be driven via electrical current (Joule heating). This introduces complex **electro-thermal dynamics** and severe physical lag caused by hardware voltage limits, convective environmental cooling rates, and structural latent heat of transformation. During phase transitions, the material absorbs or releases latent heat, acting as a thermal buffer that severely distorts standard linear temperature control and worsens tracking errors.

This project bridges the gap between material theory and hardware reality by developing an end-to-end **electro-thermal modeling and feedforward control framework**. The system models the complete energy balance—balancing electrical power inputs ($I^2R$) against transient sensible heat storage, latent heat enthalpy blocks, and ambient convective dissipation. By integrating this high-fidelity plant model with a path-dependent feedforward controller driven by pre-extracted First-Order Reversal Curve (FORC) lookup arrays, the architecture maps curvature targets into explicit current/voltage commands. This completely eliminates feedback phase confusion and mitigates the destructive lag of physical thermal buffering.


## 🚀 Pipeline & File Architecture

The repository is structured sequentially to take a robot from raw thermodynamic equations to a verified controller tracking trajectories:

### 1. Kinematic & Symbolic Modeling
* **`Joule heating for SMA wire.pdf`**: Establishes the governing electro-thermal differential equations, incorporating sensible heat storage, Joule heating inputs, and passive environmental convective dissipation.
* **`sma_pure_1d_switching.mat`**: MATLAB workspace data file containing the numerical datasets and lookup matrices extracted via First-Order Reversal Curves (FORC) to drive the feedforward control loops.

### 2. Trajectory Generation & Data Extraction
* **`StandAloneJouleHeatingSystem.slx`**: Isolated Simulink plant model used to verify baseline transient thermal responses. Implements a closed-loop PID controller regulating a 12V/6V PWM duty cycle against convective heat losses.

### 3. Dynamics & Identification
* **`FeedForwardControllerAndTheJouleHeatingSystem.slx`**: The fully integrated multi-physics system. Incorporates metallurgical latent heat of transformation enthalpy into the plant dynamics to model material buffering. Features a feedforward mapping loop that queries the FORC data arrays to convert curvature targets into explicit temperature targets, completely eliminating feedback loop phase confusion.
