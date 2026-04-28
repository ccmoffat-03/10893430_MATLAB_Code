# 10893430_MATLAB_Code
1. Project Overview

The model captures the interaction between:
- EO phase modulation of a continuous-wave optical carrier,
- wavelength-selective microring resonance filtering,
- coupling-dependent power transfer,
- thermal tuning of resonant wavelengths,
- and system-level feasibility constraints for multi-channel operation.

The simulation is implemented as a self-contained script to reflect a holistic system modelling approach.
-------------------------------------------------------------------------------------------------------------------------------------------------------------------
2. System Description

The model represents a complete photonic signal chain:

THz Signal > EO Phase Modulator > Optical Sideband Generation > Microring Resonator > Spectral Filtering > Design Feasibility Selection

The system performs:
- continuous spectral simulation,
- discrete resonance analysis,
- optimisation-based selection of viable resonator configurations.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

3. How to Run the Simulation

Requirements:
- MATLAB R2022a or later
- Signal Processing Toolbox

Execution
Load file in MATLAB, ensuring all packages are installed, and run. No preprocessing, compilation, or external dependencies are required. All figures and results are generated during runtime.

------------------------------------------------------------------------------------------------------------------------------------------------------------------

4. Input Design Parameters

All system behaviour is controlled at the top of the script.

4.1 Electro-Optic Modulation Parameters
freqs > THz frequencies to be modulated (define sidebands in THz)

Determining:
-number and spacing of generated optical sidebands


4.2 Microring Geometry
R > microring radius
W, H > waveguide cross-sectional dimensions

Determining:
-free spectral range (FSR),
-resonance density across wavelength,
-optical mode confinement.



4.3 Coupling Parameters
gap_single > waveguide-to-ring separation distance
gamma > evanescent field decay constant
k0 > maximum coupling coefficient

Determining:
-coupling regime (undercoupled / critically coupled / overcoupled),
-resonance linewidth,
-drop-port efficiency



4.4 Thermal Tuning Parameters
dn_dT > thermo-optic coefficient of waveguide material
DeltaT > applied temperature change

Determining:
-resonance wavelength shift,
-acceptable tuning range of the device,



4.5 Simulation Resolution Parameters
fs > sampling rate
lambda > wavelength resolution grid
T > simulation total time window

Determining:
-numerical resolution of EO modulation,
-spectral accuracy of resonator response,
-computational cost.


-------------------------------------------------------------------------------------------------------------------------------------------------------------------

5. Physical and Mathematical Model

5.1 EO Phase Modulation

The optical carrier is phase-modulated using multiple THz frequencies, producing a multi-sideband optical spectrum. Each tone contributes sinusoidal phase variation to the optical field.



5.2 Microring Resonator Model

The resonator is modelled using coupled-mode theory, including:
-round-trip phase accumulation,
-wavelength-dependent propagation loss,
-coupling coefficients.

Resonance occurs when constructive interference satisfies the phase condition.



5.3 Coupling Model

Waveguide-to-ring coupling is modelled using an exponential decay function of gap separation, representing evanescent field overlap.



5.4 Thermal Effects

Thermal tuning is modelled via a linear thermo-optic coefficient applied to the effective refractive index, resulting in a wavelength shift of resonance conditions.



5.5 Selection Algorithm

A constraint-based optimisation routine evaluates candidate resonator configurations and selects feasible designs based on:
-fabrication tolerances (ring radius quantisation),
-thermal tuning limits,
-resonance alignment accuracy,
-spectral separation constraints between channels

-------------------------------------------------------------------------------------------------------------------------------------------------------------------


6. Outputs Generated

The simulation produces:
-EO optical sideband spectrum
-Through-port microring transmission
-Drop-port resonance response
-Coupling gap vs wavelength heatmap
-Thermal resonance shift characteristics
-Sideband-localised spectral windows
-Final selected device configuration table


-------------------------------------------------------------------------------------------------------------------------------------------------------------------

7. Assumptions and Limitations

The model is based on the following assumptions:
-linear EO phase modulation (no nonlinear optical effects),
-ideal sinusoidal RF excitation,
-simplified exponential coupling model,
-linear thermo-optic response,
-no fabrication disorder or stochastic variability,
-high-resolution wavelength sampling approximates continuous behaviour.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------
8. Known Limitations
-computational cost increases significantly with spectral resolution,
-discretisation effects may exclude marginally feasible designs,
-coupling model is phenomenological rather than full electromagnetic simulation,
-no noise sources included in optical or RF domains.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------
9. Future Improvements
-incorporation of nonlinear optical effects (Kerr, TPA),
-FDTD-calibrated coupling model,
-Monte Carlo fabrication variability analysis,
-computational optimisation via vectorisation or GPU acceleration.
