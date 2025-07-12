---
layout: post
title:  "Modern Robotics 1"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---

Here is the knowledgical information extracted from the provided sources, with colloquial language removed:

The **Modern Robotics (MR) code library** accompanies the book "Modern Robotics" and is available for download at https://github.com/NxRLab/ModernRobotics. A PDF manual describing each function is included, and examples of usage are provided in the code comments. The library supports **Python, Mathematica, and MATLAB**.
*   Python can be obtained for free from python.org.
*   Mathematica requires payment.
*   A free license for MATLAB Online is available for the duration of the course via MathWorks support, accessible at https://www.mathworks.com/licensecenter/classroom/modernrobotics/ or https://www.mathworks.com/licensecenter/classroom/modernrobotics1/ for Course 1. A free 2-hour tutorial, "MATLAB Onramp," is available for new users.
*   **GNU Octave**, a free scientific programming language with syntax essentially identical to MATLAB, is an alternative.

The first course in the Modern Robotics specialization focuses on **Chapters 2 and 3**, covering foundational material on robot configurations, velocities, and the representation of spatial motions and forces. This material is crucial for understanding later topics such as quadrotor motion, closed-loop mechanisms, robot control, force application, object manipulation, navigation, coordinated control, and dynamics.

***

### Chapter 2: Configuration Spaces

Chapter 2 introduces foundational concepts related to the spatial representation of robots.
*   **Configuration**: A specification of the positions of all points of a robot. In this book, robots are constructed from rigid bodies (links) connected by joints.
*   **Configuration Space (C-space)**: The space representing all possible configurations of a robot.
*   **Degrees of Freedom (DOF)**: The dimension of the C-space, representing the minimum number of real numbers required to represent the configuration.
    *   A rigid body in three-dimensional space has **6 degrees of freedom**: three linear (x-y-z) and three angular (roll, pitch, yaw). This is derived from fixing three non-collinear points: 3 coordinates for the first point, 2 for the second (constrained to a sphere), and 1 for the third (constrained to a circle).
    *   A rigid body in a two-dimensional plane has **3 degrees of freedom**: two linear and one angular.
    *   The general rule for DOF: The sum of the freedoms of points/bodies minus the number of independent constraints.
*   **Joints**: Common types of joints place constraints on robot motion, thereby affecting the DOF of the mechanism.
    *   **Revolute Joint**: 1 DOF (5 constraints between spatial bodies).
    *   **Prismatic (Linear) Joint**: 1 DOF.
    *   **Helical Joint**: 1 DOF.
    *   **Cylindrical Joint**: 2 DOF.
    *   **Universal Joint**: 2 DOF.
    *   **Spherical (Ball-and-Socket) Joint**: 3 DOF.
*   **Grubler's Formula**: A formula to calculate the DOF of most robots, assuming independent joint constraints. For a robot with N links (including ground) and J joints, where m is the DOF of a single body (3 for planar, 6 for spatial), and f_i is the freedom allowed by joint i:
    *   DOF = m(N-1) - Σ(m - f_i).
    *   Grubler's formula may yield incorrect results if joint constraints are not independent.
*   **Topology of C-space**: An important property describing the "shape" of the C-space, independent of the coordinate representation.
    *   Two spaces are **topologically equivalent** if one can be smoothly deformed into the other without cutting or gluing. Examples: a torus and a coffee mug surface are topologically equivalent; neither are equivalent to a plane.
    *   Examples of topologically distinct C-spaces:
        *   **Plane**: Topology is 2-dimensional Euclidean space (e.g., point moving in a plane).
        *   **Sphere**: Topology is the 2-dimensional surface of a sphere (e.g., spherical pendulum C-space).
        *   **Torus**: Topology is a 2-dimensional surface (e.g., C-space of a 2R robot).
        *   **Cylinder**: Topology is a 2-dimensional surface (e.g., C-space of a rotating sliding knob).
    *   Coordinate representations of curved C-spaces may exhibit discontinuities or rapidly changing coordinates at certain points (singularities), even if the underlying space is smooth.
*   **Representations of C-spaces**:
    *   **Explicit Parametrization**: Uses a minimum number of coordinates to represent the space (e.g., latitude and longitude for a sphere). Advantage: simplicity of minimum coordinates. Disadvantage: may have poor behavior or singularities at certain points.
    *   **Implicit Representation**: Uses more coordinates, subject to constraints, viewing the n-dimensional space as embedded in a higher-dimensional Euclidean space (e.g., x-y-z coordinates for a sphere with a constant radius constraint). Advantage: no problems with discontinuities or rapidly changing coordinates. Disadvantage: greater complexity. **Implicit representations are used throughout the book**, particularly for the curved space of rigid body orientations.
*   **Constraints on Robot Motion**:
    *   **Holonomic Constraints**: Constraints on configuration that reduce the dimension of the C-space. They are "integrable" and can be written as g(theta) = 0.
    *   **Nonholonomic Constraints**: Constraints on velocity that cannot be integrated to equivalent configuration constraints. They reduce the space of possible velocities but not the space of configurations.
    *   **Pfaffian Constraints**: Velocity constraints of the form A(theta) * theta-dot = 0. Holonomic constraints can be expressed as Pfaffian constraints, but not all Pfaffian constraints are holonomic.
*   **Task Space**: A space in which the robot's task can be naturally expressed (e.g., Euclidean plane for marker position, 6D space for rigid body position/orientation). Defined by the task, not the robot.
*   **Workspace**: A specification of the configurations that the robot's end-effector can reach, typically defined by Cartesian points, possibly including orientation (dexterous workspace).

***

### Chapter 3: Rigid-Body Motions

Chapter 3 focuses on specific implicit representations of configurations, velocities, and forces for rigid bodies in 3D space.
*   **Frames**: A frame consists of an origin and orthogonal x, y, and z coordinate axes, all right-handed.
    *   **Space Frame ({s})**: A fixed reference frame.
    *   **Body Frame ({b})**: A frame fixed to the rigid body, describing its configuration relative to the space frame.
*   **Rotation Matrix (R)**: A 3x3 matrix representing the orientation of one frame relative to another. The columns of R are the unit coordinate axes of the body frame expressed in the space frame coordinates.
    *   **Properties**:
        *   9 entries, but only 3 independent parameters (3 DOF for orientation).
        *   Subject to 6 constraints: column vectors are unit vectors, and orthogonal to each other (R^T R = I, where I is the 3x3 identity matrix).
        *   Determinant must be 1 (for right-handed frames).
        *   The set of all rotation matrices forms the **Special Orthogonal Group SO(3)**.
        *   Inverse of R is its transpose (R^-1 = R^T), which is also a rotation matrix.
        *   Product of two rotation matrices is also a rotation matrix.
        *   Matrix multiplication is associative but generally not commutative.
        *   R times a 3-vector x preserves the length of x.
    *   **Uses**:
        1.  Represent an orientation.
        2.  Change the frame of reference of a vector or frame (e.g., R_sc = R_sb * R_bc; p_s = R_sb * p_b). Subscript cancellation rule applies.
        3.  Rotate a vector or frame. Pre-multiplication (R * R_sc) implies rotation about axes of the first frame's (space) coordinates; Post-multiplication (R_sc * R) implies rotation about axes of the second frame's (body) coordinates.
*   **Angular Velocity (omega)**: A 3-vector representing the rate of rotation of a body.
    *   The space of angular velocities is a flat 3-dimensional vector space, tangent to SO(3).
    *   Represented by a unit rotation axis (omega-hat) and a speed of rotation (theta-dot).
    *   **Skew-symmetric matrix ([omega])**: A 3x3 matrix representation of a 3-vector, where [x] is equal to -[x]^T. This allows cross products to be written as matrix-vector multiplication (x cross y = [x]y).
    *   The set of all 3x3 skew-symmetric matrices forms **little so(3)**, related to SO(3).
    *   Relationship between R-dot (time derivative of R) and angular velocity: R-dot = [omega_s]R (spatial angular velocity) or [omega_b] = R^-1 R-dot (body angular velocity).
    *   Conversion between spatial and body angular velocities: omega_b = R^-1 omega_s and omega_s = R omega_b.
*   **Exponential Coordinates (for Rotation)**: A 3-parameter representation of orientation (omega-hat * theta), where omega-hat is a unit axis and theta is the rotation angle.
    *   Analogous to integrating a constant angular velocity.
    *   **Matrix Exponential (for Rotation)**: Takes a skew-symmetric matrix representation of exponential coordinates ([omega-hat * theta] in little so(3)) and calculates the corresponding rotation matrix R.
        *   For 3x3 skew-symmetric matrices, this has a closed form (Rodrigues' formula): R = I + sin(theta)[omega-hat] + (1 - cos(theta))[omega-hat]^2.
    *   **Matrix Logarithm (for Rotation)**: The inverse of the matrix exponential, taking a rotation matrix R and returning the skew-symmetric matrix representation of the exponential coordinates ([omega-hat * theta]).
*   **Homogeneous Transformation Matrix (T)**: A 4x4 matrix representing the full configuration (position and orientation) of a body frame {b} relative to a space frame {s}.
    *   Structure: [ R p; 0 0 0 1 ], where R is the 3x3 rotation matrix and p is the 3x1 position vector of the {b} frame origin in {s} coordinates. The bottom row (0,0,0,1) simplifies matrix operations.
    *   The set of all transformation matrices forms the **Special Euclidean Group SE(3)**.
    *   **Properties**: Analogous to rotation matrices.
        *   Each T has an inverse (T * T^-1 = Identity matrix).
        *   Product of two T matrices is also a T matrix.
        *   Matrix multiplication is associative but generally not commutative.
    *   **Uses**:
        1.  Represent a rigid-body configuration.
        2.  Change the frame of reference of a vector (requires homogeneous coordinates, appending a 1 to the 3-vector) or a frame (e.g., T_sc = T_sb * T_bc). Subscript cancellation rule applies.
        3.  Displace a vector or a frame.
            *   Left-multiplication (T * T_sb) implies the transformation (translation vector p and rotation axis omega-hat) is expressed in the frame of the first subscript ({s}).
            *   Right-multiplication (T_sb * T) implies the transformation is expressed in the frame of the second subscript ({b}) and the operations are reversed (translation then rotation).
*   **Twist (V)**: A 6-vector representing any rigid-body velocity, consisting of a 3-vector angular component (omega) and a 3-vector linear component (v). It is equivalent to instantaneous velocity about a screw axis.
    *   **Screw Axis (S)**: Defined by a point q on the axis, a unit vector s in the direction of the axis, and the pitch h (ratio of linear speed to angular speed).
        *   Represented as a 6-vector (S_omega, S_v) in a reference frame. S_omega is the unit angular velocity, S_v is the linear velocity of the origin when rotational speed is 1.
        *   If pitch is infinite (pure linear motion): S_omega is zero, S_v is a unit vector, and theta-dot is linear speed.
        *   If pitch is finite: S_omega is a unit vector, and theta-dot is rotational speed.
    *   Twist V = S * theta-dot, where theta-dot is the scalar rate of rotation/translation along the screw.
    *   **Body Twist (V_b)**: Screw axis S expressed in body frame {b} coordinates.
    *   **Spatial Twist (V_s)**: Screw axis S expressed in space frame {s} coordinates.
    *   Both V_b and V_s represent the same motion in different coordinate frames.
    *   **Matrix Representation of Twists ([V])**: A 4x4 matrix in **little se(3)**, related to SE(3).
        *   [V_b] = T^-1 * T-dot.
        *   [V_s] = T-dot * T^-1.
        *   Structure: [ [omega] v; 0 0 0 0 ], where [omega] is the 3x3 skew-symmetric matrix of angular velocity and v is the 3x1 linear velocity of the origin.
    *   **Adjoint Representation ([Ad_T])**: A 6x6 matrix used to change the frame of representation of a twist (V_a = [Ad_T_ab] * V_b).
*   **Exponential Coordinates (for Rigid-Body Motion)**: A 6-parameter representation of a configuration as S * theta, where S is the screw axis and theta is the displacement (angle or linear distance).
    *   **Matrix Exponential (for Rigid-Body Motion)**: Maps matrices in little se(3) to transformation matrices in SE(3).
        *   For purely translational screw axis: T = [I, S_v*theta; 0 0 0 1].
        *   For screw axis with rotation: A more complex closed-form solution exists.
    *   **Matrix Logarithm (for Rigid-Body Motion)**: The inverse, mapping a transformation matrix T to the matrix representation of exponential coordinates.
*   **Wrench (F)**: A 6-vector representing torques (moments) and forces. It combines a 3-vector moment (m) and a 3-vector force (f).
    *   Power is the dot product of a twist and a wrench, and is coordinate frame-independent (V_s^T F_s = V_b^T F_b).
    *   Transformation of wrenches from body frame {b} to space frame {s}: F_s = [Ad_T_sb]^-T F_b.

Appendix A provides a summary of useful equations from Chapter 3, including analogies between rotation matrices and transformation matrices, and between angular velocities and twists.
