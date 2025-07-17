
Here is the knowledge-based information extracted from the sources, with colloquial language removed, and key concepts bolded for clarity:

**1. Hardware and Software in System Design**
*   **Systems are designed from a combination of hardware and software**.
*   Hardware interacts with the physical world, receiving input and performing actions (actuating). Examples include microphones for sound input and speakers for sound output.
*   Software typically functions as the **intelligence** of the system. It processes data received from hardware, interprets it, and then commands the hardware to perform actions.
*   For instance, in a voice-activated system, a microphone (hardware) receives sound, the software processes and interprets the words (e.g., "turn on TV"), and then instructs an actuator (hardware) to turn on the TV.
*   Designing these combined hardware/software systems is often more challenging than traditional software systems because the software is written for a specific hardware platform, which may still be under development. Both sides must be designed to work together.

**2. Basic Electrical Circuit Properties**
Understanding basic electrical circuits is necessary for IoT design, even if the primary focus is on software.

*   **Analogy to Water Pumping System:** Electrical current flowing through a wire is analogous to water flowing through pipes.
    *   A **battery** in an electrical circuit is like a **water pump**; both provide the force to push current/water through the system.
*   **Voltage (V):**
    *   Defined as the **potential difference** between two points in a circuit.
    *   Analogous to **pressure** in a water system.
    *   A battery provides voltage, which effectively provides pressure on electrons to push them through the circuit.
    *   **Current flows only if there is a difference in voltage** (or pressure in the water analogy). For example, a 5-volt battery has a 5-volt potential difference between its positive and negative terminals, causing current to flow when connected.
    *   Measured in **volts**.
    *   Points connected by a plain, conductive wire with no resistance have the **same voltage**.
*   **Current (I):**
    *   The **rate at which charge carriers flow** past a point in a circuit.
    *   Analogous to the **rate of water flow** in a pipe.
    *   By convention, current is said to flow from **positive to negative**.
    *   In reality, electrons (negatively charged carriers) flow from negative to positive. However, the convention of positive-to-negative current flow is widely used.
    *   Measured in **amperes (amps)**.
*   **Resistance (R):**
    *   An **obstacle to current flow**.
    *   Analogous to **rocks** or a **narrow pipe** slowing water flow.
    *   In an electrical circuit, resistance can be provided by components called **resistors**.
    *   Materials that are **sub-optimal conductors** (less conductive than pure copper wire) have resistance.
    *   **Insulators** have extremely high resistance.
    *   **Narrower conductors** have **more resistance**. Large, thick wires are needed for high power electronics to reduce resistance and prevent excessive heat generation.
    *   Measured in **Ohms**.

**3. Ohm's Law**
*   **Relationship:** Ohm's Law describes the relationship between voltage, current, and resistance: **V = I * R** (Voltage = Current × Resistance).
*   **Applications:**
    *   Provides intuition about current flow, voltage, and resistance.
    *   Allows calculation of one variable when the other two are known (e.g., I = V/R).
    *   **Crucial for limiting current flow:** If a component has a current limit (e.g., an LED), a resistor can be added in series to reduce current to the appropriate level using Ohm's Law (R = V/I).
    *   **Determining expected voltage:** Can be used to calculate the voltage expected at a point in a circuit given known current and resistance (V = I * R).

**4. Circuit Components and Schematics**
*   **Schematic Diagrams:**
    *   A **symbolic representation** that shows how components are electrically connected in a circuit.
    *   Shows what components connect to what terminals, but **does not show exact physical placement** or appearance.
    *   Essential for both **building a circuit from a given design** and **drawing one's own circuit designs**.
*   **Common Component Symbols:**
    *   **Resistor:** Represented by a **sawtooth diagram**.
        *   **Physical characteristics:** Resistors typically have two leads, are bidirectional (current can flow in either direction), and have a specific resistance value.
        *   **Resistance Value:** Encoded by **color bands** on the resistor. One band indicates accuracy (e.g., gold for 5% tolerance), while others represent digits and a power of ten multiplier (scientific notation). Reading these bands can be tedious.
    *   **Battery:** Symbol has a **long bar (positive terminal) and a short bar (negative terminal)**.
    *   **Power Source (DC):**
        *   Can be represented by an **upward-pointing triangle**, often with the voltage value (e.g., +5V) next to it.
        *   Most circuit boards and devices like Arduinos operate on **direct current (DC)**, where current flows in one direction. **Alternating current (AC)**, where current moves back and forth, is used for long-distance transmission and converted to DC for devices.
    *   **Ground:** Represented by a series of **three decreasing horizontal bars**.
*   **Short Circuit:**
    *   Occurs when two wires are accidentally connected, especially **power to ground**, creating a path with **effectively zero resistance**.
    *   According to Ohm's Law (I = V/R), if resistance (R) approaches zero, current (I) approaches infinity.
    *   Results in a **rush of current**, causing components to smoke, become extremely hot, and potentially damage the board. **Should be avoided**.
*   **Diodes and Light Emitting Diodes (LEDs):**
    *   **Diodes** are semiconductors that allow current to flow predominantly in **one direction**.
    *   **LEDs** are diodes that **emit light** when current flows through them.
    *   **Schematic Symbols:** A regular diode is a triangle pointing to a line; an LED adds two small arrows pointing away from the diode to indicate light emission.
    *   **Terminals:** Both have an **anode** (+) and a **cathode** (-).
    *   **Current Flow:** Current primarily flows from the **anode to the cathode**. This is analogous to a one-way valve.
    *   **Forward Bias:** Current flows when the **anode is positive with respect to the cathode**, and the **voltage difference exceeds a specific threshold voltage** (e.g., 1.7 volts), which varies by diode. Below this threshold, current will not flow.
    *   **Reverse Bias:** When the anode is negative with respect to the cathode, there is typically **no current flow** at normal operating voltage levels.
    *   **Current Limit:** Diodes have a **maximum current limit** (e.g., 20 milliamps for typical LEDs). Exceeding this limit will damage or destroy the diode.
    *   **Caution:** **Never connect an LED directly across a 5-volt supply** (anode to 5V, cathode to ground) without a series resistor. LEDs have very little resistance when on, leading to a very high current flow that will destroy the LED. Ohm's Law can be used to calculate the necessary resistor value to limit current.
*   **Switches and Push Buttons:**
    *   **Purpose:** To **complete or close a circuit**, allowing current to flow.
    *   **Function:** When a switch is **open (off)**, the circuit is not connected, and no current flows. When the switch is **closed (on)** or the button is **pushed**, it connects the two ends of the circuit, creating a complete path for current.
    *   **Schematic Symbols:** Represented as a break in a line, with a movable part to show connection.
    *   **Voltage:** When two points are connected via a closed switch (no resistance), their **voltage is the same**.
    *   **Push Buttons:** Some push buttons have four leads; two on one side are internally connected, and two on the other side are internally connected. Pressing the button connects the two sides.
*   **Potentiometers:**
    *   **Function:** An **adjustable resistor** that acts as a **voltage divider**.
    *   **Appearance:** Typically has a **knob** (rotary) or a **slider**.
    *   **Leads:** Has **three leads**.
    *   **Schematic Symbol:** Looks like a resistor with an arrow pointing to its middle.
    *   **Voltage Divider Operation:**
        *   The total resistance between the two outer leads is **constant**.
        *   Turning the knob changes the **ratio of resistance** between the middle lead and each of the outer leads.
        *   This change in resistance ratio causes the **output voltage (V_out)** at the middle lead to vary.
        *   When connected between a voltage input (V_in) and ground, the potentiometer's middle lead provides a variable voltage output (V_out) that is a fraction of V_in, determined by the knob's position. This makes it useful for providing variable input signals to devices like an Arduino.

**5. Wiring Circuits with Solderless Breadboards**
*   **Purpose:** **Solderless breadboards** allow components to be easily connected in a **non-permanent way**, which is ideal for **prototyping**.
*   **Advantages over Soldering:** Easier to modify connections than soldering, which creates permanent (but more secure and conductive) bonds.
*   **Wire Compatibility:** Holes are designed to fit **24 American Wire Gauge (AWG) solid wire**, a standard thickness found in kits.
*   **Internal Connections:**
    *   **Main Section:** Consists of rows of **five holes that are horizontally connected**. To connect two components, their leads are inserted into the same five-hole row.
    *   **Side Columns (Power Rails):** Long vertical columns, typically on the sides, where **all holes within each column are connected**. These are commonly used for **power and ground connections** as many components require them, allowing short wires to connect components to these rails.
*   **General Wiring Process (from a Schematic):**
    1.  Select a hardware component from the schematic.
    2.  Select one terminal of that component.
    3.  Insert the terminal into a breadboard row.
        *   If connecting to an existing component, use the row it is already in.
        *   If not, use any available free row.
    4.  Repeat steps 2-3 for all remaining terminals of the current component.
    5.  Move to the next hardware component on the schematic and repeat the process until all components are wired.

**6. Example Circuits with Arduino**
*   **Push Button to Control LED (on Arduino):**
    *   **Components:** Arduino, breadboard, push button, 10 kilo-ohm resistor.
    *   **Goal:** Have Arduino digital pin 2 change state (0V or 5V) based on button press, which in turn controls the built-in LED on Arduino pin 13.
    *   **Wiring:**
        1.  Insert the push button into the breadboard (ensure leads are in different rows).
        2.  Connect one lead of the push button (e.g., top-left) to the Arduino's **5V power supply** (via the breadboard power rail).
        3.  Connect the other active lead of the push button (e.g., bottom-left) to one end of the **10k resistor**.
        4.  Connect the other end of the 10k resistor to **ground** (via the breadboard ground rail).
        5.  Connect the point where the push button and the 10k resistor meet to **Arduino digital pin 2**.
    *   **Outcome:** Pressing the push button turns on the LED connected to Arduino pin 13.
*   **Potentiometer to Control LED Blink Rate (on Arduino):**
    *   **Components:** Arduino, breadboard, potentiometer.
    *   **Goal:** Read the analog voltage from the potentiometer using Arduino analog input A0 and use it to control the blink rate of the built-in LED on Arduino pin 13.
    *   **Wiring:**
        1.  Insert the potentiometer into the breadboard, ensuring its three leads are in different rows.
        2.  Connect one outer lead of the potentiometer (e.g., top) to the Arduino's **5V power supply**.
        3.  Connect the other outer lead of the potentiometer (e.g., bottom) to **ground**.
        4.  Connect the **middle lead** of the potentiometer to **Arduino analog input A0**.
    *   **Outcome:** Turning the potentiometer knob changes the voltage read at A0 (between 0V and 5V), which in turn changes the blinking rate of the LED on pin 13.
