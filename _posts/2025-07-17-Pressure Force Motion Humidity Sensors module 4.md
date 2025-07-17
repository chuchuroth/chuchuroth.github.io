---
layout: post
title:  "Pressure Force Motion Humidity Sensors module 4"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---


Here is a comprehensive summary of the technical and factual information regarding sensors and related concepts from the provided sources, with colloquial language removed:

### I. Motion Detectors

Motion detectors are routinely used in burglar alarm systems to alert security services of an intruder's presence when a property is unoccupied. Some systems trigger a security camera to record events. Early motion detector development involved challenges in distinguishing human intruders from large pets, such as a 140-pound (64 kg) dog, to prevent false alarms, as such an animal emits more infrared energy than many people.

**A. Passive Infrared (PIR) Sensors**
PIR motion sensors detect infrared radiation emitted by objects, living or not, as a function of their absolute temperature. They respond to infrared radiation primarily centered around a wavelength of **10 microns**, corresponding to an average skin temperature of 93°F (34°C), though most sensors respond between 4 and 20 microns.

1.  **Principle of Operation:**
    *   PIR sensors utilize **pyroelectric sensors** that convert heat from skin (infrared radiation) into a voltage.
    *   **Pyroelectric materials** are crystals that generate an electric charge in response to **heat flow**. They absorb heat by contact with a hot surface or by absorbing infrared radiation.
    *   When electrodes are attached to opposite faces, the crystal functions as a **capacitor**.
    *   A key distinction: **pyroelectric materials generate charge when heated, while piezoelectric materials generate charge when stressed**. Many pyroelectric materials also exhibit piezoelectric properties.
    *   Pyroelectric materials generate charge **only when temperature changes**, acting as detectors of heat flow rather than thermal energy itself.
    *   The process involves heat application via infrared radiation, warming the absorption layer and one side of the pyroelectric material. This causes that side to expand, straining the crystal, producing thermal stress, and changing the dipole orientation. Consequently, opposite polarity charges are generated on the electrodes, inducing a voltage.
    *   **Dipole moment (M)** of a bulk pyroelectric sensor is calculated as **M = μAH**, where μ is dipole moment per unit volume, A is sensor area, and H is thickness. The charge collected by electrodes (Q_a) relates to dipole moment by **M_0 = Q_aH**, leading to **Q_a = μA**.
    *   The **pyroelectric charge coefficient (P_Q)** is defined as **dP_s/dT** (change in spontaneous polarization P_s with temperature T), and the **pyroelectric voltage coefficient (P_v)** as **dE/dT** (change in electric field strength E with temperature T).
    *   The ratio **P_Q / P_v = Kε₀**, where K is permittivity and ε₀ is vacuum permittivity.
    *   Changes in charge (ΔQ) and voltage (Δv) due to a temperature change (ΔT) are **ΔQ = P_Q A ΔT** and **Δv = P_v H ΔT**.
    *   Sensor capacitance (C_e) is **ΔQ / Δv = Kε₀A / H**.
    *   The change in voltage (ΔV) is proportional to the temperature change and **inversely proportional to the sensor thickness**: **ΔV = (P_Q A / C_e) * ΔT = (P_Q / (Kε₀)) * (A / H) * ΔT**. This inverse relationship has influenced the design of **MEMS pyroelectric sensors**.
    *   **Lead titanate (PbTiO3)** is often used in MEMS sensors due to its high pyroelectric coefficient and high Curie temperature (490°C), at which its polarization goes to zero.
    *   Sensor sensitivity and non-linearity typically increase with temperature.

2.  **PIR Sensor Construction and Detection:**
    *   A **Fresnel lens** concentrates the IR energy onto the sensor's focal plane.
    *   The sensor element is housed in a **hermetically sealed metal can** for electrical noise immunity and environmental stability. The can's window is made of IR transmissive material, usually coated silicon, to protect the sensing element.
    *   The focusing lens creates an **inverted image of the room** on the focal plane.
    *   Detection is based on the **change** in infrared energy when an intruder's moving image overlaps and then moves off the sensing element.
    *   A negative analog voltage indicates movement in one direction, while a positive voltage indicates movement in the opposite direction.
    *   A **comparator** converts the analog voltage output into logic levels (0 for no motion, 1 for motion). The frequency of the digital output is proportional to the intruder's speed.

3.  **False Alarm Prevention (Differential Detectors):**
    *   A negative side effect of pyroelectric elements also being piezoelectric is that **mechanical stress** (e.g., loud sounds, structural vibrations) can generate spurious charges, leading to false alarms.
    *   To counteract this, PIR detectors are typically fabricated as **differential detectors**.
    *   They contain **two identical sensing elements** positioned inside the housing, with two slots in the cover to sequentially view an approaching subject.
    *   The elements are connected to an interface circuit that **cancels in-phase spurious signals** (like those from mechanical stress) applied simultaneously to both elements.
    *   Since infrared energy is focused by the Fresnel lens onto only one element at a time, its signal is not cancelled, ensuring only IR energy is used for detection.
    *   A differential PIR detector is created by applying two pairs of electrodes on both sides of a single plate, forming capacitors. The upper electrodes are connected, and the two bottom electrodes are separated, forming two serially connected capacitors.
    *   When a thermal image moves across the electrodes (e.g., from slot one to slot two), the current flowing from the sensing element to a high-resistance bias resistor (typically 10 gigaohms) changes, generating a small output voltage (e.g., 10 millivolts from picoamp current). A **JFET transistor** is used as an impedance converter and voltage follower to trigger detection.

4.  **Commercial Features and Design Considerations:**
    *   Commercial PIR motion detectors often feature temperature compensation (-10°C to 55°C), high humidity performance (when not wet), and **RF immunity**.
    *   They can have **low sensitivity settings** to prevent false alarms from pets. Installers often mount sensors high to mostly detect people.
    *   For large areas, detectors use a **faceted infrared Fresnel lens**, which is divided into an array of smaller lenses (facets). Each facet creates its own image on a **common focal plane**, similar to insect eyes. This ensures that when an object moves, at least one of its multiple images will be detected.
    *   Ceiling-mounted detectors commonly used in commercial settings (e.g., museums, banks) use this design, with zones fanning out (e.g., up to 36 feet radius and 12 feet high). These sensors require an even number of symmetrically oriented electrode pairs to reject in-phase signals.
    *   Formulas for lens design include:
        *   **Focal length of a single facet (f)**: **f = Ld / Delta**, where L is object distance from lens, d is width of sensing element, and Delta is minimum object displacement.
        *   **Facet pitch (p)**: **p = 2nd**, where d is width of sensing element and n is number of facets.

**B. Ultrasonic Detectors**
Ultrasonic sensors are distance measurement devices inspired by animal echolocation (bats, dolphins, whales).

1.  **Principle of Operation:**
    *   These detectors emit an ultrasonic wave pulse (>20 kHz, outside human hearing range), then remain silent to receive reflected echoes.
    *   **Object distance (d)** is calculated using the **time of flight (t)** (time delay between emission and reception) and the **speed of sound (c)**: **d = (t * c) / 2**.
    *   Accurate distance calculation requires accounting for the **medium type and its temperature**, as the speed of sound varies significantly with these factors. For example, dry air at 0°C has c = 331.2 m/s, while in distilled water at 20°C, c = 1,482 m/s. Sound does not travel in a vacuum.
    *   For objects not normal to the sensor's axis, the formula becomes **d = (t * c * cos(theta)) / 2**, where theta is the angle the transmitter/receiver make with the normal line. This equation presents an ambiguity as both distance and angle are unknown. Therefore, ultrasonic sensors are typically used for **modest distances, usually under 10 meters**, where the angle is small and cos(theta) is approximately one.
    *   The **amplitude of ultrasonic waves attenuates proportionally with object distance**, more significantly at higher frequencies.

2.  **Components and Functionality:**
    *   A **piezoelectric crystal** serves as the generator of ultrasonic sound waves.
    *   Typical burst waves are 20 cycles at 10-20 volts RMS amplitude, with frequencies between 32-68 kHz. Higher burst frequencies generally lead to longer detection ranges.
    *   Voltage applied to the crystal causes it to flex and transmit waves. A **backing material** dampens oscillations to allow for reception.
    *   Due to the reversible piezoelectric effect (crystal generates voltage when stressed by reflected waves), a single element can function as both transmitter and receiver, but not simultaneously. This necessitates a programmed **idle time** between transmission and reception.
    *   For continuous sensing, separate transmitters and receivers are required.
    *   For optimal sensitivity, the driving circuit should transmit at the **resonant frequency of the piezoelectric ceramic**.
    *   The sensor's front cone is typically circular for uniform directional sensitivity. An **asymmetric cone** (narrow field of view) can increase receiver sensitivity.
    *   Commercial ultrasonic sensors (e.g., Murata MA40S4S, MA40S4R) often operate at 40 kHz, detecting objects from 20 cm to 4 m. Their block diagrams include:
        *   A processor (e.g., Murata MC9S12ZVL32) for control.
        *   A **pulse-width modulator (PWM)** and **burst signal generator** for transmission.
        *   A **programmable gain amplifier (PGA)** for received signal amplification.
        *   A **band pass filter** to improve signal-to-noise ratio before analog-to-digital conversion (ADC).
        *   Software modules for distance calculation, temperature compensation, and averaging. The receiving sensor is saturated for 1 millisecond after burst transmission.

3.  **Applications:**
    *   Aiding drivers in detecting vehicles in blind spots and during parking. Parking systems typically use 2-4 sensors on the rear bumper to detect objects 2-5 meters away.
    *   Distance is communicated via visual displays (yellow/red lines) or auditory beeps of varying frequencies.
    *   Often used as **liquid level sensors**, for example, in gasoline tanks.

**C. Microwave Detectors**
Microwave detectors emit radio frequency pulses and detect reflected waves. They are suitable for scanning wide areas and operating in extreme temperature and weather conditions.

1.  **Fundamental Characteristics:**
    *   The size of the detected object must be **equal to or larger than the wavelength** of the transmitted signal.
    *   Like ultrasonic detectors, **time of flight** is used for distance measurement.
    *   **Frequency shift (Doppler Effect)** is used for calculating object speed.
    *   Radio waves travel at the **speed of light in air** (approximately six orders of magnitude faster than sound). Due to this high speed, microwave detectors **cannot be used for sensing close-up objects** in air because the time of flight is too short for electronics to distinguish received signals before the next is sent.
    *   They are well-suited for industrial door and gate openers that need to detect vehicles far enough away for the door to open in time, as these systems typically trigger based on object velocity, not proximity.
    *   Their performance is unaffected by night, damp/dry air, or ambient temperatures, as these conditions do not influence the speed of radio waves.
    *   **Standard radar frequencies** categorize microwaves as wavelengths shorter than 4 centimeters (Ka and S bands). These wavelengths can pass through atmospheric contaminants like fog and dust but are reflected by large objects.
    *   When used for distance measurement, they typically detect objects several kilometers away, providing a time of flight on the order of 0.01 milliseconds.

2.  **Components and Operation:**
    *   A microwave detector consists of an **oscillator, antenna, and a mixer diode**.
    *   The core of the oscillator is a **Gunn diode**, a **Transferred Electronic Device (TED)**. The term "diode" is a misnomer as it lacks a PN junction.
    *   **Gunn Diode Structure and Mechanism:**
        *   Composed of a **single piece of n-type semiconductor with three layers**: heavily doped N+ (top), lightly doped N (middle - active region), and N+ (bottom).
        *   It uses only n-type semiconductors because its operation relies solely on **electrons as carriers**.
        *   Metallic contacts apply DC biasing voltage, and a heat sink prevents damage from excessive heat.
        *   When voltage is applied, electrons transfer from the conduction band to a **third, higher-energy band** due to the kinetic energy of "ballistic electrons".
        *   This transfer results in a **decrease in current** as the effective mass of electrons increases and their velocity decreases (while momentum remains constant). This current decrease occurs in the **negative resistance region** of the IV curve, a region that is inherently unstable.
        *   The Gunn diode generates **radio-frequency pulses with each DC voltage phase reversal**, operating as an oscillator with frequencies from 10 gigahertz to 1 terahertz.
        *   The **thickness of the active region controls the frequency of current oscillations**.
        *   The diode is mounted within a metal cavity (Gunn oscillator) that acts as a **resonator** for the microwaves. Mechanical adjustment of the cavity size (e.g., via a micrometer) allows tuning of the resonance frequency.
        *   The **maximum oscillation frequency (f_max) = 1 / (2 * t_d)**, where t_d is the diode's oscillation time. Optimal frequency and cavity length (l) are achieved when **l = c * t_d** and **f = 1 / (2 * t_d)**.
    *   The Gunn oscillator is sensitive to applied DC voltage stability, requiring a **high-quality voltage regulator**.
    *   The **antenna** directs transmitted waves (10-20 milliwatts power) towards the object. An **iris** controls the amount of microwave energy reaching the mixing diode.
    *   A smaller portion of the transmitted microwave oscillations is coupled to a Schottky mixing diode for use as a **reference signal**.
    *   Reflected waves induce an electric current in the mixing diode at various harmonics.

3.  **Doppler Effect and Velocity Measurement:**
    *   The **frequency of the reflected wave (f_r)** is influenced by the object's velocity, according to the **Doppler effect**.
    *   For practical measurements where object velocity (v) is much less than the speed of light (c_0), the simplified reflected frequency is **f_r = f_0 / (1 + v/c_0)**.
    *   The **Doppler Frequency shift (Δf)** is calculated as **Δf = f_0 - f_r ≈ v / λ_0** (where f_0 is transmitted frequency, λ_0 is transmitted wavelength). This means the **Doppler shift frequency is directly proportional to velocity**.
    *   If the object moves at an angle (theta) not normal to the detector, **Δf = (v / λ_0) * cos(theta)**.
    *   Typical Doppler shift frequencies are 10-100 Hertz. This range is susceptible to interference from AC power lines (50/60 Hz) and fluorescent light harmonics (100/120 Hz). Therefore, the signal requires an **amplifier and a notch filter**.

4.  **Signal Strength and Directional Detection:**
    *   **Received microwave power (P_r)** must be sufficiently high and is given by **P_r = ρ * P_0 * A² * a / (4 * π * λ² * R⁴)**, where P_0 is transmitted power, A is antenna aperture area, a is target area, λ is transmitted wavelength, R is distance to target, and ρ is coefficient of reflectivity.
    *   An optimal target has a **high coefficient of reflectivity (ρ)**, like metals, which are conductive and have high dielectric constants. Vehicles are easily detected due to their metal bodies.
    *   **Plastics are highly transmissive, not reflective**, making plastic enclosures cost-effective as they allow unimpeded transmission and reception by internal antennas.
    *   To detect the **direction of motion** (towards or away), an additional mixing diode is integrated, offset in the waveguide by one quarter wavelength. Their outputs are amplified and converted to square pulses, which a **digital phase discriminator logic circuit** analyzes. If Diode 1 goes high before Diode 2, the object is moving towards; if Diode 1 goes high after Diode 2, it's moving away.
    *   Automatic door openers can be adjusted for **bidirectional or unidirectional sensitivity**.

5.  **Commercial Specifications:**
    *   A commercial microwave detector typically has an **ABS plastic case** with no opening for the antenna, as plastic is transmissive to microwaves.
    *   The antenna angle can be manually adjusted vertically and horizontally to shape the scan area.
    *   These detectors find objects through **motion only** and cannot detect stationary objects.
    *   Example specifications include a transmitter frequency of **24.150 gigahertz**, low power consumption (2 watts), and power supply options of 12-24 VAC or VDC.
    *   Minimum detection speed can be 2 inches/second (51 mm/second).
    *   Mounting height range is 6 to 13 feet.
    *   An **IP54 ingress protection rating** indicates it should not be mounted where rain can directly hit it, typically used indoors or under awnings.

### II. Humidity Sensors

Humidity sensors measure the moisture content in the air, primarily focusing on **Relative Humidity (RH)**, which is a relative measurement as higher temperatures allow air to hold more moisture. Ideal human comfort range for RH is 20-60%. Maintaining specific RH levels is critical in various production processes (food, chemical, electronics) to ensure high yields, such as injecting moisture in clean rooms to prevent **electrostatic discharge (ESD)** damage to components.

**A. Terminology and Concepts**
1.  **Absolute Humidity:** The mass of water vapor in the air divided by its volume. It is rarely used in practice because it depends on atmospheric pressure, which varies with elevation.
2.  **Pressure of Saturated Water Vapor (P_s):** The equilibrium pressure of water vapor above a sealed container of water at a given temperature. This equilibrium is established when the rate of water molecules evaporating equals the rate of condensation. P_s increases with temperature up to the boiling point.
3.  **Relative Humidity (RH):** The ratio of the partial pressure of water vapor in air (P_w) to the pressure of saturated water vapor (P_s), expressed as a percentage: **RH = (P_w / P_s) * 100%**. RH is highly temperature-dependent; a given RH at a high temperature corresponds to a much larger mass of water vapor than at a low temperature.
4.  **Atmospheric Pressure (P_atm):** The pressure of open air, which depends on elevation (due to gravity) and moisture content. It is the sum of the partial pressure of dry air (P_a) and the partial pressure of water vapor (P_w): **P_atm = P_w + P_a**.
5.  **Dew Point Temperature (DP):** The temperature to which air can be cooled while retaining its maximum moisture content. At the dew point, RH equals 100%, and moisture condenses on surfaces.

**B. Humidity Sensor Calibration and Types**
Humidity sensors are highly nonlinear and require calibration during manufacturing. Saturated salt solutions in sealed boxes are often used as reference humidity sources, where the RH value depends on the type of salt and temperature uniformity.

1.  **Capacitive Humidity Sensors:**
    *   Engineered as a thin film of **hygroscopic polymer** placed between two conductive electrodes, all integrated on a substrate.
    *   The polymer is coated with porous metal electrodes that protect it from contamination and condensation while providing conductive surfaces for capacitance measurement.
    *   The **dielectric constant of the polymer changes almost proportionally with incremental changes in relative humidity**.
    *   The polymer film is typically 8-12 microns thick, with metal electrodes a few hundred angstroms thick.
    *   For example, an Innovate Sensor Technology capacitive sensor shows a nearly linear RH vs. capacitance curve (1.5% linearity error), with a slope of approximately 0.25 picofarads per percent RH change. Its bulk capacitance ranges from 142-167 pF (wired) to 170-202 pF (surface mount).
    *   They have a relatively fast response time (under 5 seconds for a 50% to 0% RH change at 23°C).
    *   The dielectric constant of water and the polymer is a function of temperature.
    *   Operating temperature ranges are wide, from -50°C to +150°C.
    *   Typical accuracy is an RMS error of 2.1% (sum of squares of 1.5% linearity and 1.5% hysteresis error).
    *   Digital capacitive humidity sensors typically require factory calibration if replaced in the field.

2.  **Resistive Humidity Sensors:**
    *   Consist of a **hygroscopic polymer film** deposited on cone-shaped electrodes (gold or platinum) printed on a ceramic substrate.
    *   The **resistance of the polymer film decreases with relative humidity**. This occurs because the absorption of water molecules by the polymer enables movable ions to move more freely.
    *   While primarily resistive, their capacitance also changes with humidity.
    *   Impedance at a given RH increases as frequency decreases, and at a constant frequency, impedance decreases non-linearly as humidity increases.
    *   These sensors can be calibrated with **only one fixed humidity point**.
    *   The output signal depends on air temperature, so they typically include an **onboard temperature sensor** for temperature compensation in the signal conditioning circuit.
    *   For example, a TE Connectivity resistive sensor has an accuracy of 3-5% RH, which is lower than capacitive sensors, and a hysteresis of 1.5% RH. Its temperature coefficient is 0.1% RH per °C.
    *   An advantage is that they can be swapped in the field with a simple resistance calibration.
    *   The impedance-humidity relationship is highly non-linear and cannot be modeled by a simple algebraic function. To create an exponential relationship, a **Z-F conversion circuit** is used, which changes the driving circuit's frequency to adjust impedance based on humidity. This circuit converts frequency into a pulse wave with a pulse width that is large at low humidity and small at high humidity, achieving logarithmic compression of the output voltage.
    *   The impedance of a resistive humidity sensor is significantly affected by air temperature; for instance, at 30% RH, impedance can increase tenfold when temperature drops from 45°C to 5°C. An NTC thermistor alone cannot provide sufficient temperature compensation across the full range. Compensation in these systems utilizes the temperature characteristics of all semiconductor elements in the circuit.
