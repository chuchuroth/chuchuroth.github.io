
The sources provide comprehensive knowledge regarding the kinematics and statics of open-chain and closed-chain robots. This includes forward kinematics, velocity kinematics (Jacobian), inverse kinematics, and the relationship between end-effector wrenches and joint forces/torques.

Here is a summary of the technical information:

### I. Forward Kinematics of Open-Chain Robots
*   **Problem Definition**: The forward kinematics problem for open-chain robots is to determine the configuration of the **end-effector frame {b}** relative to a **fixed space frame {s}** (represented by the transformation matrix T_sb or T(theta)) given the **vector of joint angles theta**.
*   **Zero Configuration (Home Position)**: When all joint variables are set to zero, the robot is in its home position. The configuration of the {b}-frame at this zero configuration is denoted as **M** (T(0)). At the zero configuration, the {b}-frame typically has the same orientation as the {s}-frame.
*   **Screw Axis (S)**: A **screw axis** represents the motion of a rigid body and is defined by an angular component (omega) and a linear component (v).
    *   For a revolute joint, the screw axis has **zero pitch**. The angular component (omega) is a **unit vector** aligned with the axis of rotation. The linear component (v) can be visualized as the linear velocity of a point at the origin of the {s}-frame when the joint rotates with unit angular velocity, or calculated as **-omega cross q**, where q is any point on the joint axis expressed in the {s}-frame.
    *   For a prismatic joint, the screw axis has **zero angular component (omega)**, and the linear component (v) must be a **unit vector** aligned with the direction of translation.
*   **Product of Exponentials Formula**: This formula calculates the {b}-frame configuration T(theta).
    *   **Space-Frame Formulation**: The formula is expressed in terms of **space-frame screw axes (S)**, which are defined in the {s}-frame when the robot is at its zero configuration. The transformation is applied by **premultiplying M** by exponential transformations for each joint. For a serial robot with *n* joints, the procedure is:
        1.  Define the **M matrix**.
        2.  Define the **{s}-frame screw axes S_1 to S_n** for each joint when joint variables are zero.
        3.  Evaluate **T(theta) = e^[S_1 * theta_1] * e^[S_2 * theta_2] * ... * e^[S_n * theta_n] * M**.
        *   The relationship of a joint's screw axis to the {s}-frame is unaffected by motions of joints that are not between that joint and the {s}-frame.
    *   **Body-Frame Formulation**: An alternative formulation uses **body-frame screw axes (B)**, defined in the {b}-frame when the robot is at its zero configuration. The transformation is applied by **postmultiplying M** by exponential transformations. For a serial robot with *n* joints:
        1.  Define the **M matrix**.
        2.  Define the **{b}-frame screw axes B_1 to B_n** for each joint when joint variables are zero.
        3.  Evaluate **T(theta) = M * e^[B_1 * theta_1] * e^[B_2 * theta_2] * ... * e^[B_n * theta_n]**.
        *   The relationship of a joint's screw axis to the {b}-frame is unaffected by motions of joints that are not between that joint and the {b}-frame.
*   **Deriving Screw Axes by Inspection**: For many open-chain robots, screw axes (S or B) can be derived by inspecting a drawing of the robot at its zero configuration.

### II. Velocity Kinematics (Jacobian)
*   **Problem Definition**: Velocity kinematics studies the relationship between **joint velocities** (theta-dot) and the **end-effector velocity**.
    *   If end-effector configuration is represented by a minimum set of coordinates (x), then **x-dot = J * theta-dot**, where J is the Jacobian matrix.
    *   If end-effector velocity is represented by a **twist (V)**, then **V = J * theta-dot**.
*   **Jacobian Definition**: The Jacobian (J) is a matrix of partial derivatives relating joint velocities to end-effector velocities. Each column of the Jacobian represents the **end-effector velocity (or twist)** when a specific joint rotates at unit speed and all other joint velocities are zero.
    *   For a general open-chain robot, the Jacobian is a **6-by-n matrix**, where *n* is the number of joints.
*   **Space Jacobian (J_s)**:
    *   Maps joint velocities to the **twist V_s expressed in the space frame {s}**.
    *   It is a 6-by-n matrix.
    *   Each column J_s,i is the **spatial twist** corresponding to a unit velocity at joint *i* at the robot's current configuration.
    *   J_s,i is obtained by transforming the zero-configuration screw axis S_i using the transformation from the frame just before joint *i* to the {s}-frame. This transformation is a product of exponentials of screw axes of joints preceding joint *i*.
    *   **J_s,1 = S_1** (S_1 is the screw axis when the robot is at its zero configuration) because no joints are between joint 1 and the {s}-frame.
    *   The space Jacobian is **independent of the choice of the end-effector {b} frame**.
*   **Body Jacobian (J_b)**:
    *   Maps joint velocities to the **twist V_b expressed in the end-effector frame {b}**.
    *   It is a 6-by-n matrix.
    *   Each column J_b,i is the **body twist** corresponding to a unit velocity at joint *i* at the robot's current configuration.
    *   J_b,i is obtained by transforming the zero-configuration screw axis B_i using the transformation from the current {b}-frame to the frame just after joint *i*. This transformation involves the inverse of a product of exponentials of screw axes of joints following joint *i*.
    *   **J_b,n = B_n** (B_n is the screw axis when the robot is at its zero configuration) because no joints are between joint *n* and the {b}-frame.
    *   The body Jacobian is **independent of the choice of the space frame {s}**.
*   **Relationship between J_s and J_b**: J_b is obtained from J_s by the **matrix adjoint of T_bs**, and J_s is obtained from J_b by the **matrix adjoint of T_sb**.
*   **Jacobian Rank and Singularities**:
    *   The **rank of the Jacobian** can be no greater than **min(6, n)**.
    *   A Jacobian is **full rank** if its rank equals min(6, n).
    *   A Jacobian is **singular** at a configuration if its rank is less than the maximum rank it can achieve.
    *   At a singular configuration, the robot **loses the ability to move in one or more directions**.
*   **Jacobian Categories based on Joint Number (n)**:
    *   **n < 6 (Tall Jacobian)**: Robots are **kinematically deficient**, meaning the set of reachable configurations for the end-effector is less than 6-dimensional.
    *   **n = 6 (Square Jacobian)**: Often called **general purpose manipulators**, capable of general 6-dimensional rigid-body motion at their end-effectors.
    *   **n > 6 (Fat Jacobian)**: Robots are **redundant**, capable of achieving the same end-effector twist with different joint velocities, allowing internal arm motion not visible at the end-effector.
*   **Manipulability Ellipsoid**:
    *   Visualizes how close a robot is to being singular and its motion capabilities.
    *   A **unit sphere of joint velocities** (theta-dot^T * theta-dot = 1) maps through the Jacobian (J) to an **ellipse or ellipsoid of possible tip velocities (v_tip)**.
    *   The ellipsoid is defined by the quadratic equation **v_tip^T * A_inv * v_tip = 1**, where **A = J * J^T** (a symmetric, positive definite matrix).
    *   The **principal axes** of the ellipsoid are aligned with the **eigenvectors of A**, and the **half-lengths** of the ellipsoid along these axes are the **square roots of the eigenvalues** of A.
    *   As a robot approaches a singularity, the ellipsoid **collapses to a line segment**, stretching in directions it is easy to move and squashing where it is difficult.
*   **Manipulability Measures**: Single numbers to quantify how close a robot is to being singular:
    1.  **Ratio of longest to shortest axis** (lower-bounded by 1; if 1, ellipsoid is isotropic).
    2.  **Condition number** (square of the first measure).
    3.  **Square root of the product of eigenvalues of A** (proportional to the volume of the ellipsoid).
*   **Separation for Body Jacobian**: The 6-by-n body Jacobian can be split into a 3-by-n **angular velocity Jacobian (J_b-omega)** and a 3-by-n **linear velocity Jacobian (J_b-v)**, useful due to different units. These can be used to create separate angular and linear manipulability ellipsoids.

### III. Statics (Wrenches and Forces)
*   **Relationship between End-Effector Wrench and Joint Torques**:
    *   **tau = J^T * F**, where tau is the vector of joint torques/forces and F is the wrench applied by the end-effector (or the force to be resisted).
    *   This relationship holds irrespective of the frame (space or body) in which the Jacobian and wrench are expressed.
    *   It assumes the robot is at equilibrium and joint efforts solely resist end-effector forces.
*   **Force Ellipsoid**:
    *   Maps a **unit sphere of joint torques/forces** to an **ellipse or ellipsoid of possible tip forces**.
    *   Defined using the matrix that is the **inverse of the matrix defining the manipulability ellipsoid (J * J^T)^-1**.
*   **Reciprocal Relationship**: Force and manipulability ellipsoids have the **same principal axes**, and their principal semi-axis lengths are **reciprocals**. This means it is easy to apply force in a direction that is difficult to move, and difficult to apply force in a direction that is easy to move.

### IV. Inverse Kinematics of Open-Chain Robots
*   **Problem Definition**: Given a **desired end-effector configuration**, find the **joint positions (theta)** that achieve it.
*   **Nature of Solutions**: Unlike forward kinematics, inverse kinematics may have **zero, one, or multiple solutions**.
    *   Zero solutions if the desired configuration is outside the robot's **workspace**.
    *   One solution if on the workspace boundary.
    *   Multiple solutions if in the workspace interior (e.g., two for a planar 2R robot).
*   **Approaches to Solving**:
    *   **Analytic Closed-Form Solutions**: Available in some cases, exploiting geometric insight and specific robot structure. May not exist for arbitrary kinematics. Useful tools include the **two-argument arctangent (atan2)** function and the **law of cosines**.
    *   **Iterative Numerical Methods**: Used when analytic solutions are not available. Requires an initial guess and converges iteratively to one solution.
*   **Newton-Raphson Numerical Inverse Kinematics Algorithm**:
    *   **For coordinate-based end-effector configuration (x_d = f(theta))**:
        1.  Start with an **initial guess theta_0**.
        2.  Calculate the **end-effector error e = x_d - f(theta_i)**.
        3.  If `e` is small enough, theta_i is the solution.
        4.  Otherwise, update the guess: **theta_i+1 = theta_i + J_pseudo_inv * e**.
        5.  Repeat until convergence.
        *   **Initial guess should be close** to a solution for convergence.
    *   **For transformation matrix end-effector configuration (T_sd)**:
        1.  Start with an **initial guess theta_0**.
        2.  Calculate the current end-effector configuration **T_sb(theta_i)** using forward kinematics.
        3.  Determine the configuration of the desired frame relative to the current end-effector frame: **T_bd = T_sb(theta_i)^-1 * T_sd**.
        4.  Extract the **body twist (V_b)** that moves {b} to {d} in unit time: **[V_b] = log(T_bd)**. This V_b serves as the error vector.
        5.  If the angular (omega_b) and linear (v_b) components of V_b are small, theta_i is the solution.
        6.  Otherwise, update the guess: **theta_i+1 = theta_i + J_b_pseudo_inv * V_b**.
        7.  Repeat until convergence.
*   **Pseudoinverse of J**: Used when the Jacobian is non-square or singular.
    *   If multiple solutions exist (redundant robot), the pseudoinverse finds the solution with the **smallest joint velocity length** (minimal change in joint values).
    *   If no exact solution exists (kinematically deficient or singular robot), the pseudoinverse finds a solution that **minimizes the error** in satisfying the equation.
*   **Inverse Velocity Kinematics**: Finds joint velocities (theta-dot) that achieve a desired end-effector twist (V_d). Solved by **theta-dot = J_pseudo_inv * V_d**.

### V. Closed-Chain Robots
*   **General Characteristics**:
    *   More complex kinematics and statics due to diverse designs and **loop-closure equations**.
    *   May have unique classes of **singularities** not present in open chains.
    *   **Actuation**: Many joints are often unactuated, unlike open-chain robots where typically each joint has a motor.
    *   **Workspace**: Tend to have a **small workspace** due to constraints from parallel legs.
    *   **Strength/Stiffness**: Tend to be **stiff and strong** as end-effector force is distributed among legs, unlike open-chain robots which are weaker as each joint supports the full force.
    *   **Forward Kinematics**: Generally **challenging** to evaluate, often involving complex nonlinear equations and multiple solutions.
    *   **Inverse Kinematics**: Can sometimes be **straightforward**, especially for parallel robots like the Stewart platform.
*   **Examples of Closed-Chain Robots**:
    *   4-DOF robot arm with parallelogram-type linkage.
    *   Delta robot (3-DOF or 4-DOF).
    *   **Stewart Platform**: A 6-DOF parallel robot with a moving platform attached to a base via six actuated prismatic legs with spherical/universal joints.
*   **Inverse Kinematics of Stewart Platform**:
    *   Straightforward: Given desired T_sb, the length of each leg (theta_i) can be calculated as the distance between the transformed end-effector joint point and the base joint point (e.g., ||T_sb * b_ib - a_is||).
*   **Inverse Velocity Kinematics of Stewart Platform**:
    *   The **inverse of the space Jacobian (J_s^-1)** can be constructed where the *i*-th row is the transpose of a screw axis V_i, which represents the motion capability of the *i*-th leg.
    *   Then, **theta-dot = J_s^-1 * V_s**.
*   **Singularities in Closed-Chains**:
    *   More complex than in open-chains. The **constraint Jacobian** (from loop-closure equations) losing rank is a common cause.
    *   Examples include **configuration-space singularities, actuator singularities, and end-effector singularities**.
*   **Forward Kinematics of Closed-Chains**:
    *   Often involves solving one or more complex nonlinear equations.
    *   Generally has **multiple possible solutions** (e.g., up to 6 for a 3-by-RPR robot, up to 40 for a 6-DOF Stewart platform).
    *   In practice, **iterative numerical methods** (similar to Newton-Raphson for open-chain IK) are common, using a nearby solution as an initial guess.
