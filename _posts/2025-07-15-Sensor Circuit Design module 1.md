Here's an extraction of the knowledge-based information from the sources, with colloquial language removed and important points bolded for clarity:

### General Sensor and Actuator Concepts

*   **Sensors are integral to most electronic products and drive the "Internet of Things" technology revolution**.
*   **Applications of sensors** include:
    *   **Process sensors** in petrochemical, pharmaceutical, and semiconductor industries for chemical reaction measurement and control.
    *   **Position sensors** in vehicles and aircrafts.
    *   **Motion sensors** in vehicles, aircrafts, smartphones, and security systems.
    *   **Ergonomic sensors** in tablets, PCs, and phones.
    *   **Chemical sensors** for fire and toxic vapor hazard protection.
    *   **Electrical sensors** in lab instruments and security systems.
*   **Sensors in smartphones**:
    *   **Thermistors** sense internal temperature to prevent overheating and shut down the device.
    *   **GPS sensors** enable navigation applications like Google Maps.
    *   **Proximity sensors** near the earpiece turn off the screen during calls to save battery.
    *   **Gyroscopes** enable compass applications.
    *   **Capacitive sensors** on touchscreens detect finger input.
    *   **Light sensors** adjust screen brightness based on ambient light.
    *   **Battery sensors** correlate charge level to remaining battery life.
*   **Sensors in modern automobiles**:
    *   **Temperature sensors** monitor engine combustion, radiator cooling, and cabin comfort.
    *   **Pressure sensors** ensure sufficient oil for lubrication and proper tire pressure for safety.
    *   **Flow sensors** ensure sufficient air intake for gasoline engine combustion.
    *   **Position sensors** monitor engine throttle, crank, and camshaft angles.
    *   **Radar detectors** are critical for autonomous vehicle software.
    *   **Accelerometers** detect imminent collisions for airbag deployment.
    *   **Dashboard touchscreens** use capacitive sensors.
    *   **Oxygen sensors** monitor intake for engine combustion.
    *   **Oxygen and hydrogen sensors** are used in experimental fuel cells for battery-operated cars.
    *   **Battery sensors** are essential in all cars, whether gasoline or battery-operated.
*   **Signal Processing for Sensors**:
    *   Most measured quantities (e.g., temperature, pressure) are continuously varying.
    *   **Sensor data must be converted to a digital format** for interpretation by a microprocessor.
    *   **Excitation** is the process of applying power to a sensor to produce a usable output.
    *   **Signal conditioning** involves analog circuitry that excites, filters, and amplifies the raw sensor signal.
    *   The conditioned signal is sent to an **Analog-to-Digital Converter (ADC)**.
    *   ADC outputs are typically 8, 12, 16, or 24 bits.
    *   ADC data is usually converted to a **serial format** (e.g., I2C, SPI, RS-232).
    *   Signal conditioning circuitry is located **close to the sensor** to shield against external interference, as raw sensor output is easily corrupted.
    *   Once converted, the **digital signal can be transmitted over long distances with minimal error**.
*   **Microcontrollers for Sensor Systems**:
    *   It is beneficial to use a **microcontroller**, which consists of a microprocessor with a built-in ADC.
    *   The **Cypress PSoC series** of microcontrollers are used in the course, containing amplifiers, multiplexers, comparators, timers, counters, and shift registers.
    *   PSoC microcontrollers minimize discrete components between the sensor and the microcontroller.
    *   They are **hardware programmable parts**, allowing electronic circuits to be implemented as real hardware inside the chip, interacting seamlessly with code.
    *   The design environment for PSoC is **PSoC Creator**, which includes schematic capture and a code editor.
*   **Actuators**:
    *   **Four classes of actuators** are used in automobiles, production equipment, and home appliances.
    *   **Hydraulic actuators** use pressure from compressed oil to push large cylinders in construction equipment (lifts, cranes, excavators). They are characterized by **slow speed of response** due to oil compression time and high gear ratios.
    *   **Pneumatic actuators** offer a **faster speed of response** due to faster air compression. They are common in production assembly equipment but are noisy, and small leaks lead to large compression losses.
    *   **Electrical motors** convert electrical energy to rotary motion and are extensively interfaced with sensors.
    *   **Mechanical actuators** (e.g., gears, belts, lead screws) either boost torque or convert rotary motion to linear motion.
    *   **Electrical actuators come in three types**:
        *   **Stepper motor**: Has multiple coils organized in phases; energizing coils sequentially allows precise step rotation.
        *   **Brushed DC motor**: Has a coil generating a magnetic field around an armature; opposing forces from motor casing magnets cause rotation. Continuous rotation is achieved by reversing current on each half cycle. Brushes wear rapidly and require frequent replacement.
        *   **Brushless DC motor**: Resolves the brush wear issue by using permanent magnets rotating around a fixed armature; an electronic controller switches phase to windings for rotation.

### Thermal Sensors

*   There are **four major types of thermal sensors**: thermocouple, resistance temperature detector (RTD), thermistor, and infrared sensor.
*   All but infrared sensors are commonly used in embedded systems.
*   **The technology used in thermal sensors determines its suitability for applications**.
*   Each type has **limiting aspects**.

#### 1. Thermocouples

*   **Principle**: Consists of **two wires of dissimilar metals joined at a heated junction** and connected to circuitry at the other end. The **voltage read is proportional to the temperature at the heated junction and the choice of metals**. This phenomenon is called the **Seebeck effect**.
*   **Temperature Range**: Can measure temperatures **up to 1800°C**. Certain alloy pairs, like Type C, can measure up to **2300°C** with specific protection.
*   **Characteristics**:
    *   **Highest measurement range** among thermal sensors.
    *   Subject to **drifting over time** due to metallurgy changes with thermal cycles, requiring **annual recalibration**.
    *   **Bare thermocouple wires** (0.1 to 3 mm diameter) are fragile but offer fast response times. Protection inside a metal sheath with ceramic insulation is common for durability at high temperatures.
    *   The **United States National Institute of Standards (NIST) publishes ITS-90**, a standard listing thermoelectric voltages for thermocouple alloy pairs at 1°C intervals, usable for table lookup software.
    *   **Alloy pairs are designated by letters** (e.g., J, K, T, S). **Type K is the most popular** due to its broad temperature range and low cost.
    *   **Nominal accuracy is 1% of reading**. Individual calibration by the supplier can improve this.
    *   **ASTM spec 230 governs accuracy**: nominally 0.75% of reading, but at least 2.2°C. This means errors can be up to 2.2°C below 293°C, and up to 0.75% above 293°C.
    *   **Thermoelectric voltage versus temperature curves are non-linear**, showing small negative readings at very cold temperatures.
    *   **Quasi-linearity can be assumed for small temperature changes** using the local slope 'b'. Calculations should be in degrees Kelvin to avoid sign issues for temperatures below 0°C.
*   **Applications**:
    *   **Metal and semiconductor fabrication**.
    *   **Low-cost contact temperature measurements above 800°C**.
    *   Heavy usage in **aerospace, heat treating, and metal forming industries**.
    *   Can be used for their **lower cost than RTDs** if annual recalibration/replacement is acceptable.
    *   Cost-effectiveness is a significant factor in applications requiring **hundreds of measurement points** (e.g., automotive/aerospace engine test stands).
    *   Popular in **injection molding machines** to monitor plastic melt temperature.
*   **Packaging**: Available as straight probes with connectors, penetration probes (for cooked meat), or screw-in probes for furnaces.
*   **Cold Junction Compensation (CJC)**:
    *   **Problem**: Connecting thermocouple leads to a voltmeter creates additional junctions of dissimilar metals (e.g., Constantan lead to copper terminal), introducing a **back-EMF thermoelectric voltage** that corrupts the primary voltage reading.
    *   **Historical Solution (Ice Point Reference)**: Fifty years ago, junction J2 (the reference junction) was placed in an **ice bath (0°C)**, forcing a known temperature.
    *   **Modern Solution**: An **isothermal metal block** is used instead of an ice bath. The Law of Intermediate Metals states that inserting a third metal between two dissimilar metals at an isothermal block does not change the thermoelectric voltage. This allows simplified circuits where intermediate connections on the block can be ignored.
    *   **Process of CJC**:
        1.  Measure the temperature (T2) of the isothermal block using a **thermistor or RTD** (thermistor is preferred for small package size and range suitability).
        2.  Find the **equivalent thermoelectric voltage (V2)** for T2 using thermocouple lookup tables (e.g., ITS-90).
        3.  Measure the **total voltage (V)** at the voltmeter.
        4.  Calculate the voltage from the heated junction: **V1 = V + V2**.
        5.  Use **thermocouple lookup tables with V1 to determine the actual temperature T1**.
    *   CJC is implemented in every process instrument with thermocouple input. For example, the GRAPHTEC model 840 data logger uses a thermistor inside its terminal block to measure the ambient block temperature (T2).
*   **Installation Considerations**:
    *   Probes can be bent at a right angle with a **minimum bend radius of half an inch (12 mm)**.
    *   A **minimum installation depth of 3 inches (76 mm)** is required for accurate readings to prevent thermal mass outside the furnace from conducting heat away, which would lead to incorrectly low readings.
    *   **Sheath material** (e.g., Inconel vs. 316 stainless steel) is crucial; Inconel is needed for higher temperatures (e.g., 1249°C for Type K) to prevent corrosion.

#### 2. Resistance Temperature Detectors (RTDs)

*   **Principle**: Works on the principle that the **resistance of metal (typically platinum) increases as temperature increases**. The relationship for platinum is nearly linear.
*   **Composition**:
    *   Historically: Coils of **platinum wire wound around a ceramic core or glass tube**, protected by a glass, ceramic, or metal sheath.
    *   Modern: **Thin film RTDs** made by depositing thin, parallel layers of platinum onto a ceramic substrate; the pattern length determines the resistance.
*   **Temperature Range**: Typically **-200°C to 800°C**.
*   **Characteristics**:
    *   **More precise and stable than thermocouples**.
    *   **Excellent accuracy and linearity**.
    *   **Stable over many years**, typically no need for annual recalibrations.
    *   Require an **accurate current source**.
    *   Require **three- or four-wire RTD circuits** to nullify the effects of lead length on resistance measurement.
    *   The **European standard, DIN or IEC 60751, specifies a resistance of 100 ohms at 0°C and a temperature coefficient of resistance (TCR) of 0.00385 ohms per ohm degree C** between 0°C and 100°C, aiming for a nearly straight line for temperature vs. resistance.
    *   **Two types of specs for tolerances**: **Class A** (0.06 ohms tolerance at 0°C) and **Class B** (0.12 ohms tolerance at 0°C).
    *   While very linear, they are **not perfectly linear** and require calibration for perfect linearity.
    *   **Long-term drift stability is tiny**.
    *   Manufacturers also sell **500 ohms and 1000 ohms RTDs**, which improve system accuracy for three-wire configurations because lead wire resistances become comparatively smaller.
*   **Applications**:
    *   Popular in **pharmaceutical and biotechnology industries** due to accuracy and repeatability requirements for strict audits.
    *   Used where **high-accuracy temperature measurement is needed** within their range (-200°C to 800°C).
    *   Suitable for applications where the sensor cannot be accessed again after installation (e.g., space shuttle).
    *   Common for **measuring temperature in gas or air streams**, where the bare RTD element is exposed to minimize response time.
    *   A **hot wire anemometer** is an RTD run in reverse.
*   **Packaging**: Available as surface mount chips (e.g., 0603) or as sensors on surface probes to be bolted to objects, and as stainless steel probes designed to screw into tanks or furnaces. Sanitary sensors combine explosion-proof heads with clean construction for good manufacturing practices.
*   **Integration and Linearization**:
    *   **Lead Wire Resistance Issue**: Simple two-wire circuits are flawed because lead wire resistance (e.g., 1-10 ohms) adds a fictional temperature reading (e.g., 1 ohm adds 2.6°C to a 100 ohm RTD reading).
    *   **Wheatstone Bridge**:
        *   Initial attempts with a Wheatstone bridge with three fixed resistors suffer if fixed resistors are exposed to temperature variations.
        *   Adding long lead lengths to remote, stable-temperature resistors recreates the original lead length problem.
        *   **Three-wire configuration**: Uses equal length and same metallurgy lead wires (A and B) on opposite sides of the bridge, causing their resistances to cancel. Lead wire C carries no current. This configuration can lose linearity.
        *   **Four-wire RTD**: Recommended for best accuracy, as it accounts for varying lead wire lengths.
    *   **Linearization**: RTDs are not perfectly linear.
        *   **Polynomial curves** are used to linearize the RTD.
        *   For **temperatures below 0°C**, a **third-order polynomial** is used, requiring calibration at three points.
        *   For **temperatures above 0°C**, a **second-order polynomial** is used, requiring calibration at two points.
        *   Calibration involves **calibrating the RTD to a fixed, more accurate temperature source** at several points.

#### 3. Thermistors

*   **Principle**: Made of **sintered semiconductor or metal oxide particles**.
*   **NTC (Negative Temperature Coefficient) Thermistors**: Exhibit a **large decrease in electrical resistance for a relatively small increase in temperature**. Their resistance decreases drastically as temperature increases.
*   **Characteristics**:
    *   Even with **severe non-linearity**, they are **very accurate**.
    *   **Small package size** makes them ideal for phones and computers.
    *   **Accurate and stable**, similar to RTDs.
    *   Measure temperatures **only up to 200°C**.
    *   Their **high degree of non-linearity requires significant programming** in the embedded system to handle.
    *   **Base resistance** is its resistance at 25°C, common values are **2,252 Ohms and 10,000 Ohms**.
    *   Typical accuracies are **0.1°C to 0.2°C** with good calibration.
    *   Packaged in glass or epoxy, which limits their upper temperature range.
    *   Higher base resistances (e.g., 30,000 Ohms or 50,000 Ohms) are needed for accuracy at higher temperatures up to 200°C.
    *   Response time can be slow (e.g., 10 seconds in air).
    *   Low power dissipation (e.g., 30 MilliWatts).
*   **Applications**:
    *   Wide usage in applications where **small package size and narrow temperature range intersect**.
    *   Commonly used for **overheating protection in smartphones, PCs, and laptops**.
    *   Measures internal temperature of LCDs to **compensate contrast signal** which fades at higher temperatures.
    *   Used in modern **thermostats** (replacing bi-metallic strips).
    *   Integrated into **lithium batteries** for internal temperature measurement to prevent overheating.
*   **Packaging Forms**: Can be bought as an IC (e.g., MCP9700), packaged in a metal probe (like a thermocouple), or as a through-hole part (e.g., 44008RC) for board assembly.
*   **Theory and Integration**:
    *   The **resistance versus temperature curve for an NTC thermistor shows a stunning four orders of magnitude drop in resistance for a 100°C temperature increase**.
    *   The **Steinhart-Hart Equation models this highly non-linear behavior**. It involves logarithmic terms and an inverse relation to temperature, explaining the large fall-off and smooth curve. Temperature must be calculated in degrees Kelvin.
    *   A simplified form of the Steinhart-Hart Equation allows calculation of temperature based on any two points (R and T) and one material constant (beta), making it easier to program in firmware.
    *   **Table lookup methods** can be used if resistance vs. temperature data is available (e.g., from manufacturer's Excel spreadsheet), avoiding logarithmic calculations. This requires sufficient onboard memory.
    *   **Measuring Resistance**: A **simple voltage divider circuit** can be used. However, its accuracy depends on the accuracy of the voltage source and the fixed resistor.
    *   **Accuracy Considerations**:
        *   Standard PSoC reference voltage sources may have 0.5% accuracy, while precision shunt references offer 0.2% accuracy at higher cost.
        *   Using a precision fixed resistor (e.g., 0.25% accurate 10K ohm resistor) can improve accuracy significantly.
        *   The VDAC in a PSoC kit provides a fixed voltage but may have poor accuracy (e.g., 5% gain error). An OpAmp can provide extra current drive.
    *   **Firmware**: Requires code to set up the ADC, sequence inputs, and calculate current and temperature. Nonlinear logarithmic equations can tax the processor, making table lookup a viable alternative.

#### 4. Infrared Sensors

*   **Principle**: The **only non-contact temperature sensor**. Calculates the surface temperature of an object from its **emitted infrared energy**.
*   **Applications**: Excellent for **measuring very high temperatures safely from afar**. Commonly used in hostile environments (e.g., firefighters detecting flames behind walls).
*   **Characteristics and Limitations**:
    *   Normally packaged inside handheld thermometers and **not integrated directly into embedded systems** for in-depth exploration in the course.
    *   Requires knowing the **emissivity of the surface accurately** for an accurate surface temperature.
    *   The surface being measured must be **fully contained within the field of view of the infrared lens**, which can be difficult to determine from afar.
    *   **Cannot measure the temperature inside an object**.
