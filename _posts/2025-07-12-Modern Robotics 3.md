---
layout: post
title:  "Modern Robotics 3"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---


The sources provide extensive knowledge regarding robot dynamics, trajectory generation, and motion planning. The key concepts and formulations are detailed below:

### Robot Dynamics

**I. Formulations for Dynamics Problems**
Robot dynamics problems involve calculating motion given forces or vice-versa. Two primary approaches are used:
*   **Lagrangian Formulation**: A variational approach based on the kinetic energy (K) and potential energy (P) of the robot.
    *   The **Lagrangian (L)** for a mechanical system is defined as its kinetic energy minus its potential energy (L = K - P).
    *   **Potential energy (P)** depends only on the configuration (theta), while **kinetic energy (K)** depends on both configuration (theta) and joint velocities (theta-dot).
    *   The vector of **joint forces and torques (tau)** is derived from the time derivative of the partial derivative of L with respect to theta-dot, minus the partial derivative of L with respect to theta.
    *   Tau is dual to theta-dot, meaning their dot product represents power consumed or produced by the joints.
    *   **Equations of Motion**: For an n-joint robot, the general form is **tau = M(theta) * theta-double-dot + c(theta, theta-dot) + g(theta)**.
        *   **Mass Matrix (M)**: An n-by-n matrix, positive definite and symmetric, that depends on the joint configuration (theta). It describes the inertia of the robot and can be used to express kinetic energy as one-half theta-dot-transpose * M * theta-dot. Its elements indicate how inertia about each joint varies with arm configuration.
        *   **Velocity-Product Term (c)**: A vector composed of terms that are quadratic in joint velocities (e.g., theta_i-dot-squared or theta_i-dot * theta_j-dot).
            *   **Centripetal terms**: Terms with the square of a single joint velocity.
            *   **Coriolis terms**: Terms with a product of two different joint velocities.
            *   These terms arise because joint coordinates are not inertial.
            *   They can also be expressed as theta-dot-transpose * Gamma(theta) * theta-dot, where Gamma consists of Christoffel symbols of the mass matrix, or as the product of a Coriolis matrix and the joint velocity vector.
        *   **Gravity Term (g)**: A vector that depends on the configuration (theta) and arises from potential energy (e.g., due to gravity or springs).
        *   **End-effector Wrench (F_tip)**: An additional term, Jacobian transpose * F_tip, can be added to the right-hand side to account for forces and torques applied by the end-effector to the environment.
*   **Newton-Euler Formulation**: Derived directly from **F = m*a** applied to each individual link (rigid body) of the robot.
    *   **Advantage**: Leads to an efficient recursive algorithm for calculating inverse dynamics.
    *   **Rigid Body Dynamics**: For a single rigid body, the total wrench **F_b** (moment m_b and force f_b) needed to accelerate the body with acceleration **V_b-dot** when moving with a twist **V_b** can be expressed as:
        *   **f_b = m * v_b-dot + [omega_b] * v_b**.
        *   **m_b = I_b * omega_b-dot + [omega_b] * I_b * omega_b**.
        *   Where **m** is total mass, **v_b** is linear velocity, **omega_b** is angular velocity, **I_b** is the **inertia matrix**.
        *   **Inertia Matrix (I_b)**: Symmetric and positive definite. Its elements indicate the moment of inertia and products of inertia. Principal axes of inertia are aligned with its eigenvectors, and principal moments of inertia are its eigenvalues, leading to a simplified diagonal form when the body frame is aligned with these axes.
    *   **Spatial Inertia Matrix (G_b)**: A 6-by-6 matrix defined for a rigid body, incorporating both rotational inertia (I_b) and mass (m). It is symmetric and positive definite.
        *   Kinetic energy of a rotating and translating rigid body: one-half * V_b-transpose * G_b * V_b.
        *   The **Lie bracket** (little-adV_1 * V_2) for 6-dimensional twists is analogous to the cross-product for 3-dimensional vectors, measuring how motion along V_2 changes if the body follows V_1.
        *   The rigid body equations of motion can be compactly written as: **F_b = G_b * V_b-dot - little-adV_b-transpose * G_b * V_b**. The second term is a velocity-product term.

**II. Dynamics Problems**
*   **Forward Dynamics Problem**: Calculates joint accelerations (theta-double-dot) given current joint positions (theta), joint velocities (theta-dot), and applied joint forces and torques (tau). Useful for simulation.
    *   Can be solved using the inverse dynamics algorithm.
    *   The mass matrix M(theta) and the combined c, g, and F_tip terms can be found by running the inverse dynamics algorithm multiple times.
    *   The problem reduces to solving **M * theta-double-dot = known vector**.
*   **Inverse Dynamics Problem**: Finds the joint forces and torques (tau) needed to create specific joint accelerations (theta-double-dot) for given joint positions and velocities. Useful in robot control.
    *   **Recursive Newton-Euler Inverse Dynamics Algorithm**: An efficient algorithm for open-chain robots.
        *   **Forward Iterations (Link 1 to N)**: Calculate the configuration, twist (V_i), and acceleration (V_i-dot) for each link.
            *   Twist of link *i* is calculated from the twist of link *i-1* (expressed in frame *i*) plus the added velocity due to joint *i*'s velocity.
            *   Acceleration of link *i* includes the acceleration of link *i-1* (expressed in frame *i*), acceleration from joint *i*'s acceleration, and a velocity-product term.
        *   **Backward Iterations (Link N to 1)**: Calculate the required joint forces and torques (tau_i).
            *   Wrench (F_i) required for link *i* is the sum of the wrench from link *i+1* (expressed in frame *i*) and the wrench needed to accelerate link *i*.
            *   Joint torque tau_i is the component of F_i along the joint screw axis.
        *   Advantages: No differentiation involved and computationally efficient due to recursive nature.

**III. Advanced Dynamics Concepts**
*   **Task-Space Dynamics**: Formulates dynamics in terms of end-effector motions and wrenches.
    *   If the Jacobian (J) is invertible, the end-effector wrench (F) equals **Lambda(theta) * V-dot + eta(theta, V)**.
    *   **Lambda(theta)**: Robot's mass matrix expressed in task space.
    *   **eta(theta, V)**: Sum of velocity-product and gravity terms expressed as an end-effector wrench.
*   **Dynamics with Constraints**: For robots with constraints (e.g., nonholonomic due to wheels, loop-closure in parallel robots, feet contact in humanoids, or environmental contact like erasing a whiteboard).
    *   Constraints can be expressed as **b(theta) = 0** for configuration constraints or **A(theta) * theta-dot = 0** for velocity constraints (Pfaffian constraints).
    *   Assumed workless constraints, meaning forces enforcing them do no work.
    *   Constraint torques (tau_con) are a linear combination of the rows of A, with coefficients being Lagrange multipliers (lambda).
    *   The dynamic equation becomes **M * theta-double-dot + h = tau + A-transpose * lambda**.
    *   A projection matrix **P(theta)** can be used to eliminate Lagrange multipliers, leading to **P * tau = P * M * theta-double-dot + P * h**. P projects joint torques to components that move the robot.
*   **Dynamics with Geared Motors**: Incorporates the dynamics of actuators, typically electric motors with gearheads.
    *   Gearheads: Increase torque and decrease speed by a gear ratio G.
    *   **Apparent Inertia**: The rotor's kinetic energy is one-half * I_rotor * (G * theta-dot)^2, meaning the apparent inertia of the rotor about the joint axis is **G-squared * I_rotor**. This can significantly affect dynamics, especially for large gear ratios.
    *   Large gear ratios cause the apparent inertias of the rotors to dominate dynamics, making the coupled robot dynamics behave more like independent joints.
    *   Modified Newton-Euler algorithms account for geared motors, calculating motor torque needed for both rotor and link acceleration.

### Trajectory Generation and Planning

**I. Trajectories and Paths**
*   **Trajectory**: A robot configuration as a function of time, theta(t).
*   **Path**: A curve in configuration space as a function of a path parameter 's' (from 0 to 1), theta(s). It defines the geometric shape of motion.
    *   **Time Scaling**: A function s(t) that maps time (0 to T) to the path parameter (0 to 1), controlling the speed of path execution.
    *   Derivatives: **theta-dot = (d-theta/d-s) * s-dot** and **theta-double-dot = (d-theta/d-s) * s-double-dot + (d-squared-theta/d-s-squared) * s-dot-squared**.
*   **Simple Paths**:
    *   **Joint-space Straight Line**: **theta(s) = theta_start + s * (theta_end - theta_start)**. Advantage: Joint limits are usually independent, and the feasible configuration space is convex, so a straight line remains within it.
    *   **SE(3) Screw Path**: Frame follows a constant twist from X_start to X_end, defined by **X(s) = X_start * exp(s * log(X_start-inverse * X_end))**. A "straight-line path" in the sense of constant twist.
    *   **Decoupled Rotation and Translation**: Origin follows a straight line, while orientation follows a path similar to a constant twist.

**II. Time Scalings**
*   **Third-Order Polynomial**: s(t) is a cubic function of time, with s-dot a parabola and s-double-dot a line. It provides zero s-dot at start and end times but discontinuous s-double-dot.
*   **Fifth-Order Polynomial**: s(t) is a fifth-order polynomial, allowing s-double-dot to be zero at start and end times, resulting in smoother motion.
*   **Trapezoidal Time Scaling**: Characterized by a constant acceleration, then constant velocity, then constant deceleration. It also has discontinuous jumps in acceleration.
*   **S-Curve Time Scaling**: Provides smoother motion by incorporating constant jerk segments (time derivative of acceleration). Acceleration is zero at the beginning and end.

**III. Trajectories through Via Points**
*   **Via Points**: Specified configurations through which the robot must transit, along with the times at which they should be reached.
*   **Third-Order Polynomial Interpolation**: Can be used between via points for each joint.
    *   With specified via times and velocities: Four terminal constraints (start/end position and velocity) solve for four coefficients, resulting in continuous positions and velocities but potentially discontinuous accelerations.
    *   With specified via times only: Velocities at via points are left free, but velocity and acceleration continuity are constrained before and after a via point.
*   Other methods like B-splines ensure the path remains within the convex hull of control points, which helps prevent violation of joint limits.

**IV. Time-Optimal Trajectory Planning**
*   **Problem**: Given a desired path theta(s), find the time-optimal time scaling s(t) that minimizes total travel time (T), starting and ending at rest, while satisfying robot dynamics and joint torque limits.
*   **Path-Restricted Dynamics**: The robot dynamics equation can be rewritten in terms of the path parameter 's' and its derivatives: **m(s) * s-double-dot + c(s) * s-dot-squared + g(s) = tau**. Here, m(s) plays the role of a mass (though elements can be negative).
*   **Actuator Limits**: Joint torque limits (**tau_i-min <= tau_i <= tau_i-max**) translate into limits on the feasible accelerations (s-double-dot) along the path at a given state (s, s-dot).
    *   **L(s, s-dot)**: Minimum feasible acceleration, the maximum of all lower limits (L_i) across joints.
    *   **U(s, s-dot)**: Maximum feasible acceleration, the minimum of all upper limits (U_i) across joints.
    *   Constraints: **L(s, s-dot) <= s-double-dot <= U(s, s-dot)**. If L > U, no feasible acceleration exists, implying the robot cannot stay on the path at that state.
*   **Graphical Interpretation (s, s-dot plane)**:
    *   **Feasible Motion Cone**: At any state (s, s-dot), the tangent vector to the time scaling (horizontal component = s-dot, vertical component = s-double-dot) must lie within a cone defined by L(s, s-dot) and U(s, s-dot) to satisfy actuator limits.
    *   **Velocity Limit Curve**: A curve in the (s, s-dot) plane where only a single acceleration is possible, or above which no motions are feasible, meaning the robot is moving too fast to remain on the path.
*   **Time-Optimal Algorithm**: Seeks to keep speed (s-dot) as high as possible.
    *   **"Bang-Bang" Trajectory**: Often, the time-optimal solution involves maximally accelerating along the path (forward integration of U) until a switch point, then maximally decelerating (backward integration of L) to bring the robot to rest at the end point. One or more actuators operate at their limits.
    *   **Handling Velocity Limits**: If the maximum acceleration and deceleration curves do not intersect but instead hit the velocity limit curve, a more complex algorithm is needed.
        *   This algorithm involves integrating minimum acceleration (L) backward from the end state until a velocity limit is met.
        *   Then, integrating maximum acceleration (U) forward from the start state.
        *   If the forward U-segment hits the velocity limit curve, a tangent point (s_tan, s_tan-dot) is found on the velocity limit curve where a minimum acceleration (L) segment can bring the robot back to a feasible state.
        *   Switching points are identified where the robot transitions between maximum acceleration (U) and minimum acceleration (L) to maintain feasibility and optimality.
    *   This algorithm provides a theoretical understanding of a robot's maximum capabilities but is rarely used directly in practice due to perfect model requirements and actuator limitations.
