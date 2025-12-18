---
layout: post
title:  "medium voltage technology"
date:   2025-10-14
categories: jekyll update
---



The main points, knowledgeable information, know-how, and industry practices regarding medium voltage (MV) technology and switchgear, drawn from the provided sources, are listed below.

---

### I. MV Technology Fundamentals and Scope

*   **Definition and Voltage Range:** Medium Voltage (MV) technology encompasses voltages typically ranging from **$1 \text{ kV}$ up to $52 \text{ kV}$**. In international rules, MV is considered a sub-range of High Voltage (above $1 \text{ kV}$).
*   **Purpose of Switchgear:** The essential function of switchgear is to **switch energy on and off**. MV switchgear is designed to put together all necessary components, such as circuit breakers and disconnecting switches, at specified distances.
*   **Power Distribution Architecture:** MV systems form the distribution stage of the power grid, stepping down High Voltage (HV) for consumption in urban or industrial areas.
    *   **Primary Distribution:** Characterized by higher currents and short circuit values, delivering power from main substations to local distribution substations.
    *   **Secondary Distribution:** Handles lower currents and short circuit values, distributing power from distribution substations to final end consumers.
*   **Component Quantity Rule:** In a power grid hierarchy (like a pyramid), the higher the voltage level, the less quantity of components is needed, and conversely, the lowest voltage level requires the most components.

### II. Industry Standards and Compliance

*   **Global Standards:** MV switchgear requirements are described in standards across three main geographical areas: **IEC** (for most countries), **ANSI/NCSA** (North America, specifically USA and Canada), and **GB** (China).
*   **Requirements Origin:** Technical and safety requirements are created through collaboration between manufacturers and operators. The standards define the limit values necessary for safe and reliable operation.
*   **Type Testing:** Modern switchgear undergoes type testing in accordance with IEC standards (e.g., IEC 62271) to ensure the design meets requirements like dielectric strength and temperature rise.
*   **Certification Process:** To receive certification (e.g., for a specific rated voltage level like $24 \text{ kV}$), the switchgear must pass all requirements written in the standards, confirmed by successful type tests.

### III. Technical Ratings and Testing Know-How

*   **Voltage Requirements:** The switchgear must fulfill specified values for rated lighting impulse voltage (e.g., $125 \text{ kV}$ for a $24 \text{ kV}$ rated voltage switchgear). Successful testing requires no flashovers.
    *   Design criteria influencing voltage performance include distances between phases/metal parts, open contact distance, open travel speed, and material of insulating parts.
*   **Current and Thermal Management:**
    *   Current flow is restricted by conductor resistance, hence low-resistance materials (copper, aluminum) are used.
    *   Heat created by contacts (screwed, bolted, or movable) must be managed, ensuring the temperature rise does not exceed defined maximum limits (e.g., for air or $\text{SF}_6$ insulation).
    *   Ambient condition requirements for testing include $40^\circ \text{C}$ ambient temperature and an average temperature over 24 hours at $35^\circ \text{C}$.
*   **Rated Short Circuit Current:** This describes the failure current resulting from a galvanic short circuit (phase-to-phase or phase-to-earth fault). The switchgear must handle:
    *   Peak current (dynamic stress).
    *   Short-time current (thermal stress).
    *   Breaking current (must be interrupted by the circuit breaker and protection relay).

### IV. Personal and Operational Safety Practices

*   **Internal Arc Classification (IAC):** This is a crucial personal safety requirement. The switchgear must be tested to withstand the consequences of an internal arc fault, which can generate high pressure (e.g., over $1 \text{ bar}$ or $10 \text{ tons}/\text{sq meter}$) and extreme heat (over $10,000^\circ \text{C}$).
    *   Acceptance criteria include no open covers or large turn-off parts exceeding 60 grams.
    *   The **IAC designation** specifies the tested areas (F=front, L=lateral, R=rear), the accessibility type (A=authorized personnel, B=public), the tested current ($\text{kA}$), and the duration ($\text{s}$).
*   **Safety Interlocks and Operation:** Most electrical accidents are caused by neglecting the five safety rules.
    *   Switchgear must be designed to allow operation only behind an arc-resistant front cover.
    *   Mechanical and electrical interlockings are essential to prevent dangerous mistakes (e.g., ensuring the earthing switch cannot be switched on while the breaker is inserted, or operating a disconnector while the breaker is closed).
*   **Earthing Switch (Safety Gap):** The earthing switch is critical for operator safety, connecting phases to earth to ensure zero voltage on the cable side before maintenance. It must withstand the high power flow of a short circuit if power is accidentally turned on.

### V. Switchgear Design and Structure

*   **Modern vs. Past Switchgear:** Modern switchgear is highly compact, has smaller footprints, provides metal encapsulation for environmental protection, and meets high personal safety standards. Past switchgear was component-oriented, non-type-tested, had bigger dimensions, required extensive maintenance, and carried high risks from arc failures.
*   **Compartmentalization:** Switchgear is subdivided into compartments (busbar, switching device, cable connection) to enhance reliability, safety, and ease of maintenance by containing faults.
    *   **Partition Classes:** **PM (Metallic Partitions)** uses earthed metallic shields and generally offers a higher level of protection but may lead to bigger dimensions. **PI (Non-Metallic Partitions)** uses insulating materials, allowing compact design, but poses a fire load risk.
*   **Loss of Service Continuity (LSC):** Describes the extent to which the switchgear can remain operational when accessing a high voltage compartment.
    *   **LSC 2B (Highest Continuity):** Allows access to individual compartments (busbar, switching device, connection) without de-energizing the entire switchgear.

### VI. Switchgear Components and Functionality

*   **Core Components:** MV switchgear typically includes the busbar, circuit breaker, current transformers (CTs), voltage transformers (VTs), earthing switch, and the low voltage (LV) compartment.
*   **Busbar Function:** Acts as the electricity distribution center, connecting all panels together.
*   **Circuit Breakers (CBs):** Capable of switching operating currents and fault currents (high short circuit currents).
    *   The most common type is the **Vacuum Circuit Breaker (VCB)**, which uses a vacuum interrupter to eliminate the need for quenching materials.
    *   A VCB must handle both **normal service** and **disturbed service** (faulty conditions).
*   **Switching Devices Differentiation (Know-How):**
    *   **Contactor:** Operates similar to a CB but is *not* meant to interrupt fault currents; built for a much larger number of operations (up to 3 million cycles). Requires protection by an upper CB or fuses.
    *   **Switch:** Can interrupt current flow under normal operating conditions but *not* short circuit currents; used when a protective device exists upstream.
    *   **Disconnector/Isolator:** Designed only to physically separate circuits to create a safe, visible gap; *cannot* break any kind of load or fault current.
*   **Transformers (Sensors):** CTs and VTs (also called Potential Transformers, PTs) transform high currents and voltages to lower levels suitable for protection relays and meters.
    *   The **Protection Relay** (in the LV box) uses transformer signals to detect failures and send a trip signal to the circuit breaker.
*   **Fuses:** Provide quick, cost-effective protection against overload or short circuits but are one-time use devices.

### VII. Air Insulated (AIS) vs. Gas Insulated (GIS) Switchgear

| Feature | AIS (Air Insulated) | GIS (Gas Insulated) |
| :--- | :--- | :--- |
| **Insulating Medium** | Air. | Gas (traditionally SF6, moving to F-Gas free clean air). |
| **Dimensions** | Comparatively larger, needing proper isolating distances. | Compact design, due to excellent dielectric properties of gas. |
| **Environmental Influence** | More vulnerable to pollution, moisture, and saline conditions. | Primary parts enclosed and hermetically sealed for lifetime; minimum influence from environmental conditions. |
| **Maintenance** | Requires regular maintenance. Features easily accessible, withdrawable parts. | Maintenance-free design is possible. |
| **Cost & Impact** | Cost effective, lower environmental impact (using air). | SF6 gas has a high Global Warming Potential (GWP). Siemens' Blue GIS uses clean air technology (GWP < 1). |

### VIII. Sustainability and Environmental Practices

*   **Key Drivers:** Decarbonization, decentralization, and digitalization are the three main drivers shaping sustainable MV solutions.
*   **F-Gas Regulation (Mandate):** The European F-Gas regulation aims to reduce emissions from fluorinated gases. The ban on $\text{SF}_6$ in MV switchgear up to $24 \text{ kV}$ takes effect January 1, 2026 (put-into-operation date).
*   **Blue GIS Technology:** Siemens' F-Gas free GIS uses **clean air** (natural origin gases like nitrogen, oxygen, and carbon dioxide) as the insulation medium, achieving a GWP of less than one. This technology provides the benefits of traditional GIS (compactness, maintenance-free) while significantly reducing the $\text{CO}_2$ footprint.
*   **Sustainability Transparency:**
    *   **Siemens Ecotech Label:** Ensures transparent claims by requiring products to have a Type 2 Environmental Product Declaration (EPD) based on a Life Cycle Assessment (LCA), sustainable manufacturing, and feature fulfillment across manufacturing, usage, and end-of-life stages.
    *   **GHG Protocol Reporting:** Using F-Gas free switchgear drastically reduces Scope 1 emissions (related to SF6 leakage) for customers.
*   **Recycling and Circularity:** Nearly all Siemens switchgear has a recyclability rate of above 80%, with some gas insulated switchgear reaching around 90%.

### IX. Digitalization and Monitoring

*   **Digitalization necessity:** Essential for grid stability given the increasing demand from e-car charging, data centers, and volatile renewable energy generation.
*   **Key Digital Offerings:** Automation, protection, measurement, and condition monitoring (CM) using IoT applications.
*   **Condition Monitoring (CM) Components:** Sensors are used to monitor the health status and predict maintenance needs. CM includes: temperature and humidity monitoring, partial discharge (PD) monitoring (an early warning system for insulation damage), gas density monitoring, and load flow monitoring.
*   **Low Power Instrument Transformers (LPITs):** Modern, sustainable alternatives to conventional block transformers [92, 9.
*   **Electrification X:** Siemens' IoT suite that provides Software as a Service (SaaS) features for load management, asset management, and sustainable energy management, often utilizing data collected via gateways (like the $\text{SECM A}8000 \text{ RTU}$).

### X. Applications and Portfolio

*   **Portfolio Distinction:** Siemens categorizes its portfolio into **Air Insulated Switchgear (AIS)** and **Gas Insulated Switchgear (GIS)** families.
    *   The newer blue portfolio uses F-Gas free GIS technology (Clean Air).
*   **Challenging Applications (Industry Context):** MV switchgear must meet specific requirements depending on the application sector:
    *   **Data Centers:** Require high reliability and redundant power supply to minimize downtime.
    *   **Steel Industry:** Needs high current capacity, high durability, and extremely high operating cycles (switching over 100 times per day, compared to 1–2 times per year in common applications).
    *   **Wind/Mining:** Must withstand severe vibration stress and harsh environments (dusty, strong winds).
    *   **Shipbuilding:** Requires robust, compact, and encapsulated designs to withstand shocks, vibration, and salty/humid marine environments.
    *   **Generator Switching:** Considered the most challenging application, requiring high reliability to interrupt high short-circuit currents and operate reliably under asynchronous conditions (different frequencies and voltages).
