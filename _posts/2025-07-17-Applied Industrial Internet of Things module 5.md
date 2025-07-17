---
layout: post
title:  "Applied Industrial Internet of Things module 5"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---

Here is the knowledge-based information extracted from the sources, with colloquial language removed and key concepts bolded:

**1. IoT Connectivity Fundamentals**
*   **IoT connectivity** is the underlying technology that provides the **network infrastructure and communication capability** for an IoT solution, tying every part together to function as a single unit.
*   It facilitates communication between various devices, including **sensors, actuators, edge-systems, gateways, routers, other network devices, servers, cloud, applications, and APIs**.
*   The choice of connectivity protocol depends on the **devices to be connected, ease of access to a power source, required bandwidth (data rate), and the range to be covered**.
*   **Key trade-offs** for communication protocols are **power (P), bandwidth (B), and range (R)**.
    *   An ideal protocol would consume low power, provide high bandwidth, and operate over a long range, but this is not achievable.
    *   When power consumption is low, either range or bandwidth must be compromised.
*   Protocols are broadly classified into **wired and wireless**.
    *   **Wired protocols** require an enclosed material medium. They typically have high power requirements.
    *   **Wireless protocols** operate in the open, using air as the medium.
*   **Wireless network examples based on trade-offs:**
    *   **High P, High R, High B:** Cellular networks (GSM, 3G, 4G/LTE, 5G), Satellite.
    *   **Low P, Low R, High B:** Wireless LAN (Wi-Fi), Bluetooth.
    *   **Low P, High R, Low B:** Low Power Wide Area Networks (LPWAN).

**2. Long Range Protocols**
*   **Long-range protocols** typically operate over distances ranging from over one kilometer to several tens of kilometers.
*   **Low-Power Wide Area Networks (LPWAN):**
    *   Characterized by **low power consumption** and a **large range (order of several kilometers)**.
    *   The trade-off for this combination is **low bandwidth**, meaning messages must be very short.
    *   Batteries powering LPWAN communication can last for many years.
    *   A downside is that these networks tend to incur **significant packet losses**.
    *   LPWAN is preferred when a large number of sensors send short messages to an aggregating server, or when sensors run on batteries and are not easily accessible for frequent battery changes.
    *   Examples include **LoRa, SiGFOX, Weightless, Ingenu, and Symphony Link**.
*   **Cellular Networks:**
    *   Belong to the **High-Power, High-Bandwidth, High-Range connectivity group**.
    *   Operate on radio waves, with the network divided into **cells** served by base stations, providing end-to-end coverage over large geographical areas.
    *   Frequencies are differentiated in neighboring cells to prevent interference and can be reused in distant cells.
    *   Ideal for devices directly connected to power sources or those that can be recharged often. They are not suitable for remote sensor devices requiring long battery life.
    *   Commonly used for **backhaul network** (gateway to data-center or cloud connectivity) in IoT solutions.
    *   Examples of common cellular networks include **GSM, 3G, LTE (4G), 5G, CDMA, and GPRS**.
    *   **IoT-specific cellular technologies** derived from LTE and optimized for IoT requirements include:
        *   **LTE CAT-1:** A medium-frequency LTE network using a lower frequency band. It supports high-speed IoT applications with lower power consumption than regular LTE, resulting in lower data rates. It offers higher penetration through obstructions and has lower complexity and cost.
        *   **LTE-M (LTE-MTC):** An adaptation of LTE for machine-type communication, offering much lower bandwidth, lower power consumption, and lower device complexity compared to LTE CAT-1.
        *   **NB-IoT (Narrow Band IoT):** Designed specifically for IoT solutions, characterized by very low power consumption and low bandwidth. Device battery life can exceed 10 years. It optimizes system capacity and spectrum efficiency and can co-exist with existing cellular networks while providing their security features.

**3. IoT Architecture: Server Layer**
*   The **application layer** is the fourth layer of the IoT architecture, dealing with **servers, storage, applications, analytics, and visualization**.
*   Servers are components positioned between **IoT devices (data generation point) and applications (data consumption point)**.
*   **Two primary types of servers** are **On-premise servers and Cloud servers**.
*   **Server platform offerings and basic building blocks for IoT solutions include:**
    *   **Data management:** Handles data ingestion, enrichment, routing, and storage.
    *   **Processing and analysis:** Performs enrichment, extraction, data mining, and analysis.
    *   **Application development:** Provides Software Development Kits (SDKs) and APIs for developers.
    *   **Security and access control**.
    *   **Monitoring and event processing**.
    *   **Interfacing/integration with business applications:** Provides APIs for data access.
    *   **Device management:** Monitors, services, and maintains connected IoT devices, including installation, provisioning, upgrades, and maintenance.
    *   **Storage (Databases):** Manages large data volumes with scalability.
    *   **Analytics, Machine Learning (ML), Deep Learning (DL), and Visualization tools:** Provide data analysis (real-time and batch mode) and display processed data via user interfaces, reports, and dashboards.

**4. Server Architecture Types**
*   **On-premise Servers:**
    *   Installed and maintained **within the organization's premises**.
    *   Ensures **complete control over data**, as it does not leave the boundary.
    *   **Security solutions are relatively less complex**.
    *   **Maintenance, upkeep, and scaling are the responsibility of the organization**.
    *   Involve **considerable capital expenditure**, and scaling up or down can be challenging.
    *   Benefits include **security and control, customization** for unique solutions, and prevention of **vendor lock-in**.
*   **Virtual Cloud Computing Servers:**
    *   Set up in a **remote, often geographically distributed environment** with server and storage clusters.
    *   A **virtualized environment** provides transparency regarding underlying hardware and network.
    *   **Data leaves the organization's boundary**, resulting in less control over the data.
    *   **Security solutions are significantly more complex**.
    *   **Maintenance, upkeep, and scaling are the responsibility of the third-party vendor**.
    *   Involve **operational expenses**, which are considerably less than capital expenses.
    *   **Scaling up or down is very easy**.
    *   Drawbacks include **inflexibility for customization** (being generic shared platforms) and the possibility of **vendor lock-in** due to proprietary solutions.
*   **Primary technologies underlying Cloud infrastructure:**
    *   **Virtualization:** Enables a single physical instance to be shared by multiple users, providing isolated **Virtual Machines (VMs)** that give users the impression of a dedicated server.
    *   **Service-Oriented Architecture (SOA):** Allows applications to service other applications in a vendor and technology-agnostic manner, facilitating seamless data transfer.
    *   **Grid Computing:** A form of distributed computing where geographically distributed, heterogeneous computers work together to achieve a common purpose, breaking down and executing complex tasks across different machines.
    *   **Utility Computing:** Provides computational resources and applications on demand, with users paying based on duration or usage.
*   **Benefits of Cloud computing in IoT solutions:**
    *   **Scalability:** Easily adaptable up and down, allowing flexible resource allocation (e.g., adding only storage).
    *   **Data Mobility:** Data is accessible from anywhere with network connectivity.
    *   **Time to market:** Effortless implementation of IoT solutions.
    *   **Cost-effectiveness:** No large upfront investment, as resources are leased as needed.
*   **Hybrid Computing System:**
    *   A combination of On-premises server systems and Cloud computing, where parts of the system are On-premises and the rest are on the Cloud.
    *   Leverages the strengths of both models, allowing confidential data and customization to be handled On-premises, while the Cloud provides short-term scalability. This model is commonly used.

**5. Big Data Architecture and Lambda Architecture**
*   **Big Data architecture** is a collection of technologies for **handling, processing, managing, analyzing, and visualizing large volumes of data** in IoT solutions.
*   **Primary blocks of Big Data architecture include:**
    *   **Data sources:** IoT devices that collect and send data.
    *   **Real-time message ingestion:** Handles live streaming data for real-time tracking and visualization.
    *   **Data storage:** Stores received data for offline processing, archiving, and historical records.
    *   **Stream processing block:** Processes and extracts information from real-time streaming data for trends, monitoring, and visualization.
    *   **Batch processing block:** Performs offline processing of stored data in batches at regular intervals.
    *   **Analytical data suite:** Contains tools for data mining and analysis using AI and ML. It controls data flow and manages data access, resource provisioning, and process monitoring across distributed systems.
    *   **Analytics and reporting:** The second stage of analytical processing, involving visualization of analyzed information and report generation.
*   **Data ingestion** is the process of obtaining and importing data for real-time or batch processing. Tools are selected based on the **volume, velocity, variety, and veracity** of the data.
*   **Data processing types:**
    *   **Stream (Real-time) processing:** Data is sourced, manipulated, and loaded as soon as it is received, with latency being critical. Popular systems include **Apache Storm** (open-source real-time) and **Apache Spark** (open-source, scalable, high-throughput, fault-tolerant, integrates stream and batch processing).
    *   **Batch (Offline) processing:** Data is collected and processed in groups periodically over stored data.
*   **Lambda architecture** (coined by Nathan Marz) is a generic, scalable, fault-tolerant data processing design pattern for big data systems requiring near real-time processing.
    *   It enables a single system to process near real-time streaming data while simultaneously allowing storage and batch processing using traditional techniques.
    *   It is designed to be fault-tolerant from hardware failures and human mistakes.
    *   The architecture includes two paths:
        *   **Cold path (slow path or batch processing path):** Data is stored and processed offline, used for generating reports from historical data.
        *   **Hot path (fast path or real-time path):** Data from the input stream is processed in near real-time, used for real-time processing, actions, and live stream visualization.

**6. IoT Security**
*   **Importance of Security:** IoT involves the merger of **Operational Technology (OT)**, traditionally closed systems with limited security, and **Information Technology (IT)**, exposing OT to cyber access and raising new security concerns.
*   **Key concerns in IoT security:**
    *   **Limited processing power of devices:** Makes it challenging to build adequate security directly into the devices.
    *   **Vulnerability of IoT devices:** They are entry points to the enterprise; compromise can lead to loss of confidentiality, safety, integrity, and denial of service attacks.
    *   **Loss of privacy:** Sensors can record actions without awareness, and unauthorized personnel can gain entry.
    *   **Data integrity:** Securing large volumes and varieties of data is critical.
    *   **Compromise of industrial control systems (ICS):** Can lead to malfunctions or breakdown of critical infrastructure.
*   **Challenges in implementing IoT security:**
    *   **Lack of technological standardization and fragmentation:** Complicates consistent security solutions across diverse technologies.
    *   **Vast number of devices and nodes:** Every device is a potential point of entry, requiring security control on all nodes.
    *   **Cloud platform security:** Requires collaboration with third-party vendors, as data control depends on vendor reliability.
    *   **Network transition security:** Data is decrypted and re-encrypted at each network transition (e.g., at gateways), creating potential vulnerabilities. The weakest link in the network determines overall security.
    *   **Manual effort for device personalization:** Configuring secret keys on numerous devices for encryption is a significant manual effort and a potential point of failure if missed.
*   **Proactive security steps and best practices in IoT design:**
    *   **Build security into the solution from the design stage:** Do not add security as an afterthought to avoid compromises.
    *   **Secure the device life cycle:** This includes controlling firmware and software updates from authorized sources and performing upgrades by authorized personnel.
    *   **Provide secure access control and authentication:**
        *   Ensure **complete visibility of all devices** in the solution, making them remotely discoverable and manageable via a device management application, each with a unique logical ID.
        *   Implement **two-way authentication** (device authenticates to gateway, gateway authenticates to device).
        *   Utilize **two-factor authentication** for enhanced protection.
        *   Secure physical access to devices and connecting lines/media between devices and the gateway.
        *   For sensor-to-gateway links outside controlled environments, implement data encryption and secure authentication.
    *   **Control maintenance:** Devices should be checked for unauthorized tapping or modifications after maintenance, and only authorized software/firmware versions should be used.
    *   **Ensure devices adhere to security requirements:** Devices should undergo rigorous security tests and validations, with certifications (e.g., CTIA) insisted upon. Security validation should be performed periodically.
    *   **Secure software and applications:** Build security into application design from the outset, using IoT APIs security functions.
    *   **Protect data movement integrity:** Across devices, systems, applications, and servers. Identify vulnerabilities and intrusions, deploying anti-intrusion mechanisms.
    *   **Permit interaction only for authorized devices/applications** and share data only on a need-to-know basis.
    *   **Secure network endpoints:** With antivirus, antimalware, firewalls, and intrusion detection/prevention systems.
    *   **Implement robust encryption algorithms** for all data passing through gateway nodes. Where encryption is not possible (e.g., sensor to gateway), the entire connectivity system must be access-controlled and protected.
    *   **Utilize IoT security analytics** to detect IoT-specific attacks and breaches.
    *   **Develop an exit plan for data breaches** to minimize losses.
    *   **Allocate sufficient time for security implementation** to avoid compromises due to rushed launches.
    *   Plan for long-term security support and batch updates.
*   **Device vulnerabilities** can be categorized as non-invasive (e.g., parallel channel snooping, perturbation), invasive (e.g., physical modification of sensor elements), life cycle (e.g., during upgrades or maintenance), and software (e.g., intentional bugs, manipulation).
*   **End-to-end security** focuses on securing devices, data integrity/confidentiality/privacy, access/connectivity, and applications/cloud.

**7. IoT Case Studies and Applications**

**7.1. Wheel Loaders (Construction Equipment)**
*   Wheel loaders are versatile construction equipment used for road building, job site preparation, digging, carrying heavy loads, or moving material.
*   **Key sensors and IoT equipment installed:**
    *   **Inclination sensor:** Monitors boom movement (range -80 to +80 degrees).
    *   **Hydraulic oil pressure sensor:** Monitors pressure variation in boom lifting cylinder (range 0 to 400 bar).
    *   **Hydraulic oil temperature sensor:** Monitors hydraulic oil temperature (range 0° to 150°C).
    *   **Fuel level sensor:** Continuous fuel level monitoring.
    *   **Coolant temperature sensor:** Monitors coolant temperature (range 0° to 150°C).
    *   **Engine oil pressure sensor:** Monitors engine oil pressure (range 0 to 10 bar).

**7.2. Automotive Component Castings (Energy Monitoring)**
*   Casting is a process where molten metal is poured into sand molds to create durable, economical, single-piece automotive parts.
*   **Industry challenges:** Excess energy consumption, need for higher production, reduced energy costs, and improved quality. Specific energy challenges include managing maximum demand and power factor issues.
*   **IoT solution for energy monitoring:**
    *   **Digital energy meters** (replacing old analog ones) with current transformers are connected to furnaces.
    *   Data is sent from digital meters via an **IoT gateway to a centralized server**.
    *   The energy data is then pushed to the customer's customized **ERP system via APIs** for in-house use.
*   **Benefits:** Enables **batch tracking** of energy consumption (kWh readings) per product and aids in production planning. Implementation requires collaboration across factory teams.

**7.3. General Digital Input Measurement (On/Off, Cycle Time, Count)**
*   IoT can measure **on/off time (high/low time)** for digital inputs, focusing on duration rather than just status or count.
*   Applications include measuring **door open/close time** (e.g., annealing furnace) and **machine on/off time**.
*   It is used to calculate **cycle time** – the time taken to produce a particular part.
*   **Components involved:** An infrared-based **proximity sensor** providing digital on/off input, power supply, an intelligent **digital input module**, and a **Modbus Wi-Fi Gateway**.
*   The sensor connects to the digital input module, which then connects via Modbus to a **Modbus GPRS gateway** to send data to the cloud.
*   **Dashboard parameters derived:** Total off duration, total on duration, and total triggered count (e.g., production count). This information is valuable for monitoring machine status and production.

**7.4. Diesel Generator (DG) Monitoring**
*   IoT enables **smart monitoring of DG sets** for **proactive preventive maintenance**.
*   Allows **centralized, real-time monitoring** of DG sets across geographically separated locations.
*   **Benefits:** Better asset monitoring, improved equipment reliability and serviceable life, centralized control, and personnel access monitoring.
*   **IoT devices deployed:** GPS for location, video security cameras, and optical fingerprint readers for personnel entry/exit tracking.
*   **Parameters monitored:**
    *   **Input level:** Fuel level, derived fuel consumption and efficiency, engine on/off status, run hours, idle hours.
    *   **Output level:** Phase voltage, phase current, frequency, derived power factor, derived phase imbalance, peak load, and total power (kWh) consumed.
    *   **Analytics level:** Trends for fuel consumption, efficiency, output phase voltage, current, frequency, load, and power consumption.
*   **Specific benefits from IoT implementation:**
    *   **Real-time warning** on drops in efficiency, voltage/current, or abnormal loads.
    *   **Proactive serviceability** by monitoring performance trends to minimize downtime.
    *   **Optimized fuel management** by projecting daily consumption to avoid over/understocking.
    *   **Improved DG set reliability and life** through timely interventions.
    *   **Centralized tracking** generates usage/idle time reports for optimization.
    *   **Security surveillance** helps avert theft and maintains remote records of personnel access.
*   The solution involves an **energy panel meter (dual source)** to monitor mains and generator power, **temperature sensor modules** for chiller and BMC, a **digital input module** for chiller run time, and a **flow sensor with flow totalizer** for milk inflow/outflow. All data is sent via an **IoT gateway** (often GPRS due to rural locations) to the **Cloud platform** for alerts and analysis.

**7.5. Aircraft Parts Manufacturing (CNC Machine Monitoring)**
*   Aircraft parts are manufactured using high-end **Computer Numerical Controlled (CNC) machines** that operate with high precision, high speed, and require **zero tolerance/error** (zero PPM). These machines are complex and expensive.
*   **Challenges:** Maximizing machine time utilization, accurate **cycle time calculation** for production planning (critical due to long manufacturing times), and calculating **Overall Equipment Effectiveness (OEE)**.
    *   OEE is an international standard comprising **productivity, quality output, and availability**.
*   **IoT solution for CNC machines:**
    *   Machines (often from different manufacturers with varying protocols and communication ports) are modified to provide a **program completion pulse**.
    *   This pulse is connected to a **digital input card**, which then sends data to an **IoT gateway and the cloud**.
    *   The solution focuses on **counting and calculating downtimes and cycle times** from these pulses.
*   **Benefits:**
    *   Provides **real-time digital information to production planners** for optimized scheduling and rescheduling in case of downtime.
    *   Triggers **alerts (SMS, email)** to supervisors if a machine is down for extended periods, improving productivity.

**7.6. IoT Connected Workplace Solution (Organizational Operational Efficiency - OOE)**
*   This solution connects manufacturing unit machines with embedded sensors to track parameters and interfaces with operator mobile devices and an **ERP system**.
*   A **MATE (Human Machine Interface) module** syncs operator data (attendance, idle time) with machine status.
    *   This helps **optimize resource supply** (spares, raw materials) to match operator availability, reducing idle time and increasing productivity.
    *   It also links planned machine downtime with operator availability.
*   **Goal:** Improve **Organizational Operational Efficiency (OOE)**, a combination of **availability, performance, and quality**.
    *   **Availability:** Machine utilization data from controllers, job assignment from ERP.
    *   **Performance:** Comparison of planned vs. actual output/duration from ERP.
    *   **Quality:** Operator updates and inspection details via MATE.
*   **Analytics modules:**
    *   **Machine Scope Fusion (MSF):** Real-time analytics, providing a 360-degree view of the factory floor with live data feeds and trend charts for managers.
    *   **Machine Scope Genius (MSG):** Batch analytics, offering insights into inefficiencies through predictive analytics, identifying optimal maintenance times to reduce downtime, and providing visibility into machine faults and history.
*   **Dashboards** display measured trends and analytics, including OOE, loss analysis (identifying inefficiency points), health parameter (machine health/performance), and machine 360 (overall machinery productivity).

**7.7. Air Compressor Monitoring**
*   Air compressors convert electrical or fuel power into potential energy stored as pressurized air, used widely in industries for pneumatic tools, spray painting, cleaning, and HVAC systems.
*   **Critical parameters to monitor:** Pressure (multiple points), motor current, load percentage (air usage volume), vibration, oil temperature, and winding temperature.
*   **Challenges:** Compressors often run 24/7, are high energy consumers (compressed air is expensive), and require load balancing across multiple units. OEMs need remote monitoring to provide service and diagnose failures.
*   **IoT solution for air compressors:**
    *   OEMs integrate all necessary sensors (for motor current, temperatures, pressures) into a **central control panel**.
    *   An **IoT gateway connects to the control unit** (typically via RS485 protocol) to read parameters at regular intervals.
    *   Data is pushed to the **cloud** (often via GPRS or LTE due to varying local network availability).
    *   **Web analytical tools** are used for remote data analysis, and **AI/ML** can trigger alerts (e.g., low outlet pressure, high motor current, low oil level).
*   **Benefits for OEMs and end-users:** Enables **remote servicing** by allowing OEMs to monitor compressor parameters and advise customers on maintenance. Service engineers are better equipped with information and spares for efficient repairs.
