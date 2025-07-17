Networking is a fundamental aspect of the Internet of Things (IoT), with the "Internet" explicitly in its name. It is essential because it **enhances device capabilities** by providing access to computational complexity and large databases located outside the local device. For example, cars as IoT devices could communicate on a network to improve traffic flow by planning routes collaboratively.

Here's a breakdown of networking concepts and components:

### Types of Networks

*   **Local Area Network (LAN)**:
    *   A relatively **small network** that typically spans a building or a campus.
    *   Commonly accessed via **Ethernet jacks** in walls or **Wi-Fi routers**.
    *   LANs can be combined into larger components using a **bridge**, which communicates different LAN protocols to allow machines using various protocols to connect.
*   **Wide Area Network (WAN)**:
    *   Significantly **more complex** than LANs.
    *   The **Internet** is the primary example of a WAN.
    *   A WAN is formed by **combining multiple LANs using routers**.
    *   The Internet's structure is **ad hoc and largely unstructured**, allowing new networks to join dynamically. Despite its unpredictable nature, it functions effectively.
    *   Communication across a WAN involves messages "hopping" through a sequence of machines and routers to reach their destination.
*   **Mobile Ad Hoc Networks (MANETs)**:
    *   Smaller networks composed primarily of **mobile IoT devices**.
    *   They are **self-configuring and dynamic** because devices are constantly moving into and out of range, causing connections to change over time.
    *   Commonly connected to the broader Internet through a (usually non-mobile) **access point**.
    *   **Important aspects of MANETs**:
        *   **Power budget**: Devices are typically battery-driven, necessitating **power-restrictive protocols** to conserve energy due to the weight and limited life of batteries. Sending less data helps save power.
        *   **Lower data rate**: Reduced power usage often leads to **lower data transmission rates**. For example, Bluetooth Low Energy uses less power but has a significantly lower data rate than standard Bluetooth, preventing high-bandwidth applications like video streaming.
        *   **Security constraints**: Security measures like encryption or antivirus tools consume power and computational cycles. Since IoT devices are designed for efficiency and have limited excess processing capacity, **security features may be reduced** or absent to preserve main functionality and power.

### Network Components

*   **Hub**:
    *   A basic network component with multiple input/output ports (e.g., Ethernet jacks).
    *   It is "dumb" and functions as a **repeater**: any packet received on one port is copied and sent out to all other ports.
    *   This design is **wasteful in terms of bandwidth**, leading to less common use today.
*   **Switch**:
    *   More **intelligent** than a hub.
    *   It learns which ports are connected to specific **IP addresses**. When a packet is received, the switch inspects the packet header to determine the destination and **sends the message only to the relevant port**, thereby saving bandwidth.
*   **Router**:
    *   Connects different networks, such as LANs, within a WAN.
    *   Routers communicate with each other to **pass data between distant networks**.
    *   They employ **intelligent protocols** to determine the most efficient routes for packets, aiming to deliver them quickly and balance traffic across the network to prevent bottlenecks.
    *   Routers, switches, and hubs share similar physical interfaces (Ethernet jacks and lights) but differ in their internal functionality.

### Network Protocols

*   **Definition and Purpose**:
    *   A network protocol is a **set of rules for communication** that all participating entities must adhere to.
    *   These rules are designed to be minimal, providing flexibility while enabling consistent communication across diverse network types.
    *   Protocols typically involve adding **extra data** to a message, known as a **header** (at the beginning) or **footer** (at the end), which contains metadata for communication.
*   **Functions of Protocols**:
    *   **Naming scheme**: Protocols provide unique addresses for network components (e.g., **IP addresses**, which are unique four-byte numbers assigned to every machine on the Internet).
    *   **Delivery mechanism**: They define how messages (packets) are routed through a sequence of machines (hops) to reach their destination.
    *   **Message structure**: Protocols define the format of messages, including the **header** (metadata) and **payload** (actual data to be sent).
    *   **Flow control**: Managing data transmission to prevent network congestion and ensure efficient traffic distribution across routers.
    *   **Arbitration**: Establishing rules to resolve conflicts when multiple devices attempt to transmit data simultaneously over a shared network segment.
*   **Protocol Stack**:
    *   Due to their complexity, protocols are **divided into layers**. This layering, as seen in the **OSI (Open Systems Interconnection) model** and the Internet's standard protocol stack, helps manage complexity and simplifies coding by separating responsibilities.
    *   **Encapsulation**: Each layer of the protocol stack is separated, meaning it handles specific tasks (e.g., routing at one layer, flow control at another) without needing to deal with details of other layers.
    *   **Message Transmission (Sender Side)**: A message (payload) starts at the top layer. Each subsequent layer in the stack **adds its specific header information** to the message before passing it down to the next layer. The bottom layer, the **physical layer**, encodes the data for transmission over wires or as wireless broadcasts.
    *   **Message Reception (Receiver Side)**: Upon physical reception, the message travels **up the protocol stack**. Each layer reads and **strips off its corresponding header information**, processing the data until only the original payload remains at the top layer.

### Internet Standard Protocol Stack (TCP/IP)

The Internet uses a four-layer protocol stack, distinct from the seven-layer OSI model:

1.  **Application Layer**:
    *   The top layer, which **directly interacts with software applications**.
    *   Examples of application-layer protocols include:
        *   **HTTP (Hypertext Transfer Protocol)**: Used for web interactions. HTTP messages include a header (e.g., protocol version, message type, content length) and a body/payload (e.g., HTML code for a webpage).
        *   **SMTP (Simple Mail Transfer Protocol)**: Used by email clients for communicating with mail servers.
        *   **LPD (Line Printer Daemon)**: Used by printers to communicate.
        *   **FTP (File Transfer Protocol)** and **SFTP (Secure File Transfer Protocol)**: Used for file transfers.
2.  **Transport Layer**:
    *   Contains **TCP (Transmission Control Protocol)** and **UDP (User Datagram Protocol)**.
3.  **Network Layer**:
    *   Responsible for **IP (Internet Protocol)**. All machines on the Internet must use IP and adhere to its rules.
4.  **Data Link/Physical Layer**:
    *   The bottom layers, responsible for the **physical transmission of data** over a medium, such as electrical signals on wires or radio broadcasts.

### Packet Capture and IoT Device Programming

*   **Packet Capture**: Tools like **Wireshark** allow users to capture and analyze network packets. They provide detailed views of packets, including their hexadecimal representation and parsed information according to specific protocols, such as HTTP headers.
*   **IoT Device Programming**: When developing applications for IoT devices (e.g., using Arduino or Raspberry Pi), programmers typically **call high-level library functions at the application layer**. The underlying complexities of the lower protocol layers (TCP/UDP, IP, data link) are handled by the protocol stack implementation provided as a library, abstracting these details from the developer.
