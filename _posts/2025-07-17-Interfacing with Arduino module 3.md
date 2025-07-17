
The provided information describes Arduino software libraries, specifically the EEPROM and Wire (I2C) libraries, along with fundamental bitwise operations essential for advanced data handling in microcontroller programming.

### Arduino Libraries (General)

Arduino boards are supplied with software libraries that are crucial for their usability. These libraries simplify hardware interaction by providing predefined functions, allowing developers to use hardware components without understanding intricate low-level details. This capability enables individuals without extensive hardware knowledge to develop Internet of Things (IoT) devices.

Libraries facilitate control and observation of devices connected to microcontrollers. While simple devices might use basic functions like `analogRead()`, `analogWrite()`, `digitalRead()`, and `digitalWrite()`, more complex devices require dedicated libraries. Libraries are available for both internal microcontroller components (e.g., EEPROM, I2C communication, pulse width modulation (PWM) logic, timers) and external hardware, such as shields. Third-party libraries also exist.

### EEPROM Library

The EEPROM library provides functionality to access the Electrically Erasable Programmable Read-Only Memory (EEPROM) embedded within the ATMega328 processor on Arduino Uno boards.

*   **Characteristics of EEPROM**:
    *   **Non-Volatile**: EEPROM retains its data even when power is removed, similar to disk or flash memory.
    *   **Capacity**: On the ATMega328 processor, only 1 kilobyte (1024 bytes) of EEPROM is available, with addresses ranging from 0 to 1023.
    *   **Byte-Addressable**: EEPROM is more flexible than flash memory as it allows writing a single byte at a time. In contrast, flash memory typically requires writing in blocks, which can be inefficient for single-byte changes.
    *   **Write Cycles**: EEPROM supports a significantly higher number of write cycles (e.g., hundreds of thousands) compared to flash memory (tens of thousands), though less than disk drives. Repeated writes to the same address can eventually wear out the memory.
    *   **Application**: EEPROM is suitable for storing persistent settings or variables that need to be preserved across power cycles, analogous to saving small files on a regular file system.

*   **Accessing EEPROM with the Library**:
    *   To use the EEPROM library, `#include EEPROM.h` must be added at the top of the Arduino sketch.
    *   **`EEPROM.read(address)`**: This function reads a single byte from the specified `address` (an integer between 0 and 1023) and returns its content.
    *   **`EEPROM.write(address, data)`**: This function writes a single `byte` of `data` to the specified `address` (an integer between 0 and 1023). If the `data` argument is a multi-byte type (e.g., a 2-byte integer on Arduino), `EEPROM.write` will only store the least significant byte and ignore any higher bytes.
    *   **Writing Multi-Byte Data**: Since EEPROM is byte-addressable, multi-byte data (like a 2-byte integer) must be written one byte at a time. A common approach, known as **Little Endian ordering**, involves writing the least significant byte to the lowest memory address and the most significant byte to the next sequential address.

### Bitwise Operations (Masking and Shifting)

Bitwise operations are fundamental for manipulating specific subsets of bits within a larger piece of data, which is frequently required in IoT device programming, especially when dealing with data types larger than the microcontroller's native bit-width (e.g., a 16-bit integer on an 8-bit Arduino).

*   **Masking**:
    *   **Purpose**: To isolate and focus on a specific subset of bits within a number by setting all other bits to zero.
    *   **Mechanism**: A **mask** is created with `1`s in the bit positions of interest and `0`s in positions to be ignored. A **bitwise AND operation** (represented by a single ampersand `&`) is then performed between the original number and the mask. The result of a bitwise AND is `1` only if both corresponding input bits are `1`; otherwise, it's `0`. This effectively "zeroes out" any bits in the original number that correspond to a `0` in the mask. For example, to extract the low byte of a 16-bit number, a mask of `0x00FF` (binary `0000000011111111`) would be used.

*   **Right Shift (`>>`)**:
    *   **Purpose**: To extract higher-order bits of a number by moving them to lower-order bit positions.
    *   **Mechanism**: The `>>` operator shifts the bits of a number to the right by a specified number of positions. Zeroes are introduced from the left (most significant bit side).
    *   **Application**: For instance, to obtain the high byte of a 16-bit number, the number can be right-shifted by 8 bits (`bigData >> 8`). This moves the original high 8 bits into the low 8 bit positions, while the original low 8 bits are discarded, and the new high 8 bits become zeros.

### I2C (Wire) Library

The Wire library supports I2C (Inter-Integrated Circuit) communication, a serial and synchronous protocol used to enable microcontrollers to communicate with other integrated circuits or chips.

*   **I2C Protocol Characteristics**:
    *   **Serial and Synchronous**: Data is transmitted serially over a single data line (SDA), saving pins but resulting in slower transmission compared to parallel methods. Communication is synchronous, requiring all connected devices to share a common clock signal (SCL) to ensure proper timing and synchronization.
    *   **Two Wires**: I2C exclusively uses two dedicated wires: **SDA (Serial Data Line)** for data transfer and **SCL (Serial Clock Line)** for synchronization.
    *   **Open Drain Lines**: Both SDA and SCL lines are connected to the power supply through large resistors, ensuring they are **pulled high by default** when no device is actively transmitting. Any connected device can pull these lines low, and if no device is actively driving the line, it returns to a high state. This design provides a defined idle state for the bus.
    *   **Master-Slave Architecture**:
        *   **Master**: A master device initiates and terminates all communications and generates the SCL clock signal. Masters do not require their own unique address on the bus.
        *   **Slave**: Slave devices wait for the master to initiate communication and respond to commands. Each slave has a **unique 7-bit address** (with some variations supporting 10-bit addresses).
        *   **Network Configuration**: The I2C protocol supports **multiple masters and multiple slaves** on the same bus, all sharing the same SDA and SCL lines. The number of slaves does not increase the number of required wires.
        *   **Transmitter/Receiver Roles**: A device can act as a **transmitter** (putting data onto the bus) or a **receiver** (reading data from the bus), regardless of whether it is a master or a slave. For example, a master acts as a transmitter during a write transaction and a receiver during a read transaction from a slave.
    *   **Bidirectional**: Both SDA and SCL lines are bidirectional, allowing data and clock signals to travel in both directions.

*   **I2C Transaction Structure**: Each I2C transaction is either a write (master sends data to slave) or a read (master requests data from slave).
    *   **Start Condition**: Initiates every transaction. It is defined as the SDA line transitioning from **high to low while the SCL line is high**. Slaves detect this condition and prepare to listen.
    *   **Address and Direction Byte**: Following the start condition, the master transmits an 8-bit byte composed of the **7-bit slave address** and a single **direction bit**. A direction bit of `0` indicates a write transaction, while `1` indicates a read transaction. Slaves compare the received address to their own; matching slaves continue the transaction, while non-matching slaves disregard it.
    *   **Data Transfer**: After the address and direction, data bytes are exchanged.
    *   **Acknowledge (ACK) Bit**: After the transmission of every 8-bit byte (including the address/direction byte and subsequent data bytes), the receiver must send an **acknowledgement (ACK) bit**. The receiver acknowledges by pulling the SDA line low for one SCL clock pulse. If no ACK is received, the transmitter assumes an error and aborts or restarts the transmission.
    *   **Stop Condition**: Terminates the transaction. It is defined as the SDA line transitioning from **low to high while the SCL line is high**.
    *   **Bit Transmission**: Data bits are placed on the SDA line and sampled by the receiver on the **rising edge of the SCL clock**. During data transmission, the SDA line must be held constant while the SCL clock is high, with changes only permitted when the SCL clock is low. The only exceptions to this rule are the start and stop conditions.

*   **Wire Library Functions (Master Mode)**:
    *   **Include Header**: `#include Wire.h` is required at the beginning of the sketch.
    *   **Initialization**: `Wire.begin()`: Called in the `setup()` function, this initializes the I2C hardware. If called without arguments, the Arduino is configured as a **Master**. If an `address` (0-127) is provided as an argument, the Arduino is configured as a **Slave** with that address.
    *   **Writing Data (Master as Transmitter)**:
        *   `Wire.beginTransmission(address)`: Initiates a transmission to the specified `slave address`. This prepares the start condition and address bits for sending.
        *   `Wire.write(data)`: Queues a single `byte` of `data` into an internal transmission buffer. Data is buffered and not sent immediately upon calling `Wire.write()`. Multiple bytes can be queued with successive calls.
        *   `Wire.endTransmission(stop)`: Executes the transmission by sending all buffered data, including the start condition, address, buffered data bytes, and finally generates a stop condition. The optional `stop` argument controls whether the bus is released after the transaction. If `stop` is `true` or omitted, a stop condition is asserted, releasing the bus for other masters. If `stop` is `false`, the bus remains held, allowing the master to make subsequent requests without a new start condition.
    *   **Reading Data (Master as Receiver)**:
        *   `Wire.requestFrom(address, numBytes, stop)`: Initiates a request to the specified `slave address` for a total of `numBytes`. The optional `stop` argument functions similarly to `endTransmission`. Data received from the slave is placed into an internal receive buffer on the master.
        *   `Wire.available()`: Returns the number of bytes currently present in the master's receive buffer that are available for reading. This is useful for verifying that data has been received and handling cases where the slave might send less data than requested or respond slowly.
        *   `Wire.read()`: Reads and returns one byte from the master's receive buffer. This function is typically called in a loop in conjunction with `Wire.available()` to process all received bytes. The returned byte value can be cast to an `int` for arithmetic operations.

*   **Wire Library Functions (Slave Mode)**:
    *   **Initialization**: As mentioned, `Wire.begin(address)` configures the Arduino as a slave.
    *   **Event Handling (Callback Functions)**: Slaves cannot initiate communication; they must wait for requests from a master. To avoid inefficient "busy-wait" loops, the Wire library utilizes **callback functions**. A callback function is a user-defined function that is automatically invoked by the system when a specific event occurs, allowing the microcontroller to perform other tasks while waiting.
    *   `Wire.onReceive(functionName)`: This function registers `functionName` as the callback to be executed when the slave **receives data from a master** (i.e., a master performs a write transaction to the slave).
        *   The registered callback function (`functionName`) must be defined to accept one integer argument, which represents the number of bytes received. Within this function, `Wire.read()` is used to retrieve the incoming bytes from the receive buffer.
    *   `Wire.onRequest(functionName)`: This function registers `functionName` as the callback to be executed when the slave **receives a read request from a master** (i.e., the master requests data from the slave).
        *   The registered callback function (`functionName`) must be defined to take no arguments and return `void`. Within this function, `Wire.write()` is used to transmit data bytes back to the requesting master.
