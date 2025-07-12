---
layout: post
title:  "Microcontroller and Industrial Applications module 2"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---



The 8051 microcontroller system has specific architectures, capabilities, and instruction sets for memory management, serial communication, and interrupt handling.

### Microcontroller Architecture and Memory

*   **8051 Memory Organization**:
    *   The 8051 has **128 bytes of internal RAM**, **128 bytes of Special Function Registers (SFRs)**, and **4 kilobytes of internal ROM**.
    *   **External memory**, including both RAM and ROM (EPROM), can be added.
    *   The **SFR space (128-256)** overlaps with memory.
    *   On-chip instruction or program memory types include ROM, EPROM One Time Programmable (OTP), and EEPROM.
    *   The 8051 uses a **Harvard architecture**, where program and data memory are separate and can be interfaced externally. This differs from the Von Neumann architecture used by 8085.
    *   On-chip memory may be expanded with additional memory based on the status of the **Auxiliary RAM Disable (ARD) bit** in the SFR.
        *   If ARD is 0, lower addresses 0-64KB will be auxiliary memory.
        *   If ARD is 1, the entire 0-64KB address is dedicated to external ROM.

*   **External Memory Interfacing**:
    *   **Port 0 and Port 1** are utilized to carry the 16-bit address required for external memory.
    *   **Port 0 is a multiplexed port**, transmitting both address and data signals.
    *   An external memory connection necessitates an interface component, such as the **74LS373 latch**, and the **Address Latch Enable (ALE)** control signal for feasibility.
    *   External ROM (program memory) can have a capacity of 64 kilobytes.
    *   The **Program Store Enable (PSEN)** signal is required for external ROM interface, serving a similar function to the output enable signal in 8085 memory interfaces.
    *   External RAM also supports expansion, allowing both RAM and EPROM with a capacity of 64 kilobytes to be interfaced.
    *   Control signals differ for memory types: **ROM requires PSEN, while RAM requires RD bar and WR bar signals**.
    *   Schematic designs often incorporate jumpers to enable configuration for either 64 kilobyte or 32 kilobyte memory ICs based on specific requirements.
    *   **Memory Mapping Logic**:
        *   Similar to the 8085 microcontroller.
        *   **Absolute decoding** utilizes all higher-order address bits for decoding and device selection, requiring specific hardware. This method is costly but suitable for larger systems, preventing multiple addresses.
        *   **Partial decoding** is also a principle.
    *   **External Memory Access Modes**: Configured by the state of the **EA bar signal**.
        *   In **Mode 1**, with EA bar connected to VCC, the 8051 shares and uses 4 kilobytes of internal memory and 60 kilobytes as external memory.

*   **Memory Interfacing Design Examples**:
    *   **Two 4 KB External RAMs:**
        *   Required address bits for 4 KB are **12 (A0 to A11)**.
        *   Free address bits are A12, A13, A14, A15.
        *   Memory mapping: RAM1 from 0000 to 0FFF and RAM2 from 1000 to 1FFF.
        *   **A12 is used as a Chip Select (CS) signal** via a suitable decoding circuit, such as a NOT gate.
        *   A0 to A11 are connected directly to both RAM1 and RAM2. A12 is connected directly to RAM1 and through an inverter to RAM2. A13 to A15 bits are combined to enable the memory IC. WR bar and RD bar control signals facilitate data sharing.
    *   **8 KB Data Memory and 8 KB Program Memory:**
        *   Required address bits for 8 KB are **13 (A0 to A12)**.
        *   Memory mapping: RAM1 from 2000H to 3FFFH and ROM1 from 4000H to 5FFFH.
        *   A0 to A12 bits are connected directly.
        *   **A13 and A14 are used for Chip Select (CS) through decoding**.
        *   **A15 is configured as an enabling signal** for both ICs.
        *   A **2-to-4 decoder** is used with A13 and A14 as inputs, where D1 and D2 outputs serve as CE bar for the ICs. A15 enables the decoding functions.
        *   ROM uses the PSEN bar signal, while RAM uses RD bar and WR bar signals.

### Timers and Counters

*   **Purpose**: Timers and counters are essential for **automating real-life applications** that require time settings, such as robot arm structures in manufacturing or digital thermometers for temperature capture and observation duration.
*   **Principles**: Timers are counters configured to count system pulses, typically utilizing flip-flops.
*   **Basic Requirements**: Timers facilitate events, timestamping, delay generation, baud rate setting, interrupt triggering, and Pulse Width Modulation (PWM) generation.
*   **Functional Blocks**:
    *   The **control block** is a major component.
    *   Timers can connect directly to the **system clock** or use an **external pulse/event crystal connection** through a prescaler.
    *   The **prescaler** divides the applied multiplexer input clock and feeds it to the counter, extending the range of timers. TMOD register bits support prescale value configuration.
    *   The **counter range** is determined by the input from the modular register.
*   **Features**:
    *   The default timer mode uses the system clock, and the counter value is influenced by the crystal frequency.
    *   **Input capture and output provisions** allow for external event measurement and timestamping.
    *   **PWM features** are useful as digital-to-analog converters and in applications like car anti-lock brake systems.
    *   **Watchdog timers** are available on some microcontrollers, enabling endless loop code execution during hardware issues and providing event occurrences in unattended embedded systems.
    *   A **pulse accumulator feature** is also available.

*   **8051 Timer Modes**:
    *   **Mode 0 (13-bit Timer/Counter)**:
        *   Configures the timer register as a **13-bit register** (5 bits from TL and 8 bits from TH).
        *   Uses a **prescaler divided by 32**.
        *   The TF1 or TF0 flag is set upon overflow.
        *   Timer/counter operation is enabled when TRx = 1 and either GATE = 0 or INTx bar = 1.
        *   The sequence of operation involves TL incrementing, impacting TH, which impacts TF, and TF impacting the interrupt.
    *   **Mode 1 (16-bit Timer/Counter)**:
        *   The primary distinction from Mode 0 is that the timer register is configured as a **16-bit length** register.
    *   **Mode 2 (8-bit Timer/Counter with Auto-Reload)**:
        *   Operates as an **8-bit timer or counter** with an **automatic reloading facility**.
        *   TL1 (8 bits) is used for counting; upon overflow, the value of TH1 (preset by the program) is automatically pushed to TL1.
    *   **Mode 3 (Two 8-bit Counters - Timer 0 only)**:
        *   Configures **two 8-bit register counts using TL0 and TH0**.
        *   Only Timer 0 is utilized in this mode, while Timer 1 maintains its count.
        *   TR1 and TF0 status bits of Timer 1 control TH0.
        *   Timer 1 can be turned off or used by the serial port for baud rate generation.
    *   **TCON (Timer Control) and TMOD (Timer Mode) Registers**: These special function registers control timer operations and modes in the 8051.

### Serial Communication

*   **Purpose**: Serial communication offers a cost-effective method for establishing communication between processors, especially when parallel data transfer is not feasible due to bandwidth requirements or distance. It transmits a single bit at a time.
*   **Principles**:
    *   An 8-bit data is loaded into a shift register at the transmitting end, operating in parallel-to-serial mode.
    *   At the receiving end, the serial data is reconverted into a parallel pattern.
    *   Key design components for successful serial communication include **synchronization, protocol, and supporting hardware features**.
*   **Synchronization**:
    *   Shift registers at both ends require suitable clocks.
    *   Mismatch in speed (frequency and phase) between transmitting and receiving shift registers can lead to unsuccessful transmission.
    *   **Synchronous Model**: A shifted clock is sent on a dedicated connection to the receiver, creating a two-wire link (data and clock). This adds cost and is suitable for devices in close proximity.
    *   **Asynchronous Model**: Used when devices are far apart, with individual clocks at both ends. Extra bits such as **parity, start, and stop bits** are added to the data to manage speed mismatches.
*   **Protocol**:
    *   A protocol is designed to ensure shared synchronization methods and prior knowledge of transmitter operation for the receiving device.
    *   Protocol components include **bit rate, synchronous/asynchronous transmission type, parity type, frame size, and simplex/duplex transmission**.
    *   Standard serial I/O protocols include **Universal Asynchronous Receiver Transmitter (UART)** for asynchronous mode, and **Universal Synchronous/Asynchronous Receiver Transmitter (USART)**. The 8051 microcontroller has an inbuilt USART.

*   **UART (Universal Asynchronous Receiver Transmitter)**:
    *   A dedicated hardware component for serial communication, often referred to as a protocol due to specific rules.
    *   Its internal architecture includes transmitting and receiving shift registers.
    *   Being asynchronous, the transmitter and receiver operate with independent clocks.
    *   **Synchronization in UART** relies on the **falling edge of a pulse to indicate the start bit**.
    *   The receiver uses **oversampling** (sampling the RXD line 'S' bits per second) to compensate for clock frequency drift. The start bit is verified by confirming all 'S' samples are '0', and all data bits are sampled 'S' times before transmission concludes with the stop bit.
    *   **Standard UART Frame Structure**:
        *   Begins with a **start bit** (high-to-low signal, single bit) for synchronization.
        *   Followed by **data bits** (typically 5-9).
        *   An optional **parity bit** (even or odd) can be included.
        *   Ends with **one or two stop bits** (high value bits).
        *   Baud rates generally range from 9600 to 115,200 bits per second.
        *   Data format is specified as **D {E/O/N} S**, where D is data bits, E/O/N denotes parity (Even/Odd/None), and S is stop bits.
    *   **Baud Rate Design**: The system clock, with the aid of counters, determines the baud rate. A prescaler scales down the periodic clock signal by a desired value 'S'.
    *   **Example Calculation**: For an 8 MHz clock with S=10 oversampling, the baud rate is `(8/10) * (1/2) * 10^6 = 400 Kbps`.
    *   **8051 Baud Rate Calculation Example**: To interface a 13.56 MHz RFID reader via UART at 9600 baud rate with an 8051 (crystal frequency 11.0592 MHz):
        *   Timer 1 is set to mode 2 with 8-bit auto-load.
        *   Timer clock frequency `f = 11.0592 MHz / 12 / 32 = 28800 Hz`.
        *   The required oversampling value `n = (1/9600) / (1/28800) = 28800 / 9600 = 3`.
        *   Therefore, the TH1 register of Timer 1 is loaded with `-3` (which is `FDH` in two's complement).

*   **8051 Serial Communication Elements**:
    *   **SBUF (Serial Buffer Register)**: Holds data during communication.
    *   **SCON (Serial Control Register)**: An SFR for controlling data communication. Its bits include:
        *   **SM0, SM1**: Select serial I/O mode (00=Mode0, 01=Mode1, 10=Mode2, 11=Mode3).
        *   **SM2**: Multiprocessor communication bit.
        *   **REN**: Enables receiving function.
        *   **TB8**: Transmitted bit-8.
        *   **RB8**: Received bit-8.
        *   **TI**: Transmit interrupt flag.
        *   **RI**: Receive interrupt flag.
    *   **PCON (Power Control Register)**: An SFR that controls the data rate. It is not bit addressable. Its bits include:
        *   **SMOD**: MSB of PCON, used for serial baud rate.
        *   GF1, GF0: General purpose flags.
        *   PD: Power down bit.
        *   IDL: Idle mode bit.
    *   **Receiving Pin**: Port 3.0 (RXD).
    *   **Transmitting Pin**: Port 3.1 (TXD).

*   **8051 Serial I/O Modes**:
    *   **Mode 0 (Shift Register Mode)**: SM0=0, SM1=0. Uses TXD for shift clock and RXD for data. Transmission and reception occur at a fixed rate: `crystal frequency / 12`.
    *   **Mode 1 (UART)**: SM0=0, SM1=1. Uses start and stop bits, with SBUF acting as a 10-bit full-duplex receiver/transmitter. Baud rate is computed by Timer 1.
    *   **Mode 2**: SM0=1, SM1=0. Transmits 11 bits (9-bit data, one start, one stop bit). The ninth bit is from SCON's TB8 bit. Baud rate `F_baud2 = (2^SMOD / 64D) * oscillator frequency`. SM2 bit enables selective communication with receivers.
    *   **Mode 3 (UART)**: SM0=1, SM1=1. Uses an 11-bit data format (9 data bits, one start, one stop bit). Baud rate determined by Timer 1, and can be doubled using the SMOD bit (`F_baud2 = (2^SMOD / 32D) * Timer 1 overflow frequency`).

### Interrupts

*   **Concept**: Interrupts are responses to events, enabling the microcontroller to execute specific subroutines (Interrupt Service Routines or ISRs) in reaction to internal task statuses or external device behaviors. This allows for real-time programming by calling for processor attention only when an event occurs.
*   **Types of Interrupts (by Source)**:
    *   **Internal Interrupts**: Generated by internal 8051 operations (e.g., Timer 0/1 overflows, serial port data reception/transmission).
    *   **External Interrupts**: Generated by external sources (e.g., INT0 bar, INT1 bar pins receiving high-level input).
*   **Interrupt Management in 8051**: Managed using the **Interrupt Enable (IE), Interrupt Priority (IP), and Timer Control (TCON) Registers**.
*   **Interrupt Enable (IE) Register**: An 8-bit SFR that controls interrupt authorization.
    *   **IE.7 (EA - Enable All)**: A global bit that permits (1) or disables (0) all interrupts.
    *   IE.6 and IE.5 (ET2) are not implemented or reserved for future use.
    *   **IE.4 (ES)**: Serial port interrupt enable.
    *   **IE.3 (ET1)**: Timer 1 overflow interrupt enable.
    *   **IE.2 (EX1)**: External interrupt 1 enable.
    *   **IE.1 (ET0)**: Timer 0 overflow interrupt enable.
    *   **IE.0 (EX0)**: External interrupt 0 enable.
*   **Five 8051 Interrupts (Hardware/Software)**:
    *   **External**: INT0 bar, INT1 bar.
    *   **Internal**: Timer Flag 0 (TF0), Timer Flag 1 (TF1), Serial Port Interrupt (RI or TI).
        *   TF0 is generated when Timer 0 overflows.
        *   TF1 is generated when Timer 1 overflows.
        *   RI becomes one when data is received in the serial port.
        *   TI becomes one when a byte is ready for serial port transmission.
*   **Interrupt Vector Table (IVT)**:
    *   Maps interrupts to their corresponding ISRs.
    *   When an interrupt occurs, the controller preserves the Program Counter (PC) contents and directs the PC to the suitable memory location in the IVT.
    *   The 8051 IVT includes six interrupts:
        *   **Reset**: 0000H (Non-Maskable Interrupt, non-programmable).
        *   **INT0**: 0003H.
        *   **TF0**: 000BH.
        *   **INT1**: 0013H.
        *   **TF1**: 001BH.
        *   **Serial Communication (RI/TI)**: 0023H.
*   **Interrupt Control Principles**:
    *   Programs must enable interrupts, inhibit specific interrupts based on processor conditions, and monitor interrupt status.
    *   **Global Interrupt Enable (EA bit)** is used for handling multiple interrupts. When an interrupt is sensed, global IE can be disabled to prevent further requests.
    *   **Non-Maskable Interrupts (NMIs)**: These interrupts must be attended to immediately and cannot be ignored. The **8051's Reset is an NMI**.
    *   **External Interrupt Triggering**: Can be configured as **edge-triggered** or **level-triggered** by the programmer.
*   **Interrupt Priority (IP) Register**:
    *   An 8-bit, bit-addressable SFR in the 8051 that manages priority among its six interrupts.
    *   **PX0**: Priority for External Interrupt 0 (1=highest, 0=lowest).
    *   **PT0**: Priority of Timer 0 overflow interrupt.
    *   **PX1**: Priority of External Interrupt 1.
    *   **PT1**: Priority of Timer 1 overflow interrupt.
    *   **PS**: Priority of Serial port interrupt.
    *   PT2 is reserved; IP6 and IP7 are not implemented.
*   **Interrupt Priority Models**:
    *   **Nested Interrupts**: A higher-priority interrupt arriving during a lower-priority ISR will interrupt the running ISR for immediate execution of the new event's ISR.
    *   **User Designed Priorities**: Users can configure priorities based on application needs.
    *   **Current Trends**: Processors like RISC-V support **predictable interrupts** to avoid ISR-Task Priority Inversion (ITPI) and use **Platform-Level Interrupt Controllers (PLIC)** for managing external interruptions in multi-threaded architectures.

### Instruction Set Architecture (ISA)

*   **Definition**: ISA forms an abstract layer and interface between microcontroller hardware and software. It defines instruction fields and data paths for output generation.
*   **Components**: ISA covers memory, ALU, control unit (CU), and I/O devices. It dictates program operations, instruction encoding, and storage requirements, serving as a design framework for both hardware and software developers.
*   **Reference Guide**: ISA provides programmers with a reference guide on instruction sets, addressing modes, data types, registers, exception handling, memory management, multithread support, and power management.
*   **8051 ISA Model Elements**:
    *   Resembles a **CISC (Complex Instruction Set Computer) system**.
    *   Features **eight addressing modes** and **five instruction types**.
    *   Utilizes an **Opcode-operand instruction format** with four operand types.
    *   Follows the **Harvard architecture model** for memory organization.
    *   RAM (data memory) includes SFRs, register banks, and external RAM segments.
*   **Microarchitecture**: The hardware implementation of an ISA; multiple microarchitectures can exist for a single ISA. ISA also specifies generic CPU design elements like ALU, CU, and registers as microprograms.

*   **CISC vs. RISC Comparison**:
    *   **CISC**: Characterized by complex instructions, smaller static code size, a higher number of addressing modes, variable-length instructions, an emphasis on hardware, complex instruction encoding, limited general-purpose registers, specialized instructions, and the ability to incorporate load and store operations into other instructions. Examples include x86, VAX, and Z80 microcontrollers.
    *   **RISC**: Features simple, reduced instructions, larger static code size, a limited number of addressing modes, fixed-length instructions, an emphasis on software, simple instruction encoding, a large number of general-purpose registers, avoidance of specialized instructions, and independent load and store instructions. Examples include ARM, Alpha, MIPS, SPARC, and PowerPC.
    *   Current trends indicate that the distinction between CISC and RISC has become very thin, with CISC models often implemented as combinations of RISC modules.
*   **Current Trends in ISA**:
    *   **Very Long Instruction Word (VLIW) processors**: Their architecture breaks down complex program instructions into smaller components for parallel execution.
    *   **ISA Simulation**: Utilizes ISA simulators (e.g., Instruction Set Simulator or ISS) to interpret, statically compile, or dynamically compile and simulate ISA behavior.

### Addressing Modes of 8051

*   **Direct Addressing Mode**: The operand is the **direct address of the data**. Possible choices include SFR and internal data RAM addresses.
    *   Example: `MOV A, P2` (Port 2 contents to Accumulator), `MOV B, 40H` (contents of RAM address 40H to B register).
*   **Indirect Addressing Mode**: A register specified in the instruction contains the **address of the operand**. The address can be internal or external RAM. The 16-bit address can be referred to by the **Data Pointer Register (DPTR)**.
    *   Example: `MOV @R1, A` (contents of A to address pointed by R1), `MOV B, @DPTR` (contents of external data address pointed by DPTR to B register).
*   **Register Addressing Mode**: Directly accesses the **register banks (R0 to R7)**. Register selection is done via two bank selection bits in the Program Status Word (PSW).
    *   Example: `MOV R1, B` (contents of B register to R1 register).
*   **Relative Addressing Mode**: Instructions are indicated by a **relative value** that is consolidated with the Program Counter (PC) contents to identify the operand. This mode is used for specific instructions, and the destination address must be within -128 to +127 bits of the current PC.
    *   Example: `JNC NEXT` (jump if no carry, relative to current PC).
*   **Immediate Constant Addressing Mode**: The operand is an **8-bit or 16-bit constant value explicitly specified within the instruction**. The destination can be a register.
    *   Example: `SUB A, #070H` (subtract 070H from accumulator), `MOV DPTR, #01ABH` (move 01ABH to DPTR).
*   **Indexed Addressing Mode**: Useful for accessing operands from a **lookup table in program memory**. The DPTR holds a 16-bit base address, and the accumulator holds an index value; the effective address is computed by summing these values. `MOV` and `JMP` instructions commonly use this mode.
    *   Example: `MOVC A, @A+DPTR` (moves a byte from code/program memory to the accumulator, at an address calculated by A+DPTR; `MOVC` means "move constant"). Another example is `MOVC A, @A+PC`.
*   **Special Addressing Modes in Other Microcontrollers**:
    *   **MSP430**: Symbolic mode (easy-to-read code) and absolute mode (direct memory access).
    *   **ARM**: Pre-indexed and post-indexed modes (register indirect with offset).
    *   **AVR**: Direct program addressing (direct subroutine calls).
    *   **PIC**: Memory operand addressing mode (comprehensive of direct and indirect).

### Data Transfer and Logical Instructions of 8051

*   **Data Transfer (Movement) Instructions**:
    *   **Internal Memory (RAM/SFRs)**:
        *   The general format is **`MOV destination, source`**.
        *   Data can be transferred between two RAM locations or two SFRs.
        *   SFRs are accessed by direct addressing, and RAM can be accessed by indirect addressing.
        *   The accumulator is not always involved in these transfers.
        *   Examples include `MOV A, direct address`, `MOV Rr, direct address`, and `MOV address1, address2`.
        *   **Stack Memory**: `PUSH` and `POP` instructions are exclusively for stack memory, which is part of the internal RAM assigned by the programmer. The Stack Pointer (SP) is loaded with the RAM address. Stack operations follow direct addressing. In 8051, the stack generally works in an upward direction, where `PUSH` operation loads contents into `SP+1` and increments SP to `SP+2`. (Note: Source text also mentions `SP-1` and `SP-2` for PUSH, which is the typical 8051 behavior, suggesting a slight contradiction in the source).
    *   **Exchange Instructions (`XCH`, `XCHD`)**: Exchange the contents of the source and destination. The `XCHD` instruction allows exchanging only the lower nibble. All addressing modes except immediate are feasible for exchange instructions.
    *   **External Memory Access**:
        *   Always **indirect**.
        *   Registers Rr and DPTR (data pointer) hold the external memory address.
        *   Rr can access 256 kilobytes of memory, while DPTR can access 64 kilobytes.
        *   These instructions typically consume two microseconds with a 12 MHz clock.
        *   Contents can only be transferred to the accumulator when interacting with external memory.
    *   **Lookup Table Data (Program ROM)**:
        *   Pre-programmed data permanently stored in program ROM can be read into the accumulator using indirect addressing.
        *   Instructions include **`MOVC A, @A+DPTR`** and **`MOVC A, @A+PC`**. `MOVC A, @A+DPTR` copies a code byte from ROM (address computed as accumulator content plus DPTR content) into the accumulator. `MOVC` mnemonic stands for "move constant".

*   **Logical Instructions**: The 8051 provides four main logical instructions: AND, OR, NOT, and EXOR. A single instruction, `CPL`, is available for complementing the accumulator or the carry bit.
    *   **AND (`ANL`)**: Performs a bitwise AND operation. The accumulator contents can be ANDed using all four addressing modes. The result is stored back in the accumulator. No flags are affected unless the Program Status Word (PSW) is used. Results can also be directly pushed to a RAM memory location.
    *   **OR (`ORL`)**: Performs a bitwise OR operation. Similar to `ANL`, it supports all four addressing modes for logical manipulation of internal RAM and SFRs.
    *   **XOR (`XRL`)**: Performs a bitwise XOR operation. It also supports all four addressing modes.
    *   **Complement (`CPL`)**: Complements the given operand. These instructions utilize register and indirect addressing modes.
