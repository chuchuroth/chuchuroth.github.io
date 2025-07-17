---
layout: post
title:  "Arduino Platform and C Programming module 3"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---


Here is a comprehensive summary of the information regarding Arduino programming and its build process, presented without colloquial language and with key concepts bolded for clarity:

### Arduino Programs (Sketches) and Language Subset
*   An Arduino program is referred to as a **sketch**.
*   Sketches are fundamentally **C/C++ programs** with specific constraints.
*   They utilize **Arduino library functions**.
*   While C++ is a superset of C (meaning all legal C code is also legal C++), Arduino sketches typically adhere primarily to C features, although C++ features are usable.
*   Understanding **classes** is necessary for using Arduino library functions, as these libraries often employ classes. Users are expected to use pre-existing classes from libraries but not necessarily define new ones within this context.

### Object-Oriented Programming and Classes
*   **Object-Oriented Programming (OOP)** is a method for **organizing code** to enhance understanding and manageability, particularly in large codebases.
*   OOP employs **encapsulation**, which involves grouping related data and functions into cohesive units called **classes**.
*   A **class** is a **programmer-defined type** that consolidates related data (variables) and functions (methods) that operate on that data.
*   For example, an integer type combines numerical data with arithmetic operations (+, -, *, /). Classes allow for the creation of new, **application-specific types**.
*   **Benefits of using classes** include:
    *   **Encapsulation of related data** within a single object (e.g., x and y coordinates for a `Point` object).
    *   **Reduction in variable count** and function arguments (e.g., one `Point` object instead of separate `x` and `y` variables).
    *   The ability to define **class-specific functions** (e.g., a `plot` function that only applies to `Point` objects).
*   The **dot operator (`.`)** is crucial for **accessing members** (variables and functions) of a class or an object instance. The element to the left of the dot indicates the object or class from which the member is accessed (e.g., `objectName.memberName` or `className.functionName`).
*   Library functions in Arduino are frequently invoked using this **object.function** or **class.function** syntax (e.g., `Ethernet.begin`, `Serial.begin`). This prefixing helps the compiler distinguish functions with identical names across different libraries.

### Arduino Sketch Structure: `setup()` and `loop()`
*   Every Arduino sketch must define two core functions: **`setup()`** and **`loop()`**.
*   Unlike standard C/C++ programs, Arduino sketches **do not explicitly contain a `main()` function**. The `main()` function is automatically generated during the build process, combining the `setup()` and `loop()` components.
*   **`setup()` function**:
    *   Executes **once** upon Arduino power-up, following the bootloader.
    *   Primarily used for **initialization tasks** relevant to the application, such as configuring communication interfaces or setting up devices.
    *   Common library initialization functions (e.g., `Ethernet.begin`, `Serial.begin`) are typically called within `setup()`.
    *   Its signature is `void setup()` (takes no arguments, returns no values).
*   **`loop()` function**:
    *   Executes **continuously in an infinite loop** for as long as the Arduino remains powered on.
    *   This continuous operation is characteristic of embedded systems, which are designed to be always active and responsive to inputs.
    *   It contains the **main control flow** of the program, with its contents repeatedly executed.
    *   Its signature is `void loop()` (takes no arguments, returns no values).

### Arduino Build Process (Toolchain)
*   The **Arduino Toolchain** defines the sequence of operations required to translate a written sketch into executable code on the Arduino.
*   The process initiates when a user clicks **"Verify"** (to compile) or **"Upload"** (to compile and transfer) in the Arduino IDE.
*   The sequence of steps is:
    1.  **Combine and Transform (Pre-processing)**: Multiple code files (sketches, potentially assembly) are consolidated into **one large source code file**. During this step, **`#include` directives** for Arduino libraries and **function prototypes** are automatically added. A **`main()` function** is also automatically constructed from the user-defined `setup()` and `loop()` functions.
    2.  **Compile**: The combined source code undergoes **cross-compilation**.
        *   **Compilation** translates high-level C/C++ code into **machine code** that the processor understands.
        *   **Cross-compilation** specifically means compiling code on one type of machine (e.g., an Intel x86 desktop) for execution on a **different target processor** (e.g., the AVR Atmega328 on the Arduino Uno).
        *   The **`avr-gcc`** tool is invoked by the IDE to perform this cross-compilation.
        *   The resulting code is intended for the AVR processor and will not execute on the compilation host.
        *   This step produces an **object file (.o file)**.
    3.  **Link**: Object files, including those from Arduino libraries, are **combined**. This process resolves function calls within the code by inserting necessary branch or jump statements to the correct memory locations of linked functions.
    4.  **Hex File Creation**: After linking, an **executable file (.elf file)** is generated. Since the Arduino processor does not directly accept ELF files, the **`avr-objcopy`** program is used to convert the .elf file into a **.hex file**, which is the format compatible with the Arduino's processor.
    5.  **Upload**: If the **"Upload"** command is selected, the generated **.hex file is transferred and programmed into the flash memory** of the Arduino board. Once uploaded, the code begins executing immediately on the Arduino.
*   The **"Verify"** function executes all steps from combining/transforming through hex file creation but **does not perform the upload**.

### Arduino Pins and Control
*   **Pins** are the primary **physical connections** between the Arduino microcontroller and external components.
*   They can be configured as either **input** or **output** pins:
    *   **Output Pins**: The Arduino sketch controls their voltage, enabling the Arduino to drive or control other devices like LEDs or motors.
    *   **Input Pins**: External components control their voltage, allowing the Arduino to read signals and receive data from sensors or switches.
*   Pins can also be classified as **digital** or **analog**:
    *   **Digital Pins**: Handle **discrete voltage levels**, typically 0 volts (LOW) or 5 volts (HIGH) on an Arduino Uno. Pins 0-13 are digital. They can read digital inputs and drive digital outputs.
    *   **Analog Pins**: Process a **continuous range of voltages**, typically 0 to 5 volts. Labeled A0-A5, they are primarily used to read analog data from sensors. The Arduino's internal **analog-to-digital converter (ADC)** translates the analog voltage into a digital numerical value (0-1023). Analog pins **cannot generate analog output** directly.

### Pin Control Library Functions
*   **`pinMode(pin, mode)`**:
    *   Sets a specified `pin` to act as an **`INPUT`**, **`OUTPUT`**, or **`INPUT_PULLUP`** (a reversed-polarity input mode).
    *   **Must be called** for a pin before it is used for reading or writing.
    *   Usually invoked within the `setup()` function.
    *   `pin` refers to the digital pin number (0-13) or analog pin name (A0-A5).
*   **`digitalRead(pin)`**:
    *   Reads the **digital state** (HIGH or LOW) of a designated digital input `pin`.
    *   Returns an integer value (0 for LOW, 1 for HIGH).
    *   Typically used within the `loop()` function.
*   **`digitalWrite(pin, value)`**:
    *   Sets the **digital state** (HIGH or LOW) of a designated digital output `pin`.
    *   `HIGH` sets the pin to 5 volts, `LOW` sets it to 0 volts.
    *   Typically used within the `loop()` function.
*   **`analogRead(pin)`**:
    *   Reads the **analog voltage** from an analog input `pin`.
    *   The internal ADC converts this voltage into an integer ranging from **0 (for 0 volts) to 1023 (for 5 volts)**.
    *   Only accepts analog pins as arguments.

### Time Control Function
*   **`delay(msec)`**:
    *   Pauses program execution for a specified duration in **milliseconds**. (1000 milliseconds = 1 second).
    *   Primarily used to synchronize program timing with **human perception**, as microcontrollers operate at speeds far exceeding human response times. This ensures outputs (e.g., blinking lights) are perceivable.
    *   It is a standard function, sufficient for typical human interaction timing, though not designed for high-precision timing.

### The Blink Example
*   The **Blink example** is a foundational program in embedded systems, comparable to "Hello World" in traditional programming. It serves as a sanity check to ensure the Arduino is functioning correctly.
*   The built-in LED on the Arduino Uno board is connected to **digital pin 13**.
*   The sketch code typically involves:
    *   **`setup()`**: `pinMode(13, OUTPUT);` configures pin 13 as an output, executed once.
    *   **`loop()`**:
        *   `digitalWrite(13, HIGH);` turns the LED on.
        *   `delay(1000);` pauses for one second.
        *   `digitalWrite(13, LOW);` turns the LED off.
        *   `delay(1000);` pauses for another second.
    *   This sequence in `loop()` causes the LED to blink repeatedly at a one-second interval.

### Wiring an External LED (Blink Example Extension)
*   To blink an **external LED**, additional components are required: an LED, a **resistor** (e.g., 220 ohm), and wires.
*   The **resistor is crucial** to limit the current flowing through the LED and prevent its destruction, as LEDs typically have low current ratings (e.g., 20 milliamps).
*   **LED polarity** is important:
    *   The **anode (longer leg)** is the positive terminal and connects to the Arduino's output pin (e.g., pin 13).
    *   The **cathode (shorter leg)** is the negative terminal and connects to the Arduino's ground (GND) pin through the resistor.
*   **Wiring steps**:
    1.  Connect one end of the resistor to an Arduino **GND** pin via a wire.
    2.  Connect the LED's **cathode** (short leg) to the other end of the resistor.
    3.  Connect the LED's **anode** (long leg) to Arduino **digital pin 13** via a wire.
*   When powered, both the built-in LED on pin 13 and the externally wired LED will blink synchronously, as they are controlled by the same pin.
