---
layout: post
title:  "solidworks example"
date:   2025-07-01 14:56:51 +0200
categories: jekyll update
---

The process of designing a simple mouse in SolidWorks using advanced surfacing tools involves numerous steps, broadly categorized into initial sketching and surface extrusion, surface trimming, creating and defining new planes and sketches, forming complex geometries with boundary surfaces, adding features like grooves and cutouts, thickening the model, and final detailing.

Here is a comprehensive breakdown of the steps:

*   **Initial Setup and Main Body Creation:**
    *   Start by selecting the **Front Plane** for a sketch.
    *   Draw a **spline** and define its points: three points at the origin, one end horizontal, and the other side vertical and horizontal.
    *   Set the end points to **50mm**.
    *   Define arrow lengths (e.g., 105mm, 103mm, 90mm, 75mm) and the length from the origin point to **25.75mm**.
    *   Exit the sketch.
    *   Go to **Surface** and select **Extruded Surface**, extruding it up to **100mm**.

*   **First Surface Trimming:**
    *   Select the **Front Plane** again for a new sketch.
    *   Draw another **spline**, ensuring its ends are horizontal and another point is horizontal.
    *   Define end points (e.g., 100mm, 12mm, 7.75mm) and the length from the origin point to **25.75mm**.
    *   Define arrow points (e.g., 95mm, 105mm, 30mm).
    *   Exit the sketch.
    *   Select the created body, then go to **Surface** and select **Trim Surface**.
    *   Choose **Standard** as the trim type and select the current sketch as the trim tool.
    *   Select the bottom section to be removed.

*   **Creating Side Contours and Extrusions:**
    *   On the **Front Plane**, sketch a **center line** passing through the origin.
    *   Define its length (e.g., 45.75mm, 34.5mm).
    *   Use the **Three Point Arc** tool to connect points, making sure to add a **tangent relation** between the vertical line and the arc. Repeat for another arc.
    *   Go to **Surface** and **Extrude** this profile up to **10mm** in the reverse direction.

*   **Establishing New Planes and Sketches for Complex Shapes:**
    *   Create a new plane by selecting the **Right Plane**, then going to **Feature** > **Plane**.
    *   Select the first point to define the new plane.
    *   On this new plane, sketch a **center line** that coincides with the existing geometry.
    *   Ensure the end point of the center line coincides with the bottom line using a "Piers" relation.
    *   Draw a **spline** and an arc, ensuring the arc coincides with the line and its arrow is vertical.
    *   Define the arc's dimensions (e.g., 30mm, 23mm from origin).
    *   Exit the sketch and hide the plane.

*   **Creating Boundary Surfaces for Form:**
    *   Select the **Top Plane** for a sketch and draw a similar **spline**.
    *   Make both end points and the mid-point horizontal.
    *   Define the spline's dimensions (e.g., 46.5mm, 45.7mm) and arrow points (e.g., 80mm, 150mm, 95mm).
    *   Set the center distance from the origin to **10.75mm** and the length to **20mm**.
    *   Exit the sketch.
    *   Go to **Surface** and choose **Boundary Surface**.
    *   Select the first recent edge and set it to **Tangent to Face**.
    *   Select the second edge and keep it **Normal to Profile**.
    *   In **Direction 2**, select the upper edge and the geometry for the sketch, keeping tension at **1**.
    *   Adjust **Trim Direction 1** and **Trim Direction 2** (e.g., 1 and 1).
    *   Repeat the **Boundary Surface** process: select an edge and another edge, setting both to **Tangent to Face**, and adjusting directions (e.g., 100 for both). Apply trim in Direction 1.
    *   Set trim dimensions (e.g., 25, 40, and scale).
    *   Select the surface and **Extrude** it as Part 1, then hide it.

*   **Adding Further Detail and Shaping:**
    *   On **Plane 1**, sketch an "inside line" and set it as construction geometry.
    *   Choose a **spline** and an **advanced spline**, making one horizontal and the other vertical.
    *   Define dimensions (e.g., 12mm, 40mm) and create a **tangent relation** between the spline and a point.
    *   Define the gap (e.g., 37.25mm) and ensure both points are aligned.
    *   Exit the sketch.
    *   Go to **Surface** and **Extrude** this profile by **10mm**.
    *   Create **Plane 02**.
    *   On Plane 02, draw a **construction line**.
    *   Create a "Piers" relation between the outer edge of the construction line and the side outer edge.
    *   Draw a **spline** connecting to a point and another **three-point arc**, establishing "Piers" and **tangent relations**.
    *   Define dimensions (e.g., 38mm, 15mm, 26mm, 30mm vertical) and angles (e.g., 20 degrees, 30 degrees). Check final dimensions (e.g., 43.34mm for end points).
    *   Exit the sketch and hide the plane.
    *   On the **Front Plane**, sketch a **center line** from end to end and adjust its end points.
    *   Convert the outer and bottom outer edges into entities.
    *   Draw a **spline** connected to a point.
    *   Define dimensions (e.g., 25mm, 10.75mm, 37.25mm vertical, 40mm) and make the arrow horizontal. Define length (e.g., 182.5mm).
    *   Exit the sketch.

*   **Refining Complex Surfaces and Trimming:**
    *   Create a new plane using **Features** > **Plane**, selecting the arc and surface center point, making it coincident and perpendicular.
    *   On this new plane, sketch a **spline** connecting from one end to another.
    *   Create **coincident** and **tangent relations** with previous arcs and lines.
    *   Define angles (e.g., 82 degrees) and dimensions (e.g., 12.5mm, 15mm, 7.5mm).
    *   Ensure a line is a construction line.
    *   Define the arrow (e.g., 37.5mm) and recalculate the sketch.
    *   Exit the sketch and hide the plane.
    *   Select **3D Sketch**, draw a line, and convert entities.
    *   Choose a **center line**, draw a vertical line, and then a **spline** from end to end. Exit the sketch.
    *   Go to **Surface** > **Boundary Surface**.
    *   Select the arc, keeping it **Tangent to Face**. Select the second arc, keeping it **Normal to Profile**. Select the third line, keeping it **Tangent to Face**.
    *   Set **Direction 1** and **Direction 2** values (e.g., 75mm, 90%, 75%, 60%, 80%).
    *   On the **Front Plane**, sketch a structure from the previous boundary.
    *   Convert a line to an entity.
    *   Draw two vertical **center lines** and define the gap (e.g., 25mm).
    *   Use **Trim Entities** to remove half and outer lines. Exit the sketch.
    *   Go to **Surface** > **Boundary Surface**, select the lines and the 3D sketch.
    *   Set to **Normal to Profile** and **Tangent to Face** at 100%.
    *   On the **Top Plane**, sketch a **center line** and a **spline** from point to point.
    *   Make the spline's arrows vertical and horizontal.
    *   Define dimensions (e.g., 30mm on one side, 23mm on the other). Delete the construction line.
    *   Exit and go to **Surface** > **Trim Surface**. Select the outer layer, remove selection, and specify the area to remove.
    *   Apply a dark color to the whole body.
    *   On the **Front Plane**, convert sketch number two to entities.
    *   On **Plane 1**, convert the inner edge to entities. Exit.
    *   Go to **Surface** > **Boundary Surface**.
    *   Select Sketch 1 and the "N" sketch, keeping both **Normal to Profile**.
    *   Select the two parts using **Selection Manager** (open loop, group select, select one face).
    *   Set tension to 100%, both tangent faces to 100%, and set to 75% for trimming by Direction 1 and 2.
    *   Close open spaces by selecting **Surface** > **Boundary Surface** again.
    *   Select the 3D sketch geometry and convert entities.
    *   Use **Trim Entities** to trim half lines. Exit.
    *   Go to **Feature** > **Surface** > **Boundary Surface**. Select the edge and geometry, then click **Trim Both Sides**.
    *   Set **Normal to Profile** and **Tangent to Face** to 100%, and keep Normal at 75%.
    *   Select the inner face and convert it to an entity.
    *   Draw a **center line** and a vertical construction line, then use **Trim Entities** to delete extra parts. Exit.
    *   Go to **Surface** > **Boundary Surface** and select the faces.
    *   Trim by **Direction 1** (e.g., 2), ensuring tangent and normal to profile settings are correct.

*   **Creating Cutouts and Grooves:**
    *   Make cutouts.
    *   On the **Top Plane**, sketch and convert sketch number two.
    *   On the **Front Plane**, convert sketch number two to entities.
    *   Offset it up to **2mm**.
    *   Go to **Surface** > **Trim Surface**, select the face, and rotate to find the small size inside. Exit.
    *   On the **Top Plane**, sketch a **spline** connecting points.
    *   Draw another **spline** connecting both ends.
    *   Make the first spline vertical and the second horizontal.
    *   Define dimensions (e.g., 10.75mm, 5.75mm from bottom, 6.25mm from outer line, 2.35mm for end point).
    *   Make both points tangent and arrows horizontal.
    *   Define lengths (e.g., 10mm, 80mm, 65mm) and reduce tangent relation.
    *   Define offset point (e.g., 42.5mm) and reverse direction.
    *   Go to **Feature** > **Surface** and select **Revolved Cut**. Select the middle passage.

*   **Mirroring, Combining, and Thickening:**
    *   **Mirror** the design using **Front Plane** > **Mirror** > **Bodies**, selecting all relevant bodies.
    *   Go to **Surface** > **Net Surface** to combine all surfaces.
    *   Use the **Filled Surface** tool to close the back face by selecting the edges to fill.
    *   Hide unnecessary faces used for reference.
    *   Select all surfaces.

*   **Adding Scroll Wheel and Final Details:**
    *   For the scroll wheel cutout, select the **Top Plane** for a sketch.
    *   Define a **center line** (e.g., 3.75mm, 10mm) and its distance from one end to the last end (e.g., 10.25mm).
    *   Go to **Surface** and choose **Trim Surface**. Select inside to trim the hole for the scroll wheel.
    *   Add thickness using the **Thicken** tool: first **2.5mm** to the selected surface, then **20mm** for the bottom.
    *   Define the color (e.g., Red).
    *   Add another thickness of **0.5mm** to the bottom body, reducing the second thickness to **0.5mm**.
    *   Create grooves: on the **Top Plane**, sketch a horizontal **center line** and a **rectangle**.
    *   Make the rectangle symmetric to the center line.
    *   Define its width (e.g., 0.6mm), length (e.g., 50mm), and distance from the outer edge (e.g., 1mm).
    *   Go to **Feature** > **Extruded Cut**, select reverse direction, and specify bodies for the cut (only offices).
    *   Create the "ball" feature: on the **Front Plane**, sketch a **circle**.
    *   Define its distance (e.g., 30mm, 15.5mm) and diameter (e.g., 35mm).
    *   Select offset surface and set the condition to **Mid Plane** (e.g., 6.5mm, 80mm).
    *   Modify dimensions (e.g., 15mm, maximum air plane) and add a plane (e.g., 10.5mm). Exit.
    *   Add a **fillet** of **10mm** to the surface.
    *   On the **Front Plane**, sketch another **circle**, finding its mid-point and offsetting up to that point.
    *   Define its diameter (e.g., 0.5mm) and gap (e.g., 2.1mm). Connect both end points.
    *   Draw a **center line** and define its gap (e.g., 3.5mm).
    *   Go to **Features** > **Revolved Boss/Base**. Select the line as the axis and set to **90 degrees** with a **Mid Plane** condition.
    *   Use **Circular Pattern** to duplicate the cutout feature. Select the cutout feature and the circular face. Set to **3 numbers** with equal spacing.
    *   Apply a final **fillet** of **0.1mm** to the full surface.
