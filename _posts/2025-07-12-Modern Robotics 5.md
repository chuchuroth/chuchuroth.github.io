---
layout: post
title:  "Modern Robotics 5"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---


The provided sources contain extensive knowledge on robot manipulation, contact mechanics, and wheeled mobile robots. Here is a summary of the key information, with colloquial language removed:

### Robot Manipulation and Contact Mechanics

**1. Definition of Manipulation and Prerequisites**
*   **Manipulation** occurs when a robot applies motions or forces to purposefully change the state of an object.
*   Examples of manipulation primitives include grasping, carrying, pushing, kicking, throwing, tapping, sliding, rolling, pivoting, and toppling. These primitives allow robots to manipulate objects that are too large or heavy to grasp, or to manipulate several objects simultaneously.
*   Automating robot manipulation planning and execution requires an understanding of the **mechanics of contact**.
*   Analysis of rigid body manipulation requires three ingredients:
    *   **Contact kinematics**: how contact between two rigid bodies constrains their motion.
    *   **Force models**: models of forces transmissible through contact, including frictional forces.
    *   **Rigid-body dynamics**: the relationship between forces and motions.
*   The **quasistatic assumption** simplifies analysis by assuming motions are slow, making velocity and acceleration terms negligible; thus, contact forces and gravity forces must balance.

**2. Vector Spans**
*   Given a set of vectors `A = {a_1, ..., a_j}` in an n-dimensional space:
    *   **Linear span of A**: The set of all linear combinations of these vectors.
    *   **Positive span (or nonnegative span/conical span) of A**: The set of all linear combinations where the coefficients are nonnegative. `R^n` can be positively spanned by `n+1` vectors, but no fewer.
    *   **Convex span of A**: The set of all linear combinations where the coefficients are nonnegative and sum to one.
*   The convex span is a subset of the positive span, which is a subset of the linear span.

**3. Contact Kinematics**
*   **Contact kinematics** is the study of motion constraints due to contact between bodies.
*   Conditions governing contact based on distance `d` between bodies and its derivatives:
    *   `d > 0`: Bodies are not in contact.
    *   `d < 0`: Bodies are in penetration (not allowed).
    *   `d = 0`: Bodies are currently in contact.
        *   If `d-dot > 0`: Contact is about to break.
        *   If `d-dot < 0`: Bodies are about to penetrate (not allowed).
        *   If `d = 0` and `d-dot = 0`: Contact is maintained.
            *   If `d-double-dot > 0`: Contact is about to break.
*   Bodies remain in contact only if all time derivatives of `d` are zero.
*   **First-order analysis** focuses on the **contact normal**, a unit vector orthogonal to the tangent line (planar contact) or tangent plane (spatial contact) at the contact point. Second-order information (curvature) is generally ignored for simplicity, but can have consequences.
*   Contacts between rigid bodies are modeled as a **finite set of point contacts**. A line segment contact is modeled at its ends, and a planar patch contact is modeled at its vertices. Degenerate contacts (no uniquely defined tangent plane/normal) are not allowed.

**4. Contact Constraints on Twists**
*   Contact constrains the possible twists of bodies.
*   The **impenetrability constraint** states that the relative velocity of contact points in the direction of the normal must be greater than or equal to zero. If it's strictly greater than zero, bodies break contact.
*   **Contact labels** categorize contacts satisfying the impenetrability constraint:
    *   **B (Breaking contact)**: Relative normal velocity > 0.
    *   **S (Sliding contact)**: Relative normal velocity = 0, but relative tangential velocity is non-zero. This is a first-order roll-slide contact.
    *   **R (Rolling contact)**: Relative velocity at the contact point is zero. This is also called a sticking contact.
*   Constraints in terms of twists:
    *   For a sliding contact: The relative twist must lie on a hyperplane. For spatial bodies, this is a 5-dimensional hyperplane in a 6-dimensional twist space; for planar bodies, it's a line in a 3-dimensional twist space.
    *   For a rolling contact: The relative twist must be zero. For spatial bodies, this imposes 3 equality constraints; for planar bodies, 2 equality constraints.
*   A **wrench F** (linear component: normal vector; moment: vector to contact crossed with normal) can be used to express impenetrability and roll-slide constraints: `F-transpose * (V_A - V_B)`.

**5. Multiple Contacts and Feasible Twists**
*   A single contact divides the twist space of one body relative to another into a **feasible half-space** and a half-space that violates the rigid-body assumption.
*   When a rigid body is subject to **multiple contacts**, the feasible twist half-spaces intersect to create a **polyhedral convex cone** (if all fixtures are stationary) or a more general **polyhedral convex set** (if fixtures are moving).
*   The **contact mode** is a concatenation of labels (B, S, R) for each contact.
*   **Immobilization** occurs when the only allowed twist is the zero twist, resulting in an "RR" contact mode.

**6. Center of Rotation (Planar Twists)**
*   Any planar twist can be visualized as a rotation about a **center of rotation** `(x_c, y_c)` with an angular velocity `omega_z`.
*   Twist cones can be represented as **regions of rotation centers**.
*   Pure translational motion corresponds to rotation centers at **infinity**, connecting positive and negative regions of rotation centers.
*   The **positive span** of two rotation centers with opposite signs consists of two rays and a point at infinity. The positive span of two centers with the same sign is the line segment between them.
*   For a single stationary contact, rotation centers at the contact point cause **rolling (R)**. Rotation centers to the left of the contact normal (with a plus sign for counterclockwise rotation) or to the right (with a minus sign) cause **breaking (B)**. Rotation centers on the contact normal cause **sliding (S)**, further classified as left-sliding (Sl) or right-sliding (Sr).
*   **First-order kinematic analysis**: If it predicts breaking or penetration, a higher-order analysis will agree. If it predicts rolling or sliding, a higher-order analysis may change the conclusion.

**7. Form Closure**
*   **Form closure** occurs when a rigid body is fully immobilized by a set of rigid stationary fixtures.
*   **First-order form closure** means only the zero twist satisfies the impenetrability constraints for all contacts.
*   This condition is equivalent to the **positive linear span of the contact normal wrenches being the entire wrench space** (6-dimensional for spatial, 3-dimensional for planar).
*   Minimum contacts required for first-order form closure:
    *   **Planar body**: At least **4 point contacts**.
    *   **Spatial body**: At least **7 point contacts**.
*   Some objects, like a sphere, cannot be form-closure grasped kinematically.
*   **Computational test for form closure**: Let `F` be the matrix of contact normal wrenches (each wrench is a column). Form closure exists if and only if:
    *   The **rank of F is n** (3 for planar, 6 for spatial).
    *   There is a **vector `k` of positive coefficients** such that `F * k = 0`.
*   First-order form closure is a **conservative test**: if a body is in form closure by first-order analysis, it is also by higher-order analysis. However, if first-order analysis indicates only sliding/rolling, higher-order analysis might still conclude form closure. Higher-order analysis can achieve form closure with as few as 2 contacts.

**8. Contact Forces and Friction**
*   Forces transmitted through a contact include **normal forces** and **tangential forces** (friction).
*   **Coulomb friction model**: An empirical, approximate model for dry friction.
    *   If sliding velocity `v` is zero: Tangential friction force magnitude `|f_t| <= mu * f_n` (where `mu` is the friction coefficient, `f_n` is normal force).
    *   If sliding velocity `v` is non-zero: Tangential friction force magnitude `|f_t| = mu * f_n`, acting opposite to `v`.
    *   The model can be enhanced with **static friction coefficient `mu_s`** (larger) and **kinetic friction coefficient `mu_k`** (smaller). The basic model uses a single `mu`.
*   The **friction coefficient `mu`** depends on contacting materials, typically ranging from near zero (Teflon, ice) to around 1 (rubber).
*   The set of all forces transmissible through a Coulomb friction contact can be visualized as a **friction cone**.
    *   For planar contact, it's the **positive span of two forces** (edges of the cone). The angle of the cone is the **friction angle `alpha = atan(mu)`**.
    *   For spatial contact, a quadratic cone is often approximated by a **polyhedral cone** (e.g., positive span of four forces) for computational purposes. More edges provide a closer approximation.
*   **Wrench cone**: Represents moments created by contact forces about coordinate frames not at the contact point. It's the positive span of wrenches from the friction cone edges.
*   **Composite wrench cone**: The positive span of wrench cones from multiple contacts.

**9. Moment Labels (Planar Wrench Cones)**
*   A planar wrench has 3 components: moment about z-axis and linear forces in x and y.
*   **Moment labels** provide a graphical representation of planar wrench cones:
    *   Points to the **left of a wrench's line of action** are labeled **plus** (scaled wrench cannot create negative moment about these points).
    *   Points to the **right** are labeled **minus** (cannot create positive moment).
    *   Points **on the line of action** are labeled **plus-minus**.
*   To represent the **positive span of multiple wrenches**, the moment labels for individual wrenches are intersected; regions with inconsistent labeling lose their labels. The consistently labeled region is a single convex connected region.

**10. Force Closure**
*   A body is in **force closure** if the positive span of the wrench cones from its frictional contacts is the entire wrench space. This means contacts can theoretically resist any wrench applied to the body.
*   **Test for force closure**: Similar to first-order form closure. Let `F` be the matrix of friction cone edges (j columns, 3 or 6 rows). Force closure exists if and only if:
    *   The **rank of F is n** (3 for planar, 6 for spatial).
    *   There is a **vector `k` of positive coefficients** such that `F * k = 0`.
*   This definition depends only on contact locations, normals, and friction coefficients.
*   If friction coefficient is zero, **frictionless force closure is equivalent to first-order form closure**.
*   With nonzero friction, force closure can be achieved with fewer contacts than form closure:
    *   **Planar**: As few as **2 contacts**.
    *   **Spatial**: As few as **3 point contacts**. (Two soft fingers can achieve spatial force closure due to frictional moment from contact patches).
*   Force closure is a good minimum requirement for robot grasp planning, while form closure is often too strict. For machining workpieces with significant forces, a form-closure fixture is advisable.

**11. Contact Modes and Constraints (Kinematics and Forces)**
*   Analyzing manipulation tasks involves combining contact kinematics with the Coulomb friction model.
*   The total number of equality constraints on motion and force is constant, regardless of contact label.
*   For **planar contacts**:
    *   **Breaking (B)**: 0 velocity constraints, 2 force constraints (force is zero); 2 velocity freedoms, 0 force freedoms.
    *   **Sliding (S)**: 1 velocity constraint (normal velocity is zero), 1 force constraint (force on friction cone edge); 1 velocity freedom, 1 force freedom.
    *   **Rolling (R)**: 2 velocity constraints (zero relative velocity), 0 force constraints; 0 velocity freedoms, 2 force freedoms.
*   For **3-dimensional spatial contacts**:
    *   Each contact label provides **3 total constraints**.
    *   **Breaking (B)**: 0 velocity constraints, 3 force constraints; 3 velocity freedoms, 0 force freedoms.
    *   **Sliding (S)**: 1 velocity constraint (normal velocity is zero), 2 force constraints (force on friction cone edge); 2 velocity freedoms, 1 force freedom.
    *   **Rolling (R)**: 3 velocity constraints (zero relative velocity), 0 force constraints; 0 velocity freedoms, 3 force freedoms.
*   Breaking contacts provide the fewest velocity constraints and most force constraints; rolling contacts provide the most velocity constraints and fewest force constraints.

**12. Analyzing Rigid-Body Mechanics with Friction**
*   The **equation of motion** for a rigid body with frictional contacts is `F_contact + F_ext = M_b * V_b-dot - Ad_Vb^T * M_b * V_b`.
*   **Procedure for analysis**:
    1.  **Enumerate potential contact modes**.
    2.  For each mode, **determine if there is a consistent contact wrench and body motion** (with Coulomb's law and contact mode) that satisfies the equation of motion.
*   Under the **quasistatic assumption**, the right-hand side of the equation of motion is zero, meaning external and contact wrenches must balance (`F_contact + F_ext = 0`).
*   The **meter stick trick** (stick slides to keep center of mass between fingers) is explained by showing that only the contact mode where the finger closer to the center of mass slides while the other rolls allows quasistatic balance with gravity.

**13. Static and Dynamic Balance of Assemblies**
*   For an assembly of blocks, static balance requires that for each block, the **external force (e.g., gravity) and contact wrenches must balance**.
*   This can be formulated as a set of **vector static balance equations**, where the total contact wrench is in the **positive span of the friction cone edges**.
*   Solving for nonnegative coefficients `k_i` (multiplying friction cone edges `F_i`) using a linear constraint satisfaction solver determines if standing is a feasible solution.
*   A **dynamic version** of this problem involves including acceleration terms in the equations; if coefficients `k_i` become negative, the assembly must be glued to prevent collapse.

### Wheeled Mobile Robots

**1. Types and Kinematic Models**
*   **Wheeled mobile robots** move on hard, flat surfaces.
*   **Chassis configuration** `q = (phi, x, y)` (heading angle, position). **Chassis velocity** `V_b` (planar twist in body frame) or `q-dot`.
*   **Nonholonomic mobile robots** (e.g., differential drive, car-like): Employ conventional wheels that do not allow sideways sliding. The space of feasible chassis velocities is **2-dimensional**.
*   **Omnidirectional mobile robots** (e.g., using omniwheels or mecanum wheels): Allow sideways sliding through rollers. The chassis can move in any direction in its **3-dimensional velocity space**.
*   **Kinematic model**: Maps wheel speeds to chassis velocity.
    *   **Omnidirectional (general)**: Wheel driving speed `u_i = h_i * V_b`. Stacking these gives `u = H_0 * V_b`, where `H_0` is an m-by-3 matrix (m wheels). `H_0` must be full rank (rank 3) for any `V_b` to be achievable.
    *   **Omnidirectional (H-of-phi)**: `u = H_phi * q-dot`, where `H_phi = H_0 * R` (R transforms `q-dot` to `V_b`).
    *   **Nonholonomic (canonical model)**: `q-dot = G(q) * u`, where `G(q)` is an n-by-m matrix whose columns are **control vector fields** (e.g., forward motion `g_1`, spin-in-place `g_2`). The rank of `G` is less than the dimension of `q` (e.g., 2 < 3 for canonical model).
*   **Wheel characteristics**:
    *   **Conventional wheel**: No sideways sliding.
    *   **Omniwheel**: No slip in driving direction, free sliding orthogonal to driving direction.
    *   **Mecanum wheel**: No slip in driving direction, free sliding at 45 degrees to driving direction.

**2. Controllability of Wheeled Mobile Robots**
*   **Controllability**: Ability to drive a system from one state to another.
*   **Omnidirectional robots**:
    *   Any `q-dot` can be achieved by a proper choice of wheel speeds.
    *   Can be stabilized to a goal configuration using a **proportional controller** `q-dot = -K * q` (if goal is origin), because their system `q-dot = nu` (where `nu` is chassis velocity) is a linear control system with `A=0` and `B` as the identity matrix, satisfying the **Kalman rank condition**.
    *   Feasible twists are bounded by a **convex polyhedron** (e.g., 6-sided for 3-omnwheel, 8-sided for 4-mecanum wheel).
*   **Nonholonomic robots**:
    *   Are **not linearly controllable**.
    *   **Cannot be stabilized to the origin by a continuous time-invariant feedback control law**.
    *   Satisfy weaker controllability conditions from nonlinear control theory.
        *   **Global controllability**: Can drive robot from `q` to any `q_goal` in finite time.
        *   **Small-Time Local Controllability (STLC)**: Locally reachable set is full-dimensional and contains the initial configuration in its interior. A car with a reverse gear is STLC.
        *   **Small-Time Local Accessibility (STLA)**: Locally reachable set is full-dimensional but does not contain the initial configuration in its interior. A car without a reverse gear is STLA.
    *   If a robot satisfies any of these, velocity constraints do not integrate to equality constraints on configuration, confirming they are **nonholonomic constraints**.
    *   **Lie bracket of vector fields**: `[g_i, g_j]` expresses the noncommutativity of vector fields `g_i` and `g_j`, representing approximate motion in constrained directions. For the canonical nonholonomic robot, `[g_1, g_2]` (forward and spin-in-place) results in a sideways translation, effectively "breaking" the sideways constraint.
    *   **Lie Algebra Rank Condition (LARC)**: A set of vector fields satisfies LARC at `q` if their Lie products of all degrees span the n-dimensional space of feasible motions at `q`.
        *   If LARC is satisfied, and the control set **positively spans** the control space, the system is **STLC**.
        *   If LARC is satisfied, and the control set **spans but does not positively span**, the system is **STLA**.

**3. Motion Planning and Control for Wheeled Mobile Robots**
*   **Omnidirectional robots**: Most path planners from Chapter 10 (general motion planning) and feedback control from Chapter 11 (feedforward + PI feedback) can be applied directly.
*   **Nonholonomic robots**:
    *   **Optimal motion plans (obstacle-free)**:
        *   **Dubins curves**: For a car with no reverse gear, shortest paths are CSC (Circular, Straight, Circular) or CpiC (Circular, Circular > pi, Circular) combinations.
        *   **Reeds-Shepp curves**: For a car with a reverse gear, shortest paths belong to 9 classes involving circular segments, straight segments, and direction reversals (cusps).
    *   **Motion planning among obstacles**: Reeds-Shepp curves can be used in a subdivision process. An infeasible path can be iteratively subdivided and connected by feasible Reeds-Shepp paths, guaranteed to converge if the original path has free space around it and the robot is STLC.
    *   **Trajectory Tracking (Feedback Control)**:
        *   Requires an estimate of chassis configuration, often using odometry augmented by external sensors.
        *   Controlling a **point P fixed to the chassis** can track a desired trajectory, but does not always ensure good tracking of the full chassis orientation (e.g., can lead to 180-degree orientation errors).
        *   **Full chassis configuration tracking** requires a nonlinear controller (e.g., nonlinear in error coordinates phi_e, x_e, y_e). This type of controller is effective when heading error is less than pi/2 and linear velocity is nonzero.

**4. Odometry**
*   **Odometry**: Estimating chassis configuration by integrating wheel motions.
*   Errors accumulate over time due to slipping/skidding and numerical integration. Usually supplemented by exteroceptive sensors.
*   **Process**:
    1.  Measure wheel rotations `Delta theta` using encoders.
    2.  Assume constant wheel velocities over `Delta t`.
    3.  Find chassis planar twist `V_b` corresponding to `Delta theta` using an **`F` matrix**. For omnidirectional robots, `F = H_0^-1`.
    4.  Integrate the 6-dimensional twist `V_b6` using matrix exponential to find `T_sb_k+1` relative to `T_sb_k`.
    5.  Express new chassis frame in the space frame.

**5. Mobile Manipulation**
*   A **mobile manipulator** combines a mobile base with one or more robot arms.
*   Common control strategy: Drive base to location, park, then use arm for precision.
*   **Coordinated control**: Simultaneous control of wheels and arm joints is needed for underactuated tasks (e.g., 6D end-effector twist with 5-joint arm).
*   **Jacobian for mobile manipulator (J_e)**: Maps wheel and joint speeds to the end-effector twist.
    *   `V_e = J_e * [u; theta-dot]`, where `u` are wheel speeds and `theta-dot` are joint velocities.
    *   `J_e` is a 6-by-(m+n) matrix (m wheel speeds, n joint velocities).
    *   `J_e` can be decomposed into `J_base` (6-by-m) and `J_arm` (6-by-n). `J_arm` is the arm's body Jacobian.
    *   `J_base = Ad_Teb * F_6`, where `F_6` maps wheel speeds to 6D chassis twist in chassis frame.
*   **Task-space feedforward plus PI controller** from Chapter 11 can be used with `J_e` and its pseudoinverse to calculate commanded wheel and joint velocities.
