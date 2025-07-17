The third module of the specialization on embedding sensors and motors covers **position and acceleration sensors, as well as gyroscopes**.

### Position Sensors

**1. Capacitive Detection Sensors**
*   **Function:** Respond when an object comes within range, typically used on manufacturing floors.
*   **Detection Capability:** Designs exist to detect both **conductive and non-conductive objects**.
    *   **Ungrounded sensors** are limited to detecting **conductive objects**. In this design, one electrode is within the sensor, and the conductive object acts as the second electrode. A constant AC current flows, and zero voltage is registered until a conductive object enters the sensing field, at which point an AC voltage indicates its presence. These sensors are sensitive and their output can be affected by dirt and moisture due to changes in relative permeability. They work best when detecting the same object consistently. Their sensitivity is typically one volt per 100 microns of object distance.
    *   **Grounded sensors** must be used to detect **non-conductive objects**. Here, both measuring and ground electrodes are located inside the sensor. An AC current generates a measuring field. When a non-conductive object enters this field, its higher relative dielectric constant causes the sensor's capacitance to increase, and since charge is constant, the measured voltage decreases.
*   **Detection Range:** Limited, roughly **30 millimeters or less** for the largest sensors, and well under one millimeter for small ones.
*   **Mounting:** Usually mounted directly to production equipment.
*   **Principle of Operation:** Changes in the area, diameter, or relative permeability within a flat plate capacitor cause its capacitance to change.
*   **Applications:**
    *   Indicating **rough fill levels of granules** in a funnel by using two sensors.
        *   Both sensors detecting presence indicates a full or overfilling funnel.
        *   High fill sensor detecting presence, but low fill sensor not, indicates the level is between sensors.
        *   Neither sensor detecting presence means the funnel is empty or nearly empty.
    *   Detecting the **presence of a bottle** on a conveyor to trigger liquid pouring.
    *   Checking the **stability of air gaps** between the stator and rotor in AC induction motors.
*   **Calibration and Accuracy:**
    *   **Nominal sensing distance (SN)** is the distance at which a standard target is first detected.
    *   Factory calibration typically uses a grounded square steel target, 1 millimeter thick, with a side length equal to the sensing face diameter or three times SN, whichever is larger.
    *   Detecting objects with curved or rough surfaces, or with significantly skewed surfaces relative to the sensor, can cause **accuracy errors** because the electric field shape changes, potentially leading to non-detection or inaccurate voltage measurements. Correction factors may be required.
*   **Example Specifications (Grounded Sensor):**
    *   IP 65 rating: indicates it can get wet but not be immersed.
    *   Nominal sensing distance: 10 millimeters, with higher detection likelihood down to 2 millimeters.
    *   Ambient temperature range: -25°C to +75°C, with a **15% sensor output temperature drift**. For extreme temperatures, the object should be much closer than 10 millimeters.
    *   Output circuit: Normally open, meaning the output switch closes upon object detection.
    *   **Reverse polarity feature:** Prevents sensor damage if miswired.
    *   Housing length tends to be longer for larger nominal detection distances, as capacitance is proportional to plate area and inversely proportional to distance between plates, requiring larger nominal capacitance for greater detection range.

**2. Magnetic Position Sensors**
Magnetic sensors are used for linear and angular position measurements or as switches, for example, in cars. Three types are reviewed: Hall Effect Sensors, Linear Variable Differential Transformers (LVDT), and Eddy Current Sensors.

*   **Hall Effect Sensors**
    *   **Principle:** Based on **Faraday's Law**, where a lateral force acts on electrons moving through a magnetic field, causing them to shift and create a **transverse Hall potential difference (V_H)**. V_H is proportional to the coefficient of overall sensitivity (h), current (i), magnetic field strength (B), and the sine of the angle (Alpha) between the magnetic field vector and the Hall plate. The coefficient (h) depends on the number of free electrons per unit volume and the charge of the electron.
    *   **Measurement:** Measures magnetic field strength and polarity. V_H rises with one magnetic pole and falls with the other.
    *   **Hall Switch:** Closes when one magnetic pole is brought near and opens when the magnet is removed. It does not react to the opposite pole, allowing polarity determination.
    *   **Hall Latch:** Closes when one pole is brought near and remains latched even after the magnet is removed. It only opens when the opposite pole is brought near. Hall latches are often used for non-contact switching in **brushless DC motors**.
    *   **Example Specifications (Hall Switch):** Can include a Hall sensor, linear amplifier, threshold amplifier, and Schmitt trigger on a single silicon chip. Operates over a wide range of supply voltages. Output is logic high or low. Switching frequencies up to 200 kilohertz allow driving TTL logic loads.
        *   **Unipolar devices** turn on at a specified magnetic field (B_OP) from a South Pole magnet and turn off at a magnetic release point (B_RP).
        *   **Bipolar devices** turn on with a South Pole and turn off with a North Pole, making them Hall effect latches.
    *   **Performance:** Depends on ambient temperature. Nominal values are typically quoted at 25°C. Operating and release fluxes decline, and rise/fall times increase with temperature due to decreasing magnet strength (until the Curie point) and increasing terminal resistance.
    *   **Application:** Used to output a signal when a tooth is sensed in a rotating gear, determining both the **RPM and rotational direction** by changes in the magnetic field caused by the ferromagnetic material in the gear teeth.

*   **Linear Variable Differential Transformers (LVDT)**
    *   **Type:** A variable reluctance sensor that uses a ferrous non-magnetic core to alter the magnetic resistance of the flux path.
    *   **Principle:** An AC excitation current in the primary coil induces a steady AC voltage in the secondary coil. The amplitude of this induced voltage depends on the flux coupling.
        *   When the core is at the center (null point), induced voltages in the secondary coils cancel, resulting in **zero output voltage (E_out)**.
        *   Moving the core from the center creates an imbalance, causing E_out to increase linearly with core displacement within the operating range.
        *   **Direction of displacement** is determined by the phase angle relative to the primary voltage; the DC output changes sign as the core passes the null point.
    *   **Applications:**
        *   Measuring **object displacement** by permanently attaching the object to the moving core.
        *   As a **level sensor** for liquids in tanks, where a float is coupled to the LVDT core via a non-magnetic, corrosion-proof stainless steel rod. The transmitter records the core position, correlates it to liquid level, and transmits data.
    *   **Electronic Interface:** Connected to a synchronous detector that rectifies the sine wave output to a DC voltage. This detector typically includes an analog multiplexer and a zero-crossing detector, which converts the LVDT's sine wave to square pulses. The zero-crossing detector is trimmed for zero output at the null position.
    *   **Advantages:**
        *   Virtually **friction-free motion** (core does not touch coils), leading to long life and fine resolution (limited by sensor noise).
        *   No damage due to **overtravel** of the core.
        *   **Highly repeatable zero position**.
        *   **Absolute output response:** retains its position if power is lost and then restored.
    *   **Limitations:** Displacement readings become non-linear and inaccurate if the core moves too far from the center.
    *   **Travel Ranges:** Available from 1 to 300 millimeters.
    *   **Applications:** Preferred for precise servo position control, machine tools, robots, medical equipment, and ATMs due to high vibration tolerance and accuracy.
    *   **Example Specifications:** Can operate on low nominal voltage (e.g., 3 volts) with specific input frequencies (e.g., 2.5 to 3 kilohertz). Non-linearity can be as low as 0.25% of full scale, with repeatability and hysteresis errors under 0.01%. Can tolerate vibrations up to 20 g's and survive 1000 g shock loads.

*   **Eddy Current Sensors**
    *   **Detection Capability:** Sense only **conductive but non-magnetic objects**.
    *   **Principle:** One coil serves as a reference, while another senses magnetic currents induced in the conductive object. These induced **eddy currents** produce a magnetic field that opposes the sensing coil's field, reducing the field in the sensing coil relative to the reference coil. The closer the object, the greater the field reduction.
    *   **Object Thickness:** The object's thickness must exceed the depth where eddy currents are produced. This depth (delta) is calculated as 1 / sqrt(pi * F * mu * Sigma), where F is frequency, mu is magnetic permeability of free space, and Sigma is electrical conductivity.
    *   **Limitation:** Due to the thickness requirement, they can only detect relatively thick conductive objects, not metalized films or tinfoil.
    *   **Shielding:**
        *   **Unshielded sensors** detect objects on the side and far out front, but cannot be installed near metal structures as they cannot differentiate between the structure and the target object.
        *   **Shielded sensors** have a metal guard around the coils that focuses the magnetic field to the front, allowing installation in metal structures with minimal impact on detection range. Commercial eddy current sensors are typically shielded.
    *   **Application:** Routinely used in pavement underneath **traffic lights** at quiet cross streets to detect the presence of a car. When a vehicle stops above an eddy current loop, the magnetic flux induces eddy currents in the vehicle's metal components, which oppose the originating flux. This reduces the loop inductance, causing the oscillator's frequency to increase, signaling vehicle presence to the loop controller and changing the traffic light.

### Acceleration Sensors (Accelerometers)

*   **Function:** Generate an electrical signal in response to the acceleration of their internal components.
*   **Measurement:** Used to monitor vibrations in structures (e.g., automobiles, engines, crash tests) and measure impact on dummies or vehicles during collisions. They can also estimate fundamental frequencies under shock or impulse loads.
*   **Internal Mechanism:** All accelerometers contain a **mass-spring-damper system** where a **proof mass** deflects under external acceleration, producing an analog or digital signal.
    *   The differential equation of motion is: mass * acceleration + damping constant * velocity + spring constant * deflection = applied cyclical force. (mx'' + cx' + kx = F_0 sin(omega t) for forced vibrations).
*   **Damping and Oscillation:**
    *   The system is designed for an **underdamped solution**, meaning its internal components vibrate when externally excited.
    *   If overdamped, there are no oscillations, rendering the accelerometer useless.
    *   **Damping ratio (zeta)** is defined as c / (2 * sqrt(km)).
    *   **Undamped natural frequency (omega_n)** is sqrt(k/m).
    *   **Damped natural frequency (omega_d)** is omega_n * sqrt(1 - zeta^2).
    *   The system oscillates at the damped natural frequency with exponentially decaying amplitude.
    *   At **critical damping (zeta = 1.0)**, motion decays to zero without oscillation in minimum time.
*   **Analogies with Electrical Systems:** A parallel mass-spring-damper system is analogous to a series RLC circuit.
    *   Mass (m) corresponds to inductance (L).
    *   Damping coefficient (c) corresponds to resistance (R).
    *   Spring constant (k) corresponds to the inverse of capacitance (1/C).
    *   The methods of solution and graphical representations of transfer functions are consistent between mechanical and electrical systems.
*   **Accelerometer Design for Vibration Measurement:**
    *   For an accelerometer to accurately measure structural vibrations, its output transfer function (accelerometer output / structure output) must be near one, and the phase angle near zero.
    *   This requires the **accelerometer's natural frequency (omega_n) to be high** compared to the frequency of the structure being measured. This is best achieved with a **small proof mass (m) and high stiffness (k)**.
    *   The accelerometer is useful for measuring machine acceleration only when the error term is near one, which occurs at low frequency ratios (omega/omega_n).
    *   The useful range can be extended by designing the accelerometer with a **damping ratio of 0.7**. Piezoresistive and capacitive accelerometers are commonly designed with this damping ratio.
    *   Piezoelectric accelerometers, due to their quartz crystal's extreme stiffness, have very high natural frequencies and wide frequency ranges despite low damping.
*   **General Specifications:**
    *   Often, the linear response range is quoted up to the **3 dB point** (where output is 3 dB times structure output), which can extend to roughly 1 kilohertz for some MEMS accelerometers.
    *   Spec sheets typically list **resonance frequency** (e.g., 21 kilohertz) instead of natural frequency.
    *   Sensor output is in millivolts and requires **amplification**.
    *   **Cross-axis sensitivity** describes how much vibrations normal to the major axis are picked up.
    *   Sensitivity often varies with temperature, necessitating measurements at consistent ambient temperatures for accuracy.
    *   To avoid aliasing of the accelerometer signal, a sufficient sample rate (e.g., 32 kilohertz for 10 kilohertz vibrations) and appropriate filtering (e.g., two-pole R and C filter) are necessary before input to an ADC.
    *   Real sensors exhibit **statistical variance** in performance due to production processes, so manufacturers sharing statistical data is beneficial.

**Types of Accelerometers:**

**1. Piezoelectric Accelerometers**
*   **History:** The first commercial accelerometers.
*   **Piezoelectric Effect:** The generation or redistribution of electric charge within a crystal when subjected to mechanical stress. Discovered in 1880 by Jacques and Pierre Curie.
    *   In a quartz crystal, compressive or tensile loads deform the lattice, shifting silicon (positive) and oxygen (negative) ions, creating an electric charge imbalance.
    *   Attaching conductive electrodes to the crystal makes it a capacitor, with voltage across electrodes proportional to the force.
    *   The piezoelectric effect is reversible, meaning an applied voltage can produce mechanical stress.
    *   Voltage output on electrodes is directly proportional to the force.
*   **Accelerometer Design:** The piezoelectric crystal is sandwiched between a proof mass and the base. The proof mass's acceleration exerts force on the crystal.
    *   The crystal is extremely stiff, eliminating the need for an external spring.
    *   Damping within the crystal is small, but its high natural frequency allows a wide frequency range.
*   **Materials:**
    *   **Quartz:** Offers best long-term stability and does not exhibit the pyroelectric effect (no spurious voltage from temperature changes). However, it has lower charge output than ceramics, high open circuit voltage sensitivity, and limited geometries.
    *   **Ceramics:** Can be molded into various shapes and then polarized. They offer good dimensional flexibility and very high charge output, compatible with microelectronic charge amplifiers. Ceramics are pyroelectric, limiting their use to smaller temperature ranges unless specialized and expensive.
*   **Geometries (Evolution):**
    *   **Compression Mode (Original):** Crystal preloaded with seismic mass. High sensitivity and natural frequency, but sensitive to base strain.
    *   **Flexure Mode:** Crystal bends around a fulcrum. High sensitivity, small, low-cost. Fragile under shock loads, used for very short senses.
    *   **Shear Mode (Most Common Today):** Crystals mounted radially around a center post with a seismic mass outboard. Shear forces act on crystals during acceleration. This design isolates the crystal from base strain while maintaining sensitivity. Tri-shear sensors use three elements at 120-degree angles.
*   **Advantages:**
    *   **Rugged construction**, no drift.
    *   Can be used at **high temperatures** due to no internal electrical resistance.
    *   Generally have a **wider frequency response** compared to capacitive or piezoresistive types.
    *   Can measure very **high accelerations** (up to 6,000 g's) and withstand extreme shock loads (20,000 g's) without permanent damage.
*   **Disadvantages:** Produce a small charge output (picocoulombs per g), requiring a **charge amplifier** to measure the signal. Modern miniaturization means their package size is now considered large.
*   **Example Specifications (Triaxial Shear Mode):** Flat transfer function until 12.6 kilohertz, resonance frequency of 42 kilohertz. Specifies maximum and minimum mounting torques to ensure proper vibration transmission without preloading. May have a small amount of **max transverse sensitivity** (e.g., 4%), meaning axial measurements can include transverse vibrations. Can operate over a wide temperature range (e.g., -74°C to 250°C) with a low temperature coefficient of sensitivity (e.g., 0.05% per °C).

**2. Piezoresistive Accelerometers**
*   **Machined Design (Older):** A proof mass is bonded to a cantilever beam, with maximum bending strain at the beam's base measured by four strain gauges in a bridge circuit (two in tension, two in compression).
    *   **Limitations:** Lower dynamic range and frequency response compared to piezoelectric accelerometers. Can measure up to 200 G's (compared to 6,000 G's for piezoelectric), as higher accelerations would break the strain gauges or beam. Resonance frequency is lower (e.g., 4,000 hertz), limiting measurable frequencies. Size is roughly double that of piezoelectric models.
    *   **Significant temperature effect on sensitivity:** Sensitivity can change substantially across the compensated temperature range (e.g., 10% change from 21°C to 93°C). While a Wheatstone bridge reduces apparent strain from temperature coefficient of resistance (TCR), it's not perfect due to individual gauge manufacturing variations.
    *   Damping is provided by silicone oil, typically designed for 0.7 (70% of critical damping) for minimum response error.
*   **MEMS Design (Modern):** The proof mass is silicon with thin beams connecting to a rigid silicon structure. **Strain gauges (piezoresistors)** are grown in the beam corners and arranged in a **Wheatstone bridge**.
    *   The four beams can vibrate in any direction depending on acceleration. Air damping occurs between beams and their encasement.
    *   Eight piezoresistors are arranged in pairs to maximize bridge output and reduce thermal effects. For example, outside corner sensors are in tension, and inside corner sensors are in compression when the beam moves in a specific direction.
*   **Example Specifications (MEMS):** Models offer ranges from 50 G's to 6,000 G's, with natural frequency, response, and range increasing for higher-end models (due to stiffer design for high accelerations).
    *   Transverse sensitivity is typically better than machined versions (e.g., 3%).
    *   Thermal sensitivity shift remains a concern (e.g., -0.15% per °C across the operating range can result in double-digit percentage shifts), making them best used near room temperature for highly accurate results.

**3. MEMS Capacitive Accelerometers**
*   **Principle:** Acceleration is proportional to the **change in capacitance** of a moving mass suspended by micro-machined beams.
*   **Structure:** Consists of a proof mass, capacitive sensing fingers, and folded springs connecting the proof mass to the substrate. The proof mass oscillates, moving the sensing fingers between static fingers, causing a change in capacitance.
*   **Advantages:**
    *   High accuracy, excellent stability, low power dissipation, and easy integration into embedded circuits.
    *   Minimal **temperature drift** compared to piezoresistive accelerometers.
*   **Disadvantages:** Typically have a **low frequency response (under 500 hertz)**. This limitation is due to the low stiffness of the beams relative to the mass, which results in a low natural frequency.
*   **Sensing Circuitry:** Capacitive sensitivity is very small (e.g., 0.16 femtofarads per g). A **differential sensing bridge** is formed by wiring the capacitors. The small millivolt signal undergoes charge amplification, signal conditioning, demodulation, and low-pass filtering before being sent to a **sigma-delta ADC** (often used for low signal bandwidth and high resolution). The digital output is then processed via I2C or SPI interfaces.
*   **Multiple Axis Design:** Can be built as two separate accelerometers oriented at 90-degree angles, or by arranging electrodes and springs for multi-axis motion around a movable mass.
*   **Example Specifications (Single Axis MEMS):** Dynamic range is often low (e.g., only 10 Gs), much lower than piezoelectric or piezoresistive types.
    *   **Zero G voltage** specifies the expected voltage range at zero acceleration due to a finite capacitance difference.
    *   Sensitivity is typically high (e.g., 194-206 millivolts per G).
    *   The primary limiting factor is the **frequency response (bandwidth)**, typically around 400 hertz.

### Gyroscopes

*   **Function:** Measures the **rate of rotation around an axis**.
*   **Applications:**
    *   Aircraft navigation (turn coordinator, heading indicator, compasses for unmanned aircraft).
    *   Stabilizer systems (e.g., for boats).
    *   Consumer electronics (phone apps, video games, image stabilization).
*   **History:** Mechanical gyroscopes invented in the early 19th century, later combined with electric motors for naval navigation.
*   **Mechanical Gyroscope Principle:**
    *   A gimbal allows the rotor to spin without external torque.
    *   Due to **conservation of momentum**, the gyroscope resists forces that try to change its orientation, maintaining a constant angular orientation if no torque is applied.
    *   **Aircraft Position Sensing:** Mounted in a vibration-proof housing at a fixed angle. As the aircraft rotates (e.g., rolls), position sensors rotate relative to the gyroscope, allowing the roll angle to be measured.
    *   **Angular Velocity Measurement:** When an aircraft rotates around an input axis (roll, pitch, or yaw), the net torque applied to the gyroscope causes **precession** (change in the orientation of its rotational axis). The gyroscope senses this angle of rotation, and a motor rotates the input axis in the opposite direction to negate the precession. The amount of rotation divided by time yields the angular velocity of the gyroscope, which equals the aircraft's angular velocity. Angular acceleration can be derived through differentiation.

*   **MEMS Vibratory Gyroscope**
    *   **Principle:** Measures angular velocity using the **Coriolis effect**.
    *   **Mechanism:** A proof mass, suspended by comb-fingers acting as springs and dampers, is vibrated along one axis (e.g., Y-axis) by an electrostatic drive. When the sensor rotates around a perpendicular axis (e.g., Z-axis), the Coriolis force causes the proof mass to also vibrate along a third mutually perpendicular axis (e.g., X-axis). This X-axis vibration is sensed by changes in the capacitance of parallel plates along that axis.
    *   The magnitude of Coriolis acceleration is **-2 * omega * v**, where 'v' is the linear velocity of the proof mass and 'omega' is the angular velocity of the structure around the rotation axis. The Coriolis force is the proof mass multiplied by this acceleration.
*   **Example Specifications (Three-axis MEMS Capacitive Gyroscope):** Low-power, includes a sensing element and an IC interface (SPI or I2C).
    *   Full scale output is selectable (e.g., ±245, ±500, or ±2,000 degrees per second).
    *   **Zero-rate level** describes the output signal when no angular rate is present, resulting from internal mechanical stress and can change after soldering.
    *   Sensitivity is typically in millivolts per degree per second.
    *   **Non-linearity** can be erratic (e.g., nominal 0.2% to worst-case ±5% of full scale). These devices are difficult to calibrate and maintain consistently during manufacturing.
*   **Drive Circuitry:** Requires a charge amplifier to convert the charge from the capacitance circuits (one for each axis) into voltages. These sinusoidal signals are then fed into a low-pass filter and an ADC for angular velocity readout. Post-digital filtering is often required for stable outputs.
