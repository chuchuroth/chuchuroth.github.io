---
layout: post
title:  "Microcontroller and Industrial Applications module 5"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---



Here is a comprehensive summary of the "knowledgical information" from the provided sources, with colloquial language removed and key concepts highlighted:

### Role of Engineers and Microcontrollers in Industry

An engineer's essential functions include **observing environments, analyzing observations, and designing or developing solutions to optimize processes or incidents**. Microcontrollers are fundamental components in contemporary automated and digital environments. They serve as the **backbone and "brain" for robots**, controlling actions, processing sensor data, and generating signals for motor operation.

Microcontrollers are integral to various automated systems:
*   **Elevators/Lifts**: Photoelectric sensors detect presence, connected to PSoC 62S2 Wi-Fi microcontroller boards based on Arm Cortex-M4 to control door operation (sense, analyze, act: open/close).
*   **Metro Trains**: Door mechanisms are controlled by electric motors, which are, in turn, managed by microcontrollers (e.g., Arm Cortex-M series or LPC 2148).
*   **Robotics**: Microcontrollers control almost all robot actions, including data acquisition, processing, and generating control signals for motors.
*   **Aircraft Maintenance**: Automation in aircraft maintenance, including the use of robots, relies on microcontrollers as the application's core.

### Evolution of Manufacturing and Digital Transformation

Manufacturing, defined as the **large-scale assembly of components or raw materials into finished products**, has progressed through four distinct eras:
*   **First Era**: Characterized by **mechanization, powered by water and steam**.
*   **Second Era**: Focused on **mass production via assembly lines, enabled by electricity**.
*   **Third Era**: Emerged with the **introduction of computers and automation**.
*   **Fourth Era (Industry 4.0 / Smart Manufacturing)**: Aims to **automate manufacturing processes to maximize efficiency, enhance sustainability, improve supply chain management, and identify system barriers proactively** by generating, optimizing, and managing large data volumes.

This evolution signifies a **digital transformation across engineering workspaces**, including design, development, service sectors, and commercial environments. Consequently:
*   **Mechanical engineers** require an understanding of robots.
*   **Electrical engineers** must be proficient with automated machines.
*   **Civil engineers** utilize connected machinery and smart inventory for efficient construction strategies.

Acquiring knowledge and skills in microcontrollers and developing applications with them is therefore **essential for engineers across all disciplines**.

### Microcontroller Development Boards (MDBs)

A **Microcontroller Development Board (MDB)** is hardware specifically designed to **support and extend microcontroller functionalities for various applications**.

**General Layout of a Generic MDB**:
*   **Processor Core**: The central element, responsible for internal processing and interaction with supporting hardware.
*   **On-chip Memory**: Includes **Static RAM (SRAM)** for data read/write operations and **EEPROM or Flash memory** for non-volatile storage (read-only).
*   **Integrated Facilities**: Features like **counter/timer modules and interrupt controllers** enhance the microcontroller's processing capabilities.
*   **Interfaces**:
    *   **Analog Module**: For transmitting and receiving analog data.
    *   **Serial Module Interface**: For data exchange with other devices using serial communication protocols.
    *   **Digital Input/Output (I/O)**: For transmitting and receiving digital data.

### ATmega328 Microcontroller

The **ATmega328 is an 8-bit microcontroller designed by Atmel**, often found in advanced MDBs with integrated SRAM. It belongs to the **AVR family and has 28 pins** arranged chronologically, organized into three bidirectional I/O ports: B, C, and D.

**Pin Configuration and Functionalities**:
*   **Port B (8-bit bidirectional I/O with pull-up resistors)**:
    *   PB0: Timer/counter input source.
    *   PB1: Timer/counter output.
    *   PB2: Slave Select input for SPI communication.
    *   PB3: Master Data Output, Slave Data Input for SPI interface.
    *   PB4: Master Clock Input, Slave Clock Output.
    *   PB5: Serial Clock for SPI bus.
    *   PB6: Input to inverting oscillator amplifier.
    *   PB7: Output of inverting oscillator amplifier.
*   **Port C (7-bit bidirectional I/O with external pull-up resistor)**:
    *   PC0-PC7: Primarily analog inputs.
    *   PC0-PC5: Used as analog input digital values from Channels 0-5.
    *   PC4: Serial interface data connection.
    *   PC5: Serial interface clock line.
    *   PC6: Functions as a default reset pin or an I/O pin when reset is disabled.
*   **Port D (8-bit I/O with internal pull-up resistor)**: All pins are digital.
    *   PD0: Serial communication input.
    *   PD1: Serial communication output.
    *   PD2: External interrupt 0.
    *   PD3: External interrupt 1.
    *   PD4: External counter source timer 0.
    *   PD5: External source timer 1.
    *   PD6: Positive analog comparator input.
    *   PD7: Negative analog comparator input.
*   **Other Important Pins**:
    *   **VCC**: Provides power supply to the system.
    *   **Ground**: System ground for the microcontroller IC.
    *   **AVCC**: Supply voltage for the Analog-to-Digital Converter (ADC), requiring external connection to VCC even if ADC is not in use.
    *   **Air Reference**: Analog reference pin for the ADC.

**ATmega328 Architecture and Memory Features**:
*   **Hardware Architecture**: The ATmega328 utilizes a **Harvard architecture**, characterized by **separate storage and signal pathways for instructions and data**, leading to distinct memory spaces and buses for programs and data.
*   **Major Components**: Include an **Instruction Set Architecture (ISA), CPU, I/O Ports, memory, and internal/external interrupts**.
*   **Internal Memory Types**: The ATmega328 possesses three types of internal memory:
    *   **Flash Memory**: **32 kB** in size, used to **store sketches or programs** written in Arduino programming language. Code stored in Flash Memory executes upon power-up.
    *   **EEPROM (Electrically Erasable Programmable Read-only Memory)**: Similar to Flash but **exclusively used for storing data**, not programs. The ATmega328 has **2 kB of EEPROM**.
    *   **SRAM (Static Random Access Memory)**: **2 kB** in size, it stores **variables, buffers, strings, and other data modified during code execution**. Information in SRAM is volatile and **deleted when power is off**.
*   **Registers**: The ATmega328 has a rich instruction set with **32 general-purpose registers** directly connected to the Arithmetic Logic Unit (ALU).
    *   **General Purpose Registers**: 32 registers, each with an **8-bit storage capacity**, capable of storing both data and addresses.
    *   **Special Purpose Registers**:
        *   **Program Counter**: Holds the **address of the next instruction** to be executed.
        *   **Stack Pointer**: Primarily used for **storing temporary data** and results of addresses after subroutine and interrupt calls. It points to data in the SRAM stack area where interrupts are located.
        *   **Status Register (SREG)**: An **8-bit register** where each bit carries a specific meaning.

### Simulation Software (Tinkercad)

Simulation software is crucial for embedded board design. Without it, direct physical prototyping can be challenging, time-consuming, and prone to errors such as misconnections, design mismatches leading to overheating, and electrical parameter deviations causing safety hazards.

**Benefits of Simulation Tools**:
*   **Error Detection**: Can **identify potential misconnections or wiring errors** before physical assembly, providing warnings and alerts.
*   **Dynamic Design**: Allows for **dynamic updating of circuit elements** until the desired output is achieved.
*   **Analysis and Insight**: Offers an effective method of analysis that is **easily verifiable, communicable, and understandable**, providing insights into complex systems.
*   **Reduced Prototyping Effort**: Facilitates **prototyping and testing of 3D designs** incorporating electronic components controlled by boards like Arduino, reducing the time and effort required for physical builds.

**Tinkercad** is a **free, user-friendly, online 3D design and modeling tool created by Autodesk**. It enables users to create and design 3D objects without complex software. Tinkercad's **"Circuits" feature** specifically allows for the **creation and simulation of electronic circuits using virtual Arduino boards**.

**Process Flow for Designing a Prototype in Tinkercad**:
1.  Open Tinkercad in a web browser.
2.  Select necessary components for the prototype.
3.  Establish connections between components.
4.  Write embedded C code for the prototype.
5.  Initiate the simulation.

**Benefits of Tinkercad Simulation for Arduino UNO**:
*   **Easy Prototyping**: Rapid creation and testing of 3D designs for iterative development.
*   **Virtual Testing**: Simulating circuits and Arduino code in a virtual environment, eliminating the need for physical components and saving resources.
*   **Beginner Friendly**: Intuitive interface with available tutorials and resources, making it accessible for novices in electronics or 3D design.
*   **Collaboration**: Cloud-based nature allows for easy project sharing and collaborative work.
*   **Integration**: Compatibility with other platforms like Thingiverse for seamless import/export of designs and code.

An example demonstration in Tinkercad involved **automating an animal feeder system using an Arduino UNO and a servo motor**. The simulation process included connecting the servo's ground, 5V, and signal pins (D9) to the Arduino UNO, uploading code, and observing the servo turning 90 degrees every six seconds, validating the system before physical construction.

### Integrated Development Environments (IDEs)

An **Integrated Development Environment (IDE)** is an **indispensable tool for software development** in today's digital landscape, where software and hardware are integrated. It provides a **complete environment for software development**, consolidating a code editor, debugger, and other tools to enhance efficiency. Without an IDE, developers would need to use separate tools for various coding tasks and manually manage project files, which is less efficient and more time-consuming. IDEs **streamline software development** by offering a comprehensive set of tools within a single application.

**Arduino IDE** is a software development platform designed specifically for embedded solutions and for programming Arduino boards.

**Key Characteristics of Arduino IDE**:
*   **Free and Open Source**: Available for download and use without cost, and its source code is accessible for modification and customization.
*   **Easy to Use**: Features a user-friendly and simple interface, allowing beginners to quickly learn, write, and upload code for their applications.
*   **Wide Range of Libraries**: Includes a vast collection of pre-written code libraries, providing easy access to functions and features without requiring code to be written from scratch.
*   **Community Support**: Supported by an active community of developers and users who provide resources such as tutorials, forums, and troubleshooting assistance.
*   **Cross-platform Compatibility**: Operates on Windows, macOS, and Linux, enabling development on various operating systems.

**Arduino IDE Key Features (Main Menu)**:
*   **Menu Bar**:
    *   **File Option**: Manages sketches (programs in Arduino terminology), including creation, opening, saving, and uploading.
    *   **Edit Option**: Provides standard editing functionalities like undo, redo, cut, copy, paste, and find/replace.
    *   **Sketch Option**: For managing the current sketch, verifying and uploading code, and including external libraries.
    *   **Tools Option**: Configures board settings, serial port, and other development environment parameters.
    *   **Help Option**: Provides access to online help resources and documentation.
*   **Toolbar**: Contains buttons for common actions:
    *   **Verify**: Checks for compilation errors in the sketch.
    *   **Upload**: Runs the code onto the board.
    *   **New**: Creates a new sketch or opens a new window.
    *   **Open**: Opens existing files.
    *   **Save**: Saves the current sketch.
    *   **Serial Monitor**: Opens a window for serial communication to observe program outputs.
*   **Text Editor**: The area where users write and modify Arduino code, highlighting any compilation errors.
*   **Uploading Status and Message Area**: Displays compilation and uploading progress, and reveals any errors during these processes.

**Hardware Interface Aspects in Arduino IDE**:
To interface code with hardware boards, two initialization steps are required:
*   **Board Type**: Specifies the particular model or variant of the Arduino board, determining available features and pin configurations.
*   **Header File**: Declares and defines functions and objects for use in a program, crucial for code organization and reusability.

An example demonstration in Arduino IDE involved **measuring temperature using a DHT11 sensor and an Arduino board**. The process included declaring the DHT11 header file, defining the sensor's connected pin (e.g., pin 4), initializing the DHT class, configuring serial communication (e.g., 9600 bps), reading temperature data in a loop, displaying it on the serial monitor, and finally configuring the specific Arduino board and COM port before uploading the code.

### Smart Parking Management System (SPMS)

**Motivation for SPMS**: Car parking is a significant public issue, contributing to traffic congestion and driver frustration due to lack of available spaces. An SPMS offers a **technology-based solution to provide real-time information on parking lot availability**, thereby improving the overall parking experience.

**SPMS Introduction**: An **advanced technology designed to enhance parking convenience and effectiveness**. It operates using **sensors to detect whether a parking space is occupied or vacant**, with simple LED displays indicating space availability, location, size, and pricing. The system has the potential to **decrease traffic congestion**.

**Problem Statement (SPMS Prototype)**: The objective is to develop a SPMS capable of **automatically opening the gate upon vehicle entry, closing it after the vehicle crosses the entrance, and maintaining a real-time record of available and occupied parking spaces**. This involves developing a circuit with an Arduino UNO microcontroller and coding with Arduino IDE.

**Design Model**: Comprises three main components: a **sensor for input, a microcontroller for processing, and an output display**.

**Components Used in the SPMS Prototype**:
*   **IR Sensor**: Acts as an input mechanism to detect vehicle presence.
*   **Arduino UNO Microcontroller**: The central processing unit.
*   **Potentiometer**: Used to adjust the contrast level of the LCD display.
*   **LCD Display (16x2 panel)**: Shows the number of available parking spots and other messages.
*   **Servomotor**: Controls the automatic opening and closing of the gate.
*   Additionally: USB connector, jumper wires, power bank, toy cars for demonstration.

**System Overview**: An IR sensor detects vehicle movement, transmitting data to the Arduino UNO. Upon detection, a servomotor opens the gate; after the vehicle passes, the gate closes automatically. The LCD screen dynamically updates and displays the number of available parking spots.

**Code Flowchart for SPMS**:
1.  Initialize IR sensors, servomotor, and LCD.
2.  Display a welcome message and initial available slots.
3.  Check for detection by the first IR sensor (vehicle entry).
4.  Verify slot availability; if available, open the gate and decrement the slot count.
5.  If no slots are available, display "sorry parking full" on the LCD.
6.  Check for detection by the second IR sensor (vehicle exit).
7.  Open the gate and increment the slot count.

The demonstration of the SPMS prototype involved connecting all components, uploading the code, and simulating vehicle entry and exit with toy cars. The system successfully opened and closed the gate, updated the available parking slot count on the LCD, and displayed a "parking full" message when no slots were available, preventing further entry. The prototype utilized cost-effective components and demonstrated dynamic updates of parking availability.

### Automated Inventory Control System (AICS) in Construction Site

**Motivation for AICS**: Inventory control accounts for approximately **60% of project money** in large-scale projects like construction. Effective inventory control saves time and money by ensuring material and equipment availability, minimizing delays, and optimizing resource use. Real-time monitoring helps workers locate materials efficiently. Industry data indicates that 75% of retailer technology investment plans are based on sensors for tracking inventory status.

**Basics of Automated Inventory Control**: Involves using **modern technologies, such as the Internet of Things (IoT), to track and manage inventory in real-time**, leading to improved accuracy, reduced manual effort, and cost savings.

**Problem Statement (AICS Prototype)**: The objective is to develop a **motion detection sensor-based automated inventory control system for construction sites**, requiring a circuit with an ESP8266 microcontroller and code designed in Arduino IDE.

**Design Model**: Consists of a **microcontroller to receive input and push data to the cloud, a sensor for detecting material motion, and an open-source cloud for data upload**.

**Components Used in the AICS Prototype**:
*   **ESP8266 Development Board**: A **32-bit RISC processor board**, highly flexible and customizable with various I/O pins.
*   **PIR Sensor (Passive Infrared Sensor)**: An electronic device that **detects motion by measuring infrared radiation**. Used for tracking material movement. Commonly employed in security, lighting control, and home automation.
*   Power supply (9V).
*   Jumper wires and a micro-type USB cable for connection and deployment.
*   **ThingSpeak**: An open-source cloud platform used for data upload.

**Code Process Flow for AICS**:
1.  Initialize header files.
2.  Establish communication with ThingSpeak.
3.  Provide Wi-Fi credentials and connect to a Wi-Fi network.
4.  Implement a retry mechanism if Wi-Fi connection fails.
5.  Detect motion using the PIR sensor.
6.  Upload motion information to the ThingSpeak cloud.
7.  Implement a retry/debugging mechanism if data upload is unsuccessful.

### Air Quality Monitoring System (AQMS)

**Motivation for AQMS**: Air pollution is a major environmental concern. **Smart cities utilize AQMS for continuous air quality monitoring to mitigate pollution**. AQMS can be installed in various urban areas, including industrial zones, transportation hubs, residential areas, schools, hospitals, construction sites, and sewage treatment facilities. It enables safety professionals to measure pollutant levels, identify pollution sources, and implement control measures.

**AQMS Introduction**: The process of **measuring the concentration of pollutants and contaminants in the air**. This involves collecting air samples and analyzing them for various contaminant levels.

**Parts Per Million (PPM) Ranges for Air Quality**:
*   **0-50**: Acceptable.
*   **51-100**: Moderate.
*   **101-150**: Unhealthy for sensitive individuals.
*   **151-200**: Unhealthy.
*   **201-300**: Very unhealthy.
*   **301-500**: Highly hazardous.

**Problem Statement (AQMS Prototype)**: The requirement is to design an AQMS capable of **monitoring air quality via a gas sensor and calculating the overall concentration of pollutants**. The task involves developing a circuit with an ESP8266 microcontroller and coding with Arduino IDE.

**Design Model**: The AQMS design includes three essential parts: **sensor input, a microcontroller for input processing and level ranging, and an output mechanism**.

**Components Used in the AQMS Prototype**:
*   **MQ135 Sensor**: The input sensor for detecting gas concentrations.
*   **ESP8266 Microcontroller**: The controller for data processing.
*   **LED Indicators**: Three different colors (green, yellow, red) to visually indicate air quality levels.
*   **ThingSpeak Cloud**: For receiving and displaying data.
*   Additional components: 100 ohm resistor, jumper wires, breadboard, micro USB cable.

**System Overview**: The MQ135 sensor collects input data and transmits it to the ESP8266 microcontroller for processing. LEDs visually indicate the air quality level, and the data is simultaneously transferred to the ThingSpeak cloud for remote monitoring.

**Code Process Flow for AQMS**:
1.  Sensors collect air quality values.
2.  Data is sent to ThingSpeak Cloud.
3.  The PPM (parts per million) value is calculated.
4.  **Conditional LED Indication**:
    *   If PPM is less than 100, the green LED illuminates.
    *   If PPM is greater than 100 but less than or equal to 200, the yellow LED illuminates.
    *   If PPM exceeds 200, the red LED illuminates.

The demonstration of the AQMS prototype involved connecting the components, uploading the code, and powering the setup. Initially, a red LED would light up before Wi-Fi connection, turning off once established. The green LED indicated low pollution levels (e.g., 90.32 AQI), while yellow or red LEDs would illuminate if pollution conditions were met. The ThingSpeak graph displayed the real-time pollution level and its variations. The prototype successfully demonstrated the principle of air quality monitoring and displayed pollution levels via LEDs.
