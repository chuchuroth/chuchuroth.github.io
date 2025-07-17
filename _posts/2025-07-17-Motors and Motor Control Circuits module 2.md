Here is the knowledgical information extracted from the provided sources, with colloquial language removed:

AC Motor Design, Specification, and Control:

*   **AC motors** are a significant energy consumer in industrial operations.
*   Governments globally have established energy efficiency standards for motors, such as Canada's EcoAction legislation and the American Energy Independence and Security Act of 2007. These standards apply to single-speed or three-phase motors up to 600 volts, in open or enclosed designs, with 2 to 8 poles.

**Motor Efficiency and Standards**:
*   Required motor efficiency typically **increases with higher power ratings** (e.g., up to 100 horsepower or 76 kilowatts) due to greater energy-saving potential.
*   Efficiency requirements remain relatively consistent across different enclosures and pole numbers for a given power.
*   **IEC (International Electrotechnical Commission) standards** classify motor energy efficiency from IE1 (least efficient) to IE4 (most efficient). Most governments endorse IEC standards with minor modifications.

**Voltage and Frequency Specifications**:
*   Single-phase voltage in North America is typically **120 volts, 60 hertz**.
*   Single-phase voltage in many other parts of the world is **220 volts, 50 hertz**.
*   Three-phase motors in North America commonly operate on **230 volts or 460 volts at 60 hertz**.
*   Three-phase motors in Asia and Europe commonly operate on **230 volts or 400 volts at 50 hertz**.
*   Motor controllers with primarily digital circuits typically use **24 volt DC single-phase power**.
*   **Motors designed for 50 hertz power can be used with 60 hertz power**, but power output, torque, and speed will change based on frequency and voltage.
    *   Example: A 380V, 50Hz motor run at 380V, 60Hz will have 100% rated power, 85% max torque, 70% starting torque, and run at 120% rated speed.
    *   If the same motor is run at 440V, 60Hz, power increases to 115%, max torque to 98%, starting torque to 95%, and speed remains 120%.
*   **Motor speed is controlled by changing input line frequency**.
*   **Motor torque and current are controlled by changing the magnitude of input line voltage**.

**Motor Ratings and Tolerances**:
*   **IEC 60034-1 permits specific tolerances on AC motor ratings**:
    *   Efficiency: 10-15%.
    *   Locked rotor (starting) current: 20%.
    *   Locked rotor torque: over 15%.
    *   Pull-up torque: 15%.
*   Motors should be specified based on their worst-case performance within these tolerances.
*   **NEMA and IEC standards mandate prominent labels on motors** listing essential information such as rated torque, speed, current, voltage, power, wiring methods, safety ratings, and safety warnings. These labels are crucial for motor replacement and maintenance, especially for older equipment.

**Motor Frame Sizes and Mounting**:
*   **NEMA and IEC standards define frame sizes** that dictate critical mounting dimensions based on motor horsepower. This standardization facilitates purchasing from various vendors and replacing motors.
*   **NEMA frame size conventions**:
    *   Frame numbers from 143T to 445T cover motors with power ratings from 1 to 200 horsepower.
    *   The **motor shaft height (D dimension) in inches** is calculated by dividing the first two digits of the frame size by four.
    *   The remaining digit relates to the motor's length.
*   **IEC motor frame sizes** are defined by Cenelec standard EN 50347. For example, a 132s frame indicates a 38 mm shaft diameter, and a 4-pole version of this motor would output 5.5 kilowatts.
*   **Common mechanical mounting methods for motors**:
    *   **Foot-mounted**: Motor is affixed to a flat machine surface using screws through holes on the motor's base.
    *   **C-face mounted**: Tap holes are located on the motor's face, typically 90 degrees apart and 45 degrees from the motor's x-y axis. The motor frame size determines the bolt circle diameter.
    *   **Cushion-based**: Features a thick rubber pad between the motor housing and the mounting frame, used to prevent vibration transmission in high-vibration environments.
    *   **D-flange**: Similar to C-face, but the motor face is milled flat to connect to a separate machine flange, with a specific bolt pattern.
*   Manufacturers provide motor drawings and 3D CAD files on their websites to aid mechanical design.

**Motor Enclosures and Protection**:
*   **Enclosures protect AC motors from particles and liquids, facilitate convective cooling, and ensure electrical safety**. NEMA and IEC specify enclosure designs, and global agencies like UL, CSA, and ATEX certify safety.
*   **Ingress Protection (IP) ratings** use two digits: the first indicates protection against solid objects, and the second indicates protection against liquids. A higher number signifies better protection (e.g., **IP65** protects against dust and water sprays).
*   **Common enclosure types**:
    *   **Open Drip Proof (ODP)**: Prevents ingress of particles and liquids at angles up to 15 degrees from the vertical axis.
    *   **Totally Enclosed Non-Ventilated (TENV)**: Has no openings and relies on heat fins for cooling. It is not airtight but prevents dust from interfering with motor rotation. Suitable for dirt or dampness, but not explosive gas environments.
    *   **Totally Enclosed Fan Cooled (TEFC)**: Similar to TENV but includes a fan for active cooling. Suitable for dirty or damp environments, but not explosive gas environments.
    *   **Explosion Proof (TEFC-XP)**: Required in environments with potentially explosive gases (e.g., petrochemical plants). The enclosure must withstand an internal explosion, and internal electrical components must be intrinsically safe.
*   **Explosion Proof Ratings (North American System)** classify hazardous environments by:
    *   **Class**: Type of material (Class 1: flammable gases/vapors; Class 2: combustible dusts; Class 3: ignitable fibers).
    *   **Zone**: Frequency of hazard presence (Zone 0: continuous; Zone 1: likely; Zone 2: not likely).
    *   Method of protection, apparatus group, and temperature class.
*   **European ATEX and CENELEC standards** use six zones to describe hazardous environments, similar in definition to North American classes and zones but grouped differently.
*   **IEEE 841-2001 Severe Duty Motor**: Designed for harsh, corrosive environments (e.g., petrochemical plants). It is based on a TEFC enclosure with enhancements like extra heat fins, **IP65 protection for the conduit box**, and durable epoxy paint. It is not certified for explosion-proof environments and is restricted to specific power and voltage ranges.
*   **Washdown Motor**: Based on the TEFC design, it withstands direct washing with sanitary cleaning fluids and minimizes particle generation, making it suitable for food processing, clean rooms, and pharmaceutical manufacturing. Key features include stainless steel components, FDA-approved epoxy paint, and drains. These motors are required by regulatory bodies like the FDA and USDA.

**AC Motor Specification Process**:
*   A structured method, often using a form, is used to specify an AC motor.
*   **Initial homework is required**:
    *   Define the process and type of machine the motor will serve.
    *   Determine the motor mounting method.
    *   Identify required power, torque (starting and operational), and operating speed.
*   **Environmental considerations**: Ambient temperature, humidity, and vibration levels (in Gs).
*   **Electrical power considerations**: Available electric power, including 3-phase voltage variants. Motors above 20 horsepower (15 kilowatts) typically require 3-phase power.
*   **Electromechanical specifications**: Specify both starting and operational torque, accounting for motor spec tolerances. Selecting a motor that provides slightly more torque than needed is advisable.
*   **Selection process**: Rule out unsuitable motors based on requirements or over-specification, then evaluate remaining options and optimize based on availability or machine adjustments.

**Examples of Motor Specification**:
*   **Concrete Mixer Motor**:
    *   **Requirements**: 3-phase, 230V, 60Hz induction motor, NEMA Type C, 7.5 HP (5.7 kW) output, 1770 RPM operating speed, 44 lb-ft starting torque, 22 lb-ft operational torque, C-face mounting, Open Drip Proof enclosure.
    *   **Ruling out options**: Single-phase, 50Hz, wound rotor, NEMA Type E (due to torque mismatch), synchronous (due to speed mismatch), and various over-specified enclosures/types (e.g., Type D, A, B, TENV, TEFC, explosion-proof, severe duty, washdown).
    *   A motor meeting these requirements (e.g., NEMA frame 213tc with 4 poles) was found, with a locked rotor torque of 46.3 lb-ft and calculated operating torque of 22.2 lb-ft, both slightly exceeding requirements.
*   **Garage Door Opener Motor**:
    *   **Requirements**: Single-phase, 120V capacitor start motor, NEMA Type C, 0.5 HP (380 watts) output, 1139 RPM operating speed, 8 lb-ft starting torque, 2 lb-ft operational torque, foot mount, Open Drip Proof enclosure.
    *   **Ruling out options**: 3-phase, 50Hz, NEMA Type E (due to torque mismatch), synchronous (due to speed mismatch), PSC/split phase/shaded pole (insufficient starting torque), Capacitor Start and Run (cost prohibitive), and various over-specified enclosures/types.
    *   A suitable motor was identified with an operating speed of 1140 rpm (0.1% deviation) and a locked rotor torque of 8.13 lb-ft. The calculated operating torque was 2.3 lb-ft. North American single-phase voltages often vary, making a 115V motor acceptable for a 120V specification.

**AC Motor Control System Components and Starting Systems**:
*   **Control system design requires specifying**: the AC motor (voltage, frequency, phase, power, speeds, currents), the power supply, and the machine's operating environment (temperature, humidity, IP, explosion-proof ratings).
*   **High starting current (6 to 9 times operating current)** can damage motor windings or starve other equipment on the same circuit.
*   **AC starter**: Wired in series with the motor to limit starting current. Its internal contactors are electromechanical relays that switch power to the motor, closing when energized and opening when de-energized. NEMA defines motor starter ratings based on motor horsepower.
*   **Overload relay**: Protects motor windings from thermal damage caused by high current loads during stalls or jams. It trips based on motor current, and thermal overload relays specifically protect against overheating based on a rapid temperature rise.
*   **Circuit breakers**: Protect the branch electrical circuit from current overloads by opening a mechanical switch; can be reset.
*   **Fuses**: Protect against current overloads once, requiring replacement after melting. A time delay fuse is suitable for motor circuits, tolerating the initial high starting current while protecting during normal operation.
*   **Wire gauge**: Determined by motor current rating, specified by standards like the US National Electric Code (NEC), which requires a conductor current rating of not less than 125% of the motor's full load current.
*   **Four types of AC Motor Starting Systems**:
    *   **Single-phase motor starter system**: Utilizes a normally open switch (M1) energized by a DC supply, controlling contactors (e.g., L1, L2) to start/stop the motor. Overload relays limit current during starting.
    *   **Full-voltage non-reversing three-phase motor starting system**: Involves connecting three contactors (L1, L2, L3) to the external three-phase AC voltage. A start button closes all contactors, and overload relays protect stator windings.
    *   **Full-voltage reversing three-phase motor starting system**: More complex, featuring mechanical interlocks to prevent simultaneous forward and reverse actuation. Requires stop, forward, and reverse push buttons. Motor direction is reversed by switching any two of the three input phases.
    *   **Wye-Delta (60 Hz) or Star-Delta (50 Hz) open transition three-phase motor starting system**.

**Star/Delta (Wye-Delta) Starting System**:
*   **Purpose**: To reduce motor starting current and minimize power supply disturbance by a factor of three.
*   **Requirements**: Both ends of the three stator windings must be connected to a terminal board. The Delta connection voltage must match the main input voltage.
*   **Starting Sequence**: The motor initially starts by closing Star and main contactors, which reduces the motor's rated Star voltage by the square root of three. This also reduces the current and starting torque by a factor of three. The motor then accelerates to 75-85% of its rated speed.
*   **Transition to Delta**: A timer controls the transfer from the Star to the Delta connection. The Delta contactor closes, and the Star contactor opens. Electrical interlocking prevents simultaneous closure of Star and Delta contactors, avoiding short circuits.
*   **Drawbacks**: The transition involves a 30-50 millisecond break in the power supply, which can cause voltage transients, potentially counteracting the system's intended purpose of reducing disturbance. The system requires low initial torque requirements due to the reduced starting torque. It also necessitates six motor leads and two sets of cables from the starter to the motor, increasing wiring complexity.
*   Despite drawbacks, Star/Delta systems are often mandated by electrical system standards.

**AC Motor Speed Control (Variable Speed Drives)**:
*   **Basic principles**:
    *   **Synchronous speed (N_s)** is directly proportional to line frequency (f) and inversely proportional to the number of poles (p): N_s = 120 * f / p.
    *   Reducing line frequency alone can lead to increased motor current, torque, and magnetic flux saturation if voltage remains constant.
    *   **To maintain magnetic flux within operating limits, voltage is reduced proportionally to frequency (constant V/Hz ratio)**. This ensures constant torque and linearly increasing power with speed.
*   **Applications**: Spindle speed control in machine tools, varying conveyor speeds, and speed control for large fans, compressors, and pumps.
*   **Operation**: Achieved using a variable frequency power supply, commonly with three-phase AC motors.
    *   **Process**: AC line voltage is rectified to DC, filtered, then converted back to variable frequency AC power by an inverter.
    *   **Components**:
        *   **Diode rectifier**: Converts AC to DC, with a minimum of six diodes for three-phase power. More diodes (e.g., 12 or 18) or inline inductors can reduce reflected harmonics back to the AC source.
        *   **Filter**: Smoothes the DC signal from the rectifier.
        *   **Inverter**: Converts filtered DC back to AC using **Insulated Gate Bipolar Transistors (IGBTs)** via Pulse Width Modulation (PWM) switching.
        *   **Voltage and frequency controller**: Determines the motor's input voltage and frequency.
        *   An output filter smooths the quasi-sinusoidal voltage output.
*   **PWM Methods**:
    *   **Six-step PWM**: Inverter provides six distinct switching states. It is simple but produces low-order harmonics that are difficult to filter, leading to torque ripples. Motor direction reversal is done by changing inverter output phase sequence.
    *   **Space Vector PWM (SVPWM)**: Converts three-phase voltage vectors into a single rotating vector, supplying eight switching states. It reduces low-order harmonics more effectively but is computationally intensive.
*   **Starting Sequence**: The controller applies very low frequency and voltage initially to prevent high inrush current. Both parameters are slowly ramped up, maintaining a constant ratio. The motor can achieve up to 150% of rated torque at low speeds with less than 50% of rated current. Torque is kept constant during acceleration to prevent overheating.
*   **Stopping Sequence**: Frequency and voltage are ramped down at a controlled rate while maintaining a constant ratio. The motor is shut off as frequency approaches zero. A small braking torque is applied for faster deceleration, which can be supplemented by a braking circuit.
