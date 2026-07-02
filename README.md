Click here and press view raw to download and view the simulation videos explaining the complete verification process:
* **`StandaloneJouleHeatingExplanation.mp4`**: A video walk-through demonstrating voltage parameter variations and analyzing the resulting thermal ramp rates and system time constants.
* **`TheFeedForwardControllerWithJouleheating.mp4`**: A video analysis outlining the dual-lag phenomenon, proving how feedforward mapping isolates physical hardware constraints from controller error confusion to ensure absolute loop stability.

# Joule-Heating-for-SMA-wire

An end-to-end electro-thermal modeling framework and feedforward control architecture to validate Joule heating dynamics in standalone and integrated Shape Memory Alloy (SMA) bending actuators. Built using MATLAB and Simulink.

## 🛠️ Pipeline & File Architecture

The repository is structured sequentially to take the system from a standalone thermodynamic plant to a verified, integrated multi-physics actuator tracking complex trajectories:

### 1. Subsystem Modeling & Documentation
* **`Joule heating for SMA wire.pdf`**: Establishes the governing electro-thermal differential equations, incorporating sensible heat storage, Joule heating inputs, and passive environmental convective dissipation.

### 2. Standalone Subsystem Validation
* **`jouleheating.slx`**: Isolated Simulink plant model used to verify baseline transient thermal responses. Implements a closed-loop PID controller regulating a 12V/6V PWM duty cycle against convective heat losses.

### 3. Full System Integration & Advanced Control
* **`FinalShapewithjouleheating.slx`**: The fully integrated multi-physics system. Incorporates metallurgical latent heat of transformation enthalpy into the plant dynamics to model material buffering. Features a feedforward lookup table that translates reference curvature trajectories into explicit temperature targets to eliminate feedback loop phase confusion.
