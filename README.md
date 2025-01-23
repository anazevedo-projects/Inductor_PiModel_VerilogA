This project implements a Pi-model for an integrated inductor in Verilog-A. The Pi-model accurately represents the inductor's electrical characteristics, including parasitics such as series resistance, substrate resistance, and capacitances. It is designed for high-frequency applications and provides insights into the inductor's behavior in analog and RF circuit simulations.

Key Features of the Model:

The Verilog-A implementation defines the integrated inductor using parameters that represent both physical and material properties, including:

- Inductance (Ls): Calculated based on the geometry, number of turns, and shape of the inductor.
- Series Resistance (Rs): Accounts for resistive losses, modeled with frequency-dependent skin effect.
- Substrate Capacitance (Csi) and Substrate Resistance (Rsi): Represent the coupling and losses through the substrate.
- Oxide Capacitance (Cox): Models the capacitance between the inductor and the underlying oxide layer.
- Capacitance (Cs): Accounts for other parasitic capacitances in the structure.

Description of the Code:

- The inputs and outputs of the inductor are defined as ports (`port1`, `port2`) and intermediate electrical nodes (`n1`, `n2`) for Pi-model elements.
- The model calculates all key parameters using functions (getLs, get_rs, get_cs, get_csi, get_rsi) that take into account the geometry (e.g., number of sides, number of turns, width, spacing, and diameter).
- The analog block implements the relationships between currents and voltages for each branch in the Pi-model using Verilog-A's `analog` constructs.
- Fundamental circuit laws such as Ohm's law, voltage-current relationships for capacitors and inductors, and geometric considerations are used to describe the inductor’s electrical behaviour.

Key Parameter Highlights:

- Geometry-dependent values: The inductance, resistance, and capacitances are dynamically calculated based on physical dimensions such as the width (W), spacing (S), number of turns (n), and outer diameter (dOut).
- Frequency dependency: Skin effect is included in the calculation of the effective series resistance, which increases at higher frequencies.
- Material properties: Dielectric constants, substrate resistivity, and oxide thickness are incorporated into the capacitance and resistance calculations.

Validation:

The model was validated by applying a sinusoidal current to the inductor and performing AC simulations over a frequency range of 1 kHz to 100 GHz. Outputs included:

- Inductance (Imaginary part of impedance)
- Resistance (Real part of impedance)
- Quality factor (Q-factor)
