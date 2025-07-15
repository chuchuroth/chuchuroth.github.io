---
layout: post
title:  "Sensor Circuit Design module 4"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---

Here is the knowledge-based information extracted from the sources, with colloquial language removed and key concepts highlighted:

**I. Amplifiers: Theory and Characteristics**

*   Module four focuses on **amplifiers**, including the **ideal operational amplifier (op amp)** and its characteristics, how to build various types of amplifiers using resistive networks, and their respective gain equations.
*   **Amplification is critical** for sensor system design, as it helps achieve **high accuracy, low noise, and low drift**.
*   All sensors require amplification.
*   Sensor systems incorporate **complex analog front-end circuitry** to handle low-amplitude and nonlinear signals, such as the 5 to 20 millivolt, nonlinear outputs of thermocouples. Filtering sensor signals before the Analog-to-Digital Converter (ADC) is more challenging than digital control for sensored actuators.
*   Gaining expertise in amplifiers is essential for mastering the field of sensors.

**A. Ideal vs. Real Amplifiers**
The assumptions behind ideal amplifiers are highly theoretical, and real amplifiers exhibit several deviations:

*   **Open Loop Gain**: In ideal op amps, open loop gain is infinite. In real op amps, **open loop gains are finite**, and a closed-loop configuration reduces gain to a practical level.
*   **Input Impedance**: Ideal op amps have infinite input impedance. Real op amps have **finite input impedance**, allowing small currents to flow through input ports. This results in **input bias current**.
*   **Output at Equal Inputs**: For an ideal op amp, equal inputs produce zero output. In real op amps, equal inputs cause saturation, and an **offset voltage** is required to bring the output to zero.
*   **Output Response Time**: Ideal op amps change output instantaneously. Real op amps' output changes at a finite **slew rate**, meaning the output ramps up to its new level, causing a delay (e.g., 5 to 10 microseconds).
*   **Bandwidth**: Ideal op amps have infinite bandwidth. Real op amps have **finite bandwidth** with cutoff frequencies typically ranging from 10 kilohertz to 1 megahertz, depending on intended gain.

**B. General Operational Amplifier Characteristics**
*   An op amp has **two high-impedance inputs**: an inverting input (V1) and a non-inverting input (V2).
*   The **output (V0)** has very low impedance.
*   The **output voltage (V0)** is equal to the **gain multiplied by the difference between the input voltages** (V0 = Gain × (V2 - V1)). This feature is used in all closed-loop configurations.
*   An **external supply voltage** is necessary to power the amplifier.
*   The name "operational amplifier" stems from their use with resistor and capacitor networks between output and input terminals, which create unique operational features.

**II. Common Amplifier Configurations**

The following amplifier configurations are built using resistive networks:

*   **Inverting Amplifier**:
    *   Assumes current cannot flow into the input terminals.
    *   The non-inverting input is connected to ground, making the inverting input a **virtual earth**.
    *   The gain is calculated as **-R2 / R1**.
    *   The output is inverted relative to the input.
    *   Gain is adjusted by varying the ratio of resistors.
*   **Non-Inverting Amplifier**:
    *   Assumes current cannot flow into the input terminals.
    *   Both input terminals are at potential V1 (input voltage).
    *   Resistor R1 is connected to ground.
    *   The gain is calculated as **1 + R2 / R1**.
    *   Gain is adjusted by varying the ratio of resistors.
*   **Summing Amplifier**:
    *   Functions as the sum of a series of inverting amplifiers.
    *   Uses the **principle of superposition** to calculate gain, summing the individual components of V_out from each input algebraically.
    *   Offers a wide variety of gains using standard resistor values compared to a single voltage input configuration.
    *   Inverting, non-inverting, and summing amplifiers typically apply only one external voltage to their inputs.
*   **Differential Amplifier**:
    *   Applies external voltage to both inputs, making it suitable for amplifying sensor signals.
    *   Calculates gain using the **principle of superposition**.
    *   Simplified gain equation (assuming R3=R1 and R2=R4): **V_out = (R4 / R3) × (V1 - V2)**.
    *   The output is directly proportional to the difference between the two external input voltages.
    *   Thermocouple sensor signals, which have small differential voltages (5-20 millivolts), require a differential amplifier for accurate readings.
*   **Instrumentation Amplifier (IA)**:
    *   A specialized form of differential amplifier with **buffered inputs** (two op amps).
    *   Specifically designed for sensor inputs due to its **variable high gain, high input impedance, low input offset drift, and high common mode rejection**.
    *   Commonly used to amplify **small differential signals** from devices like thermocouples, strain gauges, and current sensors in motor control.
    *   Pinouts are configured for sensor signals.
    *   **Design**: Inputs V1 and V2 are fed into two operational amplifiers (A1, A2). A resistance network (R1, R2) configures them as inverting amplifiers. The outputs of these buffering amplifiers are then fed into a differential amplifier (A3).
    *   **R1** often serves as a **variable gain resistor (R_G)**, allowing gains from 1 to 1,000 in commercial IAs.
    *   The gain equation for an instrumentation amplifier is **Gain = (R4 / R3) × (R1 + 2R2) / R1**. The circuit designer adjusts R1 to achieve the desired gain.
    *   **Example: AD8422 Instrumentation Amplifier**:
        *   R1 is denoted as R_G.
        *   Features **high common mode rejection ratio (CMRR)** to prevent common-mode noise from appearing in the output.
        *   Possesses a very **small input offset voltage** for high accuracy.
        *   Exhibits **low noise distortion**, crucial for low-voltage sensor signals.
        *   Pinouts: +IN (V2), -IN (V1) for sensor leads, R_G (R1) for gain setting, +V_s and -V_s for power, V_out for the amplified signal. V_REF can be used for output voltage level shifting. In this chip, R4 is set equal to R3, and R2 to 9.9 kOhms.

**III. Amplifier Imperfections and Parameters**

Understanding amplifier imperfections is crucial for interpreting manufacturer spec sheets.

1.  **Input Offset Voltage (V_OS)**:
    *   The voltage required to bring a real op amp's output to zero when its inputs are exactly equal (as real op amps saturate under these conditions).
    *   Modeled as a voltage source in series with ground for a non-inverting amplifier.
    *   **A small V_OS is desirable** because it gets multiplied by the amplifier's gain, directly contributing to error in the amplified signal. This is especially significant for sensors like thermocouples and strain gauges that require high gains.
    *   V_OS has a base value at 25°C and **increases with temperature variations** from 25°C.
    *   **Instrumentation amplifiers** like the AD8422 have very small input offset voltages, making them suitable for high-accuracy sensor readings.
    *   Minimizing error due to input offset voltage is a primary reason to choose an instrumentation amplifier for commercial sensor circuits.

2.  **Input Bias Current (I_B)**:
    *   Tiny leakage currents that flow across the input terminals of real op amps due to their finite input impedance and internal transistors.
    *   **Causes a voltage drop across the input resistor network**; larger resistors lead to greater voltage drop.
    *   Specified in microamps.
    *   **A small I_B is desirable**. Instrumentation amplifiers like the AD8422 exhibit negligible input bias currents, leading to minimal voltage errors.
    *   Minimizing error due to input bias current is a secondary reason to choose an instrumentation amplifier for sensor applications.

3.  **Common Mode Rejection Ratio (CMRR)**:
    *   Measures a differential amplifier's ability to **reject common-mode signals** (identical, in-phase input signals) while amplifying differential signals.
    *   In real op amps, common-mode signals result in a small common mode gain in addition to the intended differential gain.
    *   **CMRR is defined as the differential mode gain divided by the common mode gain**, typically expressed in decibels: **CMRR (dB) = 20 * log10 (A_ol / A_cm)**.
    *   CMRR typically remains flat from DC up to a cutoff frequency, then degrades with increasing frequency.
    *   **Importance**: RF noise often appears as an offset on both sensor wire leads, constituting a common-mode signal. **A higher CMRR ensures that the amplifier primarily outputs the desired differential signal and less of the RF noise**.
    *   Instrumentation amplifiers, such as the AD8422, have high CMRR, which can vary with gain settings (smaller gain allows higher cutoff frequency, higher gain provides higher initial CMRR).
    *   Minimizing error due to poor common mode rejection is a third reason to choose an instrumentation amplifier for sensors.

**IV. Amplifier Frequency Response and Slew Rate**

*   **Open Loop Frequency Response**: Real op amps do not have infinite bandwidth. The **open loop gain** (output amplification without feedback) is roughly flat from DC to the -3 dB point, after which it drops linearly as frequency increases.
*   **Gain Bandwidth Product**: Defined as the product of gain and bandwidth. It remains constant if the frequency drop-off is linear. For variable gain devices like the AD8422, a smaller gain setting results in a higher frequency before reaching the -3 dB point.
*   **Frequency Compensation**: A design technique to prevent random oscillations at high frequencies, often caused by stray capacitances. It can involve substituting a high-pass filter for an internal amplifier stage, which reduces oscillations but also lowers the open loop gain.
*   **Slew Rate**:
    *   Defined as the **rate of change of the output voltage per unit time** in response to a step change in the input.
    *   Measured in **volts per microsecond**.
    *   Influenced by frequency compensation; capacitors used for compensation can reduce the slew rate.
    *   If a circuit is operated faster than its slew rate, the output signal will be distorted (e.g., a sine wave may become a triangular wave).
    *   To amplify an input signal of V0sin(2πft) without distortion, an op amp requires a **minimum slew rate of 2πfV0** (which is the maximum slope of the sine wave at its zero crossing). The LM358, for example, has a slew rate of 0.3 volts per microsecond.

**V. Sensor Noise**

*   **Sensor noise** is defined as the **random addition of meaningless data to the sensor signal**, originating from sources *inside* the circuit, such as amplifiers and ADCs. This contrasts with **interference**, which comes from *external* sources like high-voltage power lines. The solutions for noise and interference differ.
*   Noise is typically expressed as the **Signal-to-Noise Ratio (SNR)**: **SNR = 20 * log10 (V_signal / V_noise)**.
*   The noise contribution of op amps is characterized by a standard normal distribution with a mean of zero and a non-zero variance.
*   **Noise in an op amp depends on bandwidth**.
*   **Bandwidth** in analog terms is the range of frequencies a signal uses in a transmission device.
*   A **higher gain leads to lower bandwidth**.
*   It is crucial to avoid having more bandwidth in a system than is necessary for the sensor signal, as noise is directly related to bandwidth.

**VI. Types of Noise**

1.  **Johnson-Nyquist Noise (Thermal Noise)**:
    *   Generated by the **thermal agitation of charge carriers** within an electrical conductor at equilibrium, regardless of applied voltage or current.
    *   Modeled as **white noise**, meaning its power density is uniform across all frequencies.
    *   **Higher bandwidth allows more Johnson-Nyquist noise** into the system.
    *   Can be modeled as a noisy voltage source in series with a noiseless resistor.
    *   The **variance of this noise is 4 * k_B * T * R * Δf**, where k_B is Boltzmann's constant, T is absolute temperature in Kelvin, R is resistance in ohms, and Δf is bandwidth in Hertz.
    *   **Increases with both temperature and electrical resistance**.
    *   Maximum power transfer of this noise occurs when the Thevenin equivalent resistance of the rest of the circuit equals the noisy resistor's resistance.

2.  **One Over F Noise (Pink Noise)**:
    *   Its power density is **inversely proportional to frequency**.
    *   Each octave carries an equal amount of energy.
    *   Originates from **slow changes in the material properties** of conducting metals, magnetic metals, and semiconductors within electronic devices.
    *   Significant at frequencies under 1000 Hz, which can pose a problem for sensors with low frequency responses.
    *   The noise falls off at 3 dB per octave.

3.  **Shot Noise (Schottky Noise)**:
    *   Results from **random fluctuations in the flow of discrete electrons** within an otherwise constant DC current.
    *   Inherently small, as fluctuations occur one electron at a time.
    *   **Independent of temperature and frequency**.
    *   Expressed as an RMS current flow: **σ_I = sqrt(2 * q * I * Δf)**, where q is the charge of an electron, I is the DC current, and Δf is the bandwidth.
    *   Shot noise primarily dominates at **very low device temperatures combined with high frequencies**.

4.  **Quantization Noise**:
    *   Occurs during the **Analog-to-Digital Converter (ADC) conversion process** when an analog sensor signal is digitized.
    *   **Sampling** converts the signal into real numbers, and **quantization** approximates each real number with a digital value, introducing errors perceived as noise.
    *   **More digital levels (bits) in the ADC result in lower quantization noise**.
    *   Modeled as an additive, non-linear, random signal.
    *   For sawtooth or triangle waves, the noise is uniformly distributed between plus or minus half of the least significant bit (LSB).
    *   The **Signal-to-Noise Ratio (SNR)** for an ADC is given by **20 * log10 (2^Q)**, where Q is the number of bits. This simplifies to **6.021 * Q dB**. For sine wave quantization, an additional **1.761 dB** is added (total SNR = 6.021Q + 1.761 dB).
    *   **RMS noise increases with higher ADC conversion rates**.

**VII. Assessing and Reducing Sensor Noise**

*   **Total noise in a sensor circuit is additive via the RMS method**.
*   Noise contributions include Johnson and 1/f noise from amplifiers, Johnson noise from resistance, some shot noise from DC current, and quantization noise from ADCs.
*   Noise characteristics vary with temperature and frequency.
*   **Consulting component spec sheets** is advisable to identify potential noise sources before prototyping.
*   **Sensor noise negatively impacts both the accuracy and resolution** of a sensor system.
    *   **Resolution**: The smallest reliably detectable increment of signal change.
    *   **Accuracy**: The error between the sensor reading and the true value.
    *   Both are **inversely related to noise**.
*   Sensor vendors often use the RMS method for quoting accuracy because of its inverse relationship to noise.

**Steps to Reduce Sensor Noise**:

1.  Recognize that **hardware noise cannot be effectively filtered out in software** without compromising sensor response time, which is generally undesirable for performance expectations.
2.  **Analyze the circuit schematic** to calculate the relative orders of magnitude of different sensor noise sources.
3.  **Investigate source impedances** and identify the frequencies that may be contributing to noise observed in the prototype circuit.
4.  **Select an op amp that offers the lowest RMS noise** at the most common impedance levels in the circuit.
    *   For instance, amplifier voltage noise dominates at zero source impedance, Johnson noise in input resistance is significant at moderate impedances (e.g., 3000 Ohms), and shot/current noise through a resistor becomes the largest source at high impedances (e.g., 300,000 Ohms), especially at higher frequencies.
