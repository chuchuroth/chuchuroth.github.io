---
layout: post
title:  "Converter Control"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---


The following provides a comprehensive overview of converter control systems, drawing on the provided sources and excluding colloquial language:

### Converter Control Systems Overview

Converter control systems extend DC equivalent circuit models to include **converter dynamics**, allowing for the solution of AC models to determine important **converter transfer functions**. These transfer functions and models are then used to **design control systems for switching converters**. The primary objective of such control circuits is to **regulate an output voltage** (e.g., v(t) of a buck converter) or current (e.g., in grid-tied solar inverters or rectifiers) to a constant and well-controlled value.

Feedback control is essential because disturbances, such as **variations in input voltage (Vg)** and **changes in load current**, propagate through the converter, causing undesirable variations in the output. Additionally, **component tolerances** introduce uncertainties that affect the steady-state output voltage. Control systems automatically adjust the **duty cycle** to mitigate these effects, driving any error signal to zero and making the output accurately follow a reference.

Applications of control systems are nearly universal in power converters, including:
*   **DC-DC converters**: Regulating DC output voltage.
*   **DC to AC inverters**: Regulating AC output voltage to follow an AC reference signal.
*   **Grid-tied solar inverters**: Regulating output current injected into the grid.
*   **AC to DC rectifiers**: Regulating the current drawn from the AC power line to meet waveform quality requirements (e.g., sinusoidal and in-phase with voltage) and prevent harmonic pollution.

### Converter Modeling

**Modeling** is the representation of a system's physical behavior through mathematical means. Models are approximations, aiming for simplicity while adequately describing essential phenomena and ignoring unimportant details. **AC equivalent circuit models** are crucial for designing control systems, enabling **worst-case analysis** to ensure circuit performance under extreme conditions of applied signals and component tolerances. High-quality design requires models for both steady-state performance (efficiency, losses, voltage regulation) and AC control system design (stability, transient response). Simulations and laboratory prototypes are used to refine models to accurately predict observed behavior and worst-case performance.

The modeling process for converter control systems involves:
*   **Extension of Steady-State Models**: Existing DC equivalent circuit models are extended to include **dynamic elements** such as inductors and capacitors.
*   **Prediction of AC Variations**: Models must predict how AC variations in inputs (e.g., input voltage, load, duty cycle) affect the output voltage under transient conditions, effectively determining small-signal transfer functions.

### Modeling Principles: Averaging and Linearization

**1. Waveform Complexity and Simplification:**
Switching converters exhibit complex waveforms with various frequency components, including:
*   **Switching harmonics**: Components at the switching frequency and its multiples.
*   **Low-frequency variations**: Underlying average variations caused by control signal modulation.
*   **Harmonics of modulation frequency**: Generated due to the non-linear nature of the converter power stage.
*   **Modulation sidebands**: Components around the switching frequency and its harmonics.

To simplify the model and enable transfer function analysis, two key approximations are applied:
*   **Averaging**: This process removes the switching ripple and switching harmonics, preserving only the underlying low-frequency components. It is a generalization of how DC components are calculated, involving a **moving average** of the waveform over one switching period. Averaging effectively acts as a low-pass filter, passing low-frequency components unchanged while attenuating or removing higher frequencies, including switching harmonics.
    *   The core principle of averaging allows the equations for inductors and capacitors to be written as: $L \frac{d\langle i_L \rangle}{dt} = \langle v_L \rangle$ and $C \frac{d\langle v_C \rangle}{dt} = \langle i_C \rangle$, where angle brackets denote averaged values. These averaged equations are extensions of the familiar **volt-second balance** and **charge balance** equations, which are recovered when derivatives are zero (steady-state DC conditions).
*   **Linearization (Small-Signal Model)**: After averaging, the equations of the converter are often **non-linear**, involving products of time-varying quantities (e.g., duty cycle multiplied by output voltage). To apply Laplace transforms and derive transfer functions, these non-linear equations must be **linearized**.
    *   This is achieved by constructing a **small-signal model about a quiescent operating point**. This method is analogous to modeling non-linear elements like transistors in electronics.
    *   The process involves expressing each time-varying quantity (e.g., input voltage, duty cycle, inductor current, output voltage) as a sum of its **DC or quiescent value** (capital letters) and a **small AC perturbation** (hat quantities).
    *   When these perturbed expressions are substituted into the non-linear averaged equations, terms are categorized into:
        *   **DC terms**: Products of DC quantities, which sum to zero by volt-second and charge balance in steady state.
        *   **First-order linear AC terms**: Products of one hat quantity and one DC quantity; these are retained.
        *   **Second-order (non-linear) terms**: Products of two hat quantities; these are neglected due to the "small-signal approximation" (a small number multiplied by another small number is considered very small).
    *   The resulting equations are **linear differential equations** in terms of the hat quantities, with DC quantities treated as known constants. This process allows for the construction of small-signal linear AC models.
*   **State Space Averaging**: The methods described for deriving averaged AC equations are fundamentally equivalent to **State Space Averaging**, a formal approach that uses state-space descriptions (vector and matrix form) to systematically derive converter models.

### AC Equivalent Circuit Models

From the linearized small-signal AC equations, an **equivalent circuit model** can be constructed. This process is similar to creating DC equivalent circuits, but it uses hat quantities as signals and treats capital values as constants. **Dependent sources** in the linearized equations are represented as **effective transformers** (sometimes denoted with an AC squiggle to indicate the small-signal AC model) and **d-hat sources** (independent sources representing duty cycle variations).

**Canonical circuit models** represent the general form of all PWM continuous conduction mode DC-DC converter models, containing common features:
*   **DC transformers**: Represent ideal voltage/current transformation.
*   **Low-pass filter**: Composed of inductors and capacitors, it filters ripple and AC variations.
*   **Control sources**: Dependent on duty cycle variations (d-hat), typically represented as a voltage source (E of S d-hat) and a current source (J of S d-hat). All independent sources (Vg variations and d-hat sources) are pushed to the input side of the model for canonical form.

Examples of basic converter AC models:
*   **Buck converter**: Contains a buck-type transformer and d-hat sources in the output LC filter.
*   **Boost converter**: Features an inductor on the input side, a boost-type transformer, and d-hat sources.
*   **Buck-boost converter**: Includes both buck and boost transformers, similar to its DC model, with three d-hat sources.

### Pulse-Width Modulator (PWM) Modeling

The **pulse-width modulator** is a circuit that converts an analog control signal (Vc) into a switched waveform (gate drive signal) whose **duty cycle (D) is proportional to Vc**.
A common implementation involves:
*   A **sawtooth wave generator** (ramp generator) which produces a periodic signal with a period equal to the switching period, setting the converter's switching frequency.
*   An **analog comparator** that compares the sawtooth wave with the control input (Vc). The comparator's output is high when the sawtooth is less than Vc and low otherwise, thus generating the switched waveform with the desired duty cycle.
The relationship is typically **D = Vc / Vm**, where Vm is the peak amplitude of the sawtooth.
For small-signal modeling, this relationship linearizes to **d-hat = Vc-hat / Vm**, meaning the PWM acts as a **simple gain block of 1/Vm**.
The PWM inherently **samples** the control signal, producing one duty cycle value per switching period. This sampling restricts the bandwidth of the control system to be sufficiently less than the Nyquist rate (half the switching frequency) to avoid aliasing and ensure accurate models.

### Transfer Functions and Bode Plots

**Transfer functions** predict system behavior in the frequency domain, and **Bode plots** are graphical representations of these frequency responses.
**Design-oriented analysis** is an approach that simplifies the complexity of real systems by:
*   **Avoiding extensive algebra**: Instead, it focuses on obtaining physical insight and simple, invertible equations.
*   **Making engineering approximations**: Recognizing that models are inherently approximate, simple approximations are preferred for quick insights, and are refined only as necessary.
*   **Normalized forms**: Writing transfer functions in normalized forms exposes salient features and allows for the derivation of sub-equations for design parameters.
*   **Graphical construction**: Constructing Bode plots by inspection or by combining asymptotes of individual components simplifies analysis and provides physical insight.

**Bode Plot Fundamentals**:
*   A Bode plot consists of two graphs: **magnitude (in decibels)** versus frequency, and **phase (in degrees)** versus frequency, both on logarithmic scales.
*   **Decibels (dB)**: Magnitude in dB is calculated as 20 * log10(magnitude). A factor of 10 corresponds to 20 dB, and a factor of 2 corresponds to approximately 6 dB.
*   **Slopes**: Functions that vary as frequency to some power (f^n) appear as straight lines on a Bode plot with a slope of 20n dB per decade.

**Standard Forms for Transfer Functions**:
*   **Single Pole**: A term of the form 1/(1 + s/ω₀).
    *   Magnitude asymptotes: 0 dB at low frequencies (ω << ω₀) and -20 dB/decade slope at high frequencies (ω >> ω₀). The exact curve is -3 dB down at the corner frequency (ω₀).
    *   Phase asymptotes: 0 degrees at low frequencies, -90 degrees at high frequencies, with a -45 degrees/decade slope over two decades centered at ω₀.
*   **Single Zero**: A term of the form (1 + s/ω₀).
    *   Magnitude asymptotes: Similar to a pole but with opposite slopes (+20 dB/decade at high frequencies).
    *   Phase asymptotes: Similar to a pole but with opposite signs (+90 degrees at high frequencies, +45 degrees/decade slope).
*   **Right Half-Plane (RHP) Zero**: A term of the form (1 - s/ω₀).
    *   **Magnitude**: Behaves identically to a conventional (left half-plane) zero.
    *   **Phase**: Has an additional minus sign, causing its phase to resemble a pole (i.e., it introduces phase lag, similar to a pole, even though its magnitude increases like a zero).
    *   **Impact**: RHP zeros cause an initial response in the "wrong direction" (e.g., output voltage dips when commanded to rise) before eventually correcting. This "non-minimum phase" behavior makes converters difficult to control and can lead to instability if the feedback loop is too fast. Boost and buck-boost converters exhibit RHP zeros due to how inductor current is delivered to the output during switching.
*   **Inverted Pole/Zero**: Terms of the form (1 + ω₀/s) for an inverted pole and (1 + ω₀/s)^-1 for an inverted zero. These are algebraically equivalent to standard forms but emphasize high-frequency gain and low-frequency roll-off.
*   **Combining Terms**: When multiplying transfer functions, their magnitudes (in dB) are added, and their phases are added. This allows complex transfer functions to be built by summing the asymptotes of individual poles and zeros.
*   **Second-Order Systems**: A common form is 1 / (1 + s/(Qω₀) + s^2/ω₀^2).
    *   Magnitude asymptotes: 0 dB at low frequencies and -40 dB/decade slope at high frequencies.
    *   **Q-factor (Quality Factor)**: Determines the deviation from the asymptotes at the corner frequency (ω₀). A high Q (Q > 0.5) indicates complex poles and **resonance**, where the magnitude can peak significantly at ω₀. Q is defined as 2π times the peak stored energy divided by the energy dissipated per cycle.
    *   Phase asymptotes: 0 degrees at low frequencies, -180 degrees at high frequencies. The slope of the phase change at ω₀ depends on Q: higher Q leads to a sharper, more abrupt phase change.
*   **Low-Q Approximation (for Real Poles)**: When Q < 0.5, the second-order system has two distinct **real poles**. These poles can be approximated as ω₁ ≈ Qω₀ (low-frequency pole) and ω₂ ≈ ω₀/Q (high-frequency pole), providing simpler, more insightful expressions than the quadratic formula.
*   **Higher-Order Polynomial Factorization**: For polynomials of order n, approximate factorization into well-separated real roots (poles or zeros) can be achieved by relating coefficients (A₁, A₂, ...) to the roots (τ₁, τ₂, ...). This method provides simple analytical expressions for the roots when they are well-separated. Special cases exist for roots that are close together, requiring them to be left in quadratic form.

**Graphical Construction of Impedances and Transfer Functions**:
*   **Impedances**: Bode plots of series and parallel impedance combinations can be constructed graphically by taking the largest (for series) or smallest (for parallel) individual impedance asymptotes at any given frequency. This method also helps identify which impedances are dominant or negligible.
*   **Transfer Functions**: A transfer function can be expressed as a ratio of impedances (e.g., a voltage divider Z₂/(Z₁ + Z₂)). Graphical division of impedances involves subtracting their dB magnitudes and phases. The Q factor of the transfer function is determined by the ratio of impedances at the corner frequency. This method can also show how changes in operating point (e.g., duty cycle) affect the converter's transfer function parameters (e.g., corner frequency, Q factor).

### Controller Design (Feedback System Analysis)

**Objectives of Feedback Control**:
*   **Regulation**: Ensure output stability despite input voltage variations (Vg-hat) and load current variations (i_load-hat). This implies minimizing disturbance transfer functions (e.g., Gvg-hat and Zout).
*   **Reference Tracking**: Make the output accurately follow a reference signal (Vref) and be insensitive to component variations in the forward path of the feedback loop.
*   **Transient Response**: Achieve a desired response time and limit overshoot and ringing, which requires an adequate crossover frequency and phase margin.

**Negative Feedback System Structure**:
A typical negative feedback system consists of:
*   **Sensor (H(s))**: Measures the output voltage and provides a proportional signal (h * V).
*   **Reference (Vref)**: A well-controlled, accurate signal representing the desired output.
*   **Summing Node**: Generates an **error signal (Ve)** by subtracting the sensed output from the reference. The objective is to drive this error to zero.
*   **Compensator (Gc(s))**: Processes the error signal to produce a control signal (Vc). The compensator's **gain determines the error signal magnitude**: a larger compensator gain results in a smaller error signal and better regulation.
*   **Pulse-Width Modulator (PWM)**: Converts Vc into the duty cycle (D) for the switching converter.

**Closed-Loop Transfer Functions and Loop Gain (T(s))**:
The overall behavior of a closed-loop system is governed by quantities such as **T/(1+T)** and **1/(1+T)**, where **T(s) is the loop gain**. The loop gain is the product of all gains around the feedback loop (Gc * (1/Vm) * Gvd * H).
**Effects of Feedback**:
*   **Disturbance Reduction**: Feedback reduces disturbance transfer functions (e.g., line-to-output transfer function, output impedance) by a factor of **1/(1+T)**. A large loop gain (T) significantly attenuates disturbances at low frequencies.
*   **Reference Tracking**: The transfer function from the reference to the output becomes approximately **1/H** when the loop gain (T) is large. This makes the output voltage highly dependent on the accurate reference and sensor gain, and insensitive to variations in the forward path (compensator, PWM, converter power stage).

**Stability Analysis**:
*   **Pole Movement**: Closing a feedback loop moves the system's poles. This can improve bandwidth but can also move poles to undesirable locations, such as the **right half of the complex plane**, leading to **unstable responses** (growing oscillations).
*   **Phase Margin Test**: This test determines the stability of the closed-loop system by evaluating the loop gain (T) Bode plot.
    *   **Crossover Frequency (fc)**: The frequency where the magnitude of T(s) is 1 (0 dB).
    *   **Phase Margin (PM)**: The phase of T(s) at the crossover frequency, plus 180 degrees (PM = ∠T(jω_c) + 180°).
    *   **Stability Criterion**: A **positive phase margin indicates a stable feedback system**. This test generally applies to open-loop stable systems with a single crossover frequency.
*   **Phase Margin and Closed-Loop Q Factor**: The **phase margin is directly related to the Q factor of the closed-loop poles** that appear near the crossover frequency. A **larger phase margin corresponds to a lower Q factor**, resulting in:
    *   Less **overshoot and ringing** in the transient response.
    *   **Critically damped (Q=0.5)** response (fastest with no overshoot), requiring a phase margin of approximately 76 degrees.
    *   **Underdamped (Q>0.5)** response (faster but with overshoot and ringing), requiring less phase margin.
    *   **Overdamped (Q<0.5)** response (slower, no overshoot).
The required phase margin depends on the application's tolerance for overshoot and ringing.

**Compensator Design**:
Compensators (often implemented with op-amp circuits) are used to **shape the loop gain** to meet stability, transient response, and disturbance rejection requirements.
*   **Lead Compensator (PD - Proportional-Derivative)**:
    *   **Objective**: Primarily to **improve phase margin**.
    *   **Mechanism**: Adds a **zero** to the loop gain, which introduces **positive phase lead**. A high-frequency **pole** is typically added for practicality, to limit high-frequency gain.
    *   **Design**: The zero and pole frequencies are chosen to be symmetrically spaced around the desired crossover frequency (fc), maximizing the phase lead at fc.
*   **Lag Compensator (PI - Proportional-Integral)**:
    *   **Objective**: Primarily to **increase low-frequency loop gain** for better regulation and disturbance rejection.
    *   **Mechanism**: Introduces an **integrator** term (1/s or an inverted zero) which significantly boosts gain at low frequencies.
    *   **Design**: The inverted zero is placed at a frequency sufficiently below the crossover frequency to avoid significantly reducing the phase margin.
*   **PID Compensator (Proportional-Integral-Derivative)**:
    *   **Combination**: Combines features of both lead and lag compensators, using an inverted zero for low-frequency gain boost and a zero-pole pair for phase margin improvement.
    *   **Design Approach**: Typically involves designing the PD part first for phase margin, then adding the PI part for low-frequency gain enhancement.

**Op-Amp Compensator Circuit Realization**:
Compensators are commonly realized using **operational amplifier (op-amp) circuits** with feedback impedances.
*   A **voltage divider** is often used for the sensor (H).
*   A **subtractor circuit** (e.g., using an op-amp with input and feedback impedances) can implement the compensator's gain and transfer function.
*   **Resistor and capacitor networks** are used for the input (Z1) and feedback (Z2) impedances to create the desired poles and zeros.
*   **Element value selection**: With more variables than design equations, one element value can be chosen arbitrarily to set impedance levels for reasonable power dissipation and noise susceptibility (e.g., tens to hundreds of k-ohms).
*   **Practical considerations**: Interactions between the voltage divider and op-amp input impedance need to be accounted for. The **op-amp's gain-bandwidth product** is a critical limitation, as real op-amps cannot provide infinite gain at high frequencies. The op-amp's bandwidth can introduce additional poles that affect the overall loop's phase margin.
