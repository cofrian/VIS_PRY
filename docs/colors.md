# Visual Identity & Color Guidelines for `app.py`

This document outlines the technical design audit and strict color specifications required for the project, aligned with Data-Ink Ratio principles and accessibility standards (Stephen Few, Tufte).

---

## 1. Structure Palette ( The "Canvas")
**Constraint:** Non-data components must be visible but subtle to avoid visual fatigue and distraction.

* **Dashboard Background:** `#FDFDFD`.
    * *Note:* Avoid pure white (`#FFFFFF`) to reduce eye strain on screens.
* **Grid Lines:** `#E5E5E5`.
    * *Style:* Thin and barely perceptible.
* **Text (Axes & Labels):** `#455A64`.
    * *Reasoning:* More legible and softer than pure black.
* **Titles:** `#263238`.
    * *Style:* Bold for visual hierarchy.

---

## 2. Data Palettes (Logic & Hex Codes)

### A. Categorical Variables (Continents / Groups)
**Constraint:** Avoid Red-Green combinations. Use perceptually uniform intensities.
**Recommended Palette:** `Set2` or a Custom Colorblind-Safe palette.

**Specific Mapping:**
* **Europe:** `#8DA0CB` 
* **America:** `#FC8D62` 
* **Asia:** `#66C2A5` 
* **Africa:** `#E78AC3` 
* **Oceania:** `#A6D854` 

### B. Quantitative Variables (Incidence, Cases, Deaths)
**Constraint:** Use a single hue or closely related hues with varying intensity.
**Recommended Scale:** `Viridis`.
* *Reasoning:* Uniform for colorblind users and prints well in B&W.
* **Range:** From `#FDE725`  to `#440154`.

### C. Comparison Variables (Growth +/- or Diff vs. Mean)
**Constraint:** Use a **Diverging Palette**.
* **Colors:** Blue (Positive/Low Risk) - White (Neutral) - Red (Negative/High Risk).
* **Reasoning:** Red is reserved *exclusively* for critical mortality alerts (Psychology of Color).