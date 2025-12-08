

# **Working Principle of Black and White Video Monitor**

A **Black and White (Monochrome) Video Monitor** is an output device that displays images using only two intensities – **black** (no light) and **white** (full light), along with possible shades of gray. It mainly uses a **Cathode Ray Tube (CRT)** mechanism to display characters and graphics. The working principle is based on **electron beam scanning and phosphor illumination**.

---

## **1. Construction of a CRT Monitor**

A B/W monitor mainly consists of:

1. **Electron Gun** – generates a focused stream of electrons.
2. **Control Grid** – controls the intensity (brightness) of the beam.
3. **Horizontal & Vertical Deflection Plates/Coils** – guide the beam across the screen.
4. **Phosphor-coated Screen** – emits white light when struck by electrons.
5. **Video Amplifier Circuit** – converts digital signals into video signals.
6. **Synchronization Circuit** – provides proper timing for scanning.

---

## **2. Basic Working Principle**

The operation of a B/W monitor depends on controlling the electron beam to create visible patterns.

### **a) Electron Beam Generation**

* The **electron gun** emits a continuous beam of electrons.
* The beam is accelerated and focused into a narrow spot by focusing circuits.

### **b) Beam Scanning**

The beam moves across the screen in a **raster scan** pattern:

* It starts from the **top-left corner**.
* Moves **horizontally** to the right.
* Returns to the next line (**horizontal retrace**).
* After finishing all lines, it returns to the top (**vertical retrace**).

This scanning happens **30–60 times per second**, producing a stable picture.

### **c) Phosphor Illumination**

* The screen is coated with **white phosphor**.
* When the beam hits a point, the phosphor glows **white**.
* When the beam intensity is zero, the point stays **black**.

Thus, **brightness of each pixel** is controlled by the electron beam intensity.

---

## **3. Video Signal Interpretation**

The computer sends a **video signal** that tells the monitor:

* When to turn the beam ON (white pixel)
* When to turn the beam OFF (black pixel)
* How bright the pixel should be (analog intensity control)

The monitor has circuits to convert these signals into electron beam modulation.

---

## **4. Synchronization**

Two types of sync signals are supplied:

1. **Horizontal Sync (HSYNC)** – moves beam to the next line.
2. **Vertical Sync (VSYNC)** – moves beam to the top after completing all lines.

Without synchronization, the image would **tear, roll, or distort**.

---

## **5. Frame Formation**

A full picture called a **frame** is formed by:

* Scanning all pixels in multiple lines
* Updating them continuously
* Refreshing at high speed (50–60 Hz)

This fast refreshing prevents flickering.

---

## **6. Advantages of B/W Monitors**

* Simple construction
* Low cost
* High clarity for text
* Low power consumption compared to colored CRTs

---

# **Final 

A Black & White video monitor works on the principle of **electron beam scanning** inside a **CRT**. The electron gun produces a beam, which is deflected horizontally and vertically to scan the screen in a raster pattern. The screen is coated with white phosphor, which glows when struck by electrons, forming white dots (pixels). The intensity of the beam controls brightness, producing black, white, and gray shades. The video signal from the computer modulates the beam, while horizontal and vertical synchronization signals ensure proper timing and stable display. The repeated refreshing of frames results in a smooth, flicker-free image.

---
