---
layout: post
title:  "Solidworks_Example_2"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---

Designing and assembling a bicycle in SolidWorks involves creating multiple individual parts and then bringing them together in an assembly. Below are the steps to create this specific bicycle design and assembly, as described in the sources:

### **Part 1: Bicycle Steering Handle**

1.  **Start a new part and sketch the steering base:**
    *   Choose the **Top Plane** and create a **sketch**.
    *   Draw a **center line**, then a **spline**.
    *   Add **symmetric relations** between line ends/points and the center line.
    *   Define dimensions: **70 mm**, **40 mm**, **17.6 mm**, **45 mm**.
    *   Set distance from origin to **35 mm**.
    *   Apply **fillet** of **6 mm** to two ends, then change to **26 mm** for two corners, and finally **8 mm** for the last fillet.
    *   **Extrude Boss** the sketch **20 mm** using **mid plane** end condition.
    *   Assign an **orange color** to the extruded body.
2.  **Create a cut feature on the steering body:**
    *   Select the extruded body's surface and create a **sketch**.
    *   Draw a **center point arc** starting from one point and connecting to another, ensuring the two points are coincident.
    *   Define the point position as **4.75 mm** and radius as **12.5 mm** (or **11.1 mm**).
    *   **Offset** the line by **4 mm**.
    *   Connect the offset with a **line**.
    *   Use **Extrude Cut** with **flip side to cut** and **through all** end condition.
3.  **Design the handle rod:**
    *   Select the backside of the steering base and create a **sketch**.
    *   Draw a **circle** with a diameter of **20 mm**.
    *   Set the distance from the outer edge to **15.82 mm** and ensure the circle center and origin are **horizontal**.
    *   **Extrude** the circle up to **225 mm**.
    *   Create a **plane** from the **Right Plane** at **20 mm** distance, centered to the circle.
    *   Edit the rod sketch, delete coincident relation, and set diameter to **20 mm**.
4.  **Extend the handle:**
    *   Select the newly created plane and create a **sketch**.
    *   Draw a **center line** and delete its coincident relation, moving it slightly up.
    *   Draw a **line** and convert it into an **arc**, bringing it down.
    *   Define dimensions: **230 mm**, **30 mm**, **68 mm** (radius), and a gap of **57.5 mm**.
    *   Hide the plane.
    *   Choose the **Front Plane**, create a **sketch**, and draw a **circle** with **30 mm** diameter at the endpoint of the handle extension.
    *   Use **Sweep Boss Base**, selecting the circle as the profile and the extended handle line as the path.
    *   **Mirror** this extruded body using the **Front Plane**.
5.  **Add a connecting rod:**
    *   Select the face of the swept body, create a **sketch**, and draw a **circle** with **30 mm** diameter.
    *   **Extrude** it **150 mm** in the **reverse direction**.
6.  **Create additional frame geometry for the handle (complex part, involves multiple lines, angles, and points):**
    *   Create a **plane** from the **Front Plane** at **50 mm**.
    *   On this new plane, create a **sketch**.
    *   Draw a **vertical center line**.
    *   Place a **star point** at the center of the line and ensure it's coincident.
    *   Draw lines to create a complex geometry with specific dimensions:
        *   Vertical line: **11 mm**.
        *   Co-linear relation **10x10 mm**.
        *   **10 mm** length.
        *   Trim circles.
        *   Dimensions: **38 mm**, **25 mm**.
        *   Angle: **115°**.
        *   **3 mm** dimension.
        *   Star point at center.
        *   Distance from star point to bottom line: **38.75 mm**.
        *   Radius: **10 mm**.
        *   Overall distance: **90 mm**.
        *   Fillet: **30 mm**, then **4 mm** on corners.
    *   **Extrude Boss** the sketch **4 mm**, **unmerge result**.
    *   Change color to **orange**.
    *   **Mirror** the body using the **Front Plane**.
7.  **Create the handle grips (detailed geometry):**
    *   On the **Front Plane**, create a **sketch** and draw a **circle** with **25 mm** diameter.
    *   Make this circle **concentric** with an existing circle.
    *   Create a **plane** (or directly use geometry).
    *   Draw a **line** from a center point, pressing **Tab** for direction, defining length as **67 mm**.
    *   Place a **star point** somewhere.
    *   On the face, take normal position and define star point position:
        *   Distance **29 mm** then **29.5 mm** (using Tab key).
        *   Vertical distance **107.8 mm**.
        *   Distance from previous point to this point: **125 mm**.
    *   Connect points with a **line**.
    *   Place another **star point** above.
    *   Define its position:
        *   Gap **103.5 mm** (using Tab key).
        *   Vertical distance **172 mm** (using Tab key).
    *   Distance between first and second star point: **156.6 mm**.
    *   Connect with a **line**.
    *   Apply **fillet** of **72 mm** to two corners/lines.
    *   Use **Sweep Boss Base** with the defined profile and path.
    *   Assign **polished stainless steel** to several bodies and **chrome plating** to others.
    *   **Mirror** the body using the **Front Plane**.
8.  **Add connecting elements (using 3D sketch):**
    *   On the **Front Plane**, create a **sketch** with dimensions **19 mm**, **63 mm**, **25 mm**.
    *   Use **3D Sketch Spline** to connect specific points and the center point of a circle.
    *   Adjust the spline using arrows along the Z-axis for perfect shape.
    *   Apply **Sweep Boss Base**.
    *   **Mirror** the body using the **Front Plane**.
    *   Assign **chrome plate** to these two bodies.
9.  **Create rubber grips (gloves) for the handle:**
    *   Select a face, create a **sketch**, and draw a **circle** of **31.7 mm**.
    *   **Extrude** it **123 mm** in the **reverse direction**.
    *   On the back surface, create a **sketch**, draw a **bigger circle** of **61.5 mm** (or **60 mm**).
    *   **Extrude** it **4 mm** in the **reverse direction**.
    *   Create another **circle** of **40 mm** and **extrude** it **4 mm** in the **reverse direction**.
    *   Assign **rubber mat** color to the last three extruded bodies.
    *   **Mirror** these three bodies using the **Front Plane**.
    *   Apply **fillets** (edit clear, select bodies 5, 6, 7; then 10 mm fillet for inside rubber).
10. **Refine and finalize steering elements:**
    *   **Extrude** a face by **4.75 mm** (blind) using **Convert Entity**.
    *   On the **Front Plane**, create a **sketch**, draw a **circle** at the midpoint, then a **vertical line** **15 mm** long, and trim half circle.
    *   **Extrude Boss** these faces **40 mm** using **mid plane**, **unmerge result**.
    *   Apply **fillet** of **6 mm**.
    *   **Extrude Cut** two faces by **40 mm** using **Convert Entity**.
    *   Assign **orange color** to the body.
    *   On a face, **sketch a polygon** (find center point) with **40 mm** distance and **extrude** **5 mm** in **reverse**.
    *   On the back surface, sketch a **circle** **44 mm** (or **50 mm**) diameter, **extrude** **5 mm**.
    *   Apply **fillet** of **2 mm**.
    *   Make bottom body **chrome plate**.
    *   Sketch a **circle** **12 mm** then **23 mm**.
    *   **Extrude Cut** **20 mm**.
    *   **Fillet** **6 mm** (then **undo** and **cut 2 mm** specifically on a face).
    *   Sketch a **circle** **17 mm** and **extrude** **5 mm** to fix a bolt.
    *   Apply **fillet** of **5 mm** and assign **steel satin finish stainless steel**.
    *   **Save** as "part one steering".

### **Part 2: Bicycle Frame**

1.  **Sketch the main frame shape:**
    *   Choose the **Front Plane** and create a **sketch**.
    *   Draw a **spline**.
    *   Define dimensions: **390 mm** (length), **394.45 mm** (another length).
    *   Check vertical length (delete if needed), **188.3 mm**.
    *   Make a slight curve.
2.  **Create planes for lofting:**
    *   Create **two planes** tangent to the spline at its start and end points.
3.  **Sketch profiles for loft:**
    *   On the first plane, create a **sketch** and draw an **ellipse**.
    *   Define dimensions: **65 mm** (overall length), **35 mm** (width).
    *   On the second plane, create a **sketch** and draw another **ellipse**.
    *   Define dimensions: **55 mm** (length), **35 mm** (width).
    *   Hide both planes.
4.  **Create the main frame body using Lofted Boss Base:**
    *   Use **Lofted Boss Base**, selecting the two ellipses as profiles and the spline as the center line parameter.
5.  **Add a connecting piece to the frame:**
    *   Choose the **Front Plane**, create a **sketch**, and draw a **line** from the center point, making it a construction line of **45 mm** long.
    *   Create a **plane** (Plane 3) perpendicular to this line at its endpoint.
    *   On Plane 3, create a **sketch**, draw a **circle** of **35 mm** diameter.
    *   **Extrude** it **90 mm** in the **reverse direction**.
    *   Hide Plane 3.
6.  **Add another frame component:**
    *   Choose the **Front Plane**, create a **sketch**, and draw a **circle** of **55 mm**.
    *   **Extrude** this circle **75 mm** using **mid plane** end condition.
7.  **Create a complex geometry for extending the frame:**
    *   Choose the **Front Plane**, create a **sketch**, and draw a geometry with dimensions **300 mm**, **300 mm**, **270 mm**, and **40 mm**.
    *   Create a **plane** (Plane 4) from the **Right Plane** at **10 mm** distance.
    *   On Plane 4, create a **sketch**, draw a **circle** with **15 mm** diameter and **20 mm** (another diameter - ambiguity, likely refers to a second circle or an initial point).
    *   Ensure both points are **horizontal**.
    *   Use a **3D Sketch Line** from the circle's center point.
    *   Place **two star points**.
    *   Make a **parallel relation**.
    *   Set length to **207.45 mm**.
    *   Define gap as **60 mm**.
    *   Distance from a point: **7.5 mm**.
    *   Distance using Tab key: **125 mm**.
    *   Define distance **7.5 mm** (Tab key).
    *   Connect two points with a **line**.
    *   Apply **fillet** of **15 mm** (then adjust to **30 mm** if too big).
    *   Set angle to **140°**.
    *   Draw a **line** in the same plane, connect with a point, define as **230 mm**.
    *   Apply **fillet** of **100 mm** (then adjust to **20 mm**) to lines.
    *   Use **Sweep Boss Base**, selecting the circle as profile and the 3D sketch as path.
    *   **Mirror** the body using the **Front Plane**.
    *   Assign **anodized blue** (or **red**) **aluminum** material.
8.  **Add another support structure:**
    *   Create a **plane** (Plane 5) perpendicular to a line and a point.
    *   On Plane 5, create a **sketch**, draw a **circle** of **30 mm** diameter.
    *   **Extrude Boss** it **up to vertex** (select a point).
    *   Apply **fillet** of **5 mm**.
    *   Hide Plane 5.
9.  **Create a spline support (optional, for visual aid):**
    *   On the **Front Plane**, create a **sketch**, and draw a **spline** from one point to another, extending it if needed.
    *   Create a **plane** (Plane 6) on this spline at a specific point.
    *   On Plane 6, create a **sketch**, draw a **circle** of **30 mm** diameter.
    *   Use **Sweep Boss Base**.
    *   Hide Plane 6 and the spline.
10. **Apply fillets and cut features to the frame:**
    *   Apply **fillet** of **3 mm** to the ends of the frame support.
    *   On a face, **sketch a circle** and **offset** it **1.5 mm** (reverse).
    *   **Extrude Cut** **through all**.
    *   Repeat the offset and **extrude cut** process on other faces (up to surface for one, through all for another).
    *   On a face, **sketch a circle** of **40 mm**.
    *   **Convert Entities** of the inside circle.
    *   **Extrude** this face only **5 mm**, **unmerge result**.
    *   **Extrude offset** **90 mm** (reverse), **7 mm**, and **merge**.
    *   Assign **chrome brushed finish** to the last two bodies.
    *   Apply **fillet** of **3 mm** to upper and lower parts, assign **brushed** finish.
11. **Create fixing hook:**
    *   Create a **plane** (Plane 7) from the **Front Plane** at **46 mm** distance.
    *   On Plane 7, create a **sketch** and draw a line.
    *   Make the line **horizontal** and two lines **collinear**.
    *   Define dimensions: **10 mm**, **10 mm**.
    *   Apply **fillet** of **4 mm** to all corners.
    *   Set dimension **18.9 mm**.
    *   Draw a **circle**, **trim entities** (power trim) to delete inside half circle.
    *   Set gap between bottom line and this line as **84 mm**.
    *   Apply **fillet** of **5 mm** to corners.
    *   Define length as **46.35 mm**, **80 mm**, and distance from edge as **13.5 mm**.
    *   Set **75 mm**.
    *   Ensure geometry is fully defined.
    *   **Extrude Boss** **3 mm**, **merge**.
    *   Set **direction two** to **5 mm** and **3 mm**.
    *   **Mirror** the body using the **Front Plane**.
    *   Hide plane and sketch.
    *   Measure distance between two points (should be **90 mm**), adjust extruded boss direction to **1 mm** if needed.
    *   **Save** as "part number two frame".

### **Part 3: Bicycle Tire (Rear)**

1.  **Sketch the tire profile:**
    *   Choose the **Right Plane**, create a **sketch**.
    *   Draw a **vertical** and **horizontal center line**.
    *   Define dimensions: **145.25 mm**, **25 mm**.
    *   Draw a **center point arc** with **22.5 mm** diameter and **1 mm** 3-point radius.
    *   Draw a **spline** and **mirror** it against the vertical line.
    *   Adjust spline to be slightly down and tangent, define as **75 mm**.
    *   Use **Revolve Boss Base** with the defined profile and axis of revolution.
    *   Assign **rubber** color to the top face, and **chrome brushed finish** to other parts.
    *   Assign a **dark color** to easily identify.
2.  **Create the wheel hub:**
    *   Choose the **Front Plane**, create a **sketch**.
    *   Draw two circles: **10 mm** (inside) and **17.6 mm** (outside).
    *   **Extrude** **38.5 mm** in **Direction 1** and **Direction 2**.
3.  **Design the sprocket on the rear tire:**
    *   Select the back surface, create a **sketch**.
    *   Draw a **construction circle** of **29.0909 mm**.
    *   Draw another circle of **29.0909 * 2 mm**.
    *   Draw a **10 mm** circle and trim it.
    *   Make the **29.0909 mm** circle a real circle (not construction).
    *   Use **Circular Pattern** with 14 instances around the center point.
    *   **Power Trim** all excess lines to create the sprocket shape.
    *   Draw another **circle**.
    *   **Extrude** the sprocket **4 mm**.
    *   Assign **brushed chrome** to this body.
    *   On the face, create a **sketch**, draw a **circle** of **23 mm**.
    *   **Convert Entity** of this circle.
    *   **Extrude** **4 mm**.
    *   On this face, create a **sketch**, draw a **circle** of **20 mm**.
    *   **Convert Entities** of the inside circle.
    *   **Extrude** **4 mm**.
    *   **Mirror** these two parts using the **Front Plane**.
    *   Apply **fillet** of **2 mm**.
    *   Assign **dark color**.
4.  **Create the axle/shaft (inner part of wheel):**
    *   Choose the **Top Plane**, create a **sketch**.
    *   Draw a **corner rectangle** of **20 mm** by **3 mm**.
    *   Draw a **center line**.
    *   Make two lines **collinear**.
    *   Delete coincident relation for an inside line.
    *   Set **5 mm**.
    *   Draw a **horizontal center line** and **mirror** all lines against it.
    *   Use **Revolve Boss Base** with the center line as the axis.
    *   Assign **dark color**.
    *   Apply **fillet** of **4 mm** (on face) and **1 mm** (on other faces), assign **dark color** to fillets.
    *   On the face, create a **sketch**, draw two circles: **10 mm** and **14 mm**.
    *   **Extrude** **2 mm** and **merge**.
    *   Assign **dark color**.
    *   On the face, **convert entity** of the inside circle, draw a **14 mm** diameter circle, **extrude** **6 mm** and **merge**.
    *   Assign **dark color**.
5.  **Create the bicycle spokes (one side):**
    *   Select the face, use **3D Sketch**.
    *   Place a **star point** in the middle of a line and another slightly away.
    *   Draw a **line** from the star point, press **Tab** to change direction, and connect to the second star point.
    *   Adjust gap to **8 mm**.
    *   Apply **fillet** of **3 mm**.
    *   Draw another **line**, press **Tab**, extend in this direction for **3 mm**.
    *   Create a **plane** perpendicular to the line at its end point.
    *   On this plane, create a **sketch**, draw a **circle** of **3 mm** diameter.
    *   Use **Sweep Boss Base** selecting the circle as profile and the line as path.
    *   On the face, create a **sketch**, draw a **circle** of **5 mm**.
    *   **Extrude** **up to next**, **merge**.
    *   On the same plane, create a **sketch**, draw a **hexagon** with **2 mm** size.
    *   **Extrude** **6 mm** in **reverse direction** and **merge**.
    *   Assign **dark color** to swept boss base and last three extruded parts.
    *   Hide the plane.
    *   Use **Circular Pattern** for these three parts (swept, extruded circle, extruded hexagon).
    *   Select any circular face as the pattern axis. Set **14 numbers**.
    *   Apply **fillet** of **5 mm** (or **2 mm**).
6.  **Create the bicycle spokes (other side):**
    *   Select the face, use **3D Sketch**.
    *   Fix a **star point** in the center of both existing spokes.
    *   Draw a **line** from this star point, press **Tab**, drag and connect to another star point.
    *   Adjust point if needed, set to **8 mm**.
    *   Apply **fillet** of **3 mm**.
    *   Draw another **line**, extend **3 mm**.
    *   Create a **plane** perpendicular to this line at its endpoint.
    *   On this plane, create a **sketch**, draw a **circle** of **3 mm** diameter.
    *   Use **Sweep Boss Base**.
    *   On the face, create a **sketch**, draw a **circle** of **5 mm**.
    *   **Extrude** **up to next** in **reverse**.
    *   Apply **fillet** of **2 mm**.
    *   On the same plane, create a **sketch**, draw a **polygon** with **2 mm** length.
    *   **Extrude** **6 mm** in **reverse direction**.
    *   Assign **dark color** to the last three bodies.
    *   Use **Circular Pattern** for these four parts (swept, extruded circle, extruded polygon, and the initial circle extrusion from the previous side of spokes).
    *   Set **14 numbers**.
    *   Hide.
7.  **Add tire threading:**
    *   Select the face, create a **sketch**, draw a **circle** of **40 mm** diameter.
    *   Draw a **bigger circle**.
    *   **Extrude Cut** **1 mm** depth.
    *   Apply **fillet** of **10 mm** to this face.
    *   On the other side, create a **sketch**, **convert entities** from the previous sketch.
    *   **Extrude Cut** **1 mm** depth.
    *   Apply **fillet** of **10 mm**.
    *   Create a **plane** from the **Right Plane** at **180 mm** above.
    *   On this plane, create a **sketch**, draw a **circle** (exit sketch without defining).
    *   Define dimensions: **9 mm**, **4.5 mm**.
    *   Draw a **spline** connecting to a point.
    *   Draw another **spline** connecting to a point.
    *   Draw a **line**.
    *   Define **9 mm**, **4.5 mm**.
    *   Draw a **spline**.
    *   Define **7.5 mm**, **7.5 mm**.
    *   Drag and curve the spline to make a similar curve.
    *   **Extrude Boss**.
    *   On the **Top Plane**, create a **sketch**, adjust position, extend it by **5 mm** in **direction two**.
    *   Draw a **line**, convert to **arc**.
    *   Draw another **line** and **three-point arc**.
    *   Use **Revolve Cut** with a center line.
    *   Apply **fillet** of **1 mm**.
    *   Use **Circular Pattern** for the extruded body and cut part (three parts).
    *   Select a circular face, set **30 numbers** (adjust to **40 numbers** if gap remains).
    *   Assign **rubber mat** color to the last four patterns.
    *   **Save** as "tire".

### **Part 4: Front Tire**

1.  **Modify the rear tire:**
    *   Open the saved rear tire part.
    *   Select the face, create a **sketch**, draw a circle up to the existing one and another bigger one.
    *   **Extrude Cut** **4 mm** depth.
    *   **Save As** "part number nine front tire".

### **Part 5: Sprocket with Paddle Link**

1.  **Create the main body:**
    *   Choose the **Front Plane**, create a **sketch**.
    *   Draw a **25 mm** diameter circle.
    *   **Extrude** it **85 mm** using **mid plane** end condition.
    *   Assign **satin finish chrome** material.
2.  **Sketch the paddle link arm:**
    *   Choose the **Top Plane**, create a **sketch**.
    *   Draw a **line**.
    *   Select origin and line, make **midpoint relation**.
    *   Define dimensions: **135 mm**, **135 mm**.
    *   Set center gap to **150 mm**.
    *   Apply **fillet** of **15 mm** to both corners.
3.  **Create lofted paddle link sections:**
    *   Select a face, create a **sketch**, **convert entity** to create a circle.
    *   Create a **plane** perpendicular to the line at a specific point.
    *   On this plane, create a **sketch**, draw a **circle** of **18 mm** diameter.
    *   Use **Lofted Boss Base**, selecting the converted circle and the new circle.
    *   Hide the plane.
    *   Create another **plane** at the other end of the line.
    *   On this plane, create a **sketch**, draw a **circle** of **18 mm** diameter.
    *   Select a face, create a **sketch**, **convert entity** to create a circle.
    *   Apply **Lofted Boss Base** for these two circles.
    *   Hide planes and sketches.
4.  **Create cuts in the paddle link:**
    *   Choose the **Top Plane**, create a **sketch**.
    *   Draw a **rectangle** of **4 mm** by **38.5 mm**.
    *   **Extrude Cut** using **mid plane** end condition.
    *   Choose the **Top Plane**, create a **sketch**, draw **corner rectangles** of **20 mm** by **7 mm** and **7 mm** by **20 mm**.
    *   **Extrude Cut** using **mid plane** end condition.
5.  **Design the sprocket:**
    *   Select the inside face, create a **sketch**.
    *   Draw a **circle** of **151 mm**.
    *   Draw a smaller **circle** of **10 mm**.
    *   Apply **fillet** and **trim**.
    *   Use **Circular Pattern** for the trimmed shape, with **38 number of patterns**.
    *   Use **Power Trim** to cut all excess lines.
    *   **Extrude Boss** **4 mm**.
6.  **Add detailing to the sprocket:**
    *   Select the face, create a **sketch**, draw two circles.
    *   Define dimensions: **126 mm** and **83 mm**.
    *   Draw a **vertical center line** and another **line**.
    *   Define gap as **5 mm** and angle **60 mm** (degrees).
    *   Use **Power Trim**.
    *   Draw a **line** of **60 mm**.
    *   Ensure fully defined sketch.
    *   Apply **fillet** of **5 mm**.
    *   Use **Circular Pattern** for the geometry, with **six number of parts**.
    *   **Extrude Cut** **up to next**.
    *   Sketch a **circle** of **130 mm**, **extrude cut** **1 mm** depth.
    *   Repeat the same on the opposite side: sketch two circles (bigger and smaller), **extrude cut** **1 mm** depth.
    *   Apply **fillet** (inside pattern).
    *   **Save** as "sprocket with parallel link".

### **Part 6: Bicycle Seat**

1.  **Sketch the seat base outline:**
    *   Choose the **Top Plane**, create a **sketch**.
    *   Draw a **center rectangle** for construction: **230 mm** by **70 mm**.
    *   Draw a **center line**.
    *   Draw a **spline**, adjust it.
    *   **Mirror** it.
    *   Place a **star point**.
2.  **Create complex 3D curves for seat shape:**
    *   Choose the **Front Plane**, create a **sketch**, and draw a **spline**.
    *   Draw another **spline** and connect it.
    *   Adjust to be smaller.
    *   Create a **plane** from the **Top Plane** at **45°**, with a second reference plane at **90°** (adjust to **225°** or **190°**).
    *   On this plane, use **3D Sketch Spline** to connect a point.
    *   Insert multiple **spline points** and drag them to adjust rough geometry.
    *   Hide the plane.
3.  **Create multiple planes along the path:**
    *   Create **multiple planes** (e.g., 8-10 planes) from the **Right Plane** along the 3D spline path at different points.
    *   Edit sketch, add a **star point**.
4.  **Sketch profiles on each plane for lofting:**
    *   On each created plane (e.g., Plane 10, then Plane 2, etc.), create a **sketch**.
    *   Draw **vertical lines**, connect points, and use **threepoint arcs**.
    *   Use **Pierce** relation to connect points to arcs/lines.
    *   Adjust radius if too much.
5.  **Create the seat body using Lofted Boss Base:**
    *   Use **Lofted Boss Base**, selecting all the sketched profiles on the planes in sequence.
    *   Hide all geometry.
    *   **Mirror** the body using the **Front Plane**.
    *   Apply **fillet** of **10 mm** to a face, then **30 mm** to another.
6.  **Add seat post and clamp:**
    *   Choose the **Front Plane**, create a **sketch**, draw a **line**.
    *   Define dimensions: **20 mm**, **82 mm**, **19 mm**, **20 mm**.
    *   **Extrude Cut** **70 mm** using **mid plane**.
    *   Select the face, create a **sketch**, draw a **center line circle** of **28 mm** diameter.
    *   **Extrude Boss** **160 mm**.
    *   Assign **nickel** (or **satin finish stainless steel**) color to this part and **matte rubber** to the seat body.
    *   Apply some **fillets** for smooth appearance.
    *   **Save** as "bicycle seat".

### **Part 7: Chain**

1.  **Create a single chain link:**
    *   Choose the **Front Plane**, create a **sketch**.
    *   Draw a **circle** of **9.5 mm**.
    *   **Mirror** this circle against a vertical line.
    *   Set center gap to **12 mm** then **12.3 mm**.
    *   **Extrude** **2 mm** thickness using **mid plane**.
    *   Edit sketch, add two more circles in the mid, **4.5 mm**, make them **equal**.
    *   Select the front face, create a **sketch**.
    *   Draw two bigger circles of **10 mm** diameter.
    *   Draw a **three-point arc**.
    *   Make tangent relations between lines/arcs.
    *   Use **Power Trim**.
    *   **Extrude** **1 mm**.
    *   **Mirror** the full body using the **Front Plane**.
    *   Edit extruded body, select two inside circles, **convert entity**.
2.  **Create the chain path:**
    *   Choose the **Front Plane**, create a **sketch**.
    *   Draw a **bottom line** and a **vertical construction line**.
    *   Define **120 mm**.
    *   Draw a **center point arc**.
    *   Draw another **center point arc**.
    *   Draw a **three-point arc**, connect points, ensure tangent relations.
    *   Define radius **29.10 mm**, **75 mm**.
    *   Set diagonal distance between center points to **3300.06 mm** then **42 mm** then **1155.42 mm**.
3.  **Pattern the chain along the path:**
    *   Use **Curve Driven Pattern**.
    *   Select the chain link part.
    *   Set gap to **25 mm**, **40 number of chains**.
    *   Choose **tangent to curve** and **equally spacing**.
    *   Select bodies.
    *   Hide the plane.
    *   Assign **steel brush finish**.
    *   **Save** as "inner chain".

### **Part 8: Pin**

1.  **Create the pin:**
    *   Choose the **Front Plane**, create a **sketch**.
    *   Make a **10 mm** diameter circle.
    *   **Extrude** it up to **100 mm** using **mid plane**.
    *   Apply **fillet** of **0.3 mm**.
    *   Assign **polished steel**.
    *   **Save** as "part number seven pin".

### **Part 9: Paddle**

1.  **Create the paddle base:**
    *   Choose the **Top Plane**, create a **sketch**.
    *   Draw a **center rectangle** of **100 mm** by **80 mm**.
    *   **Extrude** it up to **30 mm** using **mid plane**.
    *   Select the face, create a **sketch**, draw a **circle** of **15 mm** diameter.
    *   **Extrude Cut** **through all**.
2.  **Add grip pattern (rectangular cuts):**
    *   Select the face, create a **sketch**.
    *   Draw a **corner rectangle** with a **midline**.
    *   Define dimensions: **42.65 mm**, **23 mm**.
    *   Set **5 mm** by **5 mm**.
    *   Make lines **equal** and **collinear**.
    *   **Mirror** the rectangle against the midline.
    *   **Extrude Cut** **through all**.
    *   Apply **fillet** of **20 mm** to two ends.
3.  **Create axle holes:**
    *   Select a face, create a **sketch**, draw two circles: outer **40 mm**, inner **17 mm**.
    *   **Extrude Cut** **up to surface**.
    *   Select a face (plane), create a **sketch**, **convert entity** from previous geometry.
    *   **Extrude Cut** **up to next**.
4.  **Add additional cuts and extrusions:**
    *   Select a face, create a **sketch**, draw a **corner rectangle**.
    *   **Extrude** to cut **5 mm** depth.
    *   **Mirror** this cutout using the **Top Plane**.
    *   Select a face, create a **sketch**, draw a **corner rectangle** up to the corner.
    *   **Extrude** up to **5 mm**.
    *   Select a face, create a **sketch**, draw circles **17 mm** by **10 mm** by **15 mm**.
    *   **Extrude** up to **10 mm**.
    *   Apply **fillet** of **10 mm**, then **15 mm** (outside).
5.  **Create grip textures (lines and slots):**
    *   Select the top face, create a **sketch**.
    *   Draw lines with **5 mm** and **collinear** relation.
    *   Use **linear pattern** to create multiple lines.
    *   **Extrude Cut** **3 mm** depth (edit to be up to the corner).
    *   **Mirror** this extruded cutout using the **Top Plane**.
    *   Select a face, **convert entity** of a rectangle.
    *   **Extrude Cut** **2 mm** depth.
    *   Select a face, create a **sketch**, draw a **straight slot** (drag it, set **60 mm**, **6.5 mm**).
    *   **Extrude Boss** **2 mm**.
    *   **Mirror** this extruded part using the **Front Plane**.
    *   Select a face, create a **sketch**, draw a circle of **20 mm** to cover a hole.
    *   **Extrude** **2 mm**.
    *   Add **fillets** everywhere.
    *   Assign a **dark yellow** or **dark red** color.
    *   **Save** as "part number eight paddle".

### **Bicycle Assembly**

1.  **Start assembly and insert main parts:**
    *   Open **SolidWorks Assembly**.
    *   **Browse** and insert "frame" as the first part.
    *   Right-click on the frame and choose **"Fixed"** (it was initially "Float").
    *   Insert "steering" part.
    *   **Mate** the steering rod with the hole in the frame using **concentric** relation.
    *   Mate the flat face of the steering with a face on the frame using **coincident** relation.
2.  **Assemble the front tire:**
    *   **Browse** and insert "front tire".
    *   **Mate** any circular face of the tire with its corresponding face on the steering using **concentric** relation.
    *   Use **Advanced Width Mate** by selecting the inner and outer faces of the tire and the corresponding faces on the steering to center the tire.
    *   Measure the gap between the tire and the steering (e.g., **5.5 mm**).
    *   **Edit** the "front tire" part: select the faces, **convert entities** (circles), and **extrude** by the measured gap (**5.5 mm**).
    *   Save changes in the part and assembly.
3.  **Assemble the rear tire:**
    *   **Browse** and insert "rear tire".
    *   **Mate** a circular face of the tire with its corresponding hole in the frame using **concentric** relation.
    *   Use **Advanced Width Mate** to center the tire.
4.  **Assemble the sprocket with paddle link:**
    *   **Browse** and insert "tire sprocket with paddle".
    *   **Mate** the sprocket face with a corresponding face on the frame using **concentric** relation.
    *   **Mate** a hole on the sprocket link with a hole on the frame using **coincident** relation.
    *   **Mate** the flat face of the paddle link with a face on the frame using **coincident** relation.
    *   **Copy** the paddle link part (Ctrl+key drag).
    *   **Mate** the inside face of the copied paddle with the main sprocket part, using **flip mate** and **coincident** relation.
5.  **Assemble the pins:**
    *   **Insert** the "pin" part.
    *   **Copy** the pin part (Ctrl+key drag) to make a second one.
    *   **Mate** a pin with a hole in the paddle link using **coincident** relation.
    *   Use **Advanced Width Mate** to center the pin within the hole.
    *   Repeat for the second pin on the other side.
6.  **Assemble the seat:**
    *   **Browse** and insert the "seat" part.
    *   **Mate** a face on the seat with a face on the frame using **coincident** relation, then adjust distance to **-50 mm** or **50 mm**.
    *   Adjust manually, then **mate** specific surfaces with a **90 mm** gap.
    *   **Mate** the **Front Plane** of the seat with the **Front Plane** of the frame using **coincident** relation to align.
7.  **Assemble the chain (manual adjustment):**
    *   **Browse** and insert the "inner chain" part.
    *   Rotate and **mate** the chain to fit the sprocket and rear tire.
    *   **Mate** a half circle of the chain with a circular part of the sprocket using **coincident** relation.
    *   Manually fix its position as it might not be perfectly sized for real animation.
8.  **Add a bearing (from Toolbox):**
    *   Go to **Toolbox**, **Add-in**, choose **Metric**, and select **radial ball bearing**.
    *   **Mate** a face of the bearing with a face on the wheel hub using **coincident** relation.
9.  **Add Mechanical Mate for animation:**
    *   Go to **Mate**, then **Mechanical Mate**, choose **Gear**.
    *   Select one circular path on the **sprocket** and one circular path on the **bicycle wheel**.
    *   Confirm the gear relation by trying to rotate.
10. **Setup Basic Motion (Animation):**
    *   Go to **Motion Manager**.
    *   Select **Basic Motion**.
    *   Choose a circular face (e.g., on the tire or sprocket) and set **10 revolutions** or **30 RPM**.
    *   **Calculate** the motion.
    *   **Play** the animation, and **edit** to **reverse** if needed.
    *   Recalculate and play again.
    *   **Save** the animation.
