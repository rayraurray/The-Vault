
# Tufte’s Integrity Principles

**Why Design Guidelines?**
- To ensure **data integrity**. 
- To help viewers **correctly interpret** the data.
- To promote **ethical, clear, and effective** visual communication.

---

## 1. Avoid Graphical Distortion

- Visual representations should match the underlying data ***proportionally***.
- Misleading scales, altered axes, or exaggerated graphics distort the truth.
- Show data variation, not design variation
- Graphics must not quote data out of context

## 2. Rules to Prevent Distortion

- Always **start bar charts at 0**. Non-zero axes exaggerate differences.
- Avoid manipulations of time axes (e.g., inconsistent intervals on the x-axis).
- The **lie factor** should be close to 1 (Lie Factor = visual effect / data effect).
- Don't take data out of **context**—it leads to misinterpretation.

![[Pasted image 20250518103759.png]]
*Misleading ahh*

![[Pasted image 20250518103933.png]]
***fixed**, always start bar charts at 0 dawgs*

![[Pasted image 20250518104756.png]]
*another start at 0 dawg*

![[Pasted image 20250518104103.png]]
*lmao what in the actual fac is this*

## 3. Avoid Scale Distortion

- Do not exaggerate effects by changing scales or using 3D visuals.
- Example: Using only a 15-year range instead of 50 years to hide long-term trends.

![[Pasted image 20250518105100.png]]

![[Pasted image 20250518104711.png]]

![[Pasted image 20250518104937.png]]

![[Pasted image 20250518105022.png]]

## 4. Use Proper Labeling

- Labels must be **clear and complete**—don’t assume viewer knowledge.
- Add **units**, **source**, and **context** where relevant.

![[Pasted image 20250518105459.png]]
*report the **important** number*

---
# Tufte’s Design Principles

## 1. Maximize Data-Ink Ratio

- **Data-Ink**: Ink used to present core data.
![[Pasted image 20250518105859.png]]

![[Pasted image 20250518105929.png]]

![[Pasted image 20250518110142.png]]
*TOO MUCH **INK** 💀*

- **Chart Junk**: Unnecessary visuals that distract from the data (e.g., 3D effects, gridlines, background images).
- Remove everything that doesn’t serve a **purpose**—make every pixel count.

![[Pasted image 20250518105949.png]]
*a lil ugly*

![[Pasted image 20250518110011.png]]
 *better*
 
## 2. High Data Density

> nah this might not be the best way to go dawg

- Aim for more **information per square inch**.
- Use compact formats where possible, like **small multiples**.
- Avoid graphs that show too little information for the space they occupy.

![[Pasted image 20250518110553.png]]

![[Pasted image 20250518110647.png]]

![[Pasted image 20250518110717.png]]

## 3. Layering and Separation

- Organize content visually: **group related elements**, separate unrelated ones.
- Use **visual hierarchy** (contrast, whitespace, lines, colors) to structure complex information.
- Helps prevent **visual clutter** and confusion.

![[Pasted image 20250518110957.png]]

![[Pasted image 20250518111021.png]]

![[Pasted image 20250518111032.png]]

# Munzner’s Guidelines
*3D Visualisation Issues*

---

## 1. Avoid Unjustified 3D Graphics

Human perception struggles with:
- **Depth judgment**
- **Occlusion** (objects covering each other)
- **Perspective distortion**
- **Lighting and shading** tricks
- **Tilted text**, which is hard to read

**General Rule:** 
*If 3D doesn’t add meaningful value, **don’t use it**. Use **2D** whenever clarity is more important than aesthetics.

![[Pasted image 20250518111359.png]]
*human depth perception is poor*

![[Pasted image 20250518111438.png]]
*this is all occluded lmao*

![[Pasted image 20250518111504.png]]
*perspective distortion*

![[Pasted image 20250518111535.png]]
*wonky lighting and shading*

## 2. Cognitive Load

- “**Eyes beat memory**”: side-by-side (static) comparisons are often more effective than animations.
- **Change blindness**: viewers may miss transitions or trends in animations.
- Alternatives:
    - Use **small multiples**: series of similar small charts showing changes over time.
    - Static visualizations allow for **better comparison**.

![[Pasted image 20250518111808.png]]
*small multiples in place of animation*

![[Pasted image 20250518112209.png]]
*better nè*

## 3. Visual Critique

**Common Bubble Chart Issues:**
- Viewers **misinterpret area** as radius (or vice versa).
- Diameter vs Area: **Doubling diameter** quadruples the area, which exaggerates differences.
- Use **bar charts or line charts** when precision is required.
![[Pasted image 20250518112536.png]]

**Design Critique Questions:**
- Who is the audience?
- What questions does the visual answer?
- What principles does it follow or violate?
- Can it be improved?

