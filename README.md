# Analysis and Reduction of EMI-Induced Timing Jitter in Voltage-to-Time Converters Using Differential Architectures

**B.Tech Project (BTP)**
**Department of Electrical Engineering, IIT Ropar**
**Guide:** Prof. Devarshi Mrinal Das
**Technology:** CMOS 180 nm
**Tool:** Cadence Virtuoso

## Overview

This project investigates the effect of **Electromagnetic Interference (EMI)** on CMOS **Voltage-to-Time Converters (VTCs)** and studies differential circuit architectures for reducing EMI-induced timing jitter.

A VTC converts an input voltage into a timing quantity through voltage-controlled delay elements. EMI coupled into the circuit can perturb the switching instants, resulting in phase- and frequency-dependent timing errors.

The project builds upon the VCDU/VTC analysis performed during the DEP and focuses on understanding the relationship between EMI, circuit operating conditions, and timing jitter.

## Objectives

* Establish a baseline VCDU/VTC implementation.
* Analyze PVT and Monte Carlo variations.
* Study EMI-induced timing jitter in VTCs.
* Investigate the limitations of single-ended architectures under EMI.
* Explore differential architectures for common-mode EMI rejection.
* Analyze the effect of EMI amplitude, frequency, and phase.
* Develop and evaluate a compressed differential-control architecture.
* Identify the operating conditions that limit EMI cancellation.

## Methodology

The project was implemented and analyzed using **Cadence Virtuoso**.

The major stages were:

1. Baseline VCDU/VTC implementation.
2. PVT and Monte Carlo characterization.
3. EMI injection into the VTC.
4. Frequency and phase sweeps.
5. Investigation of differential architectures.
6. Analysis of unsuccessful differential configurations.
7. Development of compressed differential control.
8. Evaluation of common-mode EMI cancellation.
9. Analysis of residual high-frequency timing jitter.

## Differential Architecture

The differential approach is based on the principle that EMI components coupled similarly into both branches can partially cancel when the differential timing response is evaluated.

For matched branches:

$$
V_{+}=V_{CM}+\frac{v_{id}}{2}+v_{cm}
$$

$$
V_{-}=V_{CM}-\frac{v_{id}}{2}+v_{cm}
$$

and ideally,

$$
V_{+}-V_{-}=v_{id}
$$

This cancellation depends strongly on branch matching, operating region, biasing, and the assumption that the disturbance is sufficiently common to both branches.

## Compressed Differential Control

A key architecture studied in the project maps the full input control range into a smaller differential swing around a common-mode voltage.

The implemented mapping was approximately:

$$
V_{CM}=0.9V
$$

$$
V_{+}=0.9+k(A-0.9)
$$

$$
V_{-}=0.9-k(A-0.9)
$$

with approximately:

$$
k\approx0.15
$$

This compressed control keeps the differential-pair devices closer to their intended operating region and improves the validity of common-mode cancellation.

## Key Observations

* EMI produces timing jitter that depends on its amplitude, frequency, and phase.
* Differential architectures can provide partial common-mode EMI cancellation when the two branches are sufficiently matched.
* Some direct differential approaches were found unsuitable because their delay response became nearly constant.
* Compressed differential control provided a more useful operating region for the differential architecture.
* Low-frequency and low-amplitude EMI showed partial cancellation.
* Residual timing jitter remained at higher EMI frequency and amplitude.
* The remaining error can be related to imperfect common-mode rejection, parasitic coupling, device mismatch, and frequency-dependent circuit behavior.

## Important Result

The project does **not** claim complete EMI immunity.

The final Cadence-based architecture demonstrated **partial EMI cancellation**, while frequency- and amplitude-dependent residual jitter remained.

This result highlights an important circuit-design trade-off: improving common-mode rejection requires maintaining appropriate biasing, matching, and small-signal operation across the relevant frequency range.

## Tools & Technologies

* Cadence Virtuoso
* CMOS 180 nm
* Analog/Mixed-Signal IC Design
* Voltage-Controlled Delay Units
* Voltage-to-Time Converters
* Differential Circuits
* PVT Analysis
* Monte Carlo Analysis
* EMI Injection
* Frequency/Phase Sweeps
* Timing Jitter Analysis

## Repository Contents

```text
.
├── README.md
├── schematics/
├── simulations/
├── results/
├── plots/
└── report/
```

The repository contains selected Cadence schematics, simulation configurations, results, plots, and project documentation.

## Relation to DEP

The DEP investigated **VCDU signal conditioning and lower-input-range linearization**.

The BTP builds on the same VCDU/VTC foundation and investigates a different problem:

```text
DEP
VCDU nonlinearity
        ↓
Signal conditioning
        ↓
Improved lower-range behavior

BTP
VTC baseline
        ↓
EMI injection
        ↓
Timing jitter
        ↓
Differential architecture
        ↓
Partial common-mode EMI cancellation
```

Together, the projects provide a broader study of **CMOS voltage-to-time circuits, their nonidealities, and circuit-level techniques for improving their behavior**.
