Here is the extracted knowledgeable information from the sources, presented in a formal tone without colloquial language:

Manufacturers utilize three primary techniques to ensure the accuracy of sensors: **linearization**, **temperature compensation**, and **calibration**. These techniques are fundamental in the design and processing of sensors.

### Sensor Accuracy and Measurement Principles

**Accuracy** is defined as the difference between the output value of a sensor and the reference value of the output as measured by a perfect calibration standard. An accuracy specification comprises two types of errors:
*   **Systematic error**: This is a predictable and repeatable error resulting from statistical bias in the sensor. Causes include sensor non-linearity, zero or span error, or operation at temperatures outside the nominal calibration range. Systematic errors can be reduced through compensation methods, such as temperature compensation.
*   **Random error**: These errors are not individually predictable and are characterized statistically. They can arise from sensor hysteresis or the calibration process itself.

**Precision** of a measurement system refers to the consistency of results from repeated measurements obtained through a consistent calibration process. It can be represented by a normal curve. A sensor may be accurate but not precise, precise but not accurate, neither, or both. If a sensor exhibits a systematic error, increasing the sample size during calibration enhances precision but does not improve accuracy, leading to consistent inaccurate measurements. A **well-calibrated sensor** implies a precise calibration system and small systematic errors in sensor readings.

**Resolution** is the smallest measurement a sensor can reliably indicate. A sensing system with high measurement resolution can distinguish a small input change from sensor noise. The goal is to obtain sensors that are **accurate with high resolution**.

### Sensor Resolution

The **resolution of a sensor system** is primarily determined by the **Analog-to-Digital Converter (ADC)** within its signal chain.
*   ADCs provide a finite number of output representations, determined by the ratio of the converter's full-scale input to twice the number of bits in the ADC.
*   A higher number of bits in an ADC results in **higher system resolution**. For example, a 16-bit ADC has 2^16 or 65,536 possible outputs. For a 5-volt peak-to-peak full-scale input, the least significant bit (LSB) size would be 0.076 millivolts, with an error of 0.038 millivolts.

ADCs are subject to various inaccuracies that reduce their Signal-to-Noise Ratio (SNR):
*   **Offset error**: The analog value by which the transfer function deviates from passing through zero.
*   **Gain error**: The difference in the full-scale value between the ideal and actual transfer function when offset error is zero.
*   **Linearity errors**: Deviations from the straight line drawn between zero scale and full scale. These include:
    *   **Differential Nonlinearity (DNL)**: The deviation difference between two adjacent codes from the ideal LSB voltage value.
    *   **Integral Nonlinearity (INL)**: The curvature deviation from a straight line between zero and full scale. INL dictates the **Spurious-Free Dynamic Range (SFDR)** performance of the ADC, which is the strength ratio of the fundamental signal to the strongest spurious signal in the output. The shape of the curvature deviation influences the dominant harmonic performance, often being frequency-dependent.

### Linearization Techniques

**Linearization** is a technique used to approximate highly non-linear sensor outputs, commonly employed in **thermocouples and certain flow sensors**. This process can be implemented in sensor software.
*   **Tangent Approximation**: The simplest method involves taking the tangent to the non-linear function at a specific point. The curve is assumed to follow a linear output along this tangent line. This method yields limited error for small deviations from the tangent point but becomes less accurate further away. For example, thermocouple voltage table lookup data requires linear approximation between single-digit degrees Celsius points.
*   **Piece-wise Linearization**: For linearizing large portions of a non-linear curve, this method uses a series of tangent lines at different points of the curve, which are then pieced together. The resulting curve is a sum of multiple straight lines. This method is easy to implement, offers fast processing, and provides accurate results. However, it requires a large code size to store the numerous coefficients for calculation.
*   **Analog Circuit Linearization**: An alternative is to feed the sensor output through an analog circuit specifically designed to provide a linear curve that closely matches the actual analog output. For instance, a **resistive network combined with a single operational amplifier (op-amp)** can linearize the output of a two-wire Resistance Temperature Detector (RTD). In such a circuit, the op-amp output forms a voltage-controlled current source, and the output voltage is directly proportional to the RTD's resistance and thus temperature. More complex circuits are needed for three-wire and four-wire RTDs, making software compensation a viable alternative.
*   **End Point Fit Method**: This simple method approximates the non-linear curve with a straight line fit through its two end points. The main drawback is a large error at the midpoint of the line.
*   **Linear Regression (Least Squares Method)**: This is a statistical method designed to determine the best fit of a straight line through a series of points, aiming to **minimize the worst-case error** at every point in the curve.
    *   The slope (m) of the line is calculated using the formula: m = Σ[(x_i - x̄)(y_i - ȳ)] / Σ[(x_i - x̄)²], where x_i and y_i are individual data points, x̄ and ȳ are the average x and y values, and n is the total number of data points.
    *   The y-intercept (b) is calculated as: b = ȳ - m * x̄.
    *   While the linearity error at the midpoint may differ from the endpoints, the maximum error at any point is generally smaller than the midpoint error observed with the end point method.
    *   The Least Squares fit line passes through various parts of the non-linear curve but not necessarily through the endpoints. For example, when linearizing Type K thermocouple voltage data between -200°C and -150°C, the Least Squares line provides a better approximation of raw data compared to the end point line. The difference in voltage estimation at the midpoint (-175°C) was 0.018 millivolts for Least Squares versus 0.052 millivolts for the end points method.
A linearized output signal can eliminate the need for table lookup software typically used with thermocouples.

### Temperature Compensation

Temperature compensation addresses the issue of **ambient temperature changes affecting both the zero setting and span** of sensors. This is a common phenomenon across various sensor types.
*   **Thermal Span Error** refers to the change in the slope of the sensor's output characteristic due to temperature. For piezoresistive pressure sensors, this change results from dimensional and stiffness alterations, leading to the sensor becoming less sensitive as temperature increases (always negative).
*   **Thermal Zero Error** is the change in the zero offset of the sensor's output due to temperature. For pressure sensors, this arises from an increase in the resistance of the bridge's four sensors as temperature rises.
*   These thermal span and zero errors are **additive**.
*   Manufacturers often use **Digital-to-Analog Converters (DACs)** for partial correction of these errors, modifying the bridge voltage (V_b).
*   Compensation involves characterizing the sensor at **extreme operating pressures and temperatures**, along with intermediate combinations. This is typically done by placing the pressure sensor in a **temperature-controlled chamber** and applying pressure from a **calibrated pressure source**.
*   **Look-up tables for span DAC and offset DAC** are loaded into the sensor's microprocessor, and minor adjustments to V_b are made based on an **independent temperature sensor** reading.
*   **Mathematical compensation** involves defining the **Temperature Coefficient of Span (TCS)** and the **Temperature Coefficient of Zero offset (TCZ)**.
    *   The **sensitivity (S_t)** of a pressure sensor (slope of bridge voltage vs. pressure) depends on TCZ and TCS.
    *   TCS for a pressure sensor will typically be a **negative number**, while TCZ will be a **positive number** with an absolute value higher than TCS.
    *   This linear model provides **partial compensation**, as non-linear effects contribute to thermal shifts and are not fully eliminated.
    *   For a pressure sensor rated 0-100 PSI gauge, operating from -125°C to +125°C with a nominal calibration temperature of 25°C, data would be measured at 25°C and 125°C (at 0 and 100 PSI). This requires precise voltage measuring instruments and pressure calibrators.
    *   After calculating TCS and TCZ, any nominal reading from the pressure sensor can be adjusted for measurements taken at temperatures other than the nominal 25°C.

### Calibration Process

**Calibration** is the process of comparing measured values from a sensor under test against those from a **calibration standard**.
*   The calibration standard must have a known accuracy that is at least four times better, and preferably ten times better, than the sensor being calibrated.
*   A **thermal bath** is an example of a standard used for calibrating thermistor and RTD probes.
*   Calibration is performed both during initial manufacturing and periodically in the field.
*   During manufacturing, **calibration constants** within the sensor's electronics may be adjusted to meet standards. Subsequent field adjustments are only made if the sensor significantly deviates from calibration. For mechanical sensors, calibration can serve as a verification that the sensor meets its stated accuracy specifications.

#### Traceability in Calibration

**Traceability** is a critical aspect of calibration, defined as the **unbroken record of equipment documentation and measurement uncertainty linked back to a known standard of metrology**.
*   The **National Institute of Standards and Technology (NIST)** in the US, and similar national laboratories globally, maintain national metrology standards.
*   To establish traceability, a calibration instrument's accuracy must be verified by an instrument of higher accuracy.
*   Manufacturers often send their calibration equipment to **ISO 17025 certified metrology laboratories** for calibration on higher-performing equipment.
*   Once verified, this equipment establishes traceability for all sensors it calibrates, ensuring that all standards can be traced back to the highest accuracy instruments at national laboratories.

The **ISO 17025 standard** is used by calibration laboratories to demonstrate competence and generate valid calibration results.
*   It is published by the **International Organization for Standardization (ISO)**, which is an umbrella group for 162 national standards bodies.
*   ISO 17025 promotes global cooperation, allowing test reports and calibration certificates to be shared across national boundaries without further testing.
*   The standard mandates that calibration labs document all processes, procedures, and test equipment, correct non-conformances, and continuously improve their services.
*   Accredited ISO 17025 laboratories issue a **calibration certificate** for each piece of customer equipment, typically on an annual basis.
*   A typical certificate includes a description of the device, its performance (as found and as adjusted), and details of the internal lab equipment used for calibration.

#### Calibration Equipment Examples

Specific equipment is used for calibrating different types of sensors:
*   **Temperature Calibration Baths**:
    *   **For RTD and Thermistor Probes**: Involves inserting the probe and a highly accurate platinum RTD reference thermometer into a cavity containing **liquid salt**. Liquid salt offers a high upper temperature limit and wide temperature range, though it can be corrosive to steel. Typical accuracy is 1% for a range of 150-550°C.
    *   **For Thermocouple Probes**: Utilizes a **constant temperature block** made of aluminum oxide with multiple holes for probes, heated by wire-wound cartridges. A specially calibrated thermocouple controls the block's temperature. Typical accuracy is 5% for a range of 150-1200°C, sufficient for common thermocouple types like J, K, E, and T.
*   **Infrared Sensor Calibrators**: These units feature a **black body plate** heated internally to a known temperature, controlled by a thermocouple. The black body plate is designed with an emissivity near one to radiate 100% of its thermal energy. The user shines the infrared thermometer on the plate and adjusts internal constants if the reading differs from the plate temperature. Typical accuracy is 1% for a range of 50-500°C.
*   **Pressure Calibration Equipment**:
    *   **High Pressure Pump System**: A pump fills a reservoir with pressurized fluid (up to 3,000 bar). A reference digital pressure gauge measures the actual pressure, and the sensor under test is adjusted to match this reference. Reference gauges should have an accuracy of 0.1% to 0.2%.
    *   **Dead Weights Pressure Calibrator**: Calibrated **dead weights** are used instead of a digital gauge. The weights press on a fluid cylinder above a pressure reservoir, creating a balance of forces. The calibration pressure is precisely determined by the weight of the dead weights divided by the piston's area, remaining stable for calibration.
*   **Load Cell Calibration Equipment**:
    *   **Tensile Load Cells**: A yoke is used to hang dead weights from the bottom of the load cell, with the top connected to a stationary frame, creating a precise **tensile load**.
    *   **Compressive Load Cells**: Dead weights are placed on top of a yoke, creating a precise **compressive load**. Users adjust internal calibration constants to match the load cell's output to the known dead weight.

### Current Control of a Brush DC Motor

Module 2 also includes a lab demonstrating **current control of a small brush DC motor** using a PSoC chip. This application is common and fundamental to understanding more complex machines like industrial robots.
*   The PSoC chip can manage current control through hardware, software, or a combination.
*   Key external components include the motor, a power transistor, a small current sensing resistor, and an external flyback diode.

#### Current Sensing Methods

*   **Ground Reference Current Sense**: Involves measuring current with a resistor that has one leg connected to ground. The PSoC chip operates within a limited voltage range (e.g., 0-5V), so voltages outside this range must be scaled down to prevent damage. If the voltage across the sense resistor exceeds approximately 5.5V or goes below ground, the PSoC chip can be damaged. Solutions include external circuitry to limit current or clamp input voltages.
*   **High Side Current Sensing**: In applications where neither leg of the current sense resistor can be grounded and both sides are at voltages outside the microcontroller's direct interface range (e.g., 42V), special **high side current sensing integrated circuits (ICs)** are used. These ICs can translate common mode voltages across the resistor into a range suitable for the microcontroller.

#### Current Sense Resistor Selection

The value of the current sense resistor is critical:
*   It should be **small enough** that the voltage developed across it does not significantly impact other circuit operations. For example, a 0.6 ohm resistor with 1 amp of current produces 0.6 volts.
*   It should **not be too small**, as a smaller value results in a smaller voltage, requiring more amplification for the ADC. This also makes the signal more susceptible to noise pickup, potentially leading to a poor Signal-to-Noise Ratio (SNR).
*   **Wire-wound resistors should be avoided** for current sensing because their inductive nature makes them sensitive to the rate of change of current, not just the current itself.

#### Motor Control Circuit Operation

A basic circuit for motor current measurement and control involves a **power Field-Effect Transistor (FET)**, which is rapidly turned on and off at a specific duty cycle. A higher duty cycle results in higher current in the motor. The current is measured via a sense resistor connected to analog input pins of the PSoC chip.
*   **Back EMF**: When a brush DC motor spins freely, it generates back electromotive force (EMF), which can limit the current. Holding the motor stalled prevents back EMF buildup, simplifying current control.
*   **Control Loop**: The system operates as a hybrid hardware/software setup. Software sets a **desired current level** via a Digital-to-Analog Converter (DAC). Hardware measures the actual current (voltage across the sense resistor), compares it to the DAC's output, and controls the FET based on this comparison. Software can adjust the DAC level, potentially based on control algorithms like PID (Proportional-Integral-Derivative) control for position error.
*   **Inductive Rise Time**: When the FET turns on, the current in the motor rises slowly due to its inductive properties.
*   **Initial Transient Spike**: A spike occurs when the FET turns on, attributed to circuit parasitic capacitance. This spike does not represent motor current and must be ignored by software by implementing a short delay before current measurement.
*   **Flyback Diode**: A power diode is essential due to the motor's inductive nature. When the FET turns off, the motor's current needs an alternative path to flow, preventing a sharp voltage rise that could damage the FET. The diode provides this path, creating a circular current flow and clamping the voltage. Current can only be measured when the FET is on, as it flows through a different path when the FET is off.
*   **Voltage Limitations**: The voltage across the current sense resistor must not be too high, as the PSoC chip has voltage input limits, and the FET requires sufficient gate-source voltage to turn on.

#### Design Improvements

*   **Sample and Hold**: A Sample and Hold circuit can be used to capture and store the measured current value (valid when the FET is on) for subsequent Analog-to-Digital conversion. However, at very low duty cycles, this circuit might incorrectly sample the initial transient spike, leading to inaccurate readings.
*   **Ringing Transient**: An initial observation of the switching transient revealed ringing behavior, which was identified as being caused by the **absence of a local bypass capacitor** on the circuit board. The inductance of long wires connecting to the power supply, combined with the power supply's capacitance, forms energy storage elements that can exchange energy, leading to oscillations.
*   **Bypass Capacitor Solution**: Adding a sufficiently sized **bypass capacitor** directly on the board near the power consumption point provides a local source of electrons, reducing the need for current to flow through long, inductive wires. This significantly reduces ringing and shortens the transient.
*   **Improved Dynamic Range**: A shorter transient, achieved by adding a bypass capacitor, allows for a shorter blanking interval. This enables the circuit to control the current closer to zero, resulting in a **better dynamic range** and potentially improved accuracy.
