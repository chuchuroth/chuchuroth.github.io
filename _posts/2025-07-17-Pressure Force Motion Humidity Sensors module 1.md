---
layout: post
title:  "Pressure Force Motion Humidity Sensors module 1"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---


The following provides knowledge extracted from the sources, presented without colloquial language, focusing on technical information, definitions, and concepts.

### **Pressure Fundamentals**

*   **Definition of Pressure**
    *   Pressure is defined as the **force per unit area exerted on a mass**.
    *   Pressure at a depth (H1) in a liquid is calculated as the **specific weight of the liquid multiplied by the height of the column (H1)**. Specific weight is equal to the **density of the liquid multiplied by the acceleration due to gravity (g)**. For example, pressure at 5,000 meters below the Pacific Ocean is approximately 49 megapascals (490 bar or 7,112 PSI).
    *   The term "fluid" is used generically to mean either a gas or a liquid.

*   **Units of Measure for Pressure**
    *   Atmospheric or blood pressure is typically recorded in **millimeters of a column of mercury (mmHg)**, e.g., normal blood pressure is around 120/70 mmHg.
    *   Vacuum is typically measured in **torr**.
    *   Process fluid pressure is typically measured in **bar or psi**.

*   **Pressure Measurement Terms**
    *   **Barometric pressure (atmospheric or absolute pressure)**: Environmental pressure that fluctuates with weather conditions, rising with clear weather and falling with precipitation or severe storms.
    *   **Absolute pressure**: Measured relative to a perfect vacuum (outer space). Examples include engine manifold pressure, atmospheric pressure, and pressures derived from water depths.
    *   **Gauge pressure**: Measured relative to barometric (atmospheric) pressure. A gauge pressure of 0 indicates one atmosphere of absolute pressure. Examples include in vivo blood pressure and tire pressure. A flat tire signifies internal pressure close to or equal to atmospheric pressure.
    *   **Hydrostatic pressure**: Pressure exerted by a fluid at a certain depth.
    *   **Line pressure (static or working pressure)**: The force exerted by flow within a pipe.
    *   **Vacuum**: A pressure below atmospheric pressure. 760 torr is equivalent to 1 atmosphere of pressure.

*   **Methods of Pressure Sensor Measurement**
    *   **Gauge pressure sensor**: Measures the difference between the measured pressure and the barometric pressure. One side connects to the gas being measured, and the other side connects to the barometric pressure reference.
    *   **Sealed Gauge sensor**: The low-pressure side of the sensor is connected to the top of a tank, while one side of the sensor is sealed to represent a reference pressure, such as barometric pressure, via a voltage.
    *   **Differential pressure sensor**: Features two ports, one open to a high-pressure source and the other to a low-pressure source. The sensor outputs the difference between these two pressures. These are frequently used as flow meters by measuring flow upstream and downstream of an orifice plate. They are also used in respirators, ventilators, and spirometers to measure lung flow rates.
    *   **Absolute pressure sensor**: Has one port open to the pressure source to be measured, and the other side is exposed to a vacuum manufactured to be as close to absolute zero as possible.
    *   **Vacuum sensor**: Has one side open to the atmosphere and the other side open to the vacuum source.

### **Pressure Sensor Terminology and Performance**

*   **Operating Pressure Range**: The difference between the maximum and minimum pressures within which a sensor operates at its stated accuracy.
    *   **Upper Range Limit (URL)**: The upper limit of measurement.
    *   **Lower Range Limit (LRL)**: The lower limit of measurement.
*   **Operating Temperature Range**: The difference between the maximum and minimum temperatures at which a sensor operates at its stated accuracy.
*   **Leakage Rate**: The maximum rate at which process fluid can leak through a seal. Metal seals are more leak-proof but more challenging to manufacture and assemble than rubber seals. Higher absolute pressure within the sensor increases fluid leakage to the atmosphere.
*   **Proof Pressure**: The maximum pressure that can be applied to a sensor before its output sensitivity permanently changes. It is typically specified as two to three times the maximum rated pressure.
*   **Burst Pressure**: The maximum pressure a sensor can withstand before it ruptures and leaks fluid to the atmosphere. This is a critical safety specification, with most sensors tested to guarantee a burst pressure of at least five times the maximum rated pressure.
*   **Full-scale**: The maximum rated pressure of the sensor at which it will provide a reading within the stated accuracy.
*   **Zero error (offset error or zero shift)**: The sensor output at zero pressure when operating at a reference ambient temperature (typically 20-25°C). This indicates the stability of the analog sensor circuit, as it is impossible for an analog sensor circuit to have zero error at any reading, including the zero-point. Jitter can be present in the zero-point.
*   **Span**: The difference in signal output at the reference temperature between the readings recorded at the minimum and maximum pressures. **Span error** captures the variance in the slope of the output versus input curve across different manufactured sensors. Some manufacturers may include linearity, hysteresis, and repeatability errors within their span error specification.
*   **Linearity error**: The deviation of the sensor's output at the reference temperature (typically 20-25°C) from a best-fit straight line. This line is determined by three signal outputs corresponding to zero, full-scale, and half-scale pressures. This error accounts for imperfections in linearization algorithms.
*   **Hysteresis error**: The deviation of the sensor's output at the reference temperature due to its inability to return to the identical output signal when pressure is increasing compared to when it is decreasing. This can be attributed to the diaphragm not acting as a perfectly linear elastic element.
*   **Thermal zero error**: The offset in the zero output caused solely by operating the sensor at an ambient temperature other than the specified reference temperature. It is typically expressed as a percentage of span per degree Celsius and results from changes in resistance within the sensor's analog electronics at varying temperatures.
*   **Thermal span error**: The offset in the span caused solely by operating the sensor at an ambient temperature other than the specified reference temperature. Like thermal zero error, it is expressed as a percentage of span per degree Celsius and arises from changes in resistance within the sensor's analog electronics. Thermal span and thermal zero errors are additive.
*   **Long-term drift**: A change in sensor reading over very extended periods without an apparent cause, often expressed as a percentage of span per year. It can result from long-term changes in the material properties of sensor components, wiring, or installation. Many sensors incorporate zero buttons or software routines to allow customers to reset the sensor output to zero when drift is observed.

### **Piezoresistive Pressure Sensors**

*   **Piezoresistive Effect**: The change in the electrical resistance of a metal or semiconductor material when subjected to mechanical strain.
    *   In a strained metal wire, its length increases, and its diameter decreases, leading to an increase in electrical resistance.
    *   In semiconductors, resistance change is more complex, involving the redistribution of light and heavy holes in the top valence bands, which alters their effective mass and resistivity.
*   **Resistivity Calculation**: The simple formula for the resistivity of a metal wire is R = rho L / A, where R is resistance, rho is the resistivity of the metal, L is the wire length, and A is the cross-sectional area. The differential of this equation is dR = (L/A) d rho + (rho/A) dL - (rho L/A^2) dA, which can be further derived to dR/R = d rho/rho + dL/L - dA/A.
*   **Strain and Poisson's Ratio**:
    *   **Strain** is a non-dimensional quantity equal to the change in one dimension divided by that same dimension. Axial strain is dL/L, and lateral strain is dD/D.
    *   **Poisson's ratio (nu)** is the negative ratio of the lateral strain to the axial strain. For most metals, nu is approximately 0.3.
*   **Gauge Factor (G)**: A measure of the sensitivity of resistance change in the sensor with strain. It is defined as G = (dR/R) / (axial strain).
    *   For metals, the gauge factor is approximately 2, making them suitable for **strain gauges** where small strain changes indicate significant force changes.
    *   **Pressure sensors** require a larger dynamic range, necessitating the higher gauge factors found in semiconductors. P-type silicon semiconductor strain gauges have commercially available gauge factors ranging from 50 to 200. P-type 3C-SiC material has a gauge factor of 28.
*   **Sensor Design**:
    *   Piezoresistive sensors are typically made with a thin silicon diaphragm. Multiple piezoresistive sensors are formed on this thin section.
    *   When external fluid pressure is applied, the diaphragm deflects, creating stress and strain in the sensors, which changes their resistance.
    *   A common design utilizes four piezoresistive sensors arranged in a **Wheatstone bridge circuit** on a silicon substrate. Compensating sensors may also be included in a separate bridge circuit.
    *   In a differential pressure sensor configuration, if high pressure (P2) is greater than low pressure (P1), the diaphragm deflects downward. This causes tensile stress and increased resistance in sensors aligned with the deflection (e.g., on the x-axis) and compressive stress and decreased resistance in sensors perpendicular to the deflection (e.g., on the y-axis). The strategic placement of sensors maximizes the voltage output of the bridge.
*   **Construction Elements**:
    *   A **square diaphragm** with symmetrically arranged implanted sensors.
    *   The diaphragm is bonded to a support chip using **glass sealing**, which seals the measured pressure from the atmosphere and bonds inlet tubing.
    *   **Epitaxial and edge layers** form the p-type silicon sensors.
    *   **Thin-film aluminum conductors** connect the resistors to the diaphragm edges.
    *   **Gold wire bonds** conduct sensor signals to connect pins.
    *   **Glass-to-metal seals** provide a reliable hermetic seal for these pins, resisting corrosion and meeting medical/food grade standards.
    *   A **cap** is bonded to the chipset for mechanical and thermal isolation.
*   **Sensor Electronics**: The bridge circuit outputs a small millivolt signal, which is amplified by a multiplexer (MUX) and preamplifier. The amplified voltage is then digitized by an Analog-to-Digital (A/D) converter. The resulting digital output is processed by a microprocessor using a calibration routine to determine the pressure value, which is then output via an I²C or SPI interface.
*   **Commercial Packages**: Available in industrial configurations (threaded for pressure ports), sealed packages with pins and corrosion-proof stainless steel housings, and simpler designs where the diaphragm is screened onto hollow ceramic. MEMS (Micro-Electro-Mechanical Systems) piezoresistive sensors can be built directly onto integrated circuits (ICs) for automotive applications. These typically include an on-board temperature diode for calibration or fluid temperature measurement.
*   **Advantages**:
    *   Available in medium to small, rugged, and durable packages.
    *   Highly reliable and proven technology (over three decades).
    *   Wheatstone bridge circuits are readily calibrated for accuracy and temperature compensation.
    *   Exhibit high linearity with low hysteresis.
    *   Simple packages offer high vibration tolerance, suitable for aerospace and automotive applications.
    *   Relatively low cost.
*   **Disadvantages**:
    *   **Safe overload** is typically limited to three times the maximum rated pressure unless complex mechanical overload stops are implemented, which increase cost.
    *   Output is in the low millivolt range, requiring amplification and signal conditioning to standard outputs (e.g., 0-5 volts or 4-20 milliamps).
    *   Operating temperature range is generally limited to -40°C to +125°C.
    *   Exhibit relatively high thermal drift and significant zero and span errors.

### **Capacitive Pressure Sensors**

*   **Capacitance Fundamentals**:
    *   For a flat plate capacitor, capacitance (C) equals k Epsilon naught A / d, where k is the relative permittivity of the dielectric, Epsilon naught is the permittivity of space, A is the cross-sectional area, and d is the distance between the plates.
    *   Capacitance for two coaxial cylinders is C = (2 Pi Epsilon L) / log(b/a), where L is length, a is the inner radius, b is the outer radius, and Epsilon is the permittivity of space between the cylinders.
    *   A capacitive level sensor for coaxial cylinders in a tank measures C_h = (2 Pi Epsilon naught / log(b/a)) * (H - h * (1 - k)), where C_h is capacitance as a function of liquid level, H is container height, h is liquid level height, and k is relative permittivity of the dielectric.
*   **General Design (Silicon-based)**:
    *   When pressure is applied to a sensing diaphragm, it deflects inward, reducing the volume of the cavity between two parallel electrodes.
    *   This reduction in distance between electrodes causes the capacitance to increase as pressure increases.
    *   This type of sensor exhibits minimal variations in output due to ambient temperature changes because its operation is not based on resistance change.
    *   They are characterized by high accuracy and minimal power consumption.
*   **Low-Cost Design (Stainless Steel Diaphragm)**:
    *   Pressurized fluid enters a cavity above a stainless steel sensing diaphragm, causing it to deflect away from an electrode.
    *   This increases the distance between the electrodes, causing capacitance to decrease as pressure increases.
    *   Commonly used in high-purity manufacturing (e.g., semiconductors) and medical products.
    *   Available in ranges from 15 psi to 10,000 psi.
    *   Offer high **overpressure** capability, typically around 10 times the maximum rated pressure, which is significantly higher than piezoresistive sensors (3x).
*   **Capacitive Differential Pressure Sensor**:
    *   More complex, typically using a stiff metal or silicon diaphragm positioned equidistantly between two stationary metal plates, forming two capacitors.
    *   Pressure is transmitted from an isolating diaphragm to the sensing element via a dielectric fluid, typically liquid silicone. The isolating diaphragm protects the delicate sensing diaphragm from corrosive gases and liquids.
    *   Differential pressure causes the sensing element to deflect away from the high-pressure zone, which decreases the capacitance of one cell and increases it in the other.
    *   A **dual diaphragm design** enhances sensitivity, effectively doubling the change in capacitance compared to a single sensing diaphragm. The Rosemount 3051S pressure transmitter employs dual capacitance diaphragms, offering a broad measurement range from 0.25 millibar to 276 bar.
    *   The Rosemount 3051S contains both a pressure sensor and electronics to transmit data. It includes a sensor diaphragm, stationary electrodes, and entry ports with cavities for high and low-pressure isolating diaphragms. Dielectric oil flows from the isolating diaphragm to the sensor electrode.
*   **MEMS Capacitive Pressure Sensors**:
    *   Available in MEMS format, featuring arrays of sensing cells with flexible membranes and reference cells with stiff membranes.
    *   Can measure absolute, gauge, or differential pressure.
    *   Advantages include low noise and simple calibration. They are beneficial for battery-powered applications and detecting very small pressure changes.

### **Vacuum Sensors**

*   **Pirani Gauge**:
    *   Invented in 1905.
    *   **Principle**: A heated wire loses heat to surrounding gas molecules through collisions. In a vacuum, fewer molecules are present, which reduces the wire's cooling rate. By accurately measuring heat loss, the level of vacuum can be indirectly determined.
    *   **Operation**: A platinum wire forms one leg of a Wheatstone bridge circuit. A control circuit detects voltage changes across the bridge (V_o) and adjusts the current (i_2) to maintain constant heat loss from the wire. As pressure (molecule count) decreases, current i_2 reduces further to maintain constant wire resistance. The gauge is calibrated by correlating the vacuum level to the current i_2 (lower pressure corresponds to lower current).
    *   **Limitation**: Pirani gauges lose accuracy at high vacuum levels, necessitating other sensor types for such conditions.
*   **Other Vacuum Sensor Types**:
    *   **Resistive sensors**: Commonly used for medium-accuracy vacuum measurements due to reasonable cost.
    *   **Dial gauges**: Provide rough estimates of vacuum levels. They are typically bulky and not corrosion-resistant, often used as a sanity check for vacuum flow.
    *   **Ionization vacuum gauges**: Ionize ambient gas molecules and correlate the resulting ion current to the vacuum level. These are also typically bulky.
*   **Capacitance Manometer**:
    *   **Principle**: Operates on the same principles as a capacitive absolute pressure sensor, but its reference side of the diaphragm is evacuated to a very high vacuum level. Pressure is determined by measuring the change in capacitance between a metal diaphragm and an adjacent fixed electrode.
    *   **Corrosion Prevention**: Outfitted with a **getter** (a reactive chemical that reacts with unwanted gas molecules to prevent diaphragm contamination and failure) or a **plasma shield** (creates a high-temperature plasma with a noble gas in front of the diaphragm to prevent reactive gases from reaching it). The sensing electrode is often made of high nickel content stainless steel for corrosion inhibition.
    *   **Accuracy**: Commercial capacitance manometers typically achieve an accuracy of 0.25%, superior to other vacuum gauges, making them the preferred vacuum sensor for modern semiconductor manufacturing.
    *   **Mechanism**: A gas inlet port allows contact between chamber gas and the back of a diaphragm. Fixed electrodes are located on a thick ceramic plate, with a reference vacuum created between them and the diaphragm during manufacturing. The diaphragm deflects in an arc under vacuum, with greater deflection in the middle. An electrode located at the diaphragm's middle measures a larger capacitance change than one at the outer edges. Roller bearings support the ceramic plate to maintain flatness despite high temperatures (e.g., 1,000°C).
    *   **Electronics**: Current from electrodes is conducted to an analog electronics module via connectors and glass-to-metal seals. This module determines the difference in capacitance between the electrodes, which is then correlated to the vacuum level.
    *   **Circuit Operation**: Two capacitors (C1, C2) are connected to a transformer's secondary winding, with their diaphragm sides grounded. A high-frequency signal source connected to the primary winding induces voltage across the secondary, which is applied to C1 and C2. The voltage across each capacitor is inversely proportional to its capacitance. The voltage differential between the fixed electrodes appears at a center tap, which is amplified. C1's capacitance (connected to the inner electrode) varies significantly with pressure changes, while C2's (connected to the outer electrode) does not. The amplifier output reflects the pressure differential.
    *   **Signal Processing**: The time-varying signal is demodulated to produce a DC voltage level proportional to the pressure differential.
    *   **Resolution**: Capacitance manometers require high signal resolution because capacitances are measured in picofarads. For example, a 12-bit A/D conversion of a 1,000 Torr manometer signal yields a resolution of 0.025% of full scale.

### **Pressure Sensors vs. Pressure Transmitters**

*   There is no standardized industry definition distinguishing a process transmitter from a process sensor. However, key attributes differentiate them:
*   **Pressure Transmitters**:
    *   Provide a **broader process measurement solution**.
    *   Have a significantly **higher price range** (typically $1,000-$4,000).
    *   Often offer **multi-variable measurements** (e.g., pressure and temperature, or pressure and flow).
    *   Feature **much wider operating pressure ranges**, suitable for large chemical plants, oil refineries, and electric utilities.
    *   Come standard with **explosion-proof and intrinsically safe certifications**.
    *   Offer standard milli-amp and milli-volt outputs, along with a broad range of communication protocols (e.g., HART, Profibus, Fieldbus, Industrial Ethernet).
    *   Typically consist of **separate modules** for sensor electronics, communication, and pipe mounting.
    *   Include an **LCD and push-button user interface**.
    *   Are **substantially heavier and larger** than sensors (e.g., a transmitter weighing about 8 kilograms versus a sensor weighing about 20 grams).
    *   May have a lower upper ambient temperature limit (e.g., 85°C) to allow for higher process fluid temperatures (up to 360°C) without compromising electronic accuracy.
    *   Offer a wide array of **pipe connections** and process connections made from various metals, ceramics, and plastics.
    *   Their spec sheets are extensive (10 to 160 pages), detailing accuracy across numerous process conditions, mounting configurations, materials, and protocols, including chemical compatibility.
*   **Pressure Sensors**:
    *   Are **smaller** (e.g., the size of a postage stamp compared to a transmitter).
    *   Generally have a higher upper ambient temperature limit (e.g., 125°C).
    *   Typically do not include explosion-proof or intrinsically safe ratings.
    *   Usually come with a small threaded connection and have fewer material choices.
    *   Their spec sheets are simpler (two to four pages) and easier to read.

### **Total Error Budget Calculation**

*   **Total Error Budget**: Encompasses all inaccuracies and performance deviations of a sensor or transmitter, regardless of their root cause. This includes:
    *   Reference accuracy.
    *   Zero and span error.
    *   Effects due to overpressurizing the sensor.
    *   Zero and span error due to operation at very low or high ambient temperatures (thermal errors).
    *   Error due to long-term drift.
*   **Calculation Methods**:
    *   **Worst Case Error**: Calculated by algebraically summing all individual error components. This approach tends to overestimate typical sensor performance.
    *   **Root Mean Square (RMS) Error**: A statistically accepted method for calculating an average error. This provides a more realistic representation of typical performance. For example, an RMS error budget of +/- 0.174% of span (0.017 MPa for a 10 MPa span) was calculated for a particular transmitter capsule, indicating high accuracy. Long-term drift is often excluded from these calculations as it can be compensated for using a zero button or software.

### **Pressure Sensor Applications and Specification**

*   **Major Industrial Users**: Pressure sensors are widely used in the oil and gas industry, power generation, HVAC systems, automotive industry, semiconductor manufacturing, and medical applications.
    *   **Oil and Gas**: Large refineries utilize pressure transmitters in tanks and pipes, requiring explosion-proof and intrinsically safe ratings. Pressures can range up to 600 bar absolute and 400 bar differential.
    *   **Power Generation**: Fossil fuel and nuclear plants use pressure transmitters (rated explosion-proof and intrinsically safe) to measure high-pressure steam (up to 270 bar) that drives turbines.
    *   **HVAC Systems**: Thousands of sensors measure and control air temperature, humidity, pressure, and flow rates. Differential pressure sensors measure flow rates across dampers in air ducts.
    *   **Automotive**: MEMS pressure sensors are prevalent due to their low cost, small size, and accuracy. They monitor engine oil, brake booster, fuel ignition, exhaust gas recirculation, gasoline tank, and airbags. Tire-pressure monitoring systems (TPMS) use MEMS sensors in tires to alert drivers if pressure falls 10% below the specified value.
    *   **Semiconductor Manufacturing**: Pressure and temperature sensors are used in cleanroom air filtration systems. Capacitance manometers and thermocouples are employed in vacuum chambers for deposition and etch processes, operating at very low pressures (e.g., 0.1 torr) and high temperatures (e.g., 1,000°C).
    *   **Medical**: MEMS pressure sensors can be implanted (e.g., in the heart) and are used in medical device production equipment (sterilizers, autoclaves) and patient assist devices (blood pressure monitors, anesthesia delivery systems, ventilators, oxygen concentrators).
*   **Sensor Specification Method**:
    *   The process involves ruling out unsuitable sensors based on specific requirements.
    *   Key parameters to specify include:
        *   Process type and process fluid.
        *   Safety, cleanliness, or ingress protection needs.
        *   Type of pressure measurement (e.g., absolute, gauge, differential).
        *   Range of process pressures and temperatures.
        *   Range of ambient temperatures.
        *   Required error budget, which significantly influences cost.
        *   Mechanical and electrical connections.
    *   Remaining possibilities are then evaluated and optimized based on available commercial products.
    *   For example, when specifying a pressure sensor for refrigerator refrigerant (HFC-134a) requiring gauge pressure measurement between 1 and 10 bar, a burst pressure of 25 bar, specific temperature ranges, a 2% error budget, and defined mechanical/electrical fittings (1/4-18 NPT, Micro M12), various sensor types can be excluded. A specialized refrigerant pressure sensor is a suitable choice, meeting criteria such as operating temperature, overpressure rating (31 bar), compatibility, and error budget.
