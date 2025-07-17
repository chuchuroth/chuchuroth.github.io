Here is a comprehensive overview of the knowledge contained in the provided sources, with colloquial language removed and key concepts highlighted:

### AC Induction Motors: Architecture and Principles

*   **General Architecture:** An AC induction motor consists of a **rotor** that revolves within a **stator**, which is a fixed electromagnet housed within a metal frame.
    *   A **drive shaft**, supported by **bearings**, is attached to the rotor to provide torque and speed to external mechanisms.
    *   A **cooling fan** extracts heat from the stator coil magnets.
    *   A **conduit box** houses and distributes electric wires from the line power to the motor windings.
*   **Stator Construction:** The stator is composed of a series of **laminated flat-steel discs** that are aligned to form channels for the **stator windings**.
    *   These windings are made of **layers of copper wire** that create loops, forming an electromagnet.
    *   The **pattern of coil windings** in the stator determines the number of poles for the motor, typically an **even number between 2 and 12**.
*   **Rotor Construction:** The rotor channels are made of **solid bars of copper or aluminum**, connected by **rings at the front and back of the rotor** to form a continuous high-current conducting loop.
    *   In smaller motors, these bars and end rings are cast as a **solid steel cylinder known as a squirrel cage**, with conductors embedded in its surface.
*   **Air Gap:** The rotor is inserted into the stator with an **air gap of approximately 20,000ths of an inch (0.5 mm)**. A larger air gap significantly reduces the stator's ability to induce current flow in the rotor.
*   **Electromagnetic Principle:** An iron rod suspended in a magnetic field will align itself with the field. If the field rotates, the iron rod will rotate with it to maintain alignment. In an AC induction motor, the rotor is analogous to this iron rod.
*   **Rotating Magnetic Field:** A rotating magnetic field is generated from fixed stator poles by driving each pole-pair from a different phase of the AC supply.
    *   For a **three-phase AC motor**, the three field windings are **120 degrees out of phase** with each other.
    *   As current in one pole pair peaks and falls, the magnetic flux weakens, while current and flux rise in the subsequent pole pair. This creates a **magnetic flux wave** that rotates from one pole to the next.
    *   The flux wave appears as rotating north and south poles around the stator. Its **magnitude is proportional to the applied voltage**.
*   **Induction and Torque:** The stator windings induce current in the rotor windings, eliminating the need for a direct electrical connection to the rotor.
    *   The AC induction motor gets its name from this induced current.
    *   There are **no external connections to the rotor**, and its windings are **shorted together**.
    *   Torque is induced in the rotor by the **reaction between the induced rotor current and the rotating magnetic flux**.

### AC Motor Specifications and Performance

*   **Synchronous Speed (Ns):** This is the angular speed of the magnetic field rotating around the stator.
    *   It is calculated as: **Ns = (120 × Line Frequency) / (Combined Number of North and South Stator Poles)**.
    *   Doubling the number of poles halves the synchronous speed.
*   **Slip:** For all AC motors, except synchronous motors, the rotor does not rotate at synchronous speed. This difference is called slip, and it depends on the motor load.
    *   Slip is calculated as a percentage: **Slip (%) = ((Ns - Nr) / Ns) × 100%**, where Nr is the rotor speed in RPM.
    *   Typical slip in AC motors ranges from **0.5% to 8%**.
*   **Rotor Current and Torque:** Rotor current is proportional to the **flux density in the air gap**, the **slip**, and the **rotor resistance**.
    *   Torque induced in the rotor is proportional to the **rotor current** and, consequently, to the **slip**.
    *   Increasing the load on an AC motor causes it to slow down, which increases slip, rotor current, and torque.
    *   An AC motor reaches an equilibrium speed when its output torque equals the load torque, providing the necessary current for the required torque.
*   **Torque-Speed Curve:**
    *   **Locked Rotor Torque (Starting Torque):** The torque output when the motor is at a standstill.
    *   As the motor accelerates, torque output decreases until it reaches the **pull-up torque**.
    *   As speed continues to increase, torque increases to a peak at the **breakdown torque (pull-out torque)**.
    *   At 100% of its rated speed (which is less than synchronous speed due to slip), the motor produces **full load torque**. Operating an AC motor at synchronous speed would produce minimal or no torque.
    *   The slope of the torque-speed curve near full load torque indicates speed regulation; a flatter slope allows for greater speed change without significant torque variation.
*   **NEMA (National Electrical Manufacturers Association) Designs:** NEMA defines three-phase AC motor designs based on their torque-speed curves and operational characteristics.
    *   These standards were developed over decades as manufacturers altered motor windings, rotor slots, and resistances to achieve custom torque-speed curves.
    *   **Current Draw:** Highest at startup (typically **6-9 times the operating current**), decreasing as the motor accelerates.
    *   **Voltage Impact:** Torque is linearly reduced with nominal voltage input; lowering voltage shifts the entire torque-speed curve downwards.

### Types of AC Motors

#### NEMA Motor Types (Three-Phase)

*   **Type D Motors:**
    *   Possess the **highest starting torque**.
    *   Used in applications requiring very high startup torque, such as **presses, elevators, and lifting equipment**.
*   **Type E Motors:**
    *   Have relatively **low starting torque**.
    *   Feature **low slip** and the **highest energy efficiency**.
    *   Used in applications like **fans, compressors, and pumps** that operate continuously (24/7).
*   **Type A and B Motors:**
    *   Exhibit **low starting torque**.
    *   Offer **medium to high energy efficiency**.
    *   Suitable for applications such as **pumps and compressors** that do not require 24/7 operation.
*   **Type C Motors:**
    *   Provide **reasonably high starting torque**.
    *   Are **more energy efficient than Type D motors**.
    *   Used for **conveyors, mixing motors, and reciprocating pumps** that need high starting torque and run for lengthy periods, justifying medium energy efficiency.

#### Wound-Rotor Induction Motors

*   **Design:** The squirrel cage rotor is replaced by **rotor windings connected via slip rings to a series of external resistors**.
*   **Torque-Speed Curve Adjustment:** The motor's torque-speed curve is adjusted by **varying the magnitude of these external resistances**.
*   **Winding Characteristics:** The rotor has more windings than a standard squirrel cage, leading to higher induced voltage and lower current.
*   **Starting:** During start-up, rotor poles are wired in series with variable power resistors, with **resistance values highest at start-up** to reduce stator field strength, decrease inrush current, and increase torque.
*   **Operation:** As the motor accelerates, the resistance is gradually decreased to zero at operating speed.
*   **Applications:** Used in **variable speed drive mechanisms, printing presses, rock crushers, and conveyors** where **very high starting torque** is required, often exceeding what NEMA Type D motors can provide.
*   **Torque-Speed Curve Modification:** Increasing resistance shifts the breakdown torque to lower synchronous speeds and can increase starting torque (e.g., resistance R2 can yield starting torque of 300% of full load torque, which is higher than NEMA Type D's 275%).

#### Synchronous Motors

*   **Speed:** Rotate at **synchronous speed (zero slip)** regardless of the motor load.
*   **Power Supply:** Large synchronous motors typically operate under three-phase AC power.
*   **Stator Design:** Similar to basic AC induction motors.
*   **Rotor Design:** Fundamentally different, containing **electromagnets connected to a separate DC power supply**. These electromagnets create stationary poles that attract to the opposite poles of the rotating stator magnetic field, allowing the rotor to move in sync.
*   **Starting Mechanism:**
    *   Often include a **squirrel cage rotor** solely to accelerate the motor to synchronous speed, as the primary copper rotor windings provide minimal starting torque.
    *   Alternatively, an **external motor** can be coupled to the drive shaft, or an **external rheostat** can be connected in series with the rotor windings (similar to a wound-rotor motor start).
    *   Once near synchronous speed, the rheostat resistance is reduced to zero, and **DC voltage is applied to the copper rotor windings**, pulling the rotor into synchronization.
    *   When synchronized, there is no relative motion, and the squirrel cage rotor no longer has an effect.
*   **Efficiency and Cost:** Synchronous motors are **more energy efficient** than induction motors due to less energy loss in rotor windings. However, they are **more expensive** to purchase than comparable induction motors.
*   **Applications:** Common in **mills and refineries** for large power applications (500 to 5000 horsepower). Small synchronous motors operating under single-phase AC power are used in mechanisms requiring **very precise speeds**, such as **aerospace guidance and navigation systems**.

#### Single-Phase AC Motors

*   **Fundamental Challenge:** Single-phase AC current in the stator winding produces a **fluctuating (not rotating) magnetic field**. This fluctuating field is equivalent to two magnetic fields rotating in opposite directions. These induce equal and opposite torques in the rotor, which would cause the motor to buzz rather than rotate.
*   **Solution: Starting Winding:** To create a net torque, an **extra winding, called the starting winding**, generates a secondary magnetic field that cancels one rotating stator field and adds to the other.
    *   After the motor reaches operating speed, it continues to rotate even if current to the starting winding is cut off.
    *   Many single-phase motor types use a **centrifugal switch** to disengage the starting winding once operating speed is attained. This disengagement can lead to a sudden drop in torque output (around 80% of full load).

##### Types of Single-Phase Motors:

*   **Split-Phase Motors:**
    *   The **starting winding wires have lower resistance and inductance** than the main stator winding wires, creating a differential in magnetic flux.
    *   A **centrifugal switch** automatically disengages the starting winding at operating speed.
    *   **Power Range:** Typically **1/20th to 1/3 horsepower (40 to 250 watts)**.
    *   **Applications:** Commonly found in **fans, blowers, and electric lawn mowers**.
    *   **Example Specifications (1/4 hp motor):** 190 watts, 1725 RPM, 1800 RPM synchronous speed (for 115V, 60Hz, 4 poles), 4.2% slip.
    *   **Construction:** Feature bare copper main stator windings on a laminated iron core, cooling fan blades on the rotor, and thinner, shorter starting windings deep inside. The centrifugal switch mechanism involves levers pressing a non-conductive plate that keeps contacts closed at rest, opening them due to centrifugal force as the motor accelerates.
*   **Capacitor-Start Motors:**
    *   A split-phase motor with **larger windings** and an **electrolytic capacitor placed in series with the starting winding**.
    *   The capacitor causes the current through the starting winding to lead the voltage, creating a significantly larger phase angle difference between starting and main winding currents (almost triple that of a split-phase motor).
    *   This results in **much larger starting torque**.
    *   A centrifugal switch disconnects both the starting winding and capacitor at operating speed.
    *   **Capacitors:** Electrolytic type, typically large (e.g., 16 mF for 1/3 hp to 50 mF for 10 hp) and often mounted externally.
    *   **Applications:** Popular in **refrigerator compressors and large pumps** where high starting torque is required.
    *   **Disadvantage:** The large capacitor occupies significant space, making packaging difficult.
*   **Permanent Split Capacitor (PSC) Motors:**
    *   Utilizes a **lower value capacitor with a high voltage rating** to generate the necessary phase shift.
    *   **No cut-off switch**; the starting winding functions as an auxiliary winding during operation.
    *   **Advantage:** Improved motor reliability due to the absence of moving parts (no switch).
    *   **Disadvantage:** Requires a smaller capacitor for continuous operation, leading to **low starting torque** (roughly 1/4 to 1/3 of a capacitor-start motor).
    *   **Applications:** Used in **fans and blowers** where frequent start-stop cycles occur and switch failure is a concern.
*   **Capacitor Start and Run Motors:**
    *   Includes a **second capacitor (run capacitor) in parallel with the starting capacitor**.
    *   Combines the benefits of both capacitor-start and permanent capacitor motors.
    *   When the centrifugal switch is closed, the capacitances add, providing the **highest starting torques among single-phase AC motors**.
    *   Once the switch opens, the run capacitor reduces operating current and improves energy efficiency, allowing the motor to operate closer to synchronous speed.
    *   **Applications:** Used for higher-powered applications such as **woodworking equipment or air compressors** where high starting torque is needed with single-phase AC power.
    *   **Disadvantage:** The two large capacitors can make packaging and wiring more complex.
*   **Shaded Pole Motors:**
    *   **Principle:** A pulsating magnetic flux from the main coil induces a voltage and current in a **shading coil (a simple copper wire loop around each pole)**, which opposes the flux change. This creates a lagging magnetic flux under the shading coil, resulting in a **small rotating magnetic field** and modest torque.
    *   **Cost:** **Very inexpensive to manufacture**.
    *   **Applications:** Used in products requiring **very low startup torque**, such as **small electric fans and pumps**.
    *   **Drawbacks:** Have the **lowest starting torque** (even less than operating torque), the **highest slip**, and the **lowest energy efficiency** of any AC motor type.

#### Gear Motors

*   **Design:** An **AC motor is directly coupled with a mechanical gear reduction assembly** on its output shaft.
*   **Function:** This assembly **significantly increases torque output** while **proportionately decreasing speed**.
*   **Housing:** Typically features separate housings for the motor and the gear reducer, with the latter containing gears, shafts, bearings, couplings, and lubrication.
*   **Gear Types:**
    *   **Spur or helical gears** are used when the output shaft is parallel to the input shaft.
    *   **Bevel or worm gears** are used when the output shaft is perpendicular to the input shaft.
*   **Applications:** Purchased when custom gear assembly design is cost-prohibitive, especially for large, expensive machines needing only one unit.
    *   Common gear ratios are **1000:1**, meaning torque is 1000 times greater and speed is 1/1000th of the motor shaft speed.
    *   Popular in **large mechanical lifts, medical equipment, and power jacks**.
    *   Can operate on **three-phase or single-phase AC power**.

#### Universal Motors

*   **Versatility:** Named for their ability to operate on **both DC and AC power**.
*   **Design:** Basic design is similar to a DC motor, with minor modifications for AC.
    *   **Field coils** are analogous to a stator, and the **armature** is analogous to a rotor.
    *   The **commutator** reverses current in the field coils and armature according to the AC line frequency.
    *   The **direction of torque** is independent of voltage polarity, determined by the commutator and field coil polarity.
*   **Construction:** Features a **two-pole field coil** made of laminated, tightly pressed coils, and an **armature (rotor)** with a laminated core overlaid with rotor windings, all pressed onto the motor shaft. The **commutator** is also on the shaft, and **brushes** contact it to supply current to the armature. There is a very small air gap (approx. 0.01 inches) between the armature's laminated core and the main iron core, allowing free rotation.
*   **Performance Characteristics:**
    *   Operate at **much higher speeds than other motors (above 4000 RPM)**.
    *   Possess **high starting torque**.
    *   Are **lightweight and small**.
*   **Applications:** The motor of choice for many consumer products, including **portable drills, power saws, vacuum cleaners, food processors, and lightweight portable fans**.
*   **Drawbacks:**
    *   **Noisy** due to the commutator.
    *   Emit significant **EMI (electromagnetic interference)**, potentially affecting nearby electronics.
    *   **Not suitable for continuous use** because the commutator brushes wear quickly.
