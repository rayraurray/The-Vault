**What:** Understand the **types of data** used in visualization.
**Why:** Knowing the data type **drives visualization design** decisions.
**How:** First, understand the **properties** of different data types; later, explore how to represent them visually.

---

# Data Semantics and Types

## 1. Semantics
**Semantics:** The **real-world meaning** of the data (e.g., "Basil" might represent a person or a plant).

**Types:**
- Numbers like **‘7’** can mean: A value (e.g., minutes, height) or A label or identifier (e.g., shop ID, dish number)
- The same value can **carry different meanings** depending on context.

**Why it matters:** If “Basil” is a person, you’d visualize it as a categorical label. If it’s an ingredient, you might embed it in a recipe network.

## 2. Data Type (Form)
*Underlying form of the datum* - number, string, date, etc.

**Example:** The value **7** can represent:
- **Quantity** of minutes to complete a task
- **Category code** for a dish on a menu

**Key insight:** **Same form**, different meaning → different visual encoding.

# Metadata
*Data about data.*

**What:** Information that describes your dataset’s structure and provenance.
- Column names, data source, update frequency.
**Why:**
- Helps automated tools parse your file.
- Documents assumptions (e.g., “temperature in °C, sampled hourly”).

---
# Data Types
Each dataset is built from these **atomic pieces**:

|Instance|Definition|Visualization Implication|
|---|---|---|
|**Items**|Discrete entities (e.g., a person, a tweet)|Each becomes a mark (dot, bar, node).|
|**Attributes**|Properties of items (e.g., age, text)|Drive color, size, position encodings.|
|**Links**|Relationships (e.g., friendship, co‑occurrence)|Render as edges in a network diagram.|
|**Positions**|2D/3D coordinates (e.g., lat/long)|Directly map to spatial axes.|
|**Grids**|Sampling structure for continuous data|Basis for heatmaps, contour plots.|
![[Pasted image 20250520105453.png]]
*items*

![[Pasted image 20250520105510.png]]
![[Pasted image 20250520105544.png]]
*attributes*

![[Pasted image 20250520105627.png]]
*links*

![[Pasted image 20250520105641.png]]
*positions*

![[Pasted image 20250520105659.png]]
*grids*

---
# Scales of Measurement
Your choice of **mathematical operations** depends on scale

## 1. Nominal
Categories without order (e.g., blood type, country code).

- Ops: equality check only.
- **Use:** distinct hues, categorical shapes.

## 2. Ordinal
Ordered categories (e.g., Likert scale, race positions).

- Ops: equality, ranking comparisons.        
- **Use:** gradient of a single hue (light $\rightarrow$ dark), size differences.

## 3. Interval
Numeric, equal spacing, _no_ true zero (e.g., °C, SAT scores).

- Ops: add/subtract, compare.	
- **Use:** color ramps, linear axes (but note zero isn’t absolute).

## 4. Ratio
Interval _plus_ an absolute zero (e.g., weight, age).

- Ops: full arithmetic (add/multiply/divide).
- **Use:** area/length encodings (since proportion is meaningful).

---
# Key Features
## 1. Sequential
*Unipolar* - Data that naturally flows from low $\rightarrow$ high

- E.g., temperature, price, density.
- **Encoding:** single‑hue ramp (pale → intense).
 
## 2. Divergent
*Bipolar* - Data with a critical midpoint (zero)

- E.g., sea‑level change (below ↔ above), budget surplus/deficit.
- **Encoding:** two contrasting hues meeting at a neutral midpoint.

## 3. Availability
**Static:** Snapshot in time. Easy to cache and preprocess.

**Dynamic (Streaming):** Live feeds (social media, sensor networks). **Challenges** include: 
- Data volume and velocity.
- Need for incremental layouts and cache‑friendly updates.

## 4. Keys
*An attribute that acts as index that is used to look up value attributes*
- **Explicit Keys:** Column in your table (e.g., `OrderID`).
- **Implicit Keys:** Row index when no dedicated ID exists.

**Requirements:**    
- Uniqueness.
- Non‑duplicated, non‑null.
- Often categorical or ordinal.

---
# Dataset Archetypes

## 1. Tables
*it's just tables bô*

A set of data that is in the form of a table made up of rows and columns

**Flat table:** 
- Rows $\rightarrow$ Items
- Columns $\rightarrow$ Attributes.
- Cell $\rightarrow$ Value specified by item and attribute

**Common:** CSV, relational DB tables.
![[Pasted image 20250520111646.png]]
## 2. Networks/Graphs
*Nodes + links.*

A set of data that is in the form of items (nodes) and the relationship between them (links). Links can go one or both ways, nodes can also be associated with attributes

**Examples:** social networks, citation graphs.
![[Pasted image 20250520111630.png]]
## 3. Fields
*Continuous measurements over space/time.*

Requires *sampling and interpolation* (to show values between sampled points)

**Examples:** climate models, MRI scans.
![[Pasted image 20250520112038.png]]

![[Pasted image 20250520112100.png]]
## 4. Geometry
*Specification of the shapes of items in a spatial position.*

Used where shape is important feature of data, with explicit shapes: points, lines, polygons, meshes, etc. 

**Examples:** CAD models, GIS shapefiles.
![[Pasted image 20250520112423.png]]

---
# Workflow

1. **Inspect** your raw data → identify items, attributes, and keys.
2. **Classify** each attribute by scale (nominal, ordinal, etc.).
3. **Choose** dataset archetype (table, network, field, geometry).
4. **Decide** on static vs. real‑time handling.
5. **Transform** or **interpolate** as needed (e.g., pivot tables, grid interpolation).
6. **Map** data to visual channels: position, color, shape, size, edge thickness.
7. **Iterate**—test, ask questions (“Does this color mislead at zero?”), refine.