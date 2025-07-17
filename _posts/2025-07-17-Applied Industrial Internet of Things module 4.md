---
layout: post
title:  "Applied Industrial Internet of Things module 4"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---


The provided sources contain comprehensive information regarding edge computing and IoT gateways, their definitions, drivers, functionalities, architectural components, configuration steps, selection criteria, and various industrial applications.

Here is the extracted knowledge:

### Edge Computing

*   **Definition**: Edge computing is a part of **distributed computing topology** where information processing is located **close to the edge**, where "things and people produce or consume that information". It involves taking computations, data management, and storage close to sensor devices on manufacturing shop floors, machinery, and heavy equipment. It complements the centralized Cloud model.
*   **Concept**: Edge computing is considered a **redefinition of the computing infrastructure's topology**, rather than a new technology. It represents a **topological change** from centralized computing. Every endpoint or edge system is an extension of the central data center or cloud.
*   **Need and Key Drivers**: The adoption of edge computing is driven by several factors, particularly with the explosive growth of IoT and real-time applications:
    *   **Latency**: Edge computing significantly **reduces the time taken** from sending a request to receiving a response or acknowledgment by handling real-time critical tasks and decision-making locally.
    *   **Bandwidth**: Processing data locally at the edge saves considerable bandwidth by transmitting only necessary information to the central location, making it unwieldy to transmit very large generated data to remote sites.
    *   **Data Privacy**: Local processing means data is not transmitted to remote sites, reducing the risk of unauthorized access or misuse by cloud vendors once it leaves premises.
    *   **Autonomy**: Edge systems provide more control over data as it remains at the site of creation and enables **offline mode operation**.
    *   **Local Interactivity**: Edge systems can handle the specific needs and protocols of individual sensors and devices locally, simplifying computational requirements at central servers.
*   **How Edge Computing Helps**:
    *   **Redistribution of Processing and Storage**: It decentralizes computation, moving processing power to where it is needed. Data is stored close to its generation point, and only extracted, cleaned information is sent remotely.
    *   **Data Processing**: Edge systems perform tasks such as **aggregation, filtering, cleanup, and information extraction** from data. Real-time analytics can be performed at the edge for quicker responses.
    *   **Customization**: Edge computing allows for customized solutions and applications specific to local system requirements and environments.
    *   **Digital Transformation**: It is a fundamental building block for digital transformation, which involves decentralization and distribution of computation and business infrastructure.
    *   **Scaling IoT Solutions**: Distributed computation enables easier scaling of IoT solutions and reduces demands on central infrastructure.
*   **Functions Handled by Edge Systems**: Data aggregation, event-filtering, complex analytics, data-processing, and visualization. The complexity of an edge system depends on data load, computation intensity, and data generation/consumption speed.
*   **Impact on Other Technologies**: Edge computing enables the expansion of use cases requiring significant local processing, such as **5G IoT, virtual and augmented reality (AR/VR) applications, connected and autonomous cars, and security cameras**. Conversely, expanding use cases (e.g., drones) demand more localized processing, impacting edge computing.
*   **Risks and Challenges**:
    *   **Infrastructure Costs**: A decentralized model with multiple edge systems increases overall system complexity and total infrastructure cost, although individual edge systems might be cheaper.
    *   **Responsibility Clarity**: A clear understanding of processing and storage responsibilities, with precise demarcation between edge and central server tasks, is crucial to avoid duplication or dropped activities.
    *   **Security Challenges**: Multiple systems in a solution necessitate securing each system and replicating security controls across all of them.
*   **Examples of Edge Computing Use Cases**:
    *   **Autonomous Cars**: Onboard computers collect, process data, initiate actions, and transmit minimal information to central servers.
    *   **AR/VR Gaming**: Local computing devices collect, process data, and initiate actions, referring to central systems only for additional information.
    *   **Toll Booths**: Local servers at toll booths can extract ID and registration numbers from car number plate images, sending only the ID for verification and toll deduction, significantly reducing bandwidth compared to sending full images to the cloud.
    *   **Industrial Monitoring (Oil & Gas, Energy, Manufacturing, Construction)**: Edge systems near heavy machinery monitor parameters (e.g., temperature, vibration) locally, enabling immediate warning and preventive action for abnormalities, avoiding machine failure and reducing latency compared to a centralized server model.
    *   **Video Analytics and Quality Control**: Video sensors send images to edge processing servers in IoT gateways. Edge systems extract information, perform analysis on picture data (e.g., detecting flaws, recording serial numbers), and provide quality approvals. This reduces latency for immediate action (e.g., discarding products) and significantly saves bandwidth by transmitting only extracted data (e.g., a 20-character serial number of 20 bytes instead of a 6.3 MB image).
    *   **Automotive Component Manufacturing (Valve Cycle Time)**: Sensors (optical or inductive) placed on cutting machines or other equipment generate digital pulses. A digitizer calculates the time between two pulses (cycle time). This data is sent to the IoT gateway and then to the cloud for analysis. This also helps count parts produced and identify machine downtime.
    *   **Aluminum Extrusion**: Monitoring process parameters like billet, die, and output profile temperatures using temperature sensors and scanners. Energy meters capture consumption data (voltage, current, power factor, units). Digital input modules with proximity sensors monitor machine on/off status, production count, and cycle time. All data is sent to the IoT gateway and then to the cloud for analysis, alerting operators to variations and aiding in costing analysis.
    *   **Packaging Industry**: Digital input cards connected to proximity sensors capture pulses for every package produced. This enables real-time monitoring of production count and downtime (when pulses stop). This data can be analyzed by the gateway or software to understand machine availability and production efficiency.
    *   **Pulse Counting (General)**: Applications include counting door open/close events, parts produced by a machine, or pump on/off cycles. Optical or proximity sensors generate pulses, which are counted by a digital input module (counter module) and transmitted via an RS485-based Wi-Fi gateway to a PC (intranet) or to MQTT servers (Internet/Cloud).

### IoT Gateway

*   **Definition and Function**: A gateway creates connectivity or an interface between two dissimilar networks, serving as a **single point of connection** for communication. In an IoT solution, an IoT gateway connects sensor networks and IoT devices on one side (physical world, including edge computing systems, controllers, sensors) to external communication networks on the other side (remote digital world, like data servers and cloud). It bridges the entire IoT solution together. IoT gateways are often referred to as **Edge Gateways** because they integrate both edge computing and gateway functionalities within the same network device.
*   **Gateway Categorization**:
    *   **Based on Data Flow Direction**:
        *   **Unidirectional Gateway**: Permits data flow only in one direction (e.g., from N1 to N2, but not N2 to N1).
        *   **Bidirectional Gateway**: Allows data to flow in both directions (N1 to N2 and N2 to N1). This is the more common type.
    *   **Based on Functionality/Solution**:
        *   **Voice over IP (VoIP) Gateway**: Facilitates transmission of voice calls (POTS) over IP networks.
        *   **Network Gateway**: The most common type, providing a bridge between two dissimilar data networks.
        *   **Internet-to-Orbit (I2O) Gateway**: Used in satellite communication, connecting internet devices to satellites and spacecraft.
        *   **Cloud Storage Gateway**: Provides an interface to a network of storage, translating storage requests to different cloud storage service API calls (e.g., SOAP, REST).
        *   **IoT Gateway**: Used specifically in IoT solutions to translate data from sensor devices to appropriate protocols and send them to data centers or the cloud.
*   **Typical Features of a Basic/Traditional Gateway**:
    *   **Single Point of Connect**: Serves as a default gateway for all nodes within a network to access external networks.
    *   **Multiple Network Interface Cards (NICs)**: Requires at least two NICs for connecting to multiple networks.
    *   **Routing Table**: Maintains information on routing paths between networks.
    *   **Protocol Translation**: Enables smooth interoperability between networks operating with different communication protocols by creating a path and providing translation.
    *   **Different Connectors/Drivers**: Supports various transmission and network protocols.
    *   **Intra-network Communication**: Facilitates inter-device communication within the network.
    *   **Bootstrapping**: Facilitates devices without onboard RAM to boot with software stored in the gateway and secure network addresses.
    *   **Packet Switching**: Uses packet switching for data transmission across networks.
    *   **Media Gateway**: Operates as a media gateway for voice and video links.
    *   **Caching and Buffering**: Supports different data rates between source and destination, balancing operational speeds.
    *   **Security**: Provides secure links with appropriate levels of security and access control, including acting as a **proxy server and firewall** for enterprises. Can include onboard security applications, storage, and platforms.
    *   **Data Processing and Management (Basic)**: Can provide data processing, analytics, and visualization with appropriate software applications, and offline control and management of devices.
*   **Enhanced Features of Modern/Smart IoT Gateway (Edge Gateway)**: Includes all standard features of a basic gateway plus:
    *   **Intelligence and Processing**: Possesses processing, storage, and a certain amount of intelligence for processing.
    *   **Platform Capabilities**: Provides platform-like features to run applications, including support for edge computing functionality and sometimes its own OS (e.g., Linux, Windows).
    *   **Reliability**: Can offer high availability, critical for industrial IoT solutions.
    *   **Data Optimization**: Performs data aggregation, pre-processing, cleansing, filtering, and optimization before communicating to remote sites.
    *   **Live Data Services**: Receives and stores live data, offering visualization and basic data analytics.
    *   **Offline Services**: Provides offline processing while enabling real-time control of IoT devices.
*   **IoT Gateway Categories (by Complexity)**:
    *   **Basic IoT Gateway**: Primarily provides gateway functionality, supporting multiple communication protocols and ports, network routing, impedance/data rate matching, bootstrapping, and minimal security. It has limited intelligence or onboard storage and no processing capability.
    *   **Intermediate IoT Gateway**: Includes all basic gateway features, plus support for **data preprocessing** (aggregation, fault isolation), common transmission protocols (MQTT, CoAP), advanced security (access control, data encryption), and limited onboard memory and RAM to execute simple applications.
    *   **Server IoT Gateway**: The high-end gateway, encompassing all intermediate gateway features. It supports **complex data processing, storage, and management, data analytics, visualization, and real-time data trends**. It includes all hardware required for a full-fledged server, including OS support (Linux, Windows) for deploying business applications.
*   **Drivers for Growth of IoT Gateway**:
    *   **Big Data Analytics**: Increasing demand for sensed and recorded data drives the need for more IoT solutions.
    *   **Rise in Connected Devices**: Leads to a rapid increase in generated data.
    *   **Digital Transformation**: Increasing pressure across industries for digital transformation demands more from IoT.
    *   **Governmental Support and Regulatory Compliance**: Thrust on digitization and stricter regulations increase the need for connected systems for compliance and reporting.
*   **IoT Gateway Hardware Architecture**:
    *   **Components**: Includes functionality-based components (ports) and standard components (central processor, onboard RAM, onboard storage, internal bus).
    *   **Primary Building Blocks**:
        *   **Devices Module**: Connects to and manages devices. For smart IoT devices, it provides connectivity and security; for non-smart devices, it provides smart capabilities (processing/storage).
        *   **Data Acquisition Module**: Acquires physical signals from sensors, converts them to digital signals, performs signal conditioning, noise removal, interpretation, scaling, and amplification.
        *   **Data Processing Module**: An onboard computer for data processing, analytics, operations, and initiating actions. Connects to HMI for visualization.
        *   **Communication Module**: Enables communication between the sensor network and external networks (cloud platforms, third-party devices, business applications).
    *   **IoT Functional Boards Examples**: Low-power boards like **Arduino Uno** (small integrated devices), **Raspberry Pi** (full processing board running OS), and high-capacity boards like **Beagle board** (single board computer with Linux OS) and **Intel Galileo/Edison** boards.
*   **Configuring an IoT Gateway (Key Steps)**:
    1.  **Connectivity**: Provide appropriate connectivity for all sensor device networks, ensuring suitable drivers for ports are integrated and enabled.
    2.  **Port and Protocol Configuration**:
        *   Configure network protocols (e.g., Ethernet, Token Ring, Wi-Fi, GSM, 4G/5G, RS-232).
        *   Establish the gateway on an IP network by assigning an IP address.
        *   Verify the network path from the gateway to the server/cloud using commands like `ping`.
        *   Run a DNS server on the gateway for dynamic IP address assignment for connected devices.
        *   Configure routing protocols (e.g., RIP, OSPF) for dynamic routing table creation and updates, or manually create the routing table.
        *   Configure transport/transmission protocols (e.g., MQTT, CoAP).
        *   Install connectors and configure relevant ports.
    3.  **Security Features Configuration**:
        *   **Access Control**: Create a list of permitted networks, configured at the port level with individual access permissions.
        *   **Encryption**: Apply encryption to each network, also configured at the port level.
        *   Binding/Unbinding devices, establishing authentication mechanisms.
    4.  **Connector Configuration**: Configure standard connectors used in IoT solutions, such as MQTT, OPC-UA, MOD Bus, BLE, HTTP/S (Request), CAN, BACnet, REST, and SNMP connectors.
    5.  **Sensor Network Configuration**:
        *   Bind and unbind devices (creating/removing association between IoT devices and gateway).
        *   Establish device authentication mechanisms with the gateway.
        *   Attach and detach transmission protocols (e.g., MQTT bridge).
    6.  **External Network Configuration**: Define and configure long-haul networks (including wireless) on the gateway, enabling access control and security features.
    7.  **Edge Functionality Configuration**:
        *   Identify required applications for edge execution (data processing, analytics).
        *   Configure applications to run on gateway software and create necessary data stores/databases.
        *   Create interfaces for visualization devices connected to the edge system.
    8.  **Future Protection**: Ensure the gateway can handle new requirements, updates, and upgrades (security updates, firmware/software upgrades) and provides flexibility in connections and protocol options.
*   **Selecting an IoT Gateway (Criteria)**:
    *   **Gateway Type**: Determine if a basic, intermediate, or server-level gateway is required based on functionality complexity.
    *   **Hardware Configuration**: Processor type and speed, onboard cache, RAM capacity, onboard/external storage, communication ports, and wireless modules. These choices are driven by IoT solution design and application requirements.
    *   **Operating System**: Identify the compatible OS (e.g., Linux, Windows, real-time OS).
    *   **Processing and Management Requirements**: Define edge processing, common applications (data acquisition, processing, analytics), Human-Machine Interface (HMI) and visualization needs, and management applications (device, data, storage, network management).
    *   **Operational Environment/Ruggedness**: Consider requirements for harsh/hazardous conditions (temperature, humidity, pressure, dust protection, shockproof, waterproofing).
    *   **Regulatory Compliance and Certifications**: Ascertain any necessary certifications.
    *   **Cost**: A significant factor, complexity increases cost.
    *   **Vendor Support**: Factor in the expected support from the vendor.
*   **Industrial Examples of IoT Gateway Deployments**:
    *   **Tower Crane**: Local IoT Gateway converts analog to digital data, aggregates digital data, and preprocesses it for local visualization to help operators and adapt dynamically (e.g., adjusting speed in wind) before sending to the cloud.
    *   **Manufacturing Unit (General Machinery)**: Gateway with a minimal edge system for data aggregation, preprocessing, and local visualization of machine working parameters, then transfers data to remote data center/cloud.
    *   **Fleet Management System (Conveyance Vehicle IoT)**: Gateway collects data from vehicle sensors (typically wired), transfers data via GPRS SIM to remote servers. Gateway selection varies based on application and parameters. Parameters monitored include geo-locations, distance traveled, ignition/engine on/off, idle/stopped hours, fuel consumption (and pilferage detection via algorithms), efficiency, and productivity. Alerts can be generated for maintenance, overspeed, gateway offline status, and underutilization. Features include real-time tracking, fuel monitoring, geofencing, alerts, and remote engine blocking. Benefits include reduced fuel costs, fewer speeding events, accurate overtime claims, cost-effective maintenance, and improved resource management and productivity.
    *   **Home Connectivity**: Modem serves as a gateway with minimal local processing, common for home networks.
    *   **Packaging Industry**: Digital input cards connected to proximity sensors send pulses to the gateway to analyze downtime and production count for high-speed machines.
    *   **PET Bottle Manufacturing**: Energy meters connected to machines (injection molding, blow molding, stickering) send data to the IoT gateway for cloud analysis, determining energy consumption per part and optimizing energy trading based on production plans.
    *   **Automotive Valve Manufacturing**: Optical or inductive sensors provide digital pulses to a digitizer, which calculates cycle time between pulses. This information is sent to the IoT gateway and then to the cloud, enabling scientific assessment of cycle times for optimizing production volume and quality.
    *   **Aluminum Extrusion**: Temperature sensors with scanners, energy meters, and digital input cards (with proximity sensors) send data to the IoT gateway (via RS485 to Wi-Fi/GPRS) for cloud analysis, monitoring billet/die/profile temperatures, energy consumption, production quantity, cycle time, and downtime.
