---
layout: post
title:  "Power Electronics"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---


The provided sources offer a comprehensive introduction to power electronics, covering foundational concepts, analytical techniques, specific converter types, and methods for modeling losses.

### **Introduction to Power Electronics Course Overview**

*   **Course Affiliation:** This course, "Introduction to Power Electronics," is taught by Professor Robert Erickson from the University of Colorado, Boulder, Department of Electrical, Computer and Energy Engineering. It is the first course in a specialization on power electronics and the initial course of a Graduate Certificate in power electronics. It also serves as a pathway specialization for admission into the Master of Science Degree (MS-EE) program.
*   **Course Numbering:** The for-credit version is ECEA 5700, and it covers the same technical material as the on-campus course ECEN 5797.
*   **Course Materials:** The course uses the textbook *Fundamentals of Power Electronics*, though purchasing it is optional as all necessary material is available in videos and PDF lecture slides.
*   **Prerequisites:** The course is taught at a **graduate level**, assuming fluency in **circuits and electronics** equivalent to a typical undergraduate electrical engineering degree.
*   **Specialization Pathway:**
    *   Course 1: Introduction to Power Electronics (ECEA 5700).
    *   Course 2: Converter Circuits (ECEA 5701) – prerequisite to Courses 3 and 4.
    *   Course 3: Control of Converters.
    *   Course 4: Design of Magnetics for Converters (ECEA 5704).
    *   The specialization aims to provide the **technical foundation to build power converters**.
*   **Graduate Certificate:** The Graduate Certificate in power electronics comprises this specialization, a follow-on control specialization, and a capstone design project that involves designing a power conversion system for a USB Type-C interface.
*   **MS-EE Admission:** Completion of the for-credit versions of the four specialization courses with a **grade point average of at least B or better** is part of a performance-based admission process to the MS-EE degree program.

### **Course Versions: For-Credit vs. Non-Credit**

*   **Non-Credit Version:**
    *   Requires payment of a Coursera fee.
    *   Awards a **Coursera certificate of completion** upon successful assignment completion.
    *   Is **continuously available**, allowing flexible start and stop times.
    *   Requires successfully passing all three homework assignments, with a typical passing threshold of **70%**.
*   **For-Credit Version:**
    *   Requires payment of **university tuition**.
    *   Awards **transcripted university credit** applicable towards the Graduate Certificate or MS-EE degree.
    *   Is **scheduled into eight-week sessions**, requiring completion within that period.
    *   Provides **access to exams** and **course facilitators (teaching assistants)** who hold remote office hours.
    *   Includes **examination preparation materials**, such as a practice exam.
*   **Shared Access:** Both versions provide access to the same lectures, homework assignments, supplementary materials, and discussion forums.
*   **Enrollment Flexibility:** Students can switch from the non-credit to the for-credit version at any time by paying university tuition; any completed homework is automatically transferred.
*   **Withdrawal Policy (For-Credit):**
    *   **Full tuition refund** for dropping within **14 days** of enrollment, with no course appearance on the university transcript.
    *   **No tuition refund** for withdrawing after 14 days; the course appears on the transcript with a **"W" (withdrawal) grade**, which does not impact GPA.
    *   Commitment to a grade occurs **once the exam is accessed**. Course grades are computed at the end of the eight-week session if not withdrawn.
*   **Grading:**
    *   Three homework assignments are auto-graded with unlimited attempts. Their weighting is 15%, 20%, and 15% respectively.
    *   The **proctored examination** is weighted **50%**. It is a closed-book, timed two-hour exam with unlimited submissions within the time limit, and the last submission counts for the final grade.
    *   In-video quizzes are for edification only and are not graded.

### **Core Concepts in Power Electronics**

*   **Definition:** Power electronics is the field concerned with the **processing and control of electrical power** using high-efficiency electronic circuits. It integrates elements from various electrical engineering sub-fields, including **analog circuits, electronic devices, control systems, feedback systems, power systems, magnetics design, electric machines, and numerical simulation**.
*   **Key Functional Element: Switching Converter**.
    *   Switching converters perform essential power processing functions.
    *   They typically have **two input terminals**: a power input and a **control input** that dictates power processing.
    *   **Common Functions:**
        *   **DC to DC Conversion:** Changing and potentially regulating the DC voltage (e.g., stepping up or down).
        *   **Rectification:** Converting AC to DC, with control over the DC output voltage and AC input current waveform.
        *   **Inversion:** Converting DC input to AC output with controllable frequency and magnitude.
        *   **AC to AC Cycloconversion:** Changing the frequency and amplitude of AC voltage.
    *   Converters are constructed with **electronic devices and reactive elements** (inductors, capacitors) with a focus on **very high efficiency**.
*   **High Efficiency is Essential:**
    *   **Energy Conservation:** To conserve energy.
    *   **Heat Management:** Low efficiency makes processing large amounts of power impractical and uneconomical due to excessive heat generation that converters cannot handle.
    *   **Efficiency Calculation:** Efficiency is the **ratio of output power to input power (Pout / Pin)**. Power loss is Pin - Pout.
    *   **Loss-Limited Design:** Higher efficiency allows for **smaller converter size** (due to reduced heat sinking requirements) or **greater output power** for the same amount of heat sinking. The goal is to achieve efficiencies approaching 100%.
*   **Control in Converters:** **Control is invariably required**, typically to regulate the output voltage, or control currents or other quantities. This can be achieved using **traditional analog feedback** or **sophisticated digital microcontrollers**.

### **Circuit Element Selection for High Efficiency**

*   **Contrast with Signal Processing:**
    *   In **signal processing**, magnetics are often avoided due to cost, integration difficulty, and design complexity. Resistors, capacitors, and linear/switched-mode semiconductors are common.
    *   In **power processing**, the objective is to **avoid elements that consume power**.
*   **Undesirable Elements (Power Consumption):**
    *   **Resistors:** Directly consume power.
    *   **Linear-Mode Transistors (e.g., Class A amplifiers):** Consume power because they operate with both voltage across and current through them simultaneously. Examples like the resistive voltage divider and series pass regulators demonstrate low efficiency (e.g., 50%) due to power dissipation.
*   **Desirable Elements (Energy Storage/Lossless):**
    *   **Capacitors and Magnetics (Inductors, Transformers):** These elements ideally **store energy** rather than consume power, and that energy can be recovered later.
    *   **Switched-Mode Transistors:** Operated as **on-off devices** (like ideal switches). When closed, there is ideally no voltage across them; when open, there is no current through them. In either ideal state, the power consumed (voltage × current) is zero, making them **lossless**.

### **Converter Analysis Techniques**

The course emphasizes **systematic approaches** to analyze switching converters:

*   **Simulation with LTspice:**
    *   LTspice is a **freely available circuit simulation program** for Windows and Macintosh.
    *   It allows users to enter a circuit schematic (e.g., a buck converter) and numerically calculate waveforms (e.g., transient analysis, frequency analysis).
    *   It can plot node voltages and element currents, and measure average and RMS values, enabling calculation of input/output powers and efficiency.
    *   Behavioral models for pulse width modulators and gate drivers are provided for course simulations.
*   **Steady-State Converter Analysis:**
    *   **Small Ripple Approximation (or Linear Ripple Approximation):**
        *   Assumes that the **ripple (AC variation) in continuous waveforms** (specifically **inductor currents and capacitor voltages**) is very small compared to their DC components in well-designed converters.
        *   This approximation allows replacing time-varying continuous waveforms with their DC components for simplified analysis, decoupling differential equations.
        *   It is **not applied to switched waveforms** (e.g., the switch output voltage) due to their discontinuous nature.
        *   This approximation simplifies the inductor current waveform to straight lines with constant slopes during switching intervals.
    *   **Inductor Volt-Second Balance:**
        *   **Principle:** In **steady state**, the **net change in inductor current over one complete switching period is zero**.
        *   **Application:** This implies that the **integral of the voltage across an inductor over one switching period must be zero** (the "volt-seconds" must balance). Equivalently, the **DC component (average value) of the voltage applied to the inductor is zero** in steady state.
        *   This principle is a fundamental method to **solve for the steady-state voltages** (e.g., output voltage) of any converter without Fourier analysis.
    *   **Capacitor Charge Balance (Amp-Second Balance):**
        *   **Principle:** In **steady state**, the **net change in capacitor voltage over one complete switching period is zero**.
        *   **Application:** This implies that the **integral of the current through a capacitor over one switching period must be zero** (the "amp-seconds" or charge must balance). Equivalently, the **DC component (average value) of the current through the capacitor is zero** in steady state.
        *   A continuous DC current into a capacitor would cause its voltage to continuously increase, preventing steady-state operation.
    *   **Component Value Selection:** These principles are used to derive equations that help **limit the amount of switching ripple** in inductor current and capacitor voltage, guiding the choice of inductance and capacitance values.

### **Specific Converter Examples and Analysis**

*   **Buck Converter:**
    *   A **step-down (buck) converter** that ideally reduces the input voltage.
    *   **Ideal Output Voltage:** **V = D * Vg**, where D is the duty cycle (fraction of time the switch is in position one).
    *   **Operation:** A switch rapidly alternates connection between the input voltage and ground. A low-pass LC filter smooths the switched waveform, allowing only the DC component to reach the load. The output voltage is adjustable by changing the duty cycle.
    *   **Output Ripple Calculation (Two-Pole Filter):** For output capacitors in two-pole LC filters, the small ripple approximation may not apply directly to the capacitor current as it primarily carries ripple. A common approximation is that **nearly all inductor current ripple flows through the capacitor**. The capacitor voltage ripple is then calculated from the integral of this triangular capacitor current waveform (area of the triangle).
*   **Boost Converter:**
    *   A converter that **increases (boosts) the voltage**.
    *   **Ideal Output Voltage:** **V = Vg / (1 - D)** or **V = Vg / D'**, where D' is (1-D).
    *   **Realization:** A power MOSFET and a freewheeling diode are often used to realize the switch. When the MOSFET turns off, the diode is forward biased by the inductor voltage, providing a path for inductor current.
    *   The ideal conversion ratio approaches infinity as D approaches one, but in practical converters, losses limit the maximum voltage.
*   **Buck-Boost Converter:** Can **invert the polarity** of the voltage and either increase or decrease its magnitude.
*   **Cuk Converter:** A higher-order converter with **two inductors and two capacitors**. Analysis requires applying **volt-second balance to each inductor** and **charge balance to each capacitor**, resulting in a system of four equations to solve for the two capacitor DC voltages and two inductor DC currents. It exhibits an **inverting buck-boost characteristic**.

### **Equivalent Circuit Modeling of Converters**

*   **Purpose:** To model the **important low-frequency (DC) components** of voltages and currents, provide insight into converter function, and **model losses and efficiency**. These are time-invariant models that simplify analysis.
*   **Ideal DC-DC Converter Properties:**
    *   **100% Efficiency:** Input power (Vg * Ig) equals output power (V * I). This holds in steady state, where reactive elements have no net energy change.
    *   **Voltage Conversion:** Output voltage (V) is the conversion ratio (M, a function of duty cycle D) multiplied by the input voltage (Vg): **V = M(D) * Vg**.
    *   **Current Conversion:** Input current (Ig) is the conversion ratio (M) multiplied by the output current (I): **Ig = M(D) * I**.
*   **Modeling Approaches:**
    *   **Dependent Sources:** The relationships can be modeled using a dependent voltage source (V = M * Vg) and a dependent current source (Ig = M * I). This approach is often used in circuit simulators like SPICE.
    *   **Ideal DC Transformer:** The ideal converter equations are analogous to those of an ideal transformer. A "DC transformer" symbol (with a straight line through it) represents this function. The turns ratio is equivalent to the conversion ratio M, relating voltages and currents with appropriate polarity. The turns ratio is a function of the duty cycle M(D).
*   **Circuit Manipulation with Ideal Transformers:** Elements can be "reflected" across a transformer to simplify analysis.
    *   **Voltage Source:** Multiplied by (n2/n1).
    *   **Current Source:** Divided by (n2/n1).
    *   **Impedance (Z):** Multiplied by (n2/n1)^2 * Z.
        *   Resistor (R): R * (n2/n1)^2.
        *   Inductor (L): L * (n2/n1)^2.
        *   Capacitor (C): C / (n2/n1)^2 or C * (n1/n2)^2.
    *   Polarity of voltage sources may reverse if transformer dots are reversed. Impedances are unaffected by dot reversal.

### **Modeling Losses in Converters**

*   **General Approach:** Losses are modeled by adding elements to the equivalent circuit. Volt-second balance is applied to the **ideal part of the inductor model**, and charge balance to the **ideal part of the capacitor model**. The resulting equations form the loop and node equations of the equivalent circuit.
*   **Inductor Winding Resistance (RL):**
    *   Modeled as a **resistor (RL) in series with an ideal inductor**. This resistance is critical for cost and efficiency optimization.
    *   **Impact on Boost Converter (Example):** Adding RL introduces an additional term (I*RL) in the inductor volt-second balance equation. This requires solving two coupled equations (volt-second balance and capacitor charge balance) for two unknowns (inductor current I and output voltage V). The result shows a **reduction in output voltage from the ideal case**, and the maximum attainable voltage is limited by RL.
    *   The equivalent circuit for a boost converter with inductor winding loss includes the ideal DC transformer and the RL in series.
    *   **Efficiency Calculation:** The efficiency of a boost converter with inductor winding loss can be expressed as a function of the conversion ratio and the ratio of RL to load resistance R.
*   **Auxiliary Equations for Switched Ports (e.g., Buck Converter Input):**
    *   For converters with switching at a port (e.g., the input of a buck converter), where inductor and capacitor are on the same side of the switch, the standard balance equations may not fully describe the input connection.
    *   An **auxiliary equation** is needed to describe the **DC component (average value) of the current drawn from the input** (Ig). This involves sketching the discontinuous Ig waveform, expressing it in terms of continuous waveforms (like inductor current IL), and then finding its average value (e.g., **Ig = D * IL** for a buck converter). This completes the equivalent circuit model by allowing the formation of the DC transformer.
*   **Semiconductor Conduction Losses:**
    *   These losses arise from the **forward voltage drops of semiconductor devices**.
    *   **MOSFET Modeling:** An ideal switch in series with an **on-resistance (Ron)**.
    *   **Diode Modeling:** A constant **forward voltage drop (VD)** and/or an **on-resistance (RD)** in series with an ideal switch. Values are typically obtained from datasheets.
    *   **Impact on Boost Converter (Example):** When Ron, VD, and RD are included, they add terms to the inductor voltage waveform, which are then integrated into the volt-second balance equation. In the equivalent circuit model, these resistances appear as effective values dependent on the duty cycle (e.g., **D * Ron** or **D' * RD**), reflecting the fraction of time they conduct current. The diode voltage drop appears as an independent voltage source (e.g., **D' * VD**).
    *   **Conduction Loss Prediction:** The averaged models correctly predict the **average power loss** (e.g., D * I^2 * Ron for MOSFET conduction loss).
    *   **Ripple Effect on Loss Prediction:** The small ripple approximation **ignores the effect of switching ripple on RMS current**. While accurate for small ripple (e.g., 0.33% error for 10% ripple), it can lead to underprediction of losses if the ripple is very large (e.g., 33% underprediction for 100% ripple).
