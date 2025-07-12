---
layout: post
title:  "Robotics Engineering and Applications module 1"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---

Here is a comprehensive summary of the knowledge-based information from the sources, presented without colloquial language and with key concepts bolded for clarity:

### Fundamentals of Robotics

*   **Robotics** is the study of designing, developing, and building robots for use in manufacturing and other fields.
*   **Goals of Robotics**: Increase productivity, reduce product lead time, reduce manpower, improve product quality, decrease man-hours lost due to accidents, and achieve high-speed, consistent production.
*   **Interdisciplinary Nature**: Robotics engineering encompasses mathematics, physics, mechanical engineering, electrical engineering, computer engineering, and science.
*   **Application**: Robotics is applied in engineering automation for automatic control of manufacturing, metal handling, and assembly processes, requiring minimal human intervention.
*   **Core Concept**: Robotics is the study of the intelligent link between **perception** (sensory system, connection, joints, links, control system, environment) and **action** (mechanical system, motion, manipulation).
*   **Definition of a Robot**: A reprogrammable, multipurpose manipulator, configurable in three or more axes, which may be stationary or movable and controlled by computers.
*   **Industrial Robot Definition (Robot Institute of America/ROBOTICA)**: A programmable, versatile manipulator designed to move material, parts, tools, or specialized equipment.
*   **Laws of Robotics (Asimov, 1942)**:
    1.  A robot may not injure a human being or allow a human being to come to harm through inaction.
    2.  A robot must obey human orders, except when such orders contradict the First Law.
    3.  A robot must safeguard its own existence as much as doing so does not break the First and Second Laws.
*   **First Modern Industrial Robot**: The **Unimate**, constructed by George Devol and Joseph Frederick Engelberger during the 1960s. Joseph Frederick Engelberger is known as the father of robotics. Unimate was a hydraulic manipulator arm capable of repeating movements, used by automobile manufacturers for metalworking and welding.

### Evolution of Robotic Engineering

The evolution of robotic engineering is categorized into generations based on their capabilities:
*   **First Generation (Remote Controlled Robots)**: Possess a simplified mechanical arm, capable of repeated accurate motions at high speed for extended periods.
*   **Second Generation (Autonomous Robots)**: Equipped with primitive intelligent machinery and sensory devices (e.g., pressure, proximity, touch, radar, sonar sensors, machine-vision systems) to gather information about surroundings. A control unit analyzes sensor data to drive the robot. Programmable and controlled by standard programmable logic controllers or minicomputers. Examples include autonomous underwater/surface/aerial vehicles (AUV, ASV, AAV).
*   **Third Generation (Networked Robots)**: Smart robots capable of working independently with an internal controller, operating without external supervision (computer or human). Includes "insect robots" with machine intelligence.
*   **Fourth Generation (Cognitive Robotics)**: Considered the engineering branch of embodied cognitive science and embedded cognition, involving robotic process automation and machine learning. Examples include robots that evolve or have biological and mechanical parts.
*   **Fifth Generation (Robots with Artificial Intelligence)**: Complete robots driven by AI support systems like machine learning, computer vision, and reinforcement learning. They possess the ability to make decisions with miniaturized sensors and controlled circuitry.

### Automation and Robotics

*   **Automation**: Utilizes principles of mechanical, electrical, electronics, and computer science-based systems to manage manufacturing and production. Examples include transfer lines, assembly machines, feedback control systems, pneumatic-controlled machine tools, and robots.
*   **Types of Automation**:
    *   **Fixed Automation**: Processing, assembly, and operation order are fixed in specially configured equipment. Modifications are difficult. Used for high production numbers with minimal product variety (e.g., automobile industry).
    *   **Programmable Automation**: Machinery designed to handle varied product configurations, allowing changes to process sequences via a control program. Suitable for low to moderate volume batch production with more product variety. Features high general-purpose investments, comparatively low productivity, but allows product variety. Examples include industrial robots and numerically controlled machine tools.
    *   **Flexible Automation**: A computer-integrated production system that reduces time lost between product reloads. Software allows creation of new items and modification of physical configurations without time loss. Product variety does not affect productivity. Enables substantial batch production of new variants alongside routine mass production. Improves communication and material handling between workstations (e.g., Flexible Manufacturing Systems - FMS).
*   **Reasons for Automation with Robotics**: Increase labor productivity, reduce labor costs, minimize labor shortages, achieve high-quality products, avoid non-automation-related costs, reduce manufacturing lead time, and improve worker safety.
*   **Hierarchical Architecture of Automation**: Five levels for automatic control manufacturing:
    1.  **Device Level**: Controls machine operation via sensory devices, actuators, and hardware elements.
    2.  **Machine Level**: Individual machines.
    3.  **Cell or System Level**: Groups of machines.
    4.  **Plant Level**: Entire production system plant.
    5.  **Enterprise Level**: Corporate information system.

### Industrial Robot Characteristics and Components

*   **Qualities of Industrial Robots**: General-purpose, programmable, configurable, often with humanoid qualities. Used in hazardous situations, routine jobs, for consistency and precision, for handling materials difficult for humans, continuous operation, reprogrammable, adaptable, and connectable to additional computer systems. They are diligent, reliable, and can work in dangerous or inaccessible environments (e.g., Mars surface, ocean bottom, nuclear power plants).
*   **Vital Components of an Industrial Robot**:
    *   **Robotics knowledge base** (for design and operation).
    *   **Robotics dynamic system models and analysis**.
    *   **Feedback control**.
    *   **Sensors**: Devices that gather information about the robot's internal state and surroundings (e.g., pressure, proximity, touch, radar, sonar, machine-vision).
    *   **Actuators**: Devices that enable motion and manipulation.
    *   **Signal conditioning**.
    *   **Hardware**.
    *   **Computer interfacing**.
    *   **System memory**.
    *   **Robotic operating system (ROS)**.
    *   **Programming**.
    *   **Controller**: Also called the "robot's brain" or "intelligence," responsible for controlling important parts, saving information, data on working conditions, and running programs. Its performance is enabled by data algorithms.
    *   **Power Unit**: Electric, pneumatic, or hydraulic sources. Electric robots are quiet, efficient, and low maintenance. Pneumatic robots use compressed air. Hydraulic robots use pressurized oil for heavy-duty tasks.
    *   **Manipulator/Linkages**: Assembly of structures or linkages connected by pin joints for specific applications. Used to move tools and grippers in the work volume and set tools.
    *   **Base**.
    *   **Interface cables**.
    *   **Gripper**: A handling mechanism subsystem for momentary interaction with elements, constraining object position and orientation for transport or joining.
    *   **End Effector**: A general term for the "robot's hand" attached to the wrist assembly, encompassing grippers and tools. Performs tasks like machining, spray painting, arc welding, spot welding, measuring, and inspection.
    *   **Wrist Assembly**: Attached to the end of the arm; end effectors connect to it. Its function is to orient end effectors.
    *   **Robot Joints**: Facilitate sliding and rotating motions of components. Links are stiff elements connected at joints. Kinematics is the study of how robot links and joints are made and how robots move.

### Classification and Applications of Industrial Robots

*   **Classifications (Japanese Industrial Robot Association - JIRA, and Robotics Institute of America - RIA)**:
    1.  Robots to handle materials
    2.  Permanent sequence robot
    3.  Variable sequence robot
    4.  Playback robot
    5.  Numerically controlled robot
    6.  Sixth sense intelligent robot
*   **Classifications (Association Francaise de Robotique - AFR)**:
    1.  Manual operated or controlled material handling robot
    2.  Programmed or automatically controlled material handling robot
    3.  Programmable and servo control robots (interact with environment)
*   **Industrial Robot Manufacturers**: ABB Robotics (Swedish), KUKA Robotics (German), Adept Technology (United States), Yaskawa Motoman (Japanese), FANUC (Japanese).
*   **Applications of Industrial Robots**:
    *   Assembly in automobiles.
    *   Spot welding of automobile bodies.
    *   Parts transfer.
    *   Pick and place.
    *   Material handling in foundries.
    *   Painting and coating.
    *   Electronics manufacturing.
    *   Palletizing.
    *   Packaging.
    *   Machine loading.
    *   Sorting.
    *   Feeding, fastening, joining.
    *   Inspection of assembly components.
    *   Heat-treatment in metal casting.
    *   3D printing.
    *   CNC machines.
    *   Coordinate measuring machines and plotters.

### Robot Configurations

**Robot configuration** is defined as the movement of all links and the end-effector, determining the robot's workspace. It allows tools to move quickly, accurately, and repetitively within a 3D workspace.

1.  **Cartesian Robot Configuration (Linear Robot or XYZ Robot/Gantry Robots)**:
    *   **Movement**: Tool moves linearly along X, Y, and Z Cartesian coordinates.
    *   **Work Envelope**: Box-like or rectangular.
    *   **Joints**: Three linear joints (prismatic joints) at right angles to each other.
    *   **Applications**: 3D printers, pick and place, loading/unloading, material handling, handling plastic molding, CNC machines, coordinate measuring machines, plotters.
    *   **Advantages**: High accuracy and speed, lower cost, simple operation, high payloads, versatile, simplifies control systems.
    *   **Disadvantages**: Requires large operating space.

2.  **Cylindrical Robot Configuration**:
    *   **Movement**: Tool rotates around a central axis, moves toward/away from the central axis, and moves up/down along the central axis.
    *   **Work Envelope**: Cylinder shape.
    *   **Joints**: A combination of prismatic and revolute joints.
    *   **Applications**: Assembly operations, machine tool handling, die-cast machines, spot welding.

3.  **Spherical Configuration**:
    *   **Movement**: Tool rotates around a central axis, turns around a second axis at a 90-degree angle to the central axis, and moves back/forth along an axis.
    *   **Work Envelope**: Sphere shape.
    *   **Applications**: Die-casting, injection molding, welding, material handling.

4.  **Selective Compliance Assembly Robot Arm (SCARA) Configuration**:
    *   **Developer**: Hiroshi Makino.
    *   **Movement**: Uses pivot points for a combination of Cartesian and cylindrical motions, allowing quick movement in arcs or curvilinear paths. Has four axes of movement, each driven by a servo motor.
    *   **Compliance**: Flexible in X-Y axes, rigid in Z-axis due to parallel axis joint layout.
    *   **Work Envelope**: Donut-shaped.
    *   **Advantages**: High speed, excellent for short-stroke, fast assembly, and pick and place applications.
    *   **Disadvantages**: Typically requires dedicated robot controller and a line master controller (PLC or PC).
    *   **Applications**: Assembly, packaging, palletizing, machine learning, measurement, pick and place.

5.  **Articulated Robot Configuration**:
    *   **Joints**: Rotary joints, ranging from two to ten or more interacting joints. Joints can be parallel or orthogonal.
    *   **Structure**: Similar to the human arm, typically requires a shoulder, elbow, and wrist joint.
    *   **Movement**: Can reach any point in 3D space.
    *   **Applications**: General palletizing, food packaging, automated foundry industries, heat-treatment robots, metal casting, spot welding.
    *   **Advantages**: High speed, large working envelope, unique control in welding and painting.
    *   **Disadvantages**: Requires dedicated robot controller and a line master controller (PLC or PC).

6.  **Parallel or Delta Robot Configuration**:
    *   **Structure**: Uses parallel linkages to sweep out its workspace quickly. "Spider-like" robots built from joint parallelograms connected to a common base.
    *   **Movement**: Very fast for lightweight pick and place tasks, sorting, component selection, and packaging. Prevents redundant movements with short, simple chains.
    *   **Work Envelope**: Contact lens shaped.
    *   **Applications**: Flight simulators, automobile simulators, in-work processors, photonics/optical fiber alignment, candy packaging.
    *   **Advantages**: Very high speed, excels in high-speed, lightweight pick and place applications.
    *   **Disadvantages**: Requires dedicated robot controller and a line master controller (PLC or PC).

### Mechanical Joints

**Joints** are connections between individual links, allowing specific and predefined relative motions (translational or rotational). Ideal joints can exhibit non-trivial mechanics like flexibility, hysteresis, backlash, and friction.

*   **Linear Joint (Type L joint)**: Relative motion is translational sliding, with parallel axes of the two links.
*   **Orthogonal Joint (Type O joint)**: Relative motion is translational sliding, but the output link is perpendicular to the input link.
*   **Rotational Joint (Type R joint)**: Provides relative rotational motion with the axis of rotation perpendicular to the axis of the input and output links.
*   **Twisting Joint (Type T joint)**: Provides rotary motion, with the axis of rotation parallel to the axis of the two links.
*   **Revolving Joint (Type V joint)**: The input link's axis is parallel to the joint's rotation axis; the output link's axis is perpendicular to the rotation axis.
*   **Prismatic Joint**: Facilitates relative translation along an axis between two links.
*   **Revolute Joint**: Facilitates relative rotation about an axis.
*   **Universal Joint**: Comprises a pair of revolute joints where the joint axes are mutually orthogonal.
*   **Spherical Joint**: Allows three rotational degrees of freedom (not explicitly defined in sources but listed as a common type).
*   **Screw Joint**: Allows coupled rotational and translational motion (not explicitly defined in sources but listed as a common type).

### Degrees of Freedom (DOF)

*   **Definition**: An **independent variable** used to describe the mobility of a robot or the relative motion permitted by an ideal joint. A robot requires 'n' independent variables to describe all its possible configurations.
*   **Calculation**: For planar mechanisms, Lambda = 3; for spatial mechanisms, Lambda = 16. The formula provided is N = Lambda * (n-1) - Sum(k, i=1, Lambda - fi), where N is number of degrees of freedom, n is number of links, k is number of joints, and fi is degrees of freedom for joint i.

### Kinematics

**Kinematics** studies how the configuration of a robot changes as joint variables are varied. It focuses on geometry, not forces or moments.

*   **Forward Kinematics**:
    *   **Problem**: Determines the **position, velocity, or acceleration** of specific points on the robot (e.g., end-effector) given the time histories of the joint variables (angles for revolute, displacements for prismatic).
    *   **Input**: Joint variables (e.g., Theta_1, Theta_2 for an RR manipulator, or Theta_1, Theta_2, Theta_4 for a 4-DOF manipulator, along with link lengths L_1, L_2).
    *   **Output**: End-effector position in world space (e.g., x, y, or x, y, z coordinates).
    *   **Methodology**: Involves trigonometric manipulations to resolve link positions with respect to coordinate axes.

*   **Inverse Kinematics**:
    *   **Problem**: Determines the **joint variables and their derivatives** for a given position, velocity, and acceleration of a point on the robot system.
    *   **Input**: End-effector position in world space (e.g., x, y, or x, y, z coordinates) and link dimensions.
    *   **Output**: Joint parameters (e.g., Theta_1, Theta_2 for an RR manipulator, or Theta_1, Theta_2, Theta_4 for a 4-DOF manipulator).
    *   **Challenges**: It is generally more difficult than forward kinematics and can yield no solution or multiple solutions depending on the robot's geometry and design.
    *   **Methodology**: Involves mathematical manipulations (e.g., squaring and adding equations) to solve for joint variables.

### Dynamics

**Dynamics** considers forces and moments that enable movement, unlike kinematics which is confined to geometry.

*   **Governing Equation**: For many robotic systems, the governing equation involves a non-linear generalized mass matrix (M(q)), a non-linear function including Coriolis and centripetal terms (N(q, q-dot)), and a force/torque vector applied by actuators (T).
*   **Forward Dynamics**:
    *   **Problem**: Solves for the **state variables** (joint variables and their derivatives) given the input forces and torques over time.
    *   **Purpose**: Determines how a specific set of input forces and torques induce a corresponding time history of the joint variables. It finds the dynamic behavior of the system given an input actuation time history.
*   **Inverse Dynamics**:
    *   **Problem**: Asks what **forces or torques** are required to yield a specific desired dynamic behavior (i.e., a specific time history of joint variables).
    *   **Application**: Control theory and inverse dynamic analysis techniques help formulate feedback control laws to calculate appropriate actuation input trajectories as a function of desired and estimated states.

### Homogeneous Transformation

*   **Concept**: Deals with **rigid body transformations**, encompassing rotation and translation. Scaling is generally not used in this context.
*   **Denavit-Hartenberg Convention**: A popular convention for homogeneous transformations in robotic systems (e.g., SCARA, cylindrical, articulated robots).
*   **Methodology**: Uses **rotation matrices** to describe orientation and a vector to describe translation. Each link in a robot system has a corresponding rotation matrix. The transformation of an end-effector with respect to a base is found by multiplying individual transformation matrices for each joint and link.

### End-Effectors and Grippers

*   **End-Effectors**: Robotic "fingers" attached to the robot's arm that interact with the environment. They are interchangeable and perform specific tasks. Wheels and feet of mobile robots are not considered end-effectors as they aid mobility.
    *   **Types**:
        *   **Grippers**: Used at workstations to acquire and manipulate objects or components.
        *   **Tools**: Used to handle and perform processes like spot/arc welding, spray painting, drilling, 3D printing, and measuring.
*   **Grippers**: A handling mechanism subsystem for momentary interaction with an element, constraining its position and orientation for tasks like transporting or joining.
    *   **Main Types (based on grasping method)**:
        *   **Impactive**: Jaws or claws that grab by direct impact.
        *   **Aggressive**: Pins, needles, or hacks that penetrate the material (e.g., textiles, carbon/glass fiber bundles).
        *   **Astrictive**: Surface suction via vacuum, magneto, or electro adhesion.
        *   **Contiguous**: Adhesion requiring direct contact using glue, surface tension, or freezing.
    *   **Operating Principle**: Often involve compressed air forcing a piston to open/close jaws through mechanical linkage. Friction secures the object.
    *   **Friction Factors**: Type of surface (e.g., metal on metal, elastomers on metal), surface texture (smooth/rough), and holding force (polyurethane pads can increase friction).
    *   **Classification (based on grasping method)**: Mechanical gripper, vacuum gripper, magnetic gripper, pneumatic/air gripper, hooks and scoops, adhesive gripper, bladder gripper.
    *   **Classification (based on contact during grasping)**: Point, line, or surface contact.
    *   **Specific Gripper Types**:
        *   **Mechanical Gripper**: Clamps objects using finger force. Used for picking, moving, placing, or holding parts, including in dangerous conditions. Types include parallel, angular, and toggle jaw movements. Can have two, three, or multi-fingers. Can be external (jaws close to hold) or internal (jaws open from inside to hold). Actuation mechanisms include linkage, slider-crank, gear and rack, cam follower, lead screw, and rope and pulley.
        *   **Vacuum Gripper**: Suitable for smooth, flat, clean objects; not for components with holes. Uses vacuum cups (suction cups) made of rubber or elastic materials, powered by a vacuum pump with compressed air. Can hold workpieces during power outages but require clean surfaces. The air pump can be loud.
        *   **Magnetic Gripper**: Grips ferrous materials. Requires full contact for effectiveness. Can pick up irregularly shaped objects if the magnet is strong enough.
            *   **Electromagnets**: Powered by direct current, lose magnetism when power is off.
            *   **Permanent Magnets**: Manipulate materials without external power, but require a separator or external force to release the workpiece.
            *   **Benefits**: Single surface grasping, can grasp material with holes, quick grasping, no distinct designs needed for various sizes.
            *   **Drawbacks**: Workpiece slippage at high speeds, weakened by oil, machining chips can stick, temperature-sensitive.
        *   **Pneumatic/Air Gripper**: Uses a lever mechanism to transfer piston motion from a pneumatic system to fingers. Switching valves actuate the grippers.
        *   **Hooks and Scoops**: Simple grippers. Hooks lift components via handles, eyeballs, or rings, useful for overhead conveyors but lack exact alignment. Scoops/ladles transport molten metal or large amounts of materials, but control can be difficult, and spillage is a problem.
        *   **Adhesive Gripper**: Uses adhesive substances (glues, bonding agents) to grasp workpieces. Repeated use reduces tackiness, requiring feeding mechanisms for continuous adhesive ribbon. Easy to use as long as the glue is sticky. Handles fabrics and lightweight/heavy objects, requires one contact surface.
        *   **Bladder Gripper**: An expandable, doughnut-shaped or cylindrical inflatable sleeve that picks up rod or cylinder-shaped objects by enlarging and tightening around them. Force sensors can detect and adjust pressure.
    *   **Gripper Selection and Design Factors**: Must reach workpiece surface, hold varying sizes, not distort/scratch fragile parts, hold a larger area for stability, adaptable pads for more connections, consider workpiece size for accurate positioning, interchangeable fingers for different sizes.
    *   **Gripping Force Considerations**: Workpiece weight, grasping at center of mass, movement speed, grasping position, and whether friction or physical constriction is used.
    *   **Steps for Gripper Design**: Determine object dimensions, weight, shape, material, density, delicateness; identify grab points; determine grasping force; design fingertip sensors and control system; select gripper mechanism and operation; determine actuator size based on mechanism efficiency.

### Robot Selection Criteria

Choosing the right robotic system involves considering quantitative and qualitative features, production demands, manufacturing system design, and economic impact.

*   **Specific Robot for Applications**:
    *   **SCARA Robot**: For compact pick and place applications.
    *   **Articulated Type Robot**: For pick and place with quick insertion of small objects.
    *   **Cobot**: For pick and place applications alongside human staff.
*   **Robot Characteristics for Selection**:
    *   **Payload Capacity**: Amount of mass the robot's wrist can support, including end-of-arm tooling weight. Must support the payload within the specified range and handle minor cyclical variations.
    *   **Workspace**: The robot's maximal horizontal and vertical reach (envelope). The required region of operations for the tooltip must be contained within this envelope.
    *   **Accuracy**: Minimal inaccuracy a robot should make to reach a desired location, which can vary with speed, positioning, and payload.
    *   **Repeatability**: The capability of the robot to achieve the precise same position consistently in each cycle.
    *   **Computational Efficiency**: Rate at which input is processed and computations performed for real-time operation and control. Algorithm and controller costs must be weighed against this.
    *   **Resolution**: Comparison of minimum and maximum values of operating parameters for applicability within the workspace.
    *   **Manipulability**: How the robot's connections and joints can travel and reorient themselves, enhancing usefulness.
    *   **Power Source Requirement**: Installation site must have required power specifications (e.g., distinct grounding for welding, uniform voltage for painting).
    *   **Axis and Joint Type**: Kinematic specifics (link and joint types) impact payload, workspace, manipulability, etc..
    *   **Project Specifications**: Robot must adhere to application requirements; flexibility in operations increases utility.
    *   **Robot Speed**: Robot should operate at high speed with minimal vibrations, though speed varies with payload and geometry.
    *   **Weight of the Robot**: Contributes to installation site dead weight and overall power requirements, especially on mobile platforms. Lighter robots are more susceptible to vibrations.
    *   **Electrical Drives**: Critical for specific applications. Robots with direct-drive electric motors to joints may have backlash; gear-based connections have less backlash. Influences payload capacity, resolution, and precision.
    *   **Controller Cards**: Must have capacity and programming flexibility. Interfaces (touchscreen) and peripherals (coding control chip) are selection criteria.
    *   **Hydraulic Drives**: Practical for demanding, cyclic operational needs. Selection criteria include closed-loop internal air pressurization.
    *   **Types of Cables and Harness**: Cable routing and harness requirements must match project specifications.
    *   **Singularity**: Geometric restrictions in robot linkages may require significant computational or input efforts in small workspace areas. Avoiding these is necessary.
    *   **Dexterity**: A quantity reflecting geometric limits on velocity, singularity, and other performance aspects. Superior dexterity is often preferred for complex jobs.
    *   **Number of Axes**: Simple applications may require fewer axes/joints; complex applications (welding, painting) may require more. Achieved by selecting appropriate architecture.
    *   **Servos**: Can be direct drive or gear drive (direct or epicyclical gear trains). Influences overall performance and repeatability.
    *   **Precision**: Robot's repeatability is based on its precision, ensuring proper repetition.
    *   **Breakdown Causes**: Understanding failure causes is crucial. Shoddy design impacts repeatability and reliability.
    *   **Mean Time to Repair (MTTR)**: High MTTR suggests frequent failure, lack of spare parts, or weak supplier service, negatively impacting choice. Fast servicing is desirable.
    *   **Mean Time Between Failures (MTBF)**: Should be as large as feasible for consistent performance; estimates overall breakdown time.
*   **Other Considerations**: Compact and economical automation design, robot controller performance, reasonable cost in offline programming, low energy consumption, security code, less coaching for workers, documented unit of time between failures, high permissible moment of inertia, cycle time for continuous operation, and brand name.

### Robot Supplier Characteristics

*   **Supplier Service Quality**: Companies may benefit from economies of scale through agreements with specific suppliers.
*   **Total Cost**: A primary determining factor, but quality and return on investment are equally important.
*   **Supplier Rating**: User companies rate providers based on past purchases, post-sale services, and robot performance, relying on these ratings for new purchases.
*   **Spare Parts Availability**: Rapid availability reduces robot downtime and favorably affects robot choice.
*   **Local Supplier Network**: A local chain of retail stores and service facilities is better equipped for maintenance, training, or breakdown issues than overseas headquarters.
*   **Warranty Terms**: Suppliers provide warranties and replacement parts; superior warranty conditions influence decision-makers.
