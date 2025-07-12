---
layout: post
title:  "Microcontroller and Industrial Applications module 3"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---


The 8051 microcontroller architecture and programming involve various operations, memory management, and control mechanisms.

### Bit Operations and Memory Configuration
*   **Bitwise Operations Scope:** The 8051 supports bitwise operations across RAM Bit Addresses, Special Function Register (SFR) Bit Addresses, and Boolean Operations, which is beneficial for programming.
*   **RAM Bit Addressable Space:** The internal RAM memory from **20H to 2FH** is bit addressable, with addresses mapped and numbered from **00H to 7FH**. For example, address 0AH refers to the third bit address of 21H.
*   **SFR Bit Addressable Space:** Many SFRs are bit addressable, with direct addresses mapped to bit addresses. For instance, the fifth bit of the accumulator has the address E04.
*   **Bitwise Operation Instructions:** Bitwise operations are enabled by data transfer, logical, and branching instructions. An example logical instruction is **`ANL C, /bit`**, such as `ANL C, /0E2`, which performs a bitwise AND operation between the carry bit and the NOT of the third bit of the accumulator.
*   **Rotate and SWAP Functions:** The 8051 supports **rotate functions** on accumulator contents, including rotate right, rotate left, with carry, and without carry. Additionally, the **`SWAP` instruction** is available to swap the nibble contents of the accumulator.
*   **Division by Two:** Dividing a value by two can be achieved by rotating the value to the right once. For even values, a rotation operation without carry is sufficient.

### Arithmetic Instructions
*   **Overview:** 8051 provides opcodes for arithmetic operations such as addition and subtraction, performed between two operands.
*   **Execution Time:** Most arithmetic instructions execute in **one microsecond**, with the exception of **`INC DPTR`**, which takes two microseconds.
*   **Increment and Decrement:** Increment and decrement operations in the internal RAM occur directly, without requiring the accumulator.
*   **Flags Affected:** Arithmetic instructions primarily affect the **Carry (C), Auxiliary Carry (AC), and Overflow (OV) flags**. The Overflow flag (OV) is set by the exclusive OR of the C7 bit with the C6 bit.
*   **Addition (`ADD`):**
    *   Results are consistently stored in the accumulator.
    *   All addressing modes are supported.
    *   For **unsigned numbers**, the Carry flag indicates if the addition result exceeds 255.
    *   For **signed numbers**, the Most Significant Bit (MSB) denotes the number's sign (positive or negative).
    *   **Flag Logic for Signed/Unsigned Addition:**
        *   If **Overflow flag is 0 and Carry flag is 0**, no action is required.
        *   If **Overflow flag is 1 and Carry flag is 0**, the sign needs to be complemented.
        *   If **Overflow flag is 0 and Carry flag is 1**, no action is required.
        *   If **Overflow flag is 1 and Carry flag is 1**, the sign needs to be complemented.
    *   **Instruction Formats:**
        *   **`ADD A, #n`**: Adds immediate 8-bit data `n` to the accumulator.
        *   **`ADD A, Rr`**: Adds contents of register bank `Rr` to the accumulator.
        *   **`ADD A, address`**: Adds contents of the specified `address` to the accumulator.
        *   **`ADD A, @Rp`**: Adds contents of the address held in register `Rp` (indirect addressing) to the accumulator.
*   **Subtraction (`SUBB`):**
    *   The only subtraction instruction is **`SUBB` (Subtract with Borrow)**.
    *   To perform a simple subtraction without borrow, the Carry bit (CY) must be set to 0. The process involves taking the two's complement of the subtrahend, adding it to the minuend, and then adding the Carry bit.
    *   Immediate, register, direct, and indirect addressing modes are applicable.
    *   Supports both signed and unsigned number subtraction.
*   **Multiplication (`MUL AB`):**
    *   Supports **unsigned byte-by-byte multiplication**.
    *   Only **register mode addressing** is possible.
    *   Format: **`MUL AB`** (no comma separator).
    *   Result storage: **Accumulator (A) holds the lower byte**, and **Register B holds the upper byte** of the answer.
    *   The two operands to be multiplied must be in registers A and B before the instruction.
    *   The **Carry flag (CY) is always cleared**. The **Overflow flag (OV) is set if the result exceeds 255**.
*   **Division (`DIV AB`):**
    *   Performs **byte-by-byte division**.
    *   Follows register mode addressing.
    *   Format: **`DIV AB`**.
    *   Result storage: **Register B holds the remainder**, and **Accumulator (A) holds the quotient**.
    *   The **Carry flag (CY) is always zero**. The **Overflow flag (OV) is set to 1 if B is zero** (indicating an error); otherwise, OV is zero.
*   **Decimal Adjust Accumulator (`DA A`):**
    *   Adjusts the contents of the accumulator for **BCD (Binary-Coded Decimal) values**.
    *   This instruction is valid when numbers are in BCD form prior to addition.
    *   It is **not useful for hexadecimal number addition**.
    *   Only outcomes of `ADD` and `ADD C` instructions can be adjusted using `DA A`.
*   **Increment and Decrement (`INC`, `DEC`):**
    *   These instructions add or subtract a binary one to a concerned number.
    *   Format: **`INC byte`**.
    *   They support different addressing modes.
    *   **Mathematical flags (Carry, Auxiliary Carry, and Overflow flags) are not affected** by these instructions.

### Call and Subroutine Instructions
*   **Purpose:** Calls and subroutines are utilized to **optimize memory and execution speed** by invoking small, frequently used, standalone programs (subroutines).
*   **Call Principle:**
    *   When a `CALL` opcode is executed (or an interrupt occurs), the **return address** (the address of the instruction following the call/interrupt) is stored from the Program Counter (PC).
    *   The return address bytes are **pushed onto the stack**, with the low byte first.
    *   The **Stack Pointer (SP) is incremented** for each byte pushed onto the stack.
    *   The **subroutine's address is then loaded into the PC**, and the subroutine begins execution.
    *   At the end of the subroutine, a **`RET` (return) opcode** is encountered, which retrieves the return address from the stack and restores the PC.
*   **`LCALL` (Long Call):**
    *   A **three-byte instruction**.
    *   Format: **`LCALL code_address`**.
    *   No flags are affected.
    *   Must be followed by a **`RET` instruction**.
*   **`ACALL` (Absolute Call):**
    *   A **two-byte instruction**.
    *   Format: **`ACALL code_address`**, where `code_address` refers to page numbers.
    *   The new PC value is calculated using an offset provided as the second byte in the instruction.
*   **`RET` (Return):**
    *   A **single-byte instruction**.

### Jump Instructions
*   **Function:** Jump instructions modify the Program Counter (PC) address to execute a specific program address.
*   **Categories:**
    *   **Type I (Memory Allocation Based):** Relative Range, Absolute Range, and Long Range.
    *   **Type II (Condition Based):** Conditional and Unconditional.
*   **General Rule:** Unconditional jumps are typically long range, while conditional jumps are short or relative range.
*   **Relative Range (`SJMP` - Short Jump):**
    *   The new destination address is specified using a **signed 8-bit offset**, allowing a range from **-128 to +127 bytes** relative to the current PC.
    *   This is a **two-byte instruction**.
    *   For jumps beyond this relative range, additional relative jumps may be chained.
*   **Absolute Range (`AJMP` - Absolute Jump):**
    *   Utilizes **logical divisions of memory called pages**.
    *   In 8051, memory is divided into **2 kilobyte pages**.
    *   Allows control to switch across these pages.
    *   Format: **`AJMP label`**, where the `label` uses **11 bits within the current page** as an offset to the PC.
    *   Offers a longer programming range compared to the relative range.
*   **Long Range (`LJMP` - Long Jump):**
    *   A **three-byte instruction**.
    *   Format: **`LJMP address`**, where `address` is a **16-bit address**.
    *   Capable of covering almost **64 kilobytes of memory**, accessing the entire memory range without constraints on bits and bytes.
    *   This instruction includes all types of jump ranges.
*   **Unconditional Jump Instructions:**
    *   **`JMP @A + DPTR`**: Jumps to the address formed by adding the accumulator (A) content to the data pointer (DPTR). Accumulator, data pointer, and flags remain unchanged.
    *   **`AJMP sadd`**: Jumps to an absolute short range address `sadd`.
    *   **`LJMP ladd`**: Jumps to a long range address `ladd`.
    *   **`SJMP radd`**: Short jump to a relative address `radd`.
    *   **`NOP` (No Operation)**: Performs no action and proceeds to the next instruction. Used for software timing loops or to leave space for future instructions. No flags are affected.
*   **Conditional Jump Instructions:**
    *   All conditional jumps are **short range or relative jumps**.
    *   **Bit Jumps:** Based on the status of the Carry flag or any bit-addressable location (including Port 2 bits).
        *   **`JC radd`**: Jumps relative if the Carry flag is set (1).
        *   **`JB b, radd`**: Jumps relative if the addressable bit `b` is set (1).
        *   **`JNB b, radd`**: Jumps relative if the addressable bit `b` is reset (0).
        *   **`JBC b, radd`**: Jumps relative if the addressable bit `b` is set, and then clears the addressable bit to 0.
    *   **Byte Jumps:** Check the byte contents.
        *   **`CJNE A, add, radd`**: Compares the accumulator content with the content of a direct address. If they are not equal, it jumps relative. The Carry flag is set to 1 if A is less than the direct address content, otherwise it is 0.
        *   **`CJNE A, #n, radd`**: Compares the accumulator content with an immediate number `n`. If they are not equal, it jumps relative. The Carry flag is set to 1 if A is less than the number, otherwise it is 0.
        *   **`CJNE Rn, #n, radd`**: Compares the content of register `Rn` with an immediate number `n`. If they are not equal, it jumps relative. The Carry flag is set to 1 if `Rn` is less than the number, otherwise it is 0.
        *   **`CJNE @Rp, #n, radd`**: Compares the content of the address pointed to by `Rp` with an immediate number `n`. If they are not equal, it jumps relative. The Carry flag is set to 1 if the content of the address pointed to by `Rp` is less than the number, otherwise it is 0.
        *   **`DJNZ Rn, radd`**: Decrements register `Rn` by 1. If the result is not 0, it jumps relative. No flags are affected.
        *   **`DJNZ add, radd`**: Decrements the direct address content by 1. If the result is not 0, it jumps relative. No flags are affected unless the direct address refers to the Program Status Word (PSW).
        *   **`JZ radd`**: Jumps relative if the accumulator (A) is 0. Flags and the A register remain unchanged.
        *   **`JNZ radd`**: Jumps relative if the accumulator (A) is not 0. Flags and the A register remain unchanged.

### Interrupts
*   **Definition:** Interrupts are requests from peripheral devices that cause the processor's current execution to complete and then fetch a new routine, known as an Interrupt Service Routine (ISR), for execution.
*   **Purpose:** In real-time applications, interrupts enable input-output devices to receive service without compromising the overall system task, allowing the main program to be suspended only when a device specifically requests service.
*   **Principle:** An interrupt signal informs the processor of an event, temporarily suspending the current program to execute a specific ISR for the device that generated the interrupt.
*   **8051 Interrupt Sources:**
    *   **Reset:** Hardware interrupt, ISR address 0000H, pin 9, used by the microcontroller (not the programmer), has auto clearance.
    *   **External Interrupt 0 (INT0):** Hardware interrupt, ISR address 0003H, pin 12, used by the programmer, has auto clearance.
    *   **External Interrupt 1 (INT1):** Hardware interrupt, ISR address 0013H, pin 13, used by the programmer, has auto clearance.
    *   **Timer Interrupt 0 (TF0):** Software interrupt, ISR address 000BH, no specific pin, used by the programmer, has auto clearance.
    *   **Timer Interrupt 1 (TF1):** Software interrupt, ISR address 001BH, no specific pin, used by the programmer, has auto clearance.
    *   **Serial Communication Interrupt:** Software interrupt, ISR address 0023H, no specific pin, used by the programmer, cleared by the programmer.
*   **Configuration Registers:** Interrupts are configured using the **Interrupt Enable (IE) register** and the **Interrupt Priority (IP) register**.
*   **General Programming Strategy:**
    1.  **Define Strategy:** Determine the number and type of interrupts required for the problem.
    2.  **Enable All (EA):** Set the `EA` (Enable All) bit of the IE register to 1, as it defaults to 0 (all interrupts disabled) upon power-up.
    3.  **Set Priorities:** Configure the IP register bits to define interrupt priorities.
    4.  **Define ISRs:** Write interrupt subroutines using the designated interrupt numbers (e.g., INT0 is 0, TF0 is 1).
*   **Timer Interrupt Programming:**
    1.  Ensure IE and ISRs are configured for the timer interrupt.
    2.  Configure the **TMOD register**.
    3.  Load the required timer or counter values into the lower and higher order bytes of the timer registers (TLx and THx).
    4.  Start the timer by setting the corresponding **TRx bit**.
    5.  The CPU monitors TF1 or TF0. When an overflow bit is set, the CPU suspends its current task and jumps to the ISR address (000BH for TF0, 001BH for TF1).
    6.  After the ISR, the controller resumes main program execution.
*   **External Interrupt Programming:**
    1.  Hardware interrupts are received at the **INT0 or INT1 pins**.
    2.  They can be configured for either **edge triggering** or **level triggering** (level triggering is the default).
    3.  In **level triggering**, INT pins receive a low-level signal for at least four machine cycles to indicate an interrupt.
    4.  In **edge triggering**, the IT1 or IT0 pins in the TCON register are enabled, and a falling edge on the port triggers the interrupt. IE0 and IE1 of TCON are enabled to prevent looping within the interrupt.
    5.  Common initial steps include setting `EA = 1` and defining the ISR with an interrupt number, which sets IE1 or IE0.
*   **Serial Interrupt Programming:**
    1.  Used during **serial data communication**, often involving the UART protocol.
    2.  The global interrupt enable bit (`EA`) and the serial enable bit in the IE register must be set.
    3.  The **SCON register** must be configured.
    4.  The subroutine for the serial interrupt is written with ISR reference number 4.
    5.  Within the ISR, the **RI (Receive Interrupt) or TI (Transmit Interrupt) flags** must be enabled.

### Programmable Interrupt Controller (PIC)
*   **Interrupt Control System Components:** The system includes the bit-configurable **Interrupt Enable (IE) register** and the **Interrupt Priority (IP) register**.
*   **Interrupt Handling:** Individual enables for external, timer, and serial interrupts are processed. A global enable/disable feature is available via the **`EA` (Enable All) bit** of the IE register, which acts as a series switch with individual enables.
*   **Priority Management:** The IP register functions as a switch to manage priorities, with the control system processing interrupts as a stack of ISRs according to defined priorities.
*   **Interrupt Control Models:**
    *   **Priority Arbitration Model:** Uses exclusive control registers for recording user-assigned priorities. A modular code handles the ordering of ISRs based on these priorities, providing user control over interrupts.
    *   **Chain Arbitration Model:** Devices are connected in series. The device at the beginning of the chain (Device 1) has the highest priority and directly interacts with the microcontroller.
    *   **Programmable Interrupt Controller (PIC) based Model:** All devices connect to a dedicated PIC IC. The user can program the PIC for flexible interrupt configuration based on its features.
*   **8259 PIC (Example for 8051):**
    *   **Internal Architecture:**
        *   **Control Logic Block:** Manages interrupt handling and acknowledgement with the microcontroller.
        *   **Interrupt Requester Register (IRR):** Devices that generate interrupts are connected here.
        *   **Priority Resolver:** Checks interrupt priorities using data from the Interrupt Mask Register (IMR).
        *   **Interrupt Mask Register (IMR):** Configurable by the user.
        *   **In-Service Register (ISR):** Records interrupt requests and communicates with the microcontroller.
    *   **Functional Architecture:**
        *   Commands from the microcontroller are accepted by the **Read/Write Control Logic**, which contains **Initialization Command Word (ICW)** and **Operation Command Word (OCW)** registers for storing commands and status.
        *   The 8259 can be configured in **master or slave mode** and supports cascade connections of slave devices.
        *   A **data bus** connects the PIC to the system bus, carrying data, control words, and status information.
        *   The Read/Write logic is connected via the **`RD bar`, `WR bar`, and `A0` signals** of the processor.

### Timer and Counter Programming
*   **Basics:**
    *   **Timers:** Built-in hardware capable of running independently, used for generating specific delays. They are configured for fixed frequencies and utilize the internal clock.
    *   **Counters:** Hardware mechanisms for counting events, typically receiving input from external sources.
*   **General Programming Model:**
    1.  **Configure Timer/Counter:** Set the **`C/T bar` bit in the TMOD register** (0 for Timer, 1 for Counter).
    2.  **Set Mode:** Use the **M0 and M1 bits of the TMOD register**.
    3.  **Enable/Disable:** Use a combination of the 8-bit TMOD and the **`TRx` bits of the TCON register**.
    4.  **Diagnose Overflow:** Check the status of the **`TF1` or `TF0` bits of the TCON register**.
*   **8051 Timer Specifics:**
    *   Has **two 16-bit timers**.
    *   Can generate delays (as timers) or count external events (as counters).
    *   Each timer can be accessed as two separate bytes.
    *   To repeat a timing process, the **TL and TH registers must be reloaded** with their original values, and the **TF (Timer Flag) must be cleared**.
*   **TMOD Register Configuration:**
    *   An 8-bit register, configurable bit-wise.
    *   The **lower nibble is for Timer 0**, and the **upper nibble is for Timer 1**.
    *   **Examples:**
        *   Timer 0, Mode 1: `MOV TMOD, #01H`.
        *   Timer 0, Mode 2: `MOV TMOD, #02H`.
        *   Timer 1, Mode 2: `MOV TMOD, #20H`.
        *   Timer 1, Mode 1: `MOV TMOD, #10H`.
*   **General Procedure for Creating Delays with Timers:**
    1.  Set the timer mode using the TMOD register.
    2.  Load the corresponding values for the lower and higher-order bits of the timer register.
    3.  Start the timer.
    4.  Check for timer overflow.
    5.  Stop the timer.
    6.  Clear the overflow flag for the next round.
    7.  Repeat from step 2.
*   **Delay Calculation Methodology (Example for 32.55 µs delay):**
    *   Given frequency (e.g., 11.0592 MHz) and required delay.
    *   **Clock time period (T)** is calculated as **1 / (Oscillator_Frequency / 12)**. For 11.0592 MHz, this is 1.085 microseconds.
    *   The **number of counts** for the timer is obtained by dividing the desired delay by the clock time period.
    *   The **load value for the timer registers** (THxTLx) is calculated as **FFFFH - (Number_of_Counts)**.
*   **Square Wave Generation:** A square wave can be generated by complementing a port bit (e.g., `CPL P1.5`) within a delay loop.
*   **Counter Programming Process Flow:**
    1.  Configure the counter by setting the **C/T bit as 1 in TMOD**.
    2.  Confirm the timer number and mode.
    3.  Set up the external timer pin as required.
    4.  Start the counter.
    5.  Respond to the counter values (can be interrupt-based or not).
    6.  Check for overflow.
    7.  Stop the counter on overflow.
    8.  Clear the overflow flag.
    9.  Repeat from step 4.
*   **Example: Digital Clock (Count 60 Seconds):**
    *   Uses Timer 1 in Mode 2 as a counter.
    *   The value to be counted (60 decimal or 3CH) is loaded into TL1.
    *   TMOD value for Timer 1 in counter mode 2 is 60H (01100000B).
    *   An external input (e.g., P3.5) feeds the count, and the count value can be sent through P2 for display.
    *   The counter starts, checks for overflow (after 60 seconds), increments a minute count, stops, clears overflow, and repeats.
*   **Example: Counting Events with Interrupt:**
    *   Timer/Counter 1 can be used as an interrupt-driven counter for a specific number of events (e.g., 20,000).
    *   The main module configures the mode, loads timers, starts the timer, and maintains an active loop.
    *   The ISR (Interrupt Service Routine) clears the counter, sets or reverses a designated bit (e.g., P1.5), and returns.

### Input Port Programming
*   **Internal Architecture Overview:**
    *   Input data from the pins is stored in **buffer registers**.
    *   Input pins are connected through hardware like switches or TTL gates.
    *   **Circuitry per Pin:** For Ports 1, 2, and 3, if the input signal is 0, it creates a short circuit path, resulting in a 0 being stored in the I/O register. If the input is 1, it passes through a buffer and is stored in the register. This circuit is common for Ports 1, 2, and 3.
    *   **Port 0 Specifics:** Port 0 **lacks an internal pull-up resistor**, thus requiring an **external pull-up resistor** for I/O operations. It also has a dual function, supporting address and data signals during external memory interfacing.
*   **Buffer Register Addresses:**
    *   Port 0: **80H**.
    *   Port 1: **90H**.
    *   Port 2: **A0H**.
    *   Port 3: **B0H**.
*   **Conventional Programming Procedure (Input Mode):**
    *   **Default State:** After a microcontroller reset, **all ports are in input mode** by default.
    *   **Manual Configuration:** If not immediately after reset, all bits of the target port must be set to 1 to configure them as input ports.
    *   **Port 0 Requirement:** If Port 0 is used as an input, an **external pull-up resistor must be connected**.
    *   **Full Content Reading:** The entire content of a port can be read into the accumulator using the instruction **`MOV A, PX`** (where X can be 0, 1, 2, or 3).
    *   **Bitwise Reading and Branching:**
        *   **`JNB PX.N L1`**: Jumps to `L1` if the specified bit `PX.N` is 0 (no bit).
        *   **`JB PX.N L1`**: Jumps to `L1` if the specified bit `PX.N` is 1 (bit is set).
        *   **`MOV C, PX.N`**: Moves the status of a specific port bit (`PX.N`) to the Carry flag (C). `N` refers to D0 through D7.
    *   **Read-Modify-Write Operations:** 8051 offers instructions that read the input port register, modify its contents, and then write the result back to the same port register.
*   **Example: Reading Name and Date of Birth:**
    *   **Problem:** Read a candidate's name and date of birth from Port 1 with a delay, storing them in R0 and R1.
    *   **ALP Steps:**
        1.  `MOV A, #0FFH`: Sets accumulator to all ones.
        2.  `MOV P1, A`: Configures all pins of Port 1 as input.
        3.  `MOV A, P1`: Reads the content of Port 1 (name) into the accumulator.
        4.  `MOV R0, A`: Stores the name from accumulator into R0.
        5.  `CALL delay`: Introduces a delay.
        6.  `MOV A, P1`: Reads the content of Port 1 (date of birth) into the accumulator.
        7.  `MOV R1, A`: Stores the date of birth from accumulator into R1.
*   **Example: Automated Water Level Monitoring:**
    *   **Problem:** Connect a low-level sensor to P1.0 and a high-level sensor to P1.1. Turn a motor ON (Port 2 output FFH) when water is low, and OFF (Port 2 output 00H) when water reaches a high level. Include delays between sensor readings.
    *   **Algorithm:** Sense low level -> Turn motor ON -> Sense high level -> Turn motor OFF.
    *   **ALP Logic:**
        1.  `MOV A, #0FFH`, `MOV P1, A`: Assign Port 1 as an input port.
        2.  `L0: JNB P1.0, L0`: Loops until P1.0 (low-level sensor) becomes 1 (water low).
        3.  `MOV A, #0FFH`, `MOV P2, A`: Turns the motor ON (Port 2 output FFH).
        4.  `CALL delay`: Introduces a delay.
        5.  `L1: JNB P1.1, L1`: Loops until P1.1 (high-level sensor) becomes 1 (water high).
        6.  `MOV A, #00H`, `MOV P2, A`: Turns the motor OFF (Port 2 output 00H).
        7.  `CALL delay`: Introduces a delay.
        8.  `SJMP L0`: Jumps back to repeat the process.

### Output Port Programming
*   **Device Choices:** 8051 can connect to end devices like **LEDs, DC motors, 7-segment displays, and LCDs** through its four output ports (P0, P1, P2, P3). These connections are made via 8-bit output port registers or drivers.
*   **LED Display Setup:** For LED displays, LED anodes are connected to VCC, and Port 0 outputs are connected to the cathodes via drivers. LEDs emit light when forward biased by the output signal.
*   **Internal Circuitry (Port 0):** The internal circuitry for Port 0 indicates that output is enabled if a 0 is provided. It has a read latch option. As with input operations, **Port 0 requires an external pull-up resistor** for output operations.
*   **Example: RFID-based Automatic Toll Gate:**
    *   **Problem:** An RFID tag's payment status is on Port 0.5 (1=balance, 0=no balance). If valid (P0.5=1), Port 2.0 sends a high signal (gate opens); if invalid (P0.5=0), Port 2.0 sends a zero signal (gate remains closed).
    *   **ALP Logic:**
        1.  `L0: MOV C, P0.5`: Moves the value of Port 0.5 to the Carry flag.
        2.  `JC L1`: If the Carry flag is set (1, valid payment), jumps to L1.
        3.  `MOV P2, #00H`: If no carry (0, invalid payment), sets Port 2 to 00H (gate closed).
        4.  `SJMP L0`: Jumps back to L0 to repeat the check.
        5.  `L1: MOV P2, #0FFH`: If Carry is 1, sets Port 2 to FFH (gate open).
        6.  `SJMP L0`: Jumps back to L0 to repeat.
*   **Example: Roadmap System (Vehicle Classification):**
    *   **Problem:** Characterize vehicles (public, private, heavy) via input (Port 0) and control an 8-LED display (Port 2) based on vehicle type.
    *   **Output Conditions for Port 2:**
        *   **Public Transport:** All 8 LEDs glow (output FFH).
        *   **Private Transport:** First four nibbles glow (output F0H).
        *   **Heavy Vehicle Transport:** Last four nibbles glow (output 0FH).
    *   **ALP Logic (Partial implementation shown in source):**
        1.  Initialize R0 with FFH (for public), R1 with F0H (for private), R2 with 0FH (for heavy).
        2.  `L0: MOV A, P0`: Reads input from Port 0.
        3.  `CJNE A, ATH, L1`: Compares A with a predefined value (`ATH` likely represents the code for public transport). If not equal, branches to L1.
        4.  `MOV A, R0`, `MOV P2, A`: If equal, outputs FFH to Port 2 (public transport indication).
        5.  `L1: CJNE A, 40H, L2`: Compares A with 40H (likely for private transport). If not equal, branches to L2.
        6.  `MOV A, R1`, `MOV P2, A`: If equal, outputs F0H to Port 2 (private transport indication).
        7.  `L2: CJNE A, 20H, L3`: Compares A with 20H (likely for heavy vehicle transport). If not equal, branches to L3.
        8.  `MOV A, R2`, `MOV P2, A`: If equal, outputs 0FH to Port 2 (heavy vehicle indication).
        9.  `L3: SJMP L0`: Jumps back to L0 to repeat the process.
