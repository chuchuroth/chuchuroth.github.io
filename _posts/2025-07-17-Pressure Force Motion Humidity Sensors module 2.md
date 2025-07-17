Here is the knowledge-based information extracted from the sources, with colloquial language removed:

**Module 2: Sensors and Motors Specialization**
*   Module two of the course specializes in **embedding sensors and motors**, specifically applying knowledge of pressure sensors to **strain gauges, load cells, and touchscreens**. The module includes reading assignments and circuit studies.

**Strain Gauges**
*   **Definition and Application:**
    *   A **strain gauge** is a deformable resistor.
    *   Strain gauges are used in products such as **load cells**, and for **safety tests on structures** like buildings, bridges, tunnels, and roads.
    *   They are employed to gather data on **stresses in critical structural elements**, which engineers use to **estimate stress from measured strain**, as direct field measurement of stress is difficult.
    *   For instance, transportation engineers place strain gauges on **lateral girders of bridges** to monitor stresses and prevent structural failure.
*   **Design and Operation:**
    *   Typical strain gauges for measuring longitudinal strain are **etched metal foils with wires aligned parallel to the direction of strain**.
    *   The gauge is **bonded to the structural element using adhesive** on its backing material.
    *   **Stress** on the gauge causes wires to be pulled or pushed: **positive strain indicates axial tension**, while **negative strain indicates axial compression**.
    *   The connecting wires of a strain gauge are typically attached to the legs of a **Wheatstone bridge** circuit.
*   **Concepts of Stress and Strain:**
    *   **Tension** occurs when a structural element is pulled.
    *   **Compression** occurs when a structural element is pushed.
    *   **Normal strain (ε)** is a non-dimensional term defined as **elongation per unit length (Δl/l₀)**, occurring perpendicular to the axis of tensile or compressive force. It can be measured in units like meters/meter or inches/inch.
    *   **Normal stress (σ)** is defined as **force (F) divided by the surface area (A)** to which the stress is applied (σ = F/A).
    *   **Normal strain (ε) is equal to normal stress (σ) divided by the modulus of elasticity (E)** (ε = σ/E). The **modulus of elasticity (E)** for most steels is approximately **30 x 10⁶ pounds per square inch (200 gigapascals)**.
    *   **Shear** occurs when a structural element is cut or twisted by torque.
    *   **Shear strain (γ)** occurs parallel to the axis of the shear force and is also a non-dimensional term. Its calculation is more complex, involving changes in cross-section from square to diamond shape. The formula for shear strain is **γ = ∂u_y/∂x + ∂u_x/∂y**.
    *   **Shear stress** in a beam is zero at the surface and peaks at the **neutral axis** (center). Peak shear stress for a rectangular beam is **1.5F/A**.
    *   **Shear strain (γ) is equal to shear stress (τ) divided by the shear modulus (G)** (γ = τ/G). The **shear modulus (G)** for most steels is approximately **11.5 x 10⁶ pounds per square inch (79 gigapascals)**.
*   **3D Stress and Strain (Isotropic Materials):**
    *   For **isotropic materials** (elastic properties are the same in all directions), normal and shear stresses exist on all six faces of a cube.
    *   Normal strains in three directions depend on normal stresses, modulus of elasticity (E), and **Poisson's ratio (ν)**.
    *   **Poisson's ratio (ν)** is the ratio of lateral strain to axial strain, typically **0.3 for most metals**. It accounts for the material shrinking laterally when elongated axially.
    *   The strain in the x-direction (ε_x) is given by: **ε_x = (σ_x / E) - (νσ_y / E) - (νσ_z / E)**, with analogous equations for ε_y and ε_z.
    *   For a bar under axial tension/compression (only σ_x), ε_y = -ν * ε_x.
*   **Strain Gauge Placement and Signal Interpretation:**
    *   Strain gauges are typically placed where **peak strains are known to occur** to enable calculation of peak stresses and determination of structural failure risk.
    *   **Wheatstone Bridge Circuits:**
        *   In typical instrument design, **four strain gauges are arranged in a full Wheatstone bridge**.
        *   The output voltage (V₀) from a full bridge is given by: **V₀ = V_i * [(R1*R3 - R2*R4) / ((R1+R2)*(R3+R4))]**.
        *   For structural experiments, strain gauges can also be placed in a **half bridge (with two fixed resistors)** or a **full bridge with three fixed resistors**, though the latter results in less accurate temperature-dependent data.
        *   The primary goal is to detect the **change in strain gauge resistance due to mechanical stress**.
        *   Full bridge circuits with active gauges in all four arms are common in pressure sensors and load cells to **compensate for temperature measurement errors**.
*   **Simplifying Assumptions for Wheatstone Bridge Calculations:**
    *   A formula for bridge output with four unknown resistance changes is insoluble without simplifying assumptions.
    *   **Assumption 1: Symmetric Installation:** Strain gauges are installed symmetrically in opposite pairs in areas of maximum tension, compression, or shear strain. This maximizes voltage output (V₀) and helps eliminate temperature measurement errors.
    *   **Assumption 2: Gauge Equivalence:** Tension gauges R₂ = R₃ and compression gauges R₁ = R₄.
    *   Under these assumptions, the change in output divided by excitation voltage is **ΔV₀/V_i = ε / GF**, where ε is the absolute strain and **GF is the Gauge Factor** supplied by the manufacturer.
    *   Therefore, strain can be calculated as **ε = GF * (V₀ / V_i)**.
    *   Output voltage V₀ is often very small, necessitating **signal amplification**.
*   **Strain Gauge Attachment:**
    *   Adhesion is critical: most gauges are affixed with **bonding glue or adhesive tape**.
    *   The bonded surface must be prepared by **cleaning (removing rust, paint, lubricants), smoothing (possibly with filler), and degreasing with organic solvents**.
    *   Gauges can be bonded to metal, plastic, wood, or concrete.
*   **Powering Strain Gauge Bridges:**
    *   Using a **constant current source** to power the bridge offers **better temperature compensation** because resistors do not heat up with increasing current, and current remains constant regardless of strain gauge resistance.
*   **Temperature Effects on Strain Gauges:**
    *   **Temperature Coefficient of Resistance (TCR):** quantifies the effect of temperature change on resistance change.
    *   **Temperature Coefficient of Gauge Factor (TCGF):** quantifies the effect of temperature change on the gauge factor. TCGF is typically low for metals but high for silicon-based gauges.
    *   **Apparent strain** refers to a strain offset caused by factors other than mechanical stress, such as temperature-induced changes in gauge resistance or gauge factor.
    *   A significant issue is when the gauge and the bonded material **expand or contract at different rates** due to temperature changes. Large differences in their coefficients of thermal expansion (C_m vs. C_s) induce mechanical stress at the joint, which appears as apparent strain.
    *   Mounting four strain gauges in a Wheatstone bridge with adjacent gauges strained in opposite directions can substantially eliminate apparent strain caused by TCR. However, this method assumes identical nominal resistance and TCR for all gauges, which is not achievable in manufacturing.
    *   **Bonding resistance** issues can occur, especially in instruments assembled at high temperatures. The differential expansion and contraction of the gauge and structure during cooling can induce mechanical stress, causing a resistance change (R_B different from R_G) and leading to strain measurement errors. If the strain gauge's coefficient of expansion is greater than the structure's, the bonded gauge's resistance will be higher.
    *   Some manufacturers offer more expensive strain gauges with **coefficients of thermal expansion matched to specific materials** like aluminum, carbon steel, or stainless steel to mitigate these issues.
*   **Strain Gauge Geometries:**
    *   **Linear gauge:** Used to measure strain predominantly in one direction, with strain wires aligned accordingly.
    *   **Rosette strain gauge:** Contains multiple elements optimized for different strain directions. Examples include gauges with grids for X and Y directions (for 3D stress states) or three grids offset at 45 degrees (when strain direction is unknown).
*   **Typical Specifications:**
    *   **Carrier material:** Often polyethylene, a rigid plastic.
    *   **Measuring grid (strain wires):** Commonly Constantan, a high-conductivity metal. Constantan's coefficient of thermal expansion is about 10% higher than steel, resulting in less apparent strain than copper wires on steel structures.
    *   **Connecting leads:** Conventional nickel-plated copper leads.
    *   **Nominal resistances:** 120, 350, 700, or 1,000 ohms, with tolerances of 1-1.5%. Larger nominal resistance is preferred for larger expected strain measurements.
    *   **TCGF:** Specified by the supplier for each manufacturing lot due to variations.
    *   **Transverse sensitivity:** A slight resistance change when strain is perpendicular to the active direction.
    *   **Temperature ranges:** Similar to piezoresistive pressure sensors.
    *   **Customization:** Gauges can be customized with discrete resistors to alter TCR and span sensitivity for specific structural materials.
    *   **Maximum elongation:** Typically 5%, which is very high for practical applications.

**Load Cells**
*   **Definition and Function:**
    *   A **load cell** is an instrument designed to **measure force**, commonly weight. It is a combination of a deformable structure and a strain gauge.
    *   Weigh scales often incorporate **four load cells**.
    *   Load cells correlate strain signals to weight through a factory calibration process.
*   **Types of Load Cells:**
    *   **Pancake load cell:**
        *   Commonly used in scales.
        *   Employs **eight strain gauges measuring shear strain** at a central machined hub.
        *   Gauges are mounted at **±45 degree angles** to the hub, aligning with planes of maximum shear stress.
        *   Uses **two bridge circuits** (one for X-axis, one for Y-axis).
        *   This configuration (two positive shear, two negative shear gauges per axis) maximizes signal strength and eliminates temperature variation errors.
        *   Includes an inner hub with an air gap for **overload protection** and a seal for **contamination protection**.
    *   **Dual beam load cell:**
        *   Features a central cut-out.
        *   Bending moments from applied loads create bending stresses.
        *   Gauges are placed at points of highest strain (two measuring tensile, two compressive).
        *   Uses **one bridge circuit** for the four gauges, similar to a cantilever beam setup.
    *   **S-Beam load cell:**
        *   Optimized for measuring **tensile or compressive loads** along its axial centerline.
        *   Used in hopper/tank batch weighing and controlling tension in heavy cables.
        *   Threaded holes allow mounting for tension or compression.
        *   Strain gauges are mounted at **±45 degree angles** to the circular cut, like the Pancake load cell.
*   **Load Cell Specifications and Operation:**
    *   **Mounting procedures are critical** for accurate load sensing.
    *   The maximum measured load must remain below the **overload limit**.
    *   Wires and gauges require protection from electrical surges, moisture, and corrosion.
    *   Output can be **nonlinear at the low end** of the operating scale.
    *   Load cell spec sheets share similarities with strain gauge spec sheets due to shared electronics.
    *   Load cells typically exhibit **lower temperature zero and span shift** compared to piezoresistive pressure sensors, attributed to the stability of metal strain gauges.
    *   Common nominal bridge resistance is 700 ohms.
    *   **Calibration** is often performed using a **five-point compression standard**, applying five precise weights across the full range.
    *   **Safe overload** is typically 150% of rated output.
    *   Error budgets for **nonlinearity, hysteresis, and repeatability** are comparable to piezoresistive pressure sensors.
    *   Mechanical dimensions and electrical pin-outs are specified, with identified loading surfaces designed to maximize shear strain for accurate calibration.

**Bathroom Scale Tear-Down**
*   A typical bathroom scale uses **one strain gauge under each of its four corners**.
*   The scale measures weight by sensing the strain caused by the user's weight bending the central glass platform.
*   The bending of the glass creates **maximum deflection in the middle** and significant tensile and compressive loads.
*   The strain gauges typically measure the **left-to-right component of strain** induced in the metal C-brackets they are bonded to.
*   The configuration of strain on the gauges (e.g., left-side gauges experience rightward strain, right-side gauges experience leftward strain) allows their strains to be summed in a Wheatstone bridge for maximum signal.
*   **Power:** Two CR2032 coin cell batteries in parallel supply 3 volts to the circuit board.
*   **Wiring Scheme:**
    *   Each strain gauge has **three wires** (red, blue, white).
    *   The wires from all four strain gauges connect to the main circuit board.
    *   The scale's strain gauges are **not wired in a standard quarter bridge circuit**, and no fixed resistors are present on the board.
    *   Instead, **each load cell (strain gauge assembly) appears to use the other load cells as its fixed resistors** within the Wheatstone bridge configuration. This is feasible because scales are typically used in temperature-stable indoor environments, and resistances become stable once a measurement stabilizes.
    *   This wiring architecture is supported by commercially available "load sensor combinator" boards, indicating it's a recognized method for connecting multiple 3-wire load cells to a Wheatstone bridge.
    *   This design choice allows manufacturers to **reduce costs**, as 3-wire load cells are inexpensive (around $1).
    *   Scales are calibrated by applying known weights and correlating them to the bridge output.

**Resistive Touchscreens**
*   **Four-Wire Resistive Touchscreens (Historical):**
    *   **Structure:** Composed of three layers: a flexible top layer of glass coated with **Indium Tin Oxide (ITO)**, a rigid middle layer also coated with ITO, and a bottom insulating glass layer.
    *   **Insulation:** Hundreds of thin insulating **spacers (dots)** separate the top and middle conductive layers to prevent constant contact.
    *   **Conducting bars:** The top layer has two conducting bars on the Y-edge, and the middle layer has two on the X-edge.
    *   **Principle:** Both conductive layers have uniform resistance. Applying voltage creates a **uniform voltage gradient**. When touched, the flexible top layer makes contact with the middle layer, completing a circuit.
    *   **Input:** Can be activated by a bare finger, gloved hand, stylus, or other pointer.
    *   **Coordinate Measurement:**
        *   To measure the Y-coordinate, the system powers the top layer, and one conductive bar on the middle layer is connected to an **Analog-to-Digital Converter (ADC)** via a high-impedance circuit.
        *   To measure the X-coordinate, the system powers the middle layer, and one conductive bar on the top layer is connected to an ADC.
        *   Only three of the four wires are active during a measurement.
    *   **Reliability Issues:**
        *   **Fatigue cracking of the ITO coating** occurs due to constant flexing of the top layer, altering its electrical resistance and linearity, particularly affecting Y-measurements.
        *   Using a stylus or pen accelerates this cracking.
        *   Polyester top layers degrade faster when exposed to outdoor temperature and humidity swings.
        *   Typical lifespan ranges from **100,000 to 1 million uses**, which is insufficient for high-traffic applications like airport kiosks, often requiring annual replacement.
*   **Five-Wire Resistive Touchscreens (Improved Reliability):**
    *   **Design Solution:** Introduced to improve reliability by removing the conducting and voltage measurement functions from the flexible top layer.
    *   **Structure:** Has a flexible top layer and a rigid bottom layer, both conductive. Insulating spacers still separate the layers.
    *   **Principle:** The **bottom layer determines both X and Y positions**, while the **top layer acts solely as a voltage probe**.
    *   **Coordinate Measurement:**
        *   For Y-coordinate: Controller applies +Vcc to the top two corners of the bottom layer and grounds the lower two corners, creating a voltage gradient. The fifth wire, attached to the flexible top layer, probes the voltage at the touch point, which is then fed to the ADC.
        *   For X-coordinate: Controller applies +Vcc to the left two corners and grounds the right two corners of the bottom layer, creating an X-voltage gradient. The fifth wire again probes the voltage at the touch point for ADC input.
    *   **Reliability:** Significantly greater than 4-wire versions because the top layer is only a voltage pointer, not a measurement layer, reducing fatigue.
    *   **Normalization:** Voltage readings are normalized by the actual X and Y axis distances to determine precise touch locations.
    *   **Typical Specifications:**
        *   Diagonal sizes: 7-22 inches.
        *   **Position accuracy:** A standard deviation of **2 millimeters** (implying 98% of touches are within 4mm of the actual point), explaining the need for large icons on kiosks.
        *   Resolution: 4096x4096 pixels.
        *   Touch force: 113 grams.
        *   Communication: Standard RS232 and USB.
        *   Environmental: Suitable for indoor and outdoor use (excluding rain).
        *   Chemical resistance: Resistant to a wide range of chemicals.
        *   Can be modified to meet **NEMA 4 and IP65 standards for water entry** (requires rubber bezel).
        *   **Endurance:** 35 million touches, meaning devices become technologically obsolete before the touchscreen fails. Manufacturers typically offer 3- to 5-year warranties.

**Capacitive Touchscreens**
*   **Surface Capacitive Touchscreens (Older Technology):**
    *   **Structure:** Protective cover (glass/plastic), middle transparent film coated with ITO, thick glass bottom layer. Four electrodes are located at the corners.
    *   **Principle:** When a bare finger touches the screen, a small electric charge transfers from the finger, creating a voltage drop relative to the electrodes. The exact voltage drop varies with finger position.
    *   **Advantages:** The top surface is not flexed, leading to a **much longer lifespan** than resistive touchscreens.
    *   **Disadvantages:**
        *   Requires a **bare hand or specially made conductive glove** for operation.
        *   **Cannot perform multi-touch gestures** like pinch-in or pinch-out, which led to their decline in applications like smartphones.
*   **Mutual Capacitive Touchscreens (Modern Technology):**
    *   **Development:** Developed to enable multi-touch gestures.
    *   **Structure:** Protective cover (glass/plastic), and a middle layer consisting of **two separate grids (X and Y) of transparent ITO electrodes**, positioned on **different planes**. A thick glass bottom layer supports them.
    *   **Principle:** A 3D electrostatic field is created by the electrodes. When a finger disturbs this field, it changes the ratio of currents in the X and Y grids.
    *   **Operation:**
        *   Current is successively driven through **transmit (TX) electrodes**.
        *   **Receiving (RX) electrode lines** are positioned underneath and across the TX lines, forming **capacitive coupling nodes** at their intersections.
        *   Commercial touchscreens have numerous electrodes and intersections.
        *   A controller records the **mutual capacitance** of each node at high speeds, enabling multi-touch gestures.
        *   A digital voltage signal (+Vcc to ground) is applied to the TX pin, and charge is received on the RX pin, proportional to the nominal mutual capacitance (C_m).
        *   When a finger is placed between TX and RX electrodes, C_m decreases (to C'_m) because a small charge leaks to the finger, reducing the charge received. The controller detects a touch when the received charge is below the nominal charge.
    *   **Advantages:**
        *   A finger does **not require direct contact** with the screen; proximity is sufficient for charge conduction.
        *   Can be activated with **thin cotton or latex surgical gloves**.
        *   Enables **multi-touch gestures**, which is a significant advantage over other touchscreen types.
    *   **Disadvantages:**
        *   **Sensitive to EMI and RFI noise** due to small transmitted currents and static charge buildup in dry conditions, requiring circuit design countermeasures.
        *   Will **not operate if the surface is soaking wet**, though a few droplets are tolerable.
*   **Apple iPhone Touchscreen (Patent 7663607):**
    *   Utilizes a two-layer grid of **driving lines and sensing lines** that form capacitive sensing nodes.
    *   These nodes are configured to sense capacitive input from an object near them.
    *   When an object approaches a node, it **"steals" charge, thereby reducing the capacitance at that node**.
    *   The capacitive sensing circuit measures all sensing lines in parallel. Driving lines are sequentially activated, and the process continuously repeats.
    *   Sensor ICs measure capacitance at each node, convert analog signals to digital data, and transmit data over a serial bus to a host controller.
    *   **Layers (cross-sectional view):** The LCD display is beneath all touchscreen layers. A **transparent sensing layer** (sensor lines in columns) is positioned over a first glass member. A **transparent driving layer** (driving lines in rows) is positioned over a second glass member, which in turn is over the first glass member. The second glass member insulates the driving and sensing layers. Driving lines intersect sensing lines to form capacitive coupling nodes.
    *   The change in capacitive coupling (due to an object shunting the field away) changes the current on the sensing lines, allowing the circuit to detect the touch and relay the node position to the host controller. This process is rapid to facilitate multi-touch gestures.
*   **Mutual Capacitive Touchscreen Specifications (for Fixed Monitors/Kiosks):**
    *   Diagonal sizes: 7-22 inches.
    *   **Position accuracy:** 1.5 millimeters (better than resistive).
    *   **Durability:** 15 million touches.
    *   Communication: Standard USB, I2C, and HID over I2C.
    *   Input: Finger, gloved hand, or stylus.
    *   Applications include gaming and lottery terminals.

**Strain Gauge and Load Cell Lab Interface**
*   **Distinction:** A **strain gauge** is the deformable resistor, while a **load cell** is the strain gauge combined with a well-characterized bendable structure (e.g., a slotted beam). The load cell's spring constant is consistent.
*   **Advantages of Strain Gauge:** Simple, versatile application, contamination resistant.
*   **Disadvantage of Strain Gauge:** Produces a very small signal.
*   **Lab Setup (Cypress CY8CKIT-059):**
    *   Load cell amplifiers are readily available.
    *   **Power and Ground:** The Cypress dev kit is powered by USB (VDD pin produces slightly less than 5V, e.g., 4.79V). The Nscope has a more robust 5V power supply. It is critical to **connect the grounds of both devices** but **not to connect the dev kit's VDD to the Nscope's 5V supply**. Small capacitors can be added to the Nscope's 5V line for noise minimization.
    *   **Strain Gauge Interface Circuit:** Uses four external resistors to represent the strain gauge. The strain gauge wires connect to a **Programmable Gain Amplifier (PGA)** for signal amplification.
    *   The resistors on the strain gauge are arranged to provide a **differential measurement** (when one resistance increases, another decreases), which is more accurate and noise-immune.
    *   **Addressing PGA Input Voltage Offset (VOS):**
        *   Inexpensive amplifiers, like the PSoC dev kit's PGA, have a significant **VOS** (e.g., up to 20 millivolts), which can be larger than the millivolt-level signal from a strain gauge, causing output inaccuracies.
        *   To null out this offset, a **Digital-to-Analog Converter (DAC) and an Op-amp** can be used with a resistor bridge.
        *   **Software controls the DAC** to adjust its output until the ADC reads a non-saturated value, indicating the VOS has been canceled. This nulling process requires the strain gauge to be **undistressed**.
        *   A limitation is the **temperature drift of the PGA's VOS** (e.g., 30 microvolts per degree Celsius), which can introduce error if the temperature changes after nulling.
    *   **UART Communication:** A **UART** (Universal Asynchronous Receiver-Transmitter) is used to communicate with a terminal emulation program (e.g., Tera Term) on a PC, eliminating the need for an on-board LCD.
    *   Windows automatically creates a virtual COM port for the USB connection to the dev kit.
    *   Terminal emulation program settings (COM port, baud rate, data bits, parity, stop bits, flow control) must **match the UART configuration** for successful communication.
