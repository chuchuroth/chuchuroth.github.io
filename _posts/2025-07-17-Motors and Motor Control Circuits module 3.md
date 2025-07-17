---
layout: post
title:  "Motors and Motor Control Circuits module 3"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---


Drawing on the provided sources, here is a comprehensive breakdown of information regarding DC motors, excluding colloquial language:

### Introduction to DC Motors and Principles
*   This discussion focuses on **DC motors**, including their principles and practical applications.
*   **DC motor operation** is based on fundamental physics principles, particularly electromagnetism.
*   **Faraday's Law of Induction** states that passing a current through a conductor within a magnetic field causes the conductor to move through that field.
*   The force exerted on the conductor is known as the **Lorentz force**, calculated as **F = B × L × I**, where **B** represents the magnetic flux density, **L** is the length of the conductor, and **I** is the current.
*   The **direction of this force** is determined by the **right-hand rule**: aligning the right index finger with the current direction, the thumb with the magnetic flux (north to south), and the middle finger will point towards the direction of the force.
*   Faraday also discovered that moving a conductor through a magnetic field induces a current in the conductor, acting as a **generator**. The generated electromotive force (EMF) is known as **back EMF** in a motor, calculated as **E = B × L × v**, where **v** is the velocity of the conductor. The right-hand rule also determines the direction of the induced electric field and current.
*   **Torque** is applied to the rotor by running current through a coil winding. Forces on the two sides of the coil closest to the magnet poles act in opposite directions, creating torque.
*   **Torque (T) = 2 × F × r**, where **F** is the force and **r** is the radius. Substituting the Lorentz force, **T = 2 × B × L × I × r**.
*   The **back EMF (E)** in a motor can also be expressed as **E = B × L × ω × r**, where **ω** is the angular velocity, as velocity (v) equals angular velocity (ω) times radius (r).

### DC Motor Components and Operation
*   In a DC motor, **current is conducted from an external line voltage to both the stator and the rotor**. This differs from AC induction motors where current is induced in the rotor.
*   The **stator** in a DC motor is frequently referred to as the **field coil**, and the **rotor** is often called the **armature**.
*   The **armature coils** are composed of multiple windings of insulated wire wrapped around a soft iron core, which serves to concentrate the magnetic field.
*   The ends of the armature wire windings are connected to a **commutator**, which sequentially energizes each armature coil.
*   The **commutator** makes contact with a set of **carbon brushes** as it rotates, connecting the rotating coils to the external DC power supply. The carbon brushes touch slip rings within the commutator, with one slip ring connected to each end of the rotating rotor coil.
*   When the coil is powered, a magnetic field is generated around the armature. As the armature approaches a vertical position, the net force that would sustain rotation in the same direction approaches zero, causing the torque to approach zero.
*   At this point, the **commutator reverses the direction of current flow** through the coil by switching the DC supply to the other slip ring. This reversal of current direction ensures that the forces continue to rotate the armature in the same direction, following the right-hand rule.
*   **Lenz's Law** dictates that as the armature windings rotate, they act as a generator, producing a current (the back EMF, Eb) that opposes the applied current. The flow of current (Ia) in the motor windings is given by **Ia = (E - Eb) / Ra**, where E is the applied voltage and Ra is the armature resistance.

### Applications of DC Motors
*   DC motors are widely utilized across various sectors.
*   **Large DC motors** are employed in electric vehicles, trains, elevators, and rolling mills.
*   **Mid-size DC motors** are found in precision instruments, automated machinery, and robots.
*   **Small DC motors** are used in appliances, tools, and toys.

### Comparison of DC and AC Motor Characteristics
*   **Torque in DC motors** is proportional to the product of the current in the rotor coil (I) and the magnetic flux (B) between the rotor and stator.
*   **Speed in DC motors** is proportional to the ratio of the voltage in the rotor coil (V) to the magnetic flux (B).
    *   DC motor speed is controlled by **varying the voltage**, as there is no line frequency concern. Reducing magnetic flux can increase speed but will decrease torque.
*   **Synchronous speed in AC motors** (Ns) is proportional to the ratio of the AC line frequency (F) to the number of poles (P) in the stator windings.
    *   AC motor speed is controlled by **varying the supplied line frequency** in constant proportion to voltage.
*   In **DC motors, maximum torque** occurs at zero speed (starting or stall torque), drawing maximum current. Torque generally decreases as speed increases, though not always linearly.
*   In **AC motors**, maximum torque (breakdown torque) typically occurs between 80% and 100% of full speed, except for Nema Type D motors which have maximum torque at zero speed.

### Motor Power and Energy Losses
*   **Motor power (P)** calculations are consistent for both AC and DC motors.
    *   In **metric units**: **P = (2 × π × N × T) / 60**, where P is in Watts, N is speed in RPM, and T is torque in Newton-meters.
    *   In **English units**: **P = (N × T) / 5,250**, where P is in horsepower, N is speed in RPM, and T is torque in pound-foot.
    *   One horsepower is equivalent to 760 Watts.
*   **Energy losses in DC motors** are similar to those in AC motors.
*   Due to the prevalence of low-power DC motors, there are generally no international standards for their energy efficiency.
*   **Energy efficiency in DC motors increases with motor speed**.
*   Power losses are largely independent of speed and are more related to the fixed magnetic windings.
*   Key **power losses** include:
    *   **I-squared-R heating** in the motor windings, dependent on motor load and current.
    *   **Magnetic saturation**, which is energy loss from using materials beyond their magnetic saturation point.
    *   **Hysteresis losses**, resulting from the magnetization and demagnetization of the iron core in the field windings during each revolution.
    *   **Eddy current losses**, caused by circulating currents induced in the magnetic circuit by the field windings.
    *   **Flux leakage**, which is the inefficiency of the field winding design in concentrating magnetic flux for optimal coupling to the armature.
    *   **Mechanical friction** in the rotating armature, though typically a small effect compared to magnetic losses.

### Types of Brushed DC Motors
*   There are three main types of brushed DC motors: **shunt wound, series wound, and compound wound**.
    *   **Shunt Wound DC Motor**:
        *   DC power is supplied in **parallel** to both the field windings and the armature.
        *   The voltage (V) across the field windings and armature is given by **V = E_b + I_a × R_a**, which also equals **K_a × Φ × Ω + I_a × R_a**. Here, E_b is back EMF, Φ is magnetic flux, Ω is angular speed, K_a is a proportionality constant, I_a is armature current, and R_a is armature resistance.
        *   Torque (T) is calculated as **T = K_a × Φ × I_a**.
        *   Angular speed (Ω) is calculated as **Ω = (-T × R_a) / (K_a × Φ)² + V / (K_a × Φ)**.
        *   **Speed is linearly proportional to torque** up to 200% of rated torque.
        *   **Speed control** can be achieved by **increasing the shunt regulator resistor (R_F)** to reduce current in field windings, decrease magnetic flux, and **increase speed** (works for speeds above R_F=0). To **decrease speed**, increasing resistor R_1 will reduce motor speed, but this incurs significant power loss due to heating.
        *   Shunt wound motors are **safe to use at any speed**, but they possess the **lowest starting torque** among brushed types.
    *   **Series Wound DC Motor**:
        *   DC power is supplied in **series** to both the field windings and the armature.
        *   The total voltage drop (V) is **V = E_b + I_a × (R_a + R_s)**, which equals **K_a × Φ × Ω + I_a × (R_a + R_s)**, where R_s is the field winding resistance.
        *   Torque (T) is **T = K_a × Φ × I_a**.
        *   Magnetic flux (Φ) is proportional to armature current (I_a) as **Φ = K_1 × I_a** (ignoring saturation), where K_1 is a proportionality constant.
        *   Back EMF (E_b) is **E_b = K_a × K_1 × I_a × Ω**.
        *   Angular velocity (Ω) is **Ω = V / (K_a × K_1 × I_a) - (R_a + R_s) / (K_a × K_1)**.
        *   **Speed is inversely proportional to torque** across the full torque-speed curve.
        *   They possess **very high starting torque**, making them suitable for applications like elevators and cranes.
        *   A significant drawback is that the motor can reach **dangerously high speeds if the load is disconnected**, necessitating safety devices such as over-speed detectors.
        *   **Speed control** can be achieved by placing a **diverter resistor (R_D) in parallel with the field winding** to reduce field current and flux, thereby **increasing speed**. To **reduce speed**, a variable resistor (R_a) can be increased in series with the armature.
        *   Series wound motors offer the **best starting torque and highest speeds**.
    *   **Compound Wound DC Motor**:
        *   These motors combine characteristics of both series and shunt wound motors by connecting the field winding partially in series and partially in parallel with the armature winding. This results in more complex wiring and higher cost.
        *   They offer a **hybrid performance**, combining high starting torque with good speed control at no-load conditions.
        *   The **torque-speed curve** resembles that of a shunt-wound motor, running slower when heavily loaded and faster when lightly loaded.
        *   Their **starting torque is intermediate** between series and shunt wound motors.
        *   There are two variations: **cumulative compound motors** where flux from field windings is in the same direction, and **differential compound motors** where flux is in the opposite direction and subtracts from magnetic field strength.
        *   Compound wound motors are among the most expensive types for a given power rating.

### Permanent Magnet (PM) DC Motors
*   A **permanent magnet motor** is a specialized and expensive type of brushed DC motor.
*   It utilizes **permanent magnets for the stator** instead of coil windings, which ensures a constant stator magnetic field. This construction can be a low-cost manufacturing approach for the stator.
*   The **armature still employs brushes and a commutator**. The armature's outer diameter is designed to barely clear the inner diameter of the magnets, creating an intense magnetic field.
*   PMDC motors exhibit a **linear torque-speed curve and linear torque-current curves** due to their constant magnetic field.
*   They demonstrate **significantly higher energy efficiency** compared to wound DC motors, as winding-associated losses like eddy currents are absent.
*   These motors are **physically smaller** than brushed motors of the same power rating.
*   Applications include **power assist for automobile windows and seats, windshield wipers, and computer hard drives** where space is limited.
*   In the commutator assembly, **carbon brush housings** are positioned 180 degrees apart, slightly radial outboard of the commutator windings. The brushes are typically held against the commutator windings by **compression springs** to maintain good contact pressure. Thick copper wires connect the brushes to the external circuit board.
*   A **250V/7A fuse** protects the motor from dangerous current overload. **Ceramic capacitors** (e.g., 250V) wired between brush housings and ground are used to absorb electrical noise generated by brush sparks.
*   An example of a PMDC motor is found in a **heavy-duty paper shredder**. The worm gear can be machined directly into the motor shaft as a low-cost manufacturing technique. Some models include a small plastic cooling fan.

### Brushless DC (BLDC) Motors
*   **Brushless DC motors** were developed to overcome the issue of carbon brushes wearing out and requiring periodic replacement.
*   BLDC motors **do not have brushes or a commutator**.
*   The **armature** consists of a series of **permanent magnets**.
*   The **stator** still uses **coil windings**, and an **electronic commutator** sequentially energizes these stator coils. This action generates a rotating electric field that provides torque to the armature.
*   **Hall effect sensors or rotary encoders** are used to sense the position of the armature, and this feedback determines when to switch the stator current. Hall effect sensors measure the magnetic field strength of the rotating armature.
*   The **stator coil circuit** can be modeled as a resistor and inductor in series, similar to a series wound DC motor.
*   **Coil current (I)** as a function of time is given by **I = (V - Vb) / R × (1 - e^(-Rt/L))**, where V is supply voltage, Vb is back EMF, R is resistance, L is inductance, and t is time. Maximum current is approached asymptotically, reaching over 99% within three time constants (L/R).
*   **Torque is proportional to the current**, with a proportionality constant K_t. Some motors may require a small initial current (e.g., 0.1 amps) to overcome mechanical friction before rotation begins.
*   **No-load acceleration** continues until the back EMF equals the applied voltage (back EMF is proportional to angular velocity, ω, via constant K_b). Frictional losses prevent exact attainment of this speed.
*   With an **external load**, the motor slows down, back EMF decreases, and additional motor current is drawn to supply the required torque.
*   Most BLDC motors have **three phases** (stator pole pairs), with each pole pair consisting of two coil windings energized simultaneously with opposite polarities.
*   The armature of a real BLDC motor typically has **between two and eight magnets** to provide sufficient torque.
*   In a three-phase BLDC motor, **only two of the three phases are energized at any given time**. This creates six polarity combinations or "states".
*   The armature rotates in **60-degree clockwise increments** by sequentially switching the polarity pattern in the stator windings across these six states. The **higher the frequency of phase switching, the higher the motor's RPM**.
*   The voltage in each phase is controlled by a pair of **inverter switches**.
*   BLDC motors require more wires: thick gauge for high-current power to the stator windings and thin gauge for low-current power to the Hall effect sensors.
*   **Key specifications** for BLDC motors include:
    *   **No load speed**, which is typically higher than rated speed.
    *   **Rated speed**, which is the speed at rated torque.
    *   The **torque constant (K_t)**, representing the torque produced per amp of current drawn.
    *   **Continuous stall torque**, the maximum torque deliverable for a short duration.
    *   **Continuous power**, the mechanical power delivered to a load, calculated as (efficiency at duty point) × (rated current) × (rated voltage).
    *   **Rotor inertia**, the mechanical moment of inertia of rotating parts, calculated as no-load torque divided by angular acceleration.
    *   **Operating temperature range** and **maximum temperature rise** for coil windings, which can indicate potential damage if exceeded.

### Trapezoidal Commutation for BLDC Motors
*   **Trapezoidal commutation** is the most common method for electronic commutation in BLDC motors.
*   The motor typically has three windings (A, B, C). Phase currents corresponding to phase voltages are square waves.
*   Six **inverter switches** (1 and 4 for winding A, 2 and 5 for B, 3 and 6 for C) control the voltage to each winding.
*   **Motor speed is controlled by the frequency of the switch pulses**, while **torque output is controlled by the phase current**.
*   **Three Hall effect sensors** are typically used to sense armature position, providing feedback for a closed-loop system to maintain constant motor speed.
*   The **back EMF in trapezoidal commutation forms a trapezoidal wave**, showing significant rise and fall times as armature poles approach and recede from stator coils. Back EMF is constant only when phase voltage is constant over a 120-degree interval of armature rotation.
*   Hall effect sensors (e.g., HE1, HE2, HE3) detect the passing of the armature's North and South poles at specific angles, triggering the controller to energize, de-energize, or switch polarity of the coils. For example, HE2 detecting a North Pole at 60 degrees triggers positive voltage to coil A, and HE1 detecting a North Pole at 180 degrees de-energizes coil A.

### Sensorless Control for BLDC Motors
*   In **sensorless control**, the motor controller monitors the **zero crossings of the back EMF** to deduce the armature angle.
*   The zero crossings of the idealized trapezoidal back EMF signals occur at odd multiples of 30 degrees, which is in the middle of the 60-degree state intervals.
*   **Challenges** with sensorless control include:
    *   Practical back EMF waveforms have **phase delays** due to winding imperfections, requiring individual measurement and calibration for each motor.
    *   At **low motor speeds**, the back EMF signal is weak, making it difficult to resolve zero crossings.
    *   Motors require **open-loop control for starting** until the back EMF signal reaches a pre-determined threshold, after which sensorless control can be engaged.
*   The **advantage** of sensorless control is reduced hardware cost and maintenance associated with Hall effect sensors, at the expense of more complex firmware.

### Torque Ripples and Torque Control in BLDC Motors
*   **Torque ripples** are slight dips in torque that occur approximately every 60 degrees of rotation in BLDC motors.
*   These ripples result from the finite time required to turn off current in one coil before turning on current in the next, causing interference between coils.
*   The magnitude of torque ripple varies from 3% to 7% of operating torque, depending on motor design.
*   **Torque control** in BLDC motors is achieved through **Pulse Width Modulation (PWM)** of the supply voltage.
*   The supply voltage is "chopped" at a high frequency (typically 20 Hz to 20 kHz) between commutation steps.
*   This chopping action reduces the mean voltage and thus the coil current, which in turn reduces the torque output.
*   **Commutation and chopping are not synchronized**, with the chopping frequency being orders of magnitude higher than the commutation frequency.
*   Using a fixed chopping frequency helps to limit both acoustic and electromagnetic interference (EMI) noise.

### DC Servomotors and Torque Motors
*   **DC servomotors** are a type of **brushless DC motor**.
*   They integrate built-in sensors, electronics, and firmware for a complete motor control loop within a single enclosure.
*   Servomotors are used to precisely control **position, velocity, or acceleration**.
*   They are characterized by **low inertia and high torque**, enabling a fast speed of response. While AC motors can serve as servomotors for very high loads, they offer a slower speed of response.
*   Common applications include **aircraft, machine tools, and precision instruments** where accurate motion control is critical.
*   A **generic motor control loop** for servomotors often employs **PID (Proportional-Integral-Derivative) control**.
    *   The control loop monitors the difference between the desired and actual position, with motor speed and acceleration being proportional to this difference.
    *   Feedback is used to compensate for position and velocity errors.
    *   A small amount of **overshoot** is inherent in the control system as the motor cannot stop instantly.
    *   **Tuning parameters (K_p, K_i, K_d)** are used to fine-tune the overshoot curve and determine the motor's response to a set point. A high K_d (derivative term) provides a fast response but may cause significant overshoot, while a high K_i (integral term) ensures no overshoot but results in a very slow response.
    *   Sensors used in servomotor control loops include potentiometers, tachometers, and accelerometers.
*   **Torque motors** are **toroidal-shaped brushless motors** designed to provide **very high starting torque**.
*   They can operate successfully even when the rotor is locked for extended periods.
*   High torque is achieved by running high currents through standard windings, which necessitates **cooling channels** (e.g., water circulation) to prevent overheating.
*   Functionally, a torque motor is akin to a linear motor rolled into a circle, lacking a commutator, frame, brushes, or bearings.
*   They are used as **actuators for direct-drive mechanisms** where large geared motors would typically be required. Historically, they found application in tape drives for maintaining light tension.

### Specifying a DC Motor
*   A systematic method for specifying a DC motor involves several steps:
    1.  **Identify the type of machinery** or application.
    2.  Determine the **available DC voltage** based on the power supply (e.g., 3V from batteries, 5V from an AC adapter, 600V for electric power trains).
    3.  Specify the necessary **electromechanical parameters**, including torque, power, and speed.
    4.  Define the requirements for **speed and position control**, as this significantly influences the appropriate motor type.
    5.  Establish a **budget** for the DC motor, noting that costs can range from $4 to $4,000.
*   An **example of motor selection for a portable electric screwdriver** demonstrates this process:
    *   **Constraints**: Portable (requires DC motor), limited space (max 25mm diameter).
    *   **Power Source**: Two 3-volt rechargeable batteries yielding 6-volt output, rechargeable via an external AC adapter.
    *   **Performance Requirements (Motor Output)**: 11 Watts of power, steady-state RPM between 3,000-7,000 (motor speed before gearing), and 21 milliNewton meters of operational torque (motor torque before gearing). A starting torque of 4 Newton-meters is required after gearing.
    *   **Gearing**: A planetary gear mechanism is required to achieve a final output of 140 RPM and 0.75 Newton-meters of torque.
    *   **Motor Type Elimination**:
        *   AC motors are unsuitable for portable tools.
        *   Brushless DC motors are unnecessary due to infrequent use, preventing brush wear.
        *   Stepper and servomotors are not needed for precision control in this application.
        *   Permanent magnet motors are not required for high energy efficiency, as batteries are rechargeable.
        *   Series wound motors are ruled out due to loss of speed control at zero torque and lack of space for safety devices.
        *   Shunt wound motors are rejected due to insufficient starting torque for self-tapping screws.
        *   Torque motors are over-specified and too expensive for the product.
    *   **Conclusion**: A **compound wound DC motor** is identified as suitable, meeting the need for high starting torque and good speed control.
    *   An example motor found online operates at 11.5 Watts, 5,000 RPM, and produces 21.6 milliNewton meters of torque. To achieve 140 RPM with this motor, a gear ratio of 35.7:1 is needed (5000 RPM / 140 RPM). This ratio, applied to the motor's torque, yields 750 milliNewton meters (0.75 Newton meters), meeting the requirement. The motor's stall torque of 143.7 milliNewton meters, multiplied by the gear ratio, provides 5.1 Newton-meters of torque after gearing, exceeding the 4 Newton-meter requirement. The current draw is 13 milliamps.

### Paper Shredder Mechanical Components (Example Application)
*   A paper shredder typically includes an **AC power board** that converts 120 VAC 60 Hz to 90 VDC.
*   A **paper presence sensor** detects paper insertion, initiating motor operation.
*   The shredder's mechanism is driven by a **DC motor** directly connected to a **worm gear assembly**.
*   The entire gear assembly provides an **82.5 to 1 gear ratio** for effective paper shredding.
    *   A **four-tooth worm** is mounted directly to the DC motor shaft, mating with a **44-tooth gear** to achieve an **11:1 gear ratio**. In some designs, the worm may be machined directly into the motor shaft.
    *   An inter-rail mounting shaft connects the 44-tooth gear to a **first spur gear**.
    *   This first spur gear (0.5 inches / 12.7 mm diameter) drives a **second spur gear** (3.75 inches / 95.3 mm diameter) for a **7.5:1 gear ratio**.
    *   The overall gear ratio is the product of these two ratios: 11 × 7.5 = 82.5:1.
    *   The second spur gear is mounted on the same hex shaft as the **first shredder roller** and a **third spur gear**.
    *   The third spur gear drives a **fourth spur gear of equal diameter**, which is attached to the **second shredder roller shaft**. Using gears of equal diameter ensures that both shredding rollers receive the same torque, leading to even paper shredding.
*   The **shredding mechanism** consists of two rollers with sharp teeth, between which paper is fed. The width of the shredded paper is determined by the gap between the hard plastic paper guide fingers.
*   The paper shredder motor is a **permanent magnet DC motor** with two semi-circular permanent magnets bonded to the inside of the steel housing, representing a low-cost stator manufacturing method. A small plastic cooling fan may be attached to the motor shaft.
