The knowledgeable information, know-how, industry practices, and technical details extracted from the two videos regarding Medium Voltage (MV) technology, power supply, and switchgear components are presented below.

---

### I. Energy Fundamentals and Power Grid Architecture

#### A. Energy and Transformation

*   **Definition of Energy:** Energy is the capacity to perform a job or produce a change, existing in forms such as mechanical, electrical, and thermal energy.
*   **Energy Transformation (Mechanical):** Mechanical energy can be transformed using interlocked gears, which determine speed and torque. Gears can be used to increase speed, increase force, change motion direction, or provide mechanical control in MV switchgear.
*   **Energy Transformation (Electrical):** Electrical energy is transformed using transformers. Alternating current (AC) flows through a primary coil, inducing a magnetic field concentrated in the core (typically iron), which then induces a voltage (either increased or reduced) in the secondary coil.
*   **Electricity Generation (Three-Phase AC):** The simplest method is a three-phase generator, converting mechanical energy into electrical energy using three coils placed $120^\circ$ apart.
    *   The rotor creates a rotating magnetic field (via permanent magnets or electromagnets).
    *   This setup produces three separate AC waveforms, $120^\circ$ out of phase, which combine to provide a continuous and balanced power supply, which is more efficient and stable than single-phase power.
    *   Power is distributed through three active wires and one neutral wire.
*   **Alternating Current (AC) Characteristics:** The flow of the electrical wave periodically reverses direction and amplitude.
    *   **Amplitude:** The maximum value of the wave (from zero line to the peak). It represents the power of the wave, measured in volts. Higher amplitude means higher voltage.

#### B. Power Grid Structure and Voltage Levels

*   **Power Grid Architecture:** The network includes infrastructure for generation, transmission, and distribution.
*   **Voltage Classification (Widely Accepted):**
    *   **Low Voltage (LV):** $120 \text{ V}$ up to $690 \text{ V}$.
    *   **Medium Voltage (MV):** $1 \text{ kV}$ up to $52 \text{ kV}$.
    *   **High Voltage (HV):** $72.5 \text{ kV}$ up to more than $1,000 \text{ kV}$.
*   **International Rules:** In principle, there are two voltage groups: LV (up to and including $1 \text{ kV}$) and HV (above $1 \text{ kV}$). MV is often defined as the sub-range of HV above $1 \text{ kV}$ up to and including $52 \text{ kV}$, serving as a bridge between LV and HV.
*   **Reasons for Multiple Voltage Ratings:**
    *   **Efficiency in Power Distribution:** Higher voltage reduces current, which reduces cable cross-section (lowering cost) and minimizes losses due to cable resistance.
    *   **Optimizing Equipment Size and Cost:** Using the appropriate voltage rating optimizes the size and cost of the equipment.
    *   **Safety and Reliability:** Lower voltages are safer for residential use, while higher voltages are used in the industrial sector.
    *   **Load Management:** Different voltage ratings allow effective load management.
    *   **Rule of Thumb:** To carry power efficiently over distance, a general rule is to **increase $1 \text{ kV}$ per kilometer** (e.g., carrying $25 \text{ MW}$ over $20 \text{ km}$ is highly inefficient at $6 \text{ kV}$ (over 40% losses) but efficient at $30 \text{ kV}$ (nearly 2% losses)).

#### C. Transmission vs. Distribution

*   **Transmission:** Transports electricity over long distances (usually above hundreds of kilometers) from generation to consumption, typically using voltages above $100 \text{ kV}$. In some countries, MV can be used for transmission over shorter distances between urban areas.
*   **Distribution:** The process of delivering electricity to consumers.
    *   **Primary Distribution:** Characterized by **higher currents and higher short circuit values**. Delivers large amounts of power from main substations to distribution substations, or for industrial consumption.
    *   **Secondary Distribution:** Characterized by **lower currents and lower short circuit values**. Delivers power from distribution substations to final end consumers.

#### D. Component Quantity Rule (The Pyramid)

*   **Principle:** The quantity of components needed in the distribution network is inversely associated with the voltage level: **The higher the voltage level, the less quantity of components; the lowest voltage level requires the most quantity of components**. This is because voltage is reduced step-by-step to distribute power to an increasing number of consumers.

#### E. Substation Functions

*   **Main Substation:** Steps down high voltage (transmission) to medium voltage (distribution). Uses power transformers and medium voltage switchgear/circuit breakers. Often includes measure, control, automation, communication, and monitoring components for high digitalization and remote control.
*   **Secondary Distribution Substation:** Steps down medium voltage (from main substation) to low voltage (for final residential consumption). Key functions include:
    *   **Protection and Control:** Includes circuit breakers/fuses to safeguard the network from faults and overloads.
    *   **Voltage Regulation:** Maintains voltage levels within limits for stability and safety.
    *   **Monitoring and Communication:** Systems to monitor performance and communicate with central control systems.

#### F. Equipment Size and Requirements

*   **Size Increase:** The size of electrical components increases at higher voltage levels due to four factors:
    1.  **Insulation:** Higher voltages require more insulation to prevent electrical breakdown.
    2.  **Clearance and Creepage Distances:** Greater distances are needed between conductive and grounded parts to prevent arcing.
    3.  **Heat Dissipation:** Higher voltage equipment generates more heat, requiring larger components and cooling mechanisms.
    4.  **Mechanical Strength:** Equipment must withstand higher mechanical stress.

#### G. Cable Infrastructure (Overhead vs. Underground)

| Feature | Overhead Lines | Underground Cables |
| :--- | :--- | :--- |
| **Installation Cost** | Cheaper (simpler installation, less expensive materials). | More expensive (complex civil work). |
| **Operational/Maintenance Cost** | Comparable during lifetime; easier fault localization/repair. | Lower operational cost; expensive and challenging fault repair/localization. |
| **Visual Impact** | High visual impact; used primarily in rural or sparsely populated areas. | Minor visual impact; suitable for urban or densely populated areas. |
| **Reliability/Susceptibility** | More susceptible to damage from storms, lightning, and weather. | Less affected by weather conditions. |
| **Downtime** | Reduced downtime (faults easier to localize). | Longer downtimes (faults harder to localize/repair). |

### II. Medium Voltage (MV) Technology and Global Context

*   **Regional Voltage Prevalence (Germany Example):**
    *   **$12 \text{ kV}$:** Most common in urban areas for residential/commercial distribution.
    *   **$24 \text{ kV}$:** Used in suburban areas, handling higher power/longer distances; integrating renewable energy sources.
    *   **$36 \text{ kV}$:** Less common; used in rural areas for long distances and heavy industrial applications.
*   **Voltage Persistence:** MV ratings often persist over the years due to the **high cost of changing existing infrastructure**.

#### A. Network Restructuring (Renewables)

*   **Energy Transition Drivers:** Electricity generation is shifting toward renewable resources (wind, solar). In Germany, over half of the electricity generated in 2023 came from renewable sources.
*   **Implications for the Power Grid:**
    1.  **Grid Modernization and Expansion**.
    2.  **Grid Stability and Flexibility**.
    3.  **Decentralization:** More small-scale renewable power generation installations.
*   **Impact on MV Switchgear:** More switchgear is needed for grid modernization; digitalization is integrated for "smart grid" capabilities.
*   **New Applications:** Decentralization drives demand for MV switchgear in new applications like electromobility (fast charging), data centers, and power storage.

#### B. MV Switchgear Applications and Specific Demands

MV switchgear must meet specific technical requirements based on the application sector:

*   **Data Centers:** Require high reliability and redundant power distribution to minimize downtime; must be expandable to support scalability.
*   **Semiconductors Manufacturing:** Needs stable, precise power distribution to sensitive equipment; switchgear must be **compact and sealed** to minimize contamination; requires high current capacity.
*   **Fast Charging Stations (Electromobility):** Requires high power demand, safe operation in public/private infrastructure, compact design, and suitability for open-air installation.
*   **Onshore Wind Power Generation:** Must withstand **vibration stress** (due to tower sway, up to $1 \text{ m}$ at the top) and harsh environmental conditions; requires a compact design to fit through narrow doors.
*   **Transportation (Rail):** Requires high reliability, safety, and uninterrupted power supply; may need high switching cycles depending on performance.
*   **Shipbuilding:** Switchgear must be **robust** to withstand vibration/shocks of the marine environment; must be **encapsulated** to operate in salty and high humidity atmospheres; must be **compact** for limited space.
*   **Steel Industry:** Needs high voltage/current capacities; requires **extremely high operating cycles** (e.g., over 100 times per day, compared to 1–2 times per year in common applications); demands high durability for harsh conditions.
*   **Brown Coal Mining:** Switchgear installed in large excavators requires **additional qualification testing for vibration and shocks**; needs a robust design for dusty, harsh environments, and high power handling capacity.

### III. Medium Voltage Switchgear Components and Know-How

#### A. Switchgear Function and Structure

*   **Main Function:** To **switch energy on and off**.
*   **Structure:** Consists of metallic boxes (panels) connected together, sharing a common busbar (similar to a fuse box at home, but typically three phases and thousands of times higher power).
*   **Incomer Panel:** Entry point of energy to the switchgear from the network.
*   **Feeder Panel:** Connects consumers (motors, transformers, etc.) to the network.
*   **Low Voltage (LV) Compartment:** Often called the "brain" of the switchgear; receives signals from sensors (transformers) and houses the protection relay.
*   **Gas Relief Chamber:** Leads hot smoke and gases to the outside in the event of an arc fault/explosion, either individually or as a common channel.
*   **Compartmentalization (LSC):** A critical design characteristic allowing different degrees of availability and safety.
    *   **LSC 2B (Loss of Service Continuity Category):** The most demanding type; means each main function (busbar, breaker, cable connection) has its own independent compartment. This allows access/maintenance of the circuit breaker compartment while other compartments remain energized.

#### B. Busbar (Buzzbar)

*   **Function:** Connects all panels together, acting as a distribution center for three phases.
*   **Material:** Usually **copper** (best choice) but aluminum can also be used.
*   **Challenges (Mechanical and Thermal):** Must be sustained by insulators to maintain grounding safety.
    *   **Heat:** Must dissipate heat during normal operation to prevent components from melting and to ensure the enclosure is safe to touch.
    *   **Mechanical Strength:** Must withstand high forces (behaving as strong magnets) during a short circuit. It must be fixed firmly but also able to bend without breaking.

#### C. Circuit Breaker (CB)

*   **Function:** Opens and closes power. Crucial difference from a light switch is its ability to operate under **disturbed service** (faulty conditions).
*   **Fault Capability:** Must be able to switch off huge currents (more than 100 times normal value) or tremendously increased voltages resulting from failures.
*   **Withdrawable Feature (AIS):** In air-insulated switchgear (AIS), CBs are often withdrawable, meaning they can be removed from contacts or the panel for maintenance/replacement.
*   **Front Door Safety:** The front door must be sturdy and built to withstand the worst-case scenario: an **internal arc fault explosion**, minimizing harm to the human operator.
*   **Vacuum Circuit Breakers (VCB):** The most common type nowadays.
    *   **Operating Mechanism:** Controls the open/close operations. Energy stored in a spring is transmitted via a connecting rod to the switching element.
    *   **Insulators:** Insulate the mechanism from earth potential and withstand high electrical stress and strong mechanical forces.
    *   **Heat Sink Parts:** Dissipate heat generated by resistance, particularly at the touching contacts where no bolts are used.
    *   **Vacuum Interrupter (The Core):** Contains the fixed and movable contacts within a vacuum. The vacuum eliminates the need for harmful arc quenching materials, minimizes contact erosion, and keeps surfaces clean. Siemens' vacuum tubes are **maintenance-free and closed for life**.

#### D. Arc Control in VCBs (The "Magic Moment")

*   **Arc Physics:** Interrupting current causes an arc (sparkle/discharge). The goal is to perform this interruption in a smooth, controlled way.
*   **Three Challenges:** To keep the arc in a confined area, to limit the arc's time, and to cool it down.
*   **Types of Arcs (Design Know-How):**
    *   **Diffuse Arc:** Characterized by being spread out over a larger area. Used for **high energy applications/highest currents**. The design allows the current to split and distribute evenly across the contact surface.
    *   **Constricted Arc:** Kept in a rotating mode at the rim of the contact. Used for **smaller currents** and allows more compact VCB designs.
*   **Contact Systems:** Flat contacts work with diffuse arcs; pot and spiral contact systems work with constricted arcs.
*   **Extinction:** The design manages the arc, preventing hot spots or melting, leading to extinction at the **current zero crossing**.

#### E. Insulating Mediums Comparison

Voltage resistance depends on the spacing between charges and the medium occupying the space.

| Medium | Advantages | Disadvantages |
| :--- | :--- | :--- |
| **Pressurized $\text{SF}_6$** | Excellent insulator, very high dielectric strength. | Potent greenhouse gas (requires careful handling). |
| **Vacuum** | Abundant, inexpensive, no environmental impact, highly effective at higher voltage. | Technically demanding, maintaining ideal vacuum is expensive. |
| **Oil** | Good insulator, readily available. | Difficult handling, potential for leaks/contamination, fire risk. |
| **Air** | N/A (serves as the medium in typical plugs). | Low resistance limit compared to others. |

#### F. Other Switching Devices

| Device | Ability to Switch Operating Current | Ability to Break Fault/Short Circuit Current | Primary Use |
| :--- | :--- | :--- | :--- |
| **Contactor** | Yes (designed for high operations, e.g., up to 3 million cycles). | No (Must be protected by an upper CB or fuses). | Switching on/off under normal service. |
| **Switch** | Yes (can interrupt current flow). | No (Can switch *into* a short circuit but cannot *open* it). | Simple disconnection means when fault protection (fuses) exists upstream. |
| **Disconnector (Isolator)** | No (can only be inserted/removed when no current is flowing). | No. | Creates a **safety gap** (physical, visible break) for personnel safety during maintenance. |
| **Switch Disconnector**| Yes (under load). | No. | Similar to a switch, but specifically designed to withstand **transient voltage**. |
| **Fuse** | N/A (Passive element). | Yes (Melts the wire to break the circuit). | Cost-effective, single-use protection device; faster reaction to overcurrent than many CBs. |

#### G. Earthing Switch (Essential Safety Component)

*   **Function:** Connects the phases to earth, ensuring the voltage is zero on the cable side before operator access.
*   **Necessity:** Required because switching off the CB alone may leave residual capacitive voltages.
*   **Safety Gap:** Creates a safe condition; often requires a padlocking facility.
*   **Know-How:** The earthing switch must be built to **withstand a short circuit** (huge power flow) for 1–3 seconds, in case the power is accidentally turned on while the operator is working, or if interlocks fail.

#### H. Transformers (Sensors)

*   **Function:** Transform high voltage and current values into small, scaled-down replica values suitable for measuring and protection relays.
*   **Protection Relay:** Installed in the LV box. It receives transformer signals, detects failures (e.g., current increasing in a known way), and sends a **trip signal** to the circuit breaker to prevent motor/system damage.

#### I. Block Transformers (Conventional)

*   **Current Transformers (CTs):** Connected in **series** with the line. The current flows through the U-shaped primary conductor, inducing flux in toroidal cores (made of silicon steel). Multiple cores can be used for separate functions (measurement, protection, metering). Characteristics (e.g., adjustable primary current ranges via tapping) are printed on a rating plate.
*   **Voltage Transformers (VTs or PTs):** Connected in **parallel**. Single-pole VTs connect across one phase and ground/neutral. The high voltage primary winding uses a large number of turns to step down the voltage to the secondary winding. Winding and core are often embedded in **cast resin** for high dielectric strength and protection.

#### J. Low Power Instrument Transformers (LPITs)

LPITs are a modern alternative to block transformers, offering several advantages.

1.  **Compact and Efficient:** Provides both voltage and current measurements in a single device (e.g., three small LPITs replace six big block transformers). Uses a **Rogowsky coil** (air coil) for current measurement, eliminating the ferromagnetic core.
2.  **Safety:** Significantly safer because they reduce the risk of open circuit conditions and have a **low output power (millivolts to a few volts)**, which is less dangerous to personnel compared to conventional transformers.
3.  **Smaller and Lighter:** Easier and more cost-effective for installation and maintenance.
4.  **Digital Outputs:** Inherently suitable for integration with modern smart grid technologies.
5.  **Reliable and Accurate:** Immune to grid disturbances (e.g., ferro-resonance); linear over the whole measuring range (up to rated short circuit fault currents), ensuring higher accuracy.
6.  **Flexible:** Single design with a wide dynamic range, allowing easy adaptation to network changes (e.g., changing feeder current) without needing taps (which consume material).
7.  **Environmental Friendly:** Supports sustainability by consuming less material (iron, copper) and having lower power consumption and minimal electromagnetic radiation, reducing energy consumption and $\text{CO}_2$ emissions.
