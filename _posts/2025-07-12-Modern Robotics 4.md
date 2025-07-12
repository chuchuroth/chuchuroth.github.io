---
layout: post
title:  "Modern Robotics 4"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---


The following outlines key concepts, definitions, algorithms, and properties related to robot motion planning and control, drawing directly from the provided sources.

### Robot Motion Planning
Robot motion planning addresses the challenge of moving a robot's end-effector from an initial configuration to a desired final configuration without colliding with obstacles in the environment.

**Key Concepts in Motion Planning:**
*   **Configuration (q):** A vector of *n* coordinates describing a robot's state. The **C-space** (Configuration Space) is the set of all possible robot configurations, typically a subset of R^n, or an arbitrary manifold like SE(3) for a rigid body.
*   **C-space Partition:** The C-space is divided into **C_free**, where the robot is not in contact with any obstacles, and **C_obs**, where the robot is in collision.
*   **C-space Obstacles:** Environmental obstacles are represented as sets of points in C-space where the robot would collide. Joint limits can also create C-space obstacles. Explicitly constructing C-space obstacles is often impractical for higher-dimensional spaces due to geometric complexity.
*   **Robot State (x):** Can be solely the configuration *q* (if controls are velocities) or *q* plus velocity (if controls are accelerations or forces). The state space is *X*.
*   **Equations of Motion:** Described by *x-dot = f(x,u)*, where *u* is a control input from a feasible set *U*.
*   **General Motion Planning Problem:** Given an initial state *x_start* and a desired final state *x_goal*, find a time *T* and a set of controls such that the motion satisfies *x(T) = x_goal* and is collision-free.
*   **Collision Detection:** Planners typically rely on a collision-detection routine to check if a configuration or path segment is in free space. Methods include checking polygon intersections or approximating objects with spheres to check distances between sphere centers.

**Variations of the Motion Planning Problem:**
*   Planning a full trajectory with timing information versus a collision-free geometric path.
*   Robots with an actuator for every degree of freedom versus fewer actuators than degrees of freedom.
*   Real-time planning for moving obstacles versus pre-computation.
*   Finding minimum-cost (e.g., time, length, energy) motions versus any collision-free motion.
*   Reaching an exact goal state versus a goal region.

**Properties of a Motion Planner:**
*   **Multiple-query planner:** Invests time in C-space representation for quick solutions to future problems in that space.
*   **Single-query planner:** Attempts to solve a single motion planning problem as quickly as possible, used when the C-space changes frequently.
*   **Complete:** Always finds a solution when one exists.
*   **Resolution Complete:** Always finds a solution when one exists at the level of discretization used.
*   **Probabilistically Complete:** The probability of finding a solution (if one exists) approaches 100% as planning time approaches infinity.
*   **Computational Complexity:** Measures memory usage or execution time as a function of problem description (e.g., number of degrees of freedom, obstacle vertices).

**Motion Planning Approaches:**

1.  **Graph Search-based Methods:**
    *   **Discretization of C-space:** Continuous C-space is typically discretized into a graph.
    *   **Graph Components:** A graph consists of **nodes** (representing configurations) and **edges** (representing free paths between configurations).
        *   **Unweighted Undirected Graph:** Edges can be traversed in either direction with uniform cost.
        *   **Weighted Graph:** Edges have different costs (e.g., path length, energy, time).
        *   **Directed Graph (Digraph):** Edges have specific directions and costs.
        *   **Tree:** A specific directed graph with one **root node**, where all other nodes have a single **parent** and there are no **cycles**. Nodes with no children are **leaves**.
    *   **A-star Graph Search:** A widely used algorithm for finding lowest-cost paths on a graph.
        *   Requires an **optimistic cost-to-go function** (heuristic) that estimates the cost from any node to the goal. This estimate must be fast to evaluate, reasonably close to the actual cost, and optimistic (actual cost is never less than the estimate). Straight-line distance is a common optimistic estimate.
        *   **Process:** Maintains an OPEN list (nodes to explore, sorted by estimated total cost) and a CLOSED list (explored nodes). Explores from the node with the lowest estimated total cost, updating past costs and parent nodes of neighbors. Terminates when the goal node is the first in OPEN.
        *   **Optimality:** A-star finds the optimal path if the optimistic cost-to-go function is truly optimistic.
    *   **Dijkstra's Algorithm:** A variation of A-star that uses a zero optimistic cost-to-go, also finds optimal paths but is typically slower due to lack of heuristic guidance.
    *   **Roadmaps:** Graphs that satisfy specific conditions to ensure **completeness**.
        *   Conditions: Easy to find free-space paths between any free configuration and the roadmap, and a connected component of the roadmap exists for every connected component of free C-space.
        *   **Visibility Graph:** An example of a true roadmap for polygonal robots translating among polygonal obstacles in a plane. Nodes are C-space obstacle corners, edges connect mutually visible nodes via straight lines. Complete and optimal.
    *   **Grid-based Methods:** Discretize C-space into grid cells, where each cell center is a graph node.
        *   Cells can be **4-connected** (North, South, East, West neighbors) or **8-connected** (including diagonals).
        *   **Properties:** Resolution complete, and the solution path is optimal for the underlying graph.
        *   **Drawback:** Not practical for high-dimensional spaces; memory and search time grow exponentially with degrees of freedom.
        *   **Multi-resolution Grids:** Mitigate the drawback by representing free C-space coarsely in open regions and finely in cluttered areas. Examples include **quadtrees** (2D) and **octrees** (3D).

2.  **Sampling-based Methods:**
    *   **Probabilistic Roadmaps (PRM):** Approximately construct a roadmap by sampling configurations.
        *   **Probabilistic Completeness:** The likelihood of the PRM being a true roadmap approaches 100% as the number of samples approaches infinity.
        *   **Construction:**
            1.  Generate *N* collision-free samples from C-space (nodes). Sampling can be uniform or non-uniform to better represent narrow passages.
            2.  Connect nodes by finding *k* nearby neighbors and testing simple local paths (e.g., straight lines) for collision-freeness.
        *   **Advantages:** Captures C-space structure with fewer nodes than grid graphs, effective for high-dimensional C-spaces.
        *   **Planner Type:** Typically a **multiple-query planner**.
    *   **Rapidly-exploring Random Trees (RRTs):** Single-query, sampling-based planners for robots with arbitrary dynamics (*x-dot = f(x,u)*).
        *   **Process:** Grows a search tree from the start state by iteratively sampling a random state (*x_samp*), finding the nearest tree node (*x_nearest*), using a local planner to generate a motion towards *x_samp*, and adding a new node/edge if collision-free. Occasionally samples from the goal region to encourage solution.
        *   **Customization:** Flexibility in choosing the sampling algorithm (e.g., uniform, Van der Corput, Halton sequence), defining distance for nearest node search, and selecting the local planner (e.g., straight-line for kinematic robots, discretized controls for dynamic robots, Reeds-Shepp curves for car-like robots).
        *   **Solution Quality:** Basic RRTs do not guarantee optimal solutions. **RRT-star** is a variant that continually rewires the tree to converge to an optimal solution, but cannot be applied to arbitrary dynamics.

3.  **Optimization-based Methods:**
    *   **Nonlinear Optimization:** Formulates motion planning as an optimization problem: minimize a cost functional (e.g., time, energy) subject to constraints (dynamics, control feasibility, collision-free motion, start-to-goal).
    *   **Transcription:** Converts the problem into a finite parameter nonlinear optimization problem.
        *   **Shooting:** Design variables include total time and control history parameters; trajectory is found by simulating dynamics.
        *   **Collocation:** Simultaneously designs control history and trajectory, enforcing dynamic consistency at test points.
    *   **Gradient Importance:** Requires calculation of gradients of cost and constraints with respect to design variables to guide the search.
    *   **Limitations:** Inherently a local method, prone to getting stuck in local minima.
    *   **Best Use:** Effective when other methods (e.g., RRTs) provide a reasonable initial guess, allowing optimization to smooth jerky motions or refine solutions.

4.  **Artificial Potential Fields:** Reactive, real-time controllers.
    *   **Principle:** Define a **virtual potential field** on the C-space, with an **attractive potential** pulling the robot towards the goal and **repulsive potentials** pushing it away from C-space obstacles.
    *   **Force:** The force on the robot is the negative gradient of the potential.
    *   **Control Laws:** Can directly control robot velocity proportional to the force, or incorporate damping to allow the robot to settle at the goal.
    *   **Limitations:** Significant problem with **local minima**, where the robot can get stuck short of the global minimum (goal). **Navigation functions** are a class of potential functions guaranteed to have no local minima, but are difficult to compute for general systems.

### Robot Control
Robot control involves continuously reading sensor data and updating actuator commands to achieve desired robot behavior.

**Control Objectives:**
*   **Motion Control:** Guiding a robot along a specified trajectory.
*   **Force Control:** Applying specific forces to an object or environment.
*   **Hybrid Motion-Force Control:** Controlling motion in some directions and forces in others, typically when interacting with constrained environments.
*   **Impedance Control:** Rendering a virtual environment by controlling how the robot reacts to user interaction.

**Fundamental Concepts in Control:**
*   **Closed-Loop Control:** Characterized by sensor feedback, where measured robot performance is sent back to the controller.
*   **Error (theta_e):** The difference between desired motion (*theta_d*) and actual motion (*theta*), *theta_e = theta_d - theta*.
*   **Error Dynamics:** Equations describing the evolution of the error in a controlled system. A good controller aims to drive initial errors to zero quickly and stably.
*   **Unit Step Error Response:** The evolution of error when the initial error is 1.
*   **Error Response Characteristics:**
    *   **Steady-state error (e_ss):** The final constant error as time approaches infinity.
    *   **Overshoot:** When the error response exceeds its steady-state value before settling.
    *   **Settling Time:** The time it takes for the error to approach and remain within a small percentage (e.g., 2%) of its final value.
    *   **Transient Response:** Consists of overshoot and settling time.
*   **Ideal Error Response:** Zero or small steady-state error, no overshoot or oscillation, and a short settling time.
*   **Linear Error Dynamics:** Error dynamics are typically approximated by linear differential equations.
    *   **Stability:** For a system described by *x-dot = A-x*, the error is guaranteed to decay to zero if the **real components of all eigenvalues (roots)** of the matrix *A* are negative. These roots are found from the characteristic equation.
    *   **P-th Order Differential Equation:** *a_p* *theta_e^(p)* + ... + *a_0* *theta_e* = *c*.
        *   **Homogeneous:** *c* = 0.
        *   **Nonhomogeneous:** *c* != 0.
    *   **First-Order Systems:** For *theta_e-dot + (1/time_constant) * theta_e = 0*, where **time constant** = *b/k* (damping/stiffness). Stable if time constant is positive. Settling time is approximately 4 time constants. Zero steady-state error and overshoot.
    *   **Second-Order Systems:** For *theta_e-double-dot + 2*zeta*omega_n*theta_e-dot + omega_n^2*theta_e = 0*.
        *   **Natural Frequency (omega_n):** sqrt(*k/m*).
        *   **Damping Ratio (zeta):** *b / (2 * sqrt(k*m))*.
        *   **Overdamped (zeta > 1):** Two distinct real negative roots, sum of two decaying exponentials, no overshoot/oscillation.
        *   **Critically Damped (zeta = 1):** Two identical real negative roots, fastest convergence to zero without overshoot/oscillation.
        *   **Underdamped (zeta < 1):** Complex conjugate roots, resulting in a decaying sinusoid response with overshoot and oscillation.
        *   **General Rule:** More negative real parts of roots lead to faster error decay; non-real roots lead to overshoot/oscillation.

**Robot Control Strategies:**

1.  **Velocity-Controlled Robots (Direct Joint Velocity Commands):**
    *   **Open-Loop Control (Feedforward):** Commands desired velocity without feedback; cannot recover from errors.
    *   **Proportional (P) Control:** Commands joint velocity proportional to error (*K_p* *theta_e*).
        *   For setpoint control (desired velocity is zero), achieves zero steady-state error.
        *   For tracking constant velocity trajectories, results in non-zero steady-state error (*c/K_p*) because error is required to generate a non-zero velocity command.
    *   **Proportional-Integral (PI) Control:** Adds an integral term (*K_i* *integral(theta_e dt)*) to P control.
        *   Eliminates steady-state error for trajectories with constant velocity.
        *   Error dynamics become second-order. *K_p* acts as a damper, *K_i* as a spring.
        *   Gains can be tuned for critical damping to achieve fast response without overshoot.
        *   Can be augmented with a feedforward term (*theta_d-dot*) to allow motion without accumulating error.
    *   **Task-Space Control:** Commands end-effector velocities (twists).
        *   **Feedforward Plus PI Feedback (Twist-based):** Commands the actual end-effector twist based on desired twist, relative configuration error (as a twist), and its integral. Joint velocities obtained via Jacobian inverse/pseudoinverse.
        *   **Decoupled Task-Space Control:** Separates rotational and linear errors, commanding angular and linear velocities independently.

2.  **Torque/Force-Controlled Robots (Considering Dynamics):**
    *   **Proportional-Integral-Derivative (PID) Control:** A widely used feedback control law.
        *   **Control Law:** *tau = K_p* *theta_e* + *K_i* *integral(theta_e dt)* + *K_d* *theta_e-dot*.
        *   **Derivative (D) Term:** *K_d* *theta_e-dot*, requires velocity feedback (often from numerically differencing position readings).
        *   **PD Control (*K_i* = 0):**
            *   For setpoint control without gravity, provides zero steady-state error.
            *   *K_d* acts as viscous friction. Gains *K_p*, *K_d* are chosen for stability (positive damping/stiffness) and transient response (e.g., critical damping).
            *   **Limitations:** With gravity, PD control results in non-zero steady-state error because error is needed to generate steady-state torque to counteract gravity.
        *   **PID Control (Full):**
            *   Adds *K_i* to address steady-state error, especially in the presence of gravity or disturbances.
            *   Error dynamics become third-order. *K_i* must be positive but also has an upper bound for stability.
            *   Adding integral control improves steady-state response but can worsen transient response (overshoot, oscillation) and potentially cause instability if *K_i* is too large. Often *K_i* is kept small or avoided.
    *   **Computed Torque Control:** Combines a dynamic model with PID feedback.
        *   **Principle:** The controller computes the joint torques needed based on an estimated robot dynamic model (*M-tilde*, *h-tilde*) for the desired motion, then adds a PID-like feedback term based on the error between desired and actual motion.
        *   **Control Law (Joint Space):** *tau = M-tilde * (theta_d-double_dot + K_p*theta_e + K_i*integral(theta_e dt) + K_d*theta_e-dot) + h-tilde(theta, theta-dot)*.
        *   **Advantages:** If the model is accurate, it effectively linearizes the dynamics, providing better trajectory tracking and lower control effort than pure feedback controllers. It can achieve zero steady-state error along arbitrary trajectories.
        *   **Generalization:** Applies to multi-joint robots using vectors for states and diagonal matrices for gains.
        *   **Limitations:** Performance degrades with poor dynamic models; computationally intensive for real-time control. Simpler variants, like PD feedback with gravity compensation, are common.
        *   **Task-Space Computed Torque Control:** An analogous approach formulated in terms of end-effector dynamics (wrench *F_b*, mass matrix *Lambda-tilde*, Coriolis/gravity wrench *eta-tilde*). Joint torques obtained by pre-multiplying *F_b* by the Jacobian transpose.

3.  **Force Control:** Aims to apply a desired end-effector wrench to the environment.
    *   **Basic Control (without force feedback):** *tau = g-tilde + J-transpose * F_d*. Uses gravity compensation (*g-tilde*) and commands joint torques to generate desired end-effector wrench (*F_d*). Requires only joint angle feedback.
    *   **PI Force Feedback Control (with force-torque sensor):** Incorporates end-effector force feedback from a force-torque sensor.
        *   Adds proportional (*K_p*) and integral (*K_i*) terms based on wrench error (*F_d* - *F_actual*).
        *   Theoretically eliminates steady-state wrench error for constant disturbances.
        *   A derivative term is generally not used due to lack of supporting dynamics in simple models and amplification of sensor noise.

4.  **Hybrid Motion-Force Control:** Controls motion in certain directions while simultaneously controlling forces in other directions, relevant when the robot interacts with rigid constraints.
    *   **Constraint Definition:** The environment imposes constraints that partition the 6-dimensional space of end-effector wrenches into subspaces: one causing motion and one pushing against the constraints. These are often described by **Pfaffian velocity constraints** (*A(theta) * V_b = 0*).
    *   **Projection Matrix (P(theta)):** A 6x6 matrix that projects an arbitrary end-effector wrench to the portion that causes motion. Its complement *(I - P)* extracts the portion of the wrench acting against constraints.
    *   **Control Law:** The total end-effector wrench is the sum of the force control law wrench (projected to act against constraints using *(I - P)*) and the task-space motion control law wrench (projected to cause motion using *P*). This allows independent design of force and motion controllers.
    *   **Joint Torques:** Calculated by pre-multiplying the resulting end-effector wrench by the Jacobian transpose.
