---
layout: post
title:  "Sensor Circuit Design module 3"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---


Here is the knowledge-based information extracted from the sources, with colloquial language removed and key concepts highlighted:

### Rotary Sensors

Rotary sensors, which include incremental encoders, absolute encoders, and resolvers, are designed based on the demands of their application, with four general categories scaling up in specifications and cost: commercial, servo, industrial, and heavy-duty.

**1. Incremental Encoders**
*   **Function**: Generate a train of electrical pulses whose **frequency is proportional to angular speed**. They are good for measuring speed but not for understanding absolute position.
*   **Applications**: Include motor speed and rate control in machine tools, robots, mixing equipment, and textile equipment. Also used for homing applications in robots.
*   **Operating Principle (Optoelectronics)**: A beam of light from an LED shines through a rotating glass or etched metal disc divided into transparent and opaque sectors. A photosensor detects the light when a transparent sector rotates past it.
*   **Output Signal**: The detected light signal is transformed into a **square wave** and sent to a counter circuit.
*   **Limitations**: The count is subject to loss during power interruption. If power is interrupted, they lose knowledge of position.
*   **Optional Features**:
    *   **Once-per-revolution pulse (Index Mark / Channel Z)**: A separate output that occurs at the same place in each revolution, telling the counter circuit to reset to zero and supplying a mechanical reference for homing.
*   **Resolution**: Defined as the **number of pulse outputs per revolution (PPR)** of the disk. Higher PPR indicates higher resolution. Limits to resolution are determined by the width of the LED beam, the diameter of the disk, and the ability to lay fine pitch, transparent, or opaque tracks.
*   **Channel Configurations**:
    *   **Single Channel (Tachometer)**: Suffices when only the speed of rotation, but not the direction, is needed.
    *   **Quadrature Encoders**: Have dual channels (A and B) phased 90 degrees apart. These two output signals determine the **direction of rotation** by detecting the leading or lagging signal in their phase relationship. Forward rotation is signified when the Channel B signal leads Channel A, and vice versa. PSAT chips have dedicated quadrature circuits.
*   **Enhanced Resolution**: When more resolution is needed, the encoder can count the leading and trailing edges of the pulse streams from both Channels A and B. This doubles the number of pulses read per revolution relative to a single channel, and doubles again the number of events read relative to simply sensing the high level of a square wave, resulting in **four times as much resolution**. This increases the complexity of electronics and firmware and typically results in higher cost.
*   **Assembly**: Consists of an encoder disk, LED, and electronics mounted in a housing with a cover. Ingress protection (IP rating) is determined by the type of sealing and cover used. Components like sensors, counters, and ICs are soldered to a PCB.
*   **Measurement Methods**: Encoders are typically used to measure the speed and position of a rotating device by measuring the encoder period.
    *   **Single Cycle Method**: Measures from rising edge to rising edge on a single channel, providing the period of one encoder cycle. This is the **most accurate way** as variations in the waveform's duty cycle do not affect the measurement.
    *   **Half Cycle Method**: Can introduce errors due to duty cycle variations.
    *   **Quarter Cycle Method**: Provides the fastest update (four measurements per cycle) but is less accurate and rarely used. Quadrature spacing, which should normally be 90 degrees, can vary in practice, causing additional error in quarter cycle measurements.
    *   **Direct Speed Measurement**: Involves counting edges in the pulse train over a defined gate time. Counting every edge on both channels (for quadrature encoders) substantially reduces quantization error. The number of counts is directly proportional to speed, eliminating the need for software inversion. The disadvantage is that the gate time must be long enough to capture a significant number of pulses, resulting in a slower update rate compared to period measurement.
*   **Typical Applications**:
    *   **Motor Speed Measurement**: Mounting an encoder directly to a motor shaft provides a direct sensor measurement. The signal can be transmitted to a PID controller to set up a closed-loop feedback system.
    *   **Cut-to-Length**: An absolute encoder mounted to a roller on a spooling machine (e.g., fabric, wire, thread) can calculate the length of material cut using the formula **Length = π * R * D** (where R is revolutions, D is diameter). Higher resolution leads to more accurate cuts.
    *   **CNC Milling Machines**: Servo motors attached to fine-pitched lead screws use encoders for precise increments. Distance traveled is calculated as **R * P** (where R is revolutions, P is lead screw pitch). Resolution for axes is given by **1 / (P * PPR)**.
    *   **Laser Cutting Tools**: Operate with servo motors and absolute encoders for precision stepping.
    *   **Robots**: High-resolution encoders are used for each axis to maintain precision and prevent angular errors from affecting tool tip accuracy.
*   **Issues**:
    *   **Environmental Contamination**: Dirt, dust, or liquids on the code disk can cause encoder failure.
    *   **LED Failure**: LEDs have a long lifespan but will eventually burn out, causing instant encoder failure.
    *   **Power Interruption**: Incremental encoders lose position knowledge during power outages. Absolute encoders are recommended if power reliability is a concern.
    *   **Mechanical Misalignment**: Failure to ensure the encoder axis is co-linear with the motor axis (measured by **Total Indicated Runout, or TIR**) is a significant problem.
*   **Specification and Purchase Considerations**:
    *   **Mechanical Configuration**:
        *   **C-Face Encoder**: Mounts directly to the face of the motor.
        *   **Round Hole Mount**: Slips onto the back of the motor shaft; must be securely attached to prevent slipping.
        *   **Precision Flex Coupling**: Attaches the encoder shaft to the motor shaft, requiring good alignment and attention to TIR.
        *   All configurations require mounting the encoder to a rigid surface.
    *   **Electrical Considerations**: Primarily about preventing signal noise from disrupting the digital signal. Precautions include separating high voltage machine power and encoder signal lines, using twisted shielded cable for signal lines, maintaining signal ground integrity, and grounding the encoder enclosure.
    *   **Selection Steps**:
        1.  Decide on mounting method.
        2.  Determine if incremental or absolute encoder is needed.
        3.  Pick required resolution (PPR for incremental).
        4.  For incremental encoders, specify if quadrature and/or an index mark are needed.
        5.  Match encoder size to motor size.
        6.  Ensure TIR meets system alignment specifications.
        7.  Verify environmental specifications (operating temperature, shock, vibration, humidity, IP rating).

**2. Absolute Encoders**
*   **Function**: Routinely used for **rotary position sensing**. They generate **digital words that represent speed, direction, and actual rotational position all at once**.
*   **Key Advantage**: The rotating disk contains a very precise pattern that creates a multi-bit digital word at each discrete angle, allowing the encoder to **always know its position** during rotation and track total revolutions. If power is interrupted, its output will be correct when power is restored, and homing the sensor is not necessary.
*   **Applications**: Found in machine tools, robots, medical, and welding equipment where precise control of position is mission-critical.
*   **Operating Principle**: The pulse stream requires multiple light detectors to read every track. A simplified model uses two channels; for example, position one could be "1 0", position two "1 1", and position three "0 1".
*   **Resolution**: A function of the **number of bits in its digital word**. Output can be in straight binary or Gray code. For example, a 24-bit encoder has a resolution of 16 million counts per revolution.
*   **Types**:
    *   **Single Turn Absolute Encoder**: The output signal repeats for every revolution of the encoder's shaft, with no ability to count total revolutions.
    *   **Multi Turn Absolute Encoder**: Counts the total number of revolutions as well as maintains knowledge of absolute rotational position. A Singleturn PCB tracks absolute position from the code disk, while a Multiturn PCB reads pulses from a multi-turn gearbox to record revolutions. This count remains valid even if power is shut down.
*   **Mechanical Design**: The encoder's shaft turns a primary gear, which then rotates etched position gears. These gears have tracks positioned directly beneath optical sensors on the PCB. Mechanical parts like bearings, shafts, and gears are designed to meet the sensor's vibration specifications.

**3. Resolvers**
*   **Function**: Measure angular position with high accuracy. They are specialized transformers.
*   **Advantages over Encoders**: Used in **extremely harsh temperature, shock, and vibration environments** that exceed encoder capabilities to maintain signal integrity.
*   **Applications**: Commonly used in military, aerospace, and construction equipment. Also favored in welding and painting robots due to high shock and vibration ratings.
*   **Operating Principle**:
    *   Works similarly to a DC generator. Its coils output two analog signals arranged 90 degrees out of phase, generating a voltage corresponding to the interaction of resulting magnetic fields.
    *   Looks like an electric motor externally, but internally, its windings are like those of a transformer.
    *   **Stator**: Has a primary winding and two two-phase secondary windings. The primary winding is excited by an external AC current.
    *   **Rotor**: Electromagnetic induction induces current in its first winding, regardless of angular position. This current flows to the rotor's second winding.
    *   **Induced Currents**: By electromagnetic induction, current is induced in the secondary windings of the stator, which are fixed at right angles to each other.
    *   **Output Signals**: The stator produces two alternating currents that are 90 degrees out of phase, varying as the sine or cosine of the rotor angle. They also vary in time as the AC line voltage frequency. The stator windings repeat their spatial waveforms every full rotation of the rotor.
*   **Analog-to-Digital Conversion**: Resolvers are analog devices. To determine the rotor angle, the relative magnitudes of the two-phase stator voltages must be measured and digitized.
    *   The ratio of the relative magnitude of the voltages is the tangent of the rotor angle (sine of rotor angle / cosine of rotor angle). The angle is calculated by taking the arctangent.
    *   **Resolver-to-Digital (R-D) Converters**: Commercially available off-the-shelf. These apply resolver signals to cosine and sine multipliers with a digital angle (phi). The resulting signals are subtracted by an error amplifier to produce an error signal (sine of theta minus phi). This error signal is fed back through the system until the digital output (phi) represents the actual angle (theta). This error amplifier has the advantage of **canceling out noise** injected on both windings.
*   **Construction Details**:
    *   **Brushless**: Better quality resolvers are brushless.
    *   **Voltage Input**: Input voltages to the static primary winding are usually less than 26 volts AC, as a resolver does not drive a load.
    *   **Frequency Ratings**: Industrial grade resolvers are designed for 50 or 60 Hz AC power. Marine or aviation resolvers are designed for 400 Hz power supplies. Military grade resolvers can go as high as 12,000 Hz.
    *   **R-D Converter Location**: The R-D converter electronics are normally not purchased with the resolver nor mounted directly to it. This allows the electronics to be kept away from the harsh environment the resolver experiences, particularly high temperatures and RF interference. This typically requires dealing with two different vendors.
    *   **Physical Construction**: Typical construction includes a mounting plate to attach to the motor's structure and a round metal cover for EMI shielding. The resolver shaft is coupled by a flex coupling to the motor shaft. Rugged bearings support the shaft rotation. Some models include a small circuit board with programmable switches for optional user settings and a back plate for electrical connections.
*   **Types of Resolvers**:
    *   **Multiple Speed Resolver**: Offers higher resolution and accuracy. A resolver with 2n pairs of secondary windings will deliver 'n' cycles of sine waves in one mechanical turn, making it 'n' times more accurate than a single speed resolver (e.g., n=8 means 8 times better accuracy).
*   **Issues with Resolvers**:
    *   **Multiple Speed Resolver Limitation**: They **do not understand absolute position** within a full mechanical turn. To determine absolute position, a single speed resolver must be mounted in series on the same shaft, which doubles the cost.
    *   **Digital Resolver Trade-off**: A digital resolver (with built-in R-D circuit) exists but cannot be placed in as extreme temperature or vibration environments as a separate resolver and R-D converter setup.
    *   **Zero Signal Output**: Resolvers typically have difficulty outputting a true zero signal, resulting in a **zero offset of 10 to 40 millivolts** due to imperfections in the secondary windings.
*   **Mechanical Configurations**: Similar to encoders.
    *   **Frameless Resolver**: Consists primarily of the stator and rotor, mounting directly to the motor shaft.
    *   **Enclosed Resolver with Hole**: Can be mounted directly to the motor shaft, requiring a strong tether to prevent slipping.
    *   **Flange Mount**: Another mounting option, similar to that shown in construction details slides.
    *   Properly specified **flex coupling** is crucial for shaft alignment.
*   **Specification and Purchase Considerations**:
    *   **Accuracy**: Specified in arc minutes or arc seconds. It is the difference between the resolver reading and the actual rotational position. Accuracy is affected by inconsistent stator and rotor windings, lack of concentricity of windings relative to the rotor shaft, and variations in magnetic properties of components.
    *   **AC Voltage and Frequency**: Important to match the electrical system supplying power to the resolver.
    *   **Transformation Ratio (TR)**: The ratio of output to input voltage at maximum magnetic coupling. It is proportional to the ratio of effective turns in the stator secondary winding to those in the rotor primary winding. The TR indicates the nominal output voltage of the resolver.
    *   **Single or Multiple Speed**: Must decide based on application trade-offs (e.g., accuracy vs. absolute position).
    *   **Tracking Rate**: The maximum angular velocity of the resolver shaft, which is a spec for resolver-to-digital converters.
    *   When selecting an R-D converter, ensure it matches the resolver's frequency and consider whether velocity output is needed. Tracking rate in revolutions per second (RPS) needs to be checked against application specs.

### Flow Sensors (Meters)

Flow sensors (referred to as "meters" as all suppliers sell meters) are transducers that measure flow and convert the signal into a digital or analog output.

**1. Variable Area Flow Meters**
*   **Technology**: One of the oldest flow technologies, a purely mechanical system still sold today.
*   **Operating Principle**: Measures flow based on the **height of a float rising inside a tapered tube** as the flow rate increases.
    *   Consists of a glass or metal float suspended in a tapered glass or metal tube.
    *   Flow enters from the bottom, causing dynamic forces and buoyancy to push the float upwards, balanced by gravity pulling it down.
    *   The tube is conically shaped, so the area around the float for fluid to pass increases as the float moves up, increasing drag force.
    *   At mechanical equilibrium, dynamic and drag forces balance, positioning the float at a constant height.
    *   The tube has gradations calibrated to correlate flow rate to float height, which the user reads.
*   **Advantages**: Not very accurate, but low cost and does not require electricity. Useful for sanity checks and as backup meters if power is lost.
*   **Applications**: Commonly found in hospital rooms and dental offices.
*   **Specification Considerations**:
    *   **Accuracy**: Poor, typically in the 2-5% range.
    *   **Materials**: Flow tubes are made of glass, metal, or plastic (e.g., polycarbonate).
    *   **Temperature Limits**: Narrow, typically 5-60 degrees C.
    *   **Process Connections**: Usually small pipe fittings (e.g., 8-inch NPT).
    *   **Size**: Most variable area meters are small and palm-sized.
    *   **Metering Valve**: Occasionally included to limit maximum flow rate.

**2. Differential Flow Meters**
*   **Invention**: Developed to measure air speed in aviation.
*   **Operating Principle**: Measures the pressure upstream and downstream of an obstruction (orifice plate) placed inside the meter. The flow rate is calculated based on the difference between the two measured pressures using the **Bernoulli equation**. Bernoulli's principle states that an increase in flow speed occurs simultaneously with a decrease in pressure or potential energy.
*   **Orifice Plate**: Typically a disc with holes. More holes allow more flow and result in a smaller pressure drop. Usually, a significant amount of flow must be blocked to create a large enough pressure drop for accurate measurement.
*   **Calculation**: If the pipe and meter are horizontal, the potential energy change due to gravity is zero. The velocity of the flow can be found using the equation **P_upstream - P_downstream = 0.5 * rho * V^2** (where rho is fluid density, V is velocity). Flow rate is then found by multiplying velocity by the cross-sectional area of the pipe.
*   **Advantages**: Highly accurate and reliable, working well with almost all gases and liquids. They constitute approximately 50% of the global flow meter market. They excel in applications requiring **high accuracy at very high pressures and temperatures**. More cost-effective than Coriolis meters for similar flow rate ranges.
*   **Flexibility**: The orifice plate can be swapped out with a different size to measure a different flow range.
*   **Specification Considerations**:
    *   **Long-term stability**: Unusually high numbers due to the absence of moving parts in the flow stream and the reliability of the decoding electronics.
    *   **Static Pressure Limits**: Can top out around 250 bar.

**3. Vortex Flow Meters**
*   **Operating Principle**: Measures the vibrational frequency of vortices downstream of an obstruction (called a **bluff body**) placed inside the meter. This phenomenon is based on the **von Karman effect**, where the bluff body creates a series of downstream vortices that shed and create a cyclical pressure wave.
    *   A piezoelectric pressure sensor picks up the frequency of this pressure wave.
    *   A higher frequency pressure wave corresponds to a higher flow rate.
    *   The output from the sensor goes into processing electronics, which then output a flow rate via a digital protocol.
*   **Advantages**: Excellent for **measuring steam flow** because they have no moving parts that can corrode in the steam. Also provide high turndown, defined as the ratio of highest to lowest flow rates to be measured.
*   **Limitations**: Susceptible to external pipe vibrations (e.g., from physical impact).
*   **Specification Considerations**:
    *   Often specifically mention "steam" as a measured fluid, indicating optimization for steam.
    *   Both resolution and accuracy are quoted.
    *   Spec sheets list the digital protocols used for communication with process control networks, which are standard for the flow industry.

**4. Ultrasonic Flow Meters**
*   **Operating Principle**: Measures the **Doppler frequency shift** caused when an ultrasonic signal is reflected by suspended particles or gas bubbles in the flow stream. The flow rate is correlated to this frequency shift.
    *   A transmitter sends an ultrasonic signal, which is reflected back to a receiver by the moving particles or bubbles.
    *   The frequency of the reflected signal is higher due to the movement of the particles (Doppler effect).
*   **Advantages**: Provide high accuracy readings at the highest process temperatures that flow meters can measure. They are **non-contact measurement** devices, meaning nothing is placed in the flow field, eliminating concerns about mechanical components melting in hot liquids or gases. Easy to install, cause no disturbance to the flow field, and can be used for temporary installations.
*   **Limitations**: Very high cost. A significant problem is that if the liquid in the pipe is too pure (lacking suspended particles or air bubbles), the ultrasonic waves will not have anything to reflect off, leading to a perceived zero flow even if fluid is moving.
*   **Specification Considerations**:
    *   Typical specs include accuracy, flow range, and temperature.
    *   Often highlight ease of clamping onto pipes and portability.
    *   Typically specified for a wide range of pipe sizes, but different mounting brackets may be required for various pipes.

**5. Turbine Flow Meters**
*   **Operating Principle**: Convert the kinetic energy of the flow stream into the angular rotation of a rotor with multiple fan blades installed in a pipe. The rotational axis of the fan blades is perpendicular to the flow direction.
    *   The faster the liquid flows, the faster the blades rotate.
    *   As blades pass near the inner diameter of the pipe, a magnetic sensor registers a pulse; the number of pulses counted is proportional to flow speed.
    *   Magnetic sensors are outside the flow stream, preventing contamination.
    *   A transmitter processes the pulse signals to calculate the flow rate.
*   **Features**: Can sense both forward and reverse flow.
*   **K-factor**: A crucial factor that correlates the flow rate with the angular speed of the rotor and the frequency measured by the magnetic sensor. This factor is necessary for process control systems to understand the flow rate in actual units.
*   **Advantages**: Provide accurate readings of **clean liquids and gases at an affordable price**. They are easy to install.
*   **Applications**: Used for custody transfer measurement of hydrocarbons and natural gas. Also used by water districts to measure flow rates in pipes.
*   **Limitations**: Work best with clean fluids; dirt can accumulate on blades and slow them down. Units typically fail due to bearing wear.
*   **Specification Considerations**:
    *   **K-factor** is essential and should be located in the spec sheet.

**6. Thermal Mass Flow Meters**
*   **Operating Principle**: Divert approximately 1% of the main gas flow into a small bypass tube where sensor coils heat the gas as it flows.
    *   A bypass mechanism (e.g., metal screen) and a laminar flow element cause the flow to transition from turbulent to laminar, which is necessary for accurate measurement.
    *   The sensor tube has upstream (T1) and downstream (T2) heating coils wrapped around its exterior, with equal and constant currents flowing through both.
    *   As gas flows, it heats up, so the downstream temperature (T2) is greater than the upstream temperature (T1).
    *   The heater coils are also resistors whose electrical resistance increases with heat; thus, the downstream coil's resistance (RHT2) will be greater than the upstream coil's (RHT1).
    *   A **Wheatstone bridge circuit** detects this difference in resistances, and the differential voltage in the circuit is proportional to the flow rate. The system is calibrated to determine proportionality constants.
*   **Advantages**: Provide **highly accurate readings of clean gases at very low flow rates**.
*   **Limitations**: Generally limited to gases, not liquids. Limited to roughly 30 to 50 liters per minute. Requires knowing the thermal properties of the gas beforehand.
*   **Applications**: Popular in the semiconductor industry for dispensing minute doses of processed gases and found in biotechnology reactors.
*   **Specification Considerations**:
    *   **Process and Gas Operating Temperature**: Very limited, as high temperatures would significantly affect the sensitive calibration.
    *   **Flow Ranges**: Limited because laminar flow is required for the sensor to work.
    *   **Attitude-sensitive**: Mounting sideways or upside down allows minute gravitational pull on the gas to affect readings, introducing unmeasurable errors. Best mounted horizontally (parallel to the ground).

**7. Coriolis Flow Meters**
*   **Operating Principle**: The fluid flow is contained inside a U-shaped or triangular tube. A magnetic coil causes the tube to oscillate.
    *   The **Coriolis effect** of the vibrating tube interacting with the dynamic force of the fluid flow causes the tube to twist in a direction perpendicular to both the mechanical vibration and fluid flow.
    *   An optical sensor measures this **twist angle**, which is proportional to the **mass flow rate**.
    *   100% of the flow is diverted from the main pipe into the flow tube.
    *   An RTD measures the inlet temperature for instrument calibration.
*   **Measurements**: Directly measure **mass flow**, not volume flow. They can also measure fluid density.
*   **Advantages**: Non-contact sensors, allowing measurement of mass flow at **very high process temperatures and pressures**. Used for very high mass flow rates in high-volume chemical, petrochemical, and municipal water plants. They typically come with **explosion-proof ratings** (ATEX certified) due to their common use with volatile chemicals.
*   **Limitations**: The **most expensive** flow meters available. They are twice as accurate with liquids as with gases. Susceptible to air bubbles trapped inside the liquid, which can fool the meter into reporting a lower mass flow rate than actual.
*   **Specification Considerations**:
    *   **Tube Material**: Metal tubes are available in various exotic metals (e.g., stainless steel, Hastelloy) to measure corrosive liquids and gases without erosion.
    *   **Explosion Protection**: Certified for explosion-proof protection, specifically for various ATEX divisions and zones, which relate to the types of explosive vapors present.
    *   **Zero Point Stability**: A manufacturer-provided "fudge factor" that needs to be added to the numerical accuracy specification to get the real accuracy. It is a measure of the voltage noise in the meter's hardware, indicating how much the electronics oscillate around a zero reading instead of simply registering zero.
    *   Manufacturers offer a range of model numbers to span the entire flow range, allowing them to quote high accuracy statistics like 0.1% or 0.2% of measured flow, which would be ten times worse if a single "one-size-fits-all" meter were attempted due to zero point stability.
