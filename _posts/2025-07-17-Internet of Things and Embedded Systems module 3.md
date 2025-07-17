---
layout: post
title:  "Internet of Things and Embedded Systems module 3"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---


The following outlines knowledgical information regarding Internet of Things (IoT) devices and embedded systems, extracted from the provided sources.

### **1. Internet of Things (IoT) Devices and Embedded Systems**

*   **IoT devices** are a combination of hardware and software working together.
*   In the design process of IoT devices, hardware and software are designed collaboratively rather than in isolation, to achieve greater efficiency.
*   **Hardware** typically handles physical interaction with the environment, including sensors and actuators. It is also utilized for computationally complex tasks.
*   **Software** is used for control operations, slower processes, and human interactions.
*   More complex IoT components may incorporate an **operating system**.

### **2. Hardware Components**

The physical design of an IoT device involves various components wired together, with a central **microcontroller**.

*   **Microcontroller:**
    *   Serves as the **central component** or "heart" of the system, responsible for executing code, processing data, and controlling other components.
    *   Microcontrollers are **integrated circuits (ICs)**, typically made of silicon, and require packaging to protect the chip, cool it during operation, and provide larger pins for electrical contact.
    *   They are generally chosen for efficiency in IoT systems and are typically **smaller, less powerful, and more cost-effective** than microprocessors found in general-purpose computers, as they are designed to perform only the necessary functions.
    *   Unlike over-engineered desktop/laptop processors, microcontrollers for IoT systems are selected to barely meet the minimum requirements of the project, prioritizing cost-effectiveness.
    *   Development boards, such as Arduino and Raspberry Pi, integrate microcontrollers and simplify the development process by providing libraries that abstract away low-level details of the chip's behavior.
*   **Sensors and Actuators:** These are hardware components that enable interaction with the physical world. An **LED (Light Emitting Diode)** is mentioned as a component that a microcontroller communicates with, for instance, telling it when to turn on or off.
*   **Integrated Circuits (ICs):**
    *   ICs are chips, commonly silicon-based, that are manufactured on wafers and then cut into individual chips. These chips are then enclosed in a package that protects them, aids in cooling, and provides accessible pins for wiring.
    *   The complexity of ICs can vary significantly, ranging from simple components to entire processors, and their **datasheets** reflect this complexity.

### **3. Component Selection and Datasheets**

*   When designing an IoT system, selecting the appropriate microcontroller is an early and crucial decision due to the wide range of available choices and the constrained nature of IoT systems.
*   Designers must consider various **parameters** for each component, including physical size, voltage requirements, and current limits.
*   **Datasheets** are information sheets for hardware components, providing essential details necessary for their proper use. Every complex component, especially integrated circuits, has a datasheet.
    *   Key information found in datasheets includes **physical dimensions**, which are critical for integrating components into a larger system or fitting them onto prototyping boards like a breadboard, where pin spacing (e.g., 0.1 inches) is a standard consideration.
    *   **Electrical parameters** (e.g., maximum/minimum voltage, current limits) are crucial for ensuring component compatibility and preventing damage (e.g., matching a 5-volt microcontroller output with a 3.3-volt component requires careful consideration or voltage stepping).
    *   **Thermal parameters** indicate the operating temperature range, which may be relevant for specific extreme environments.
    *   While datasheets can be very complex and extensive (e.g., a microcontroller datasheet might be 150 pages), designers need to be able to at least minimally read them to find critical information for component selection.

### **4. Microcontroller Characteristics for System Design**

When selecting a microcontroller, specific characteristics are evaluated to match the system's needs and cost constraints:

*   **Datapath Bitwidth:**
    *   Refers to the number of bits in each register, indicating the size of numbers the system can process.
    *   A higher bitwidth generally provides more accuracy and greater data throughput.
    *   For instance, an 8-bit microcontroller (like the one in Arduino) is sufficient for simple control operations in many applications, where high numerical accuracy is not required.
*   **Input/Output (I/O) Pins:**
    *   These pins connect the microcontroller to other components in the system.
    *   The number of available I/O pins can become a bottleneck, as each connected component may require multiple pins. Designers must estimate the required pin count early in the design process.
*   **Performance (Clock Rate):**
    *   The necessary performance level depends on the application.
    *   For interactions with humans, who are relatively slow, lower processor speeds are often sufficient (e.g., 30 frames per second for video, or 22 kilohertz for audio).
    *   Applications involving video processing often require higher performance due to the volume of data per frame, whereas audio or tactile interactions may require significantly slower clock rates.
*   **Timers:**
    *   Commonly useful components within a microcontroller for real-time applications.
    *   Timers are used to schedule events at specific deadlines or regular intervals, such as sampling sensor data (e.g., sound or temperature).
    *   The accuracy of a timer relates to its bitwidth (e.g., an 8-bit timer is less accurate than a 16-bit timer).
*   **Analog-to-Digital Converters (ADCs):**
    *   Microcontrollers are inherently digital devices, processing discrete values (zeros and ones), while the physical world largely operates with analog, continuous signals (e.g., light brightness, sound volume).
    *   ADCs are essential components that convert these analog phenomena from sensors into digital numbers that the microcontroller can process (e.g., converting light brightness to a numerical value for conditional logic).
    *   Many microcontrollers include ADCs; however, some platforms like the Raspberry Pi do not have a built-in ADC, which can limit their direct interaction with analog sensors.
*   **Low Power Modes:**
    *   Modern microcontrollers commonly feature various low power modes, enabling them to reduce power consumption.
    *   These modes are crucial for battery-powered IoT devices, allowing them to operate for extended periods by selectively turning off or slowing down certain components when full functionality is not required.
*   **Communication Protocol Support:**
    *   Microcontrollers must communicate with other integrated circuits using specific communication protocols (e.g., UART, I2C, SPI).
    *   Most contemporary microcontrollers provide support for common communication protocols, which is important for integrating various chips within a larger system.

### **5. Storage Elements in Microcontrollers**

Microcontrollers contain various storage elements for data and program code, balancing speed, cost, and capacity:

*   **Flash Memory:**
    *   A type of **non-volatile memory** that retains its data even when power is removed, similar to thumb drives.
    *   The compiled program code for the microcontroller is typically stored in flash memory.
    *   Example: An ATmega 2560 microcontroller may have 256 kilobytes of flash memory.
*   **EEPROM:** Another type of non-volatile memory similar to flash memory.
*   **SRAM (Static Random-Access Memory):**
    *   Also known as regular random-access memory.
    *   Example: An ATmega 2560 microcontroller may have 8 kilobytes of SRAM.
*   **Registers:**
    *   The **fastest and most expensive** type of storage element.
    *   Registers store single values (e.g., a 32-bit number) and are accessed in less than a clock cycle.
    *   Due to their size and cost, microcontrollers have a limited number of registers (e.g., 32 general-purpose registers is common).
    *   They include special-purpose registers (like the program counter, which indicates the address of the current instruction) and general-purpose registers used for computations.
*   **Cache Memory:**
    *   Stores more data than registers and is slower but cheaper than registers, while being faster and more expensive than main memory.
    *   Cache is typically located on the same integrated circuit as the microcontroller.
    *   Many microcontrollers use a **Harvard architecture**, separating data cache (for program data) and instruction cache (for program instructions).
*   **Main Memory:**
    *   The **largest, cheapest, and slowest** type of memory.
    *   It is located off the CPU, on a different set of chips on the same board, and connected to the CPU via a system bus.
    *   Accessing main memory can be significantly slower than accessing cache (e.g., 100 clock cycles for main memory vs. one clock cycle for cache).
    *   The performance disparity between the processor and main memory is known as the **Von Neumann Bottleneck**, which is mitigated by the use of caches and registers to reduce reliance on slower main memory accesses.
    *   In high-level programming languages like C/C++ or Python, the compiler or interpreter manages the allocation of variables to registers, cache, or main memory, abstracting these details from the programmer.

### **6. Software Translation and Tool Chain**

The code written by programmers is not directly executed by the microcontroller; it must undergo a translation process.

*   **Machine Language:**
    *   The native language understood by a microcontroller or CPU.
    *   Consists of small, simple instructions encoded in binary (zeros and ones), typically viewed in hexadecimal.
*   **Assembly Language:**
    *   A low-level language that provides a one-to-one mapping to machine code, using human-readable mnemonics (e.g., "add R1, R2, R3").
    *   While more readable than machine code, it is still very basic and lacks high-level programming constructs (e.g., loops).
    *   Writing directly in assembly language is possible but difficult and generally not performed in this course.
*   **High-Level Languages:**
    *   Languages like C, C++, Java, and Python are easier to use and provide common programming constructs (e.g., loops, variables, objects).
    *   These languages must be translated into machine language before execution.
*   **Translation Methods:**
    *   **Compilation:** The high-level code is translated into machine code (an "executable") *once* before execution. The executable can then be run multiple times without re-translation. C and C++ are examples of compiled languages, used with platforms like Arduino. Compiled programs are generally faster than interpreted programs.
    *   **Interpretation:** The high-level code (e.g., Python) is translated into machine code *at runtime, every time* it is executed. Interpretation is generally slower but offers advantages for programmers, such as automatic variable type declaration and memory management, reducing programming burden. Python is an interpreted language, used with platforms like Raspberry Pi.
*   **Software Tool Chain (for compiled languages):**
    *   The sequence of software tools used to convert a program into an executable program on a target platform.
    *   The process typically involves:
        1.  **Host Machine:** The programmer writes code (e.g., C) on a desktop or laptop.
        2.  **Cross-Compiler:** This compiler translates the high-level code into assembly code specifically for the **target microprocessor** (e.g., an AVR ATmega processor for Arduino).
        3.  **Assembler:** Converts the assembly code into an **object file**, which contains machine code along with debugging information. Direct assembly code can also be merged at this stage.
        4.  **Linker:** Integrates pre-written **library functions** (reusable code) into the program and creates an executable file.
        5.  **Programmer:** This tool copies the executable code from the host machine to the target microprocessor's flash memory, typically via a USB cable, for execution.
        6.  **Debugger (Optional):** Allows for controlled execution and monitoring of the program on the target platform for troubleshooting.

### **7. Operating Systems (OS) in IoT Devices**

An operating system acts as an intermediary layer between the application code and the hardware.

*   **Role and Presence:**
    *   Operating systems are **not always present** in IoT devices.
    *   Simpler platforms like Arduino typically do not use an OS due to speed limitations, while more powerful platforms like Raspberry Pi generally do.
*   **Functionality:**
    *   **Manages Hardware:** The OS handles the detailed interactions with the hardware on behalf of the application code.
    *   **Supports Multiple Programs/Tasks:** A primary benefit of an OS is enabling the execution of many applications or **processes** (runtime instantiations of programs) concurrently. It manages their turns, making it appear as if they are all running simultaneously.
    *   **Resource Management:** The OS manages and allocates shared hardware resources (e.g., CPU time, memory, I/O devices, ADCs, network access) among different processes, ensuring fair usage and resolving conflicts.
    *   **User Interface:** Provides a user interface, often a command-line interface for IoT devices, which is more stripped-back than graphical interfaces found on desktops.
*   **Considerations:**
    *   An operating system is a large program that consumes significant **resources** (clock cycles, memory).
    *   Its overhead can **slow down** the system and increase the overall cost, necessitating a faster processor to support it.
    *   **Utility in Complex Systems:** An OS is highly beneficial in complex IoT devices that must perform multiple tasks concurrently, such as a web-controlled car simultaneously streaming video data, servicing motion commands, and detecting obstacles for automatic braking. It simplifies programming by allowing individual tasks to be written separately, with the OS handling their interweaving and resource allocation.
