Here is a comprehensive summary of the knowledgeable information from the provided sources, with colloquial language removed:

The course focuses on **motors and motor control circuits**, including **DC motors**, **stepper motors**, and **rotary sensors**. It covers electromagnetic principles, electronic drive information, and concludes with a **general comparison of DC and AC motors** to aid in motor selection for machine design. Practical lab exercises are included for DC motors and rotary sensors.

### DC Motors

**Characteristics and Operation:**
*   **DC motors are widely used in robotics because they are simple to construct and relatively easy to control**.
*   They can be coupled with expensive position sensors, but **speed can also be measured without external sensors**.
*   When a fixed DC voltage is applied to a motor at rest, its behavior is governed by specific equations.
*   Initially, with no speed, there is no back electromotive force (back EMF), which means it does not affect the current rise time.
*   As current builds, torque is produced, causing the motor to accelerate.
*   An **inherent feedback loop** exists in DC motors: if an external force slows the motor, the back EMF decreases, which in turn increases the net voltage available for torque, causing the motor to resist the slowdown.

**Back Electromotive Force (Back EMF):**
*   All DC motors can function as generators and produce a voltage even while powered. This generated voltage is called **back EMF**.
*   **Back EMF effectively subtracts from the voltage applied to the motor**.
*   **Back EMF is directly proportional to the speed of the motor**.
*   The **back EMF constant**, typically measured in volts per thousand RPM, is the constant of proportionality. Higher motor speed results in higher generated voltage.
*   As the motor speed increases, back EMF builds up, reducing the net voltage and current in the motor.
*   Eventually, an equilibrium is reached where the current is just sufficient to overcome friction.

**Torque Constant:**
*   The **torque constant is proportional to the back EMF constant**.
*   High torque motors generate significant back EMF, requiring a higher voltage to operate at high speeds.
*   The units for torque constant are torque divided by current (e.g., Newton meters per amp, foot pounds per amp, ounce inches per milli-amp).
*   **Motor torque output depends solely on the current and the motor's torque constant**.

**Measuring Motor Speed using Back EMF:**
*   When a spinning motor is briefly disconnected from a fixed voltage power supply, its back EMF can be observed.
*   This measurement can be done quickly, minimizing any effect on motor speed.
*   In a circuit where a power field-effect transistor (FET) interrupts the motor's connection to ground, the voltage measured at a specific point (e.g., P3_2) when the FET is off will be the externally applied voltage minus the back EMF (with a minor correction for internal resistance).
*   If the motor is stalled, the measured voltage will be close to the battery voltage.
*   If the motor is moving quickly, the back EMF subtracts from the applied voltage, resulting in a lower measured voltage. Therefore, **a lower measured voltage indicates a faster motor speed**.

**Motor Interfacing and Control Circuits:**
*   DC motors draw more current than typical microprocessors.
*   A **power field-effect transistor (FET)** can control large currents (up to 10 amps in some cases) from a smaller current produced by a microprocessor's General Purpose Input/Output (GPIO) pin.
*   **FET operation:** It is a three-terminal device (drain, gate, source) where the gate-to-source voltage controls the resistance between the drain and source. When the gate-to-source voltage exceeds a few volts, the FET turns on (low resistance); when it's zero, the FET turns off (high resistance), acting as a switch. The GPIO pin controls the gate voltage.
*   **Essential circuit components:**
    *   **Battery power** (e.g., three AA batteries providing 4.5V) for the motor.
    *   A small **current sense resistor** (e.g., 0.5 ohm) can be placed between the FET's source and ground to develop a voltage proportional to the motor current, which can be amplified.
    *   An **analog-to-digital converter (ADC)** can be connected to the FET's drain to measure voltage and determine motor speed.
    *   A **power diode** is critical. Since motors are inductive and current in an inductor cannot change instantaneously, the diode provides a path for current to flow in a circular path when the FET turns off, preventing damaging voltage spikes. This current decay is relatively slow, allowing measurements before significant change.
*   A **current-limiting resistor** (e.g., 500-1000 ohms) should be placed between the GPIO pin and the FET gate to protect the GPIO from transient high currents, as the FET gate acts like a capacitor.
*   PSoC pins can be configured with internal pull-up resistors, eliminating the need for external ones in certain circuits.

**Comparison of DC Motors with AC Motors:**

| Feature              | DC Motor Advantage                                                                                             | AC Motor Advantage                                                                   |
| :------------------- | :------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------- |
| **Speed Control**    | **Easier to adjust speed by changing input voltage**; AC requires complex, expensive frequency shifting.        | Accurate speed control was historically decades away.                           |
| **Direction Reversal**| **Easier by switching voltage polarity**; AC requires complex wired networks of contactors.                      |                                                                                      |
| **Accuracy**         | **Accurate control of acceleration and position** (especially with DC servo motors).                           | Less accurate for acceleration and position control.                                 |
| **Acceleration/Deceleration**| **Faster due to relatively small rotor inertia**. Prevalent in assembly machines and small/mid-sized robots for productivity. | Slower due to larger rotor inertia.                                                  |
| **Speed Matching**   | Relatively easy to match the speed of two DC motors.                                                           | Difficult to match speeds of two AC motors due to high tolerances on specs.           |
| **Torque Control**   | **Directly controlled by varying current**.                                                                    | Only indirectly controlled.                                                          |
| **Maintenance**      | Brush DC motors require periodic brush/commutator replacement and are vulnerable to dust. Brushless versions exist but are more expensive. | **Do not require periodic maintenance**.                                             |
| **Power Supply**     | Requires AC to DC power conversion, which loses energy and produces ripples. Needs a dedicated DC power supply (battery, generator, rectifier, fuel cell). | Can be plugged directly into wall outlets. Standard electrical infrastructure is AC.  |
| **Efficiency**       | Large DC motors would not meet legislative efficiency standards if AC-DC conversion loss were included.         | Vast majority of large motors run on AC power for efficiency given AC infrastructure. |
| **Long Distance Power Transmission** | Historically suffered significant losses.                                                              | **Transmitted over long distances with significantly less losses**.                  |

### Stepper Motors

**Fundamentals:**
*   Stepper motors are a type of **brushless DC motor**.
*   They rotate by **fixed angular increments (steps)** and then stop, unlike continuously rotating motors.
*   Considered a **"quasi-digital device"**.
*   Common step angles range from 0.75 to 90 degrees.
*   The **stator** has an even number of magnetic poles with coil windings; opposite windings form a "phase".
*   **Hybrid stepper motors**, designed for high resolution, feature two permanent magnet rotors (one North, one South) with numerous small teeth, offset by half a tooth pitch, allowing for half-angle stepping (e.g., 3.75 degrees for a 48-tooth rotor).
*   Rotation occurs as the magnetic polarity of stator windings is switched, causing rotor teeth to be attracted or repelled to new equilibrium positions. Not all stator poles need to be energized simultaneously.

**Key Characteristics and Applications:**
*   A stepper motor stays still when a steady current is applied, unless programmed to move.
*   If an external load attempts to rotate the motor, it will increase current to resist until the **holding torque** is reached. A load exceeding holding torque will force rotation.
*   **Energy Inefficiency:** Stepper motors consume power even when stationary, unlike other motors that consume no power when not in motion. For energy efficiency, perpetual motion is recommended.
*   **Applications:** Ideal where **precisely controlled angular motion is needed without requiring 100% angular resolution or constant velocity**.
    *   Can be used with gearing for precise, high-torque steps.
    *   **Can position a load without feedback** if the load does not exceed the motor's torque, which significantly reduces system cost and is a primary driver of their use.
    *   Examples include robotic assembly for low-torque, fine-pitch screwing tasks. Higher torque and speed applications typically use DC or AC motors.

**Wave Drive Example (Illustrative):**
*   A "wave drive" is a simplified stepper motor drive where only one of two stator phases is energized at a time, resulting in lower torque output.
*   An example motor has two phases (four stator windings) and two rotors (each with one tooth, one North, one South).
*   Phases are energized and de-energized sequentially, with polarity reversal each time a phase is energized.
*   This sequence can achieve a fixed rotation, for instance, 90-degree clockwise steps for a 360-degree rotation over four steps.
*   The sequence can be altered to achieve counter-clockwise rotation.

**NEMA Specifications and Motor Characteristics:**
*   **NEMA (National Electrical Manufacturers Association) establishes dimensional specifications** for stepper motors.
*   The **numerical size** defines the full width of the square motor face in inches (A dimension). Examples: Size 11 (1.1 inches), Size 14 (1.4 inches).
*   Other dimensions include: B (distance between mounting holes), C (threaded hole size for mounting screws), D (shaft diameter).
*   Motor length is not covered by NEMA and varies to optimize torque-speed curves.
*   **Torque-Speed Curve:** Torque is highest when the motor is stopped and decreases as speed increases. Speed is measured in steps per second/minute. Increasing voltage can increase torque but not linearly.
*   **Holding torque** is a crucial specification.
*   Adding motor length increases electromagnetic attraction, allows larger permanent magnets and more stator coils, which in turn increases phase resistance, inductance, and weight.
*   **Large inertia and inductance values require a high input voltage to achieve fast stepping speeds**.

**Current Control Methods (Drivers):**
*   **Unipolar Drive:**
    *   Current flows through phases in the same direction when energized.
    *   Uses only half the coil length to magnetize a pole, simplifying transistor circuitry.
    *   Results in roughly **half the current and half the possible torque**.
    *   Five-lead motors, where center taps are connected, can only be used with unipolar drivers.
*   **Bipolar Drive:**
    *   Uses the **full coil length** to magnetize a pole.
    *   Requires current direction reversal for magnetic switching, leading to more complex transistor circuitry.
    *   Provides **full torque output**.
    *   Four-lead motors, which have no common leads, require connection to an H-bridge transistor network or commercial driver chip.
    *   In bipolar H-bridge circuits, careful sequencing of transistor operation is needed to avoid damage, as transistors have capacitance requiring discharge time.

**Limitations and Issues:**
*   **Jerky motion at low speeds** with simple control methods, requiring complex firmware to smooth.
*   **Torque ripple**: Torque output varies throughout the step. Not suitable for loads with varying torque or significant mechanical backlash.
*   **Higher rotary inertia and relatively smaller torque** compared to other DC motors.
*   **Slower acceleration to maximum speed** (due to high inertia) compared to other DC motors.
*   **Maximum speed is limited by high inductance** because a high electrical time constant requires longer to ramp up current in coils, and current must ramp up/down sequentially in each coil during stepping. This significantly limits speeds above 10-20 steps per second.

**Improving Angular Resolution (Drive Types):**
*   **Full Step Operation:**
    *   Simplest method, moving the rotor one full step at a time.
    *   Provides the **highest torque** because all stator coils are energized simultaneously.
    *   Typically uses bipolar phase currents.
*   **Half Step Drive:**
    *   Cuts the step angle in half, providing **twice the resolution**.
    *   Sequence: one phase energized, then both, then back to one.
    *   Has **much weaker holding torque** than full step, making it susceptible to strong external loads.
*   **Microstepping:**
    *   Creates a quasi-sine wave of current in stator poles, often 90 degrees out of phase for two sets of poles.
    *   Modulates current slowly, resulting in **smoother motion and much finer step angle resolution**.
    *   Requires specialized motor driver firmware.
    *   Has **lower torque output** than full or half step drives.
*   **Design Trade-off:** There is a trade-off between **high torque output and fine angular resolution**. Full step offers highest torque with worst resolution, while microstepping offers best resolution with lowest torque. Half step is in between.

**Commercial Stepper Motor Driver Chips and Packages:**
*   Convert logic-level signals from a microcontroller into the currents needed to drive the motor.
*   Can handle simple commands (forward/reverse/step) or complex interfaces (I2C, SPI).
*   Driver chips often integrate H-bridge transistor networks.
*   Features may include:
    *   An **internal electric brake function** that stops the motor by briefly shorting terminals, using back EMF to create reverse torque.
    *   A **spark killer diode** to dampen coil current from abrupt open circuits.
    *   **Thermal shutdown circuits** to protect coil windings from overheating.
*   **Turnkey Drive Electronics** are available for purchase with stepper motors, offering various step options (full, half, microstepping), saving significant development time and effort.

### Rotary Sensors (Encoders)

**Applications and Types:**
*   Detecting rotary motion is a very common application.
*   Methods vary based on environment, accuracy, and cost.
*   Examples:
    *   **Inductive pickups:** Used in automobile engines for crankshaft position in harsh environments.
    *   **Optical encoders:** Used in robots for high precision.
    *   **Hall sensors:** Provide crude angular position (approx. 30 degrees) for brushless DC motors.
    *   **Back EMF:** Can also be used for brushless DC motor angular position with similar resolution.
    *   **Accelerometers:** For rotary position, e.g., in bicycle speedometers.
    *   **Mechanical rotary switches:** Commonly used in front panel control knobs, like car stereos.

**Mechanical Rotary Switch (e.g., TT Electronics EN11):**
*   Produces **two digital pulse trains that are out of phase** as the switch rotates.
*   The **phase difference between the pulse trains indicates the direction of rotation**.
*   The **number of edges counted determines the angular position**.
*   The EN11 has physical detents, providing a tactile "click" as it rotates. Each click corresponds to a high-to-low then low-to-high transition on both switches, ideally generating four edges.

**Challenges: Noise and Bounce:**
*   Mechanical switches do not make and break contact cleanly due to physical "bounce".
*   Instead of a single sharp edge, multiple sharp edges may occur closely together.
*   Microprocessors are fast enough to detect these multiple edges, which can lead to inaccurate counting.
*   Switch bounce can manifest as noise, where the signal drops, shows noise, and then jumps back up before settling.
*   During bounce, the signal may not fully reach logic high (5 volts) or logic low (ground).

**Digital Input Interpretation:**
*   For a PSoC chip powered by 5 volts:
    *   Input signals **less than 1.5 volts are considered Logic Zero**.
    *   Input signals **above 3.5 volts are considered Logic One**.
    *   Voltages between 1.5V and 3.5V are **indeterminate** and may be interpreted as either logic state.
*   Applying intermediate logic levels can cause **metastability**, a persistent problem down the signal chain.

**Debouncing and Filtering Strategies:**
*   To address switch bounce, **filtering is necessary**, either in the analog or digital domain.
*   Digital filters can be **non-linear**, for example, by implementing a rule to ignore further transitions for a set period after the first edge is detected.
*   The PSoC includes a hardware component called **QuadDec (Quadrature Decoder)** designed for this purpose.
    *   It counts switch clicks automatically in hardware.
    *   Its filtering scheme requires **three consecutive samples to match** before recognizing an input change. This is a non-linear digital filter.
    *   The filter's response is highly dependent on the **clock frequency**, which determines the sampling time.
    *   **Oscilloscope measurements of switch response are crucial** for setting the appropriate clock frequency based on noise characteristics and desired rotation speed.
*   The direction of rotation is determined by the state of one channel when an edge is detected on the opposite channel. The redundancy of four edges per click can be used for error checking.
*   Implementing the same filtering logic in software (e.g., C) allows for greater flexibility in modifying the filter, such as changing the number of matching samples required.
