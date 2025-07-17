---
layout: post
title:  "Internet of Things and Embedded Systems module 2"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---


The following outlines the knowledgical information extracted from the provided sources, presented without colloquial language.

### **1. Internet of Things (IoT) Devices**

*   An **Internet of Things (IoT) device** integrates a "thing" (any object other than a traditional computer) with computational intelligence and Internet connectivity.
*   The core concept involves adding **enhanced functionality** to a regular device without increasing its operational complexity for the user.
*   IoT devices often maintain a **simple, natural user interface**, where the internal computational complexity is hidden, allowing the device to conform to user needs rather than the user adjusting to the device.
*   Unlike general-purpose computers, IoT devices are typically **application-specific**, designed to perform one main function or a related set of functions (e.g., a car performing "car things," a camera performing "camera things").
*   **IoT devices are almost always connected to the Internet**, enabling them to access and utilize non-local resources and be accessible from the network. This networking distinguishes them from some embedded systems.

### **2. Embedded Systems**

*   **Embedded systems are computer-based systems that do not resemble traditional computers**, with their computational complexity hidden from the user.
*   There is significant **overlap between embedded systems and IoT devices**; IoT devices are typically a type of embedded system.
*   The term "embedded system" often refers to the implementation and construction of the device.
*   Embedded systems interact with the physical world through **sensors** that gather information and **actuators** that effect changes in the physical environment.
*   They can interact directly with the user (e.g., a digital camera) or indirectly through another device (e.g., a thumb drive connected to a computer, or an anti-lock braking system (ABS) within a car).
*   **Efficiency is a critical design principle** for embedded systems, meaning they must perform their tasks rapidly, with low power consumption, or at a low cost. This contrasts with traditional software engineering, which may prioritize functionality over strict efficiency.
*   Design constraints are driven by factors such as **cost-critical markets** (e.g., consumer electronics where manufacturing costs and time-to-market are paramount) and **life-critical applications** (e.g., medical or military systems where performance, reliability, and power are more important than cost).
*   Unlike general-purpose processors, which are often over-engineered and underutilized for specific tasks, embedded systems, being application-specific, can be designed with **higher efficiency** by including only necessary hardware and software components, leading to lower costs for their specific function.
*   **Hardware and software are typically designed together** for embedded systems, allowing for optimized performance and reliability by precisely matching components. This approach requires designers to have an understanding of both hardware capabilities and software requirements.

### **3. Components of Embedded Systems**

The hardware structure of an embedded system generally comprises sensors, a microcontroller, and actuators.

*   **Microcontroller:**
    *   The **central component** of an embedded system, responsible for executing programs, processing sensor data, and controlling actuators.
    *   It is an **integrated circuit** typically made of silicon, which requires packaging before use.
    *   **Microcontrollers are generally smaller, less powerful, and more cost-effective** than microprocessors found in general-purpose computers. They are chosen for efficiency in embedded and IoT devices, tailored to the specific task rather than being overpowered.
    *   They are programmed to run code written in languages like C/C++ or Python, which is then compiled and transferred to the microcontroller's **flash memory** (non-volatile memory).
    *   **Development boards** (e.g., Arduino, Raspberry Pi) are commonly used for building embedded systems, providing the microcontroller along with supporting hardware for programming and interfaces. Some boards, like Arduino and Raspberry Pi, have built-in programming capabilities via USB.

*   **Sensors (Inputs):**
    *   Receive information from the environment.
    *   **Simple sensors** provide real number outputs (e.g., voltage values), such as a **thermistor** (temperature) or a **photoresistor** (light intensity).
    *   **Complex sensors** capture intricate data (e.g., a **CMOS camera** for detailed visual data, or an **Ethernet controller** for network information).
    *   Examples include buttons, microphones, light sensors, cameras, touch screens, potentiometers (rotation sensor), and keypads.

*   **Actuators (Outputs):**
    *   Cause events or changes in the environment.
    *   **Simple actuators** include **LEDs (Light Emitting Diodes)** for illumination and **LCDs (Liquid Crystal Displays)** for simple numerical or textual output.
    *   **More complicated actuators** include **servo motors** (for precise angular control, e.g., in robotics) and an **Ethernet controller** (for outputting data to the network).

*   **Other Core Components:**
    *   **IP (Intellectual Property) Cores:** Predesigned, premanufactured integrated circuits that perform a specific set of related functions. They are highly cost-effective for **high-volume production** of common tasks (e.g., network controllers, audio/video codecs). They are typically purchased off-the-shelf and interact with the microcontroller to execute their dedicated functions.
    *   **Field Programmable Gate Arrays (FPGAs):** Reconfigurable integrated circuits that can be "rewired" to perform different tasks. They offer significant speed advantages over general-purpose processors for specific tasks because they execute functions directly in hardware. FPGAs do not require fabrication and are reprogrammable, making them suitable for **one-off designs** where cost-critical volume production is not a factor.

### **4. Analog vs. Digital Signals**

*   **Analog signals are continuous**, similar to real numbers, possessing an infinite range of values between any two points (e.g., light brightness, sound volume). The human perception of the world is largely analog.
*   **Digital signals are discrete**, similar to integers, having a finite number of distinct states (e.g., a light switch being either off or on).
*   **Microcontrollers are digital systems**, processing data in binary (zeroes and ones).
*   **Analog-to-Digital Conversion (ADC)** is necessary at the input of an embedded system to transform analog sensor signals (e.g., from a microphone) into digital values that the microcontroller can process.
*   **Digital-to-Analog Conversion (DAC)** is often required at the output to convert digital signals from the microcontroller into analog signals suitable for driving analog actuators (e.g., speakers).

### **5. Prototyping and Wiring**

*   A **breadboard** is a common tool for **non-permanent wiring** during prototyping. It consists of holes connected electrically in rows (for components) and columns (often for power and ground distribution).
*   This allows components to be connected and reconfigured easily without **soldering**, which creates permanent electrical connections.
*   **Jumper wires** are used to connect components to development boards and each other on a breadboard.
*   When wiring LEDs, **resistors** are typically placed in series to limit current and prevent the LED from burning out.

### **6. Benefits and Risks of IoT**

*   **Benefits:**
    *   **Simplification of tasks:** IoT devices can manage routine activities, freeing users for other pursuits.
    *   **Increased independence:** IoT can reduce reliance on others, for instance, through health monitors reducing doctor visits or self-driving cars providing mobility for those unable to drive.
    *   **Enhanced connectivity:** Networked devices facilitate digital interactions and access to cloud services, which provide vast computational and storage resources.

*   **Risks:**
    *   **Social isolation:** Over-reliance on devices may decrease human interaction.
    *   **Increased dependence on technology:** Malfunctions or outages in critical IoT systems (e.g., medical devices) can have severe consequences.
    *   **Privacy and security concerns:** IoT devices continuously collect and transmit personal data (e.g., location, health, purchasing habits), often without explicit user control over its use or ownership, as granted through terms-of-service agreements. This data is vulnerable to security breaches when stored on cloud servers.
