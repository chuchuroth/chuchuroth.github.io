---
layout: post
title:  "electrical one line drawings"
date:   2025-10-13
categories: jekyll update
---



The knowledgeable information from the video "Reading electrical one line drawings | Eaton PSEC" focuses entirely on the conventions, symbols, components, and practices involved in reading and understanding single line diagrams (also known as one-line diagrams or single line drawings) used in electrical power systems.

Here is a comprehensive list of the main points and knowledgeable information:

### I. Purpose and Structure of Single Line Diagrams (SLDs)

*   **Definition and Function:** An SLD simplifies the representation of a three-phase power system, illustrating the flow of power using a single line for all three phases and representing all equipment with specific symbols or abbreviations.
*   **Importance:** SLDs are the key to understanding any electrical system because they visually demonstrate how power flows through equipment, which cannot be determined simply by looking at the equipment installed in a room.
*   **Reading Direction:** A single line drawing is typically read from **top to bottom** or **left to right**.
*   **Starting Point:** When the system is fed by utility power, the system start is signaled by a **downward arrow**, a **utility transformer**, or a **reference to a utility connection**.
*   **System Flow:** After the source, you follow the lines downstream to the loads, often passing through various pieces of electrical distribution equipment.

### II. Essential Symbols and Components

| Component | Symbol/Abbreviation | Description/Function |
| :--- | :--- | :--- |
| **Transformer** | Two coils or overlapping circles. | Used to change voltage levels in an electrical system. |
| **Delta Connection** | Triangle. | Represents a transformer connection where all three phases are connected to one another. |
| **Y/Wye Connection** | Letter Y. | Represents a transformer connection where one end of each phase is connected to form a common neutral point. |
| **Switch** | Simple break in the conductor. | Represents a device that can open or close a circuit, typically through manual operation (e.g., medium voltage load interruptor switch, low voltage safety switch, fusible switches). |
| **Fuses** | A rectangle with two lines, or opposing connected semicircles. | Provides overcurrent protection to the system. A single line drawing represents a complete set of three fuses (one for each phase). |
| **Medium Voltage Breaker** | Simple Square. | Represents a circuit breaker used in MV systems. |
| **Low Voltage Breaker** | An arch bridging a gap in the conductor. | Represents a circuit breaker used in LV systems. |
| **Drawout Breaker** | Two carrots/chevrons above and below the symbol, or the abbreviation **D/O**. | Can be removed from its enclosure for maintenance or replacement without disturbing wiring; common where frequent maintenance/testing is required. |
| **Fixed Mounted Breaker** | No additional carrots or chevrons. | Permanently installed in the enclosure; used when frequent access is not required. |
| **Circuit Breaker Abbreviation** | The number **52**. | ANSI device number for a circuit breaker, often used as an abbreviation. |
| **Ground** | Series of horizontal lines that get shorter as they go down. | Represents the point where the electrical system is connected to ground, crucial for safety and protecting the system from electrical faults. |
| **Motor Load** | An **M** within a circle. | Represents a motor load; often accompanied by a horsepower rating notation. |
| **Other Load** | A labeled rectangle. | May represent any other load (e.g., a unit heater, which is a resistive load); text identifies the specific type. |
| **Power Meter** | An enclosed **M** or **PM** (Power Meter). | Fed from Current Transformers (CTs) or Potential Transformers (PTs).
| **Voltage Metering** | An **V**. | Indicates voltage metering. |
| **Current Metering** | An **A**. | Indicates current metering. |
| **Contactor** | Parallel lines perpendicular to the bus. | Switches a circuit on or off electrically or mechanically, but does **not** provide overcurrent or overload protection. The lines represent contacts in the open position. |
| **Overload Relay** | Two linked broken semicircles, or a block labeled **OL**. | Protects motors from overheating due to prolonged overcurrent conditions (overloads). This differs from a circuit breaker trip unit which provides short circuit protection. |
| **Combination Starter** | A contactor in series with an overload relay. |
| **Full Voltage Non-Reversing Starter**| Abbreviation **FVNR**. | |
| **Reduced Voltage Starter** | Abbreviation **RVSS**. | |
| **Variable Frequency Drive (VFD)** | Rectangle with a wave symbol inside or the letters **VFD**. | Controls the speed and torque of an electric motor by varying the frequency and voltage of the power supply. |
| **Generator** | A circle with a **G** inside. | Represents a permanent generator or a provision for a temporary generator hookup. |
| **Transfer Switch** | A rectangle with two inputs and one output and lines indicating switching action. | Used to switch power supply from one source to another (e.g., utility to generator). Often labeled **ATS** (Automatic Transfer Switch). |
| **Surge Protective Device (SPD) / TVSS** | Rectangle with a lightning bolt or the letters **SPD** inside. | A low voltage device used to protect equipment from voltage spikes. |
| **Surge Arrestor (SA) / Lightning Arrestor (LA)** | A lightning bolt symbol or a series of parallel lines with **SA** or **LA**. | A medium voltage device used to protect equipment from voltage spikes. |
| **Capacitor** | Two parallel lines with a gap, or one straight line and one arch with a gap. | Used for **power factor correction**. Can be confused with the contactor symbol. |
| **Resistor** | A zigzag line. | Used to limit the flow of electrical current. |
| **Inductor/Reactor** | Half of a transformer with a single winding connected in line with a drive. | May be shown in front of a VFD. |
| **Indicating Light** | A circle with lines indicating illumination. | Provides visual indication of circuit status; often includes a letter inside showing the color. |

### III. Equipment Enclosures and Designations

*   **Enclosure Representation:** A **rectangle** (solid or dashed line) enclosing breakers denotes that all these items are within **one piece of equipment**.
*   **Bus:** The horizontal line between the main and feeder breakers within the enclosure represents the **bus** (busbar), which distributes power from the main breaker to the feeder breakers.
*   **Critical Notations:** Within the enclosure rectangle, you will find notations for the **voltage, amperage, and short-circuit rating** of the equipment.
*   **Close Coupled Equipment:** When multiple rectangles (representing equipment like switches or transformers) are adjacent to one another, it likely indicates the equipment is **directly bus connected** (close coupled) instead of cable connected.

### IV. Circuit Breaker Details and Protection

*   **Low Voltage (LV) Breaker Trip Units (Integral):**
    *   **TM (Thermo-magnetic):** Indicates a thermomagnetic trip unit.
    *   **Electronic Trip Units:** Indicated by **ET, LS, LSI, or LSI G**.
        *   **L, S, I, G** refer to the types of protection provided: **Long** (time), **Short** (time), **Instantaneous**, and **Ground**.
*   **Mechanically vs. Electrically Operated Breakers:**
    *   **Mechanically Operated (MMO):** Can only be opened by the integral trip unit or operated manually by a person.
    *   **Electrically Operated (EO):** Includes a **shunt trip** (allows opening from an external signal) and a **spring release** (allows closing from an external signal). The external signal may come from a control switch or protective device.
*   **Arc Flash Reduction Maintenance System (ARMS):**
    *   An option for electronic trip units.
    *   Provides a maintenance mode switch that, when activated, causes the breaker to trip faster than the programmable instantaneous setting at the first sign of a fault, protecting workers downstream.
*   **Medium Voltage (MV) Breaker Protection:** MV breakers typically **do not** have integral trip units and rely entirely on **protective relays** for overcurrent protection.

### V. Protective Relays and Instrument Transformers

*   **Protective Relays:**
    *   **Symbol:** A two-digit number within a circle, referencing the **ANSI device number** corresponding to the relay function.
    *   **Example:** A circle noting **50/51** indicates protection by **Function 50 (Instantaneous Overcurrent)** and **Function 51 (Time Delay Overcurrent)**.
    *   **Alternative Symbol:** A rectangle showing the model number of the relay (e.g., Eaton EDR 5000).
*   **Current Transformer (CT):**
    *   **Symbol:** Two half circles end to end, with a line extending from the center, connected to the main circuit.
    *   **Function:** Takes line current and transforms it to a lower amperage to be safely read by protective relays and meters.
    *   **Ratio:** The **CT ratio** (line current to CT secondary current) may be noted on the SLD.
*   **Voltage Transformer (VT) / Potential Transformer (PT):**
    *   **Symbol:** A smaller version of the standard transformer symbol.
    *   **Function:** Takes line voltage and transforms it to a lower voltage to be safely read by protective relays and meters.

### VI. System Status Indication (Indicating Lights)

*   **Standard Color Scheme (Power Systems):** Indicating lights are used to show the status of a circuit breaker.
    *   **Red Light:** Breaker is **closed** (power is on). *Caution: This is the opposite of what many might anticipate, as red means power is flowing and caution should be taken*.
    *   **Green Light:** Breaker is **open**.
    *   **Amber Light:** Breaker has **tripped** due to a fault on the system.
