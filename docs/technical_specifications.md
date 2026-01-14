# COVID-19 Dashboard: Technical Specifications

## 1. Data Structure & Variables

### Categorical & Temporal
* **pais:** Name of the location.
* **fecha:** Temporal record (AAAA-mm-dd).
* **iso-3c:** Standardized conversion (e.g., "Spain" -> "ESP") for map projections.

### Numerical (Original & External)
* **poblalcion:** Total inhabitants.
* **confirmados_dia:** New daily cases.
* **confirmados:** Accumulated cases.
* **muertes_dia:** New daily deaths.
* **muertes:** Accumulated deaths.
* **pib_per_capita_2019:** Indicator of national wealth.
* **gasto_salud_pib:** Indicator of public health investment.

### Calculated Metrics (Feature Engineering)
* **IA_100k:** (Accumulated Cases / Population) * 100,000.
* **IA_100k_dia:** (New Daily Cases / Population) * 100,000.
* **tasa_mortalidad_por_100k:** (Accumulated Deaths / Population) * 100,000.
* **tasa_mortalidad_por_100k_dia:** (New Daily Deaths / Population) * 100,000.
* **letalidad_CFR_pct:** (Accumulated Deaths / Accumulated Cases) * 100.
* **letalidad_CFR_pct_dia:** (New Daily Deaths / New Daily Cases) * 100.

---

## 2. Project Goal
Analyze if economic wealth (GDP) was a determining factor against COVID-19 mortality or if performance depended more on health management and geographic patterns.

---

## 3. Chart Implementation Details

### 1. The "Motion Chart" (Animated Bubble Chart) 
* **Objective:** Show the correlation between a country's wealth and the mortal impact of the virus over time. [cite: 48]
* **Type:** Animated Scatter Plot.
* **Variables:**
    * **X-Axis:** GDP per capita (Logarithmic Scale). 
    * **Y-Axis:** Mortality Rate (per one hundred thousand inhabitants). 
    * **Bubble Size:** Total Population. 
    * **Color:** Continent. 
    * **Animation:** Date (January - December).
* **Theoretical Justification:** Introduces the narrative (**Data Storytelling**) by allowing the observation of temporal evolution, which is lost in a static chart. It allows observing if countries with greater economic resources managed to "flatten the curve" of mortality sooner. 

### 2. "The Waves" (Ridgeline Plot) 
* **Objective:** Compare contagion "waves" between different continents without cluttering the view with multiple overlapping lines. 
* **Type:** Ridgeline Plot. 
* **Variables:**
    * **X-Axis:** Time. 
    * **Y-Axis:** Selected Countries (Dynamic based on user selection).
    * **Height/Color:** Density of new daily cases.
* **Theoretical Justification:** Applies the **Gestalt principle (Proximity)**. By stacking distributions vertically, the brain can easily compare when peaks started and ended in selected countries, avoiding the visual clutter (**chart junk**) of a conventional line chart with too many series.

### 3. The "Dumbbell Plot" 
* **Objective:** Visualize the net increase in incidence between the start and end of the studied period.
* **Type:** Dumbbell Chart (or DNA chart). 
* **Variables:**
    * **Y-Axis:** Country (Top 15 affected by deffault. Dynamic based on user selection). 
    * **X-Axis:** Accumulated Incidence Rate. 
    * **Points:** Green Point (January) connected to Red Point (December). 
* **Theoretical Justification:** Maximizes the **Data-Ink Ratio**. Instead of using two bars per country (which would take up space and ink), we use a thin line connecting two points. The length of the line visually represents the "velocity" or magnitude of the problem's growth in that specific country. 

### 4. "Heatmap Calendar" (Intensity Calendar) 
* **Objective:** Detect cyclical temporal patterns or anomalies in data reporting. 
* **Type:** Heatmap in calendar format. 
* **Variables:**
    * **X-Axis:** Week of the year. 
    * **Y-Axis:** Day of the week (Monday - Sunday). 
    * **Color:** Intensity of daily deaths (Sequential Red scale).
* **Theoretical Justification:** Allows for quick identification of temporal "hotspots" and data problems (e.g., if weekends systematically appear lighter due to a lack of administrative reporting). It is an intuitive visualization for non-expert audiences.

### 5. Multivariable Quadrant Scatter (Sanitary Efficiency Matrix)
* **Objective:** Analyze the cost-effectiveness of health systems, verifying if higher public investment (% GDP) actually translated into lower lethality during the pandemic. 
* **Type:** Multivariable Scatter Plot (Static Bubble Chart) with Quadrant division. 
* **Variables:**
    * **X-Axis:** Accumulated Incidence (Cases per 100k inhabitants). 
    * **Y-Axis:** Lethality Rate (Deaths / Cases). 
    * **Color (Gradient):** % of GDP allocated to Health Expenditure (Sequential scale: Light=Low, Dark=High). 
    * **Size (Area):** Country Population.
    * **Annotations:** Average lines (mean or median) dividing the chart into 4 management zones. 
* **Theoretical Justification:**
    * **Data Density:** Applies the principle of maximizing information density without increasing noise (**Chart Junk**). We move from a bivariate chart to a **4-dimensional** one (X, Y, Color, Size) on a single plane. 
    * **DIKW Hierarchy (Knowledge):** This chart allows extracting real **Knowledge**. If we find countries with dark colors (high investment) in the "High Lethality" quadrant, we visually demonstrate that money does not guarantee good crisis management. 
    * **Diagnosis:** The quadrants act as a manual clustering tool, allowing for quick labeling of each country's performance (e.g., "Efficient", "Overwhelmed", "Resilient"). 

### 6. Global Choropleth Map
* **Objective:** Visualize the global distribution of the pandemic using color intensity to represent the severity of the impact in each region.
* **Type:** Interactive Choropleth Map.
* **Variables:**
    * **Location:** Country (mapped via ISO-3 Code or Name).
    * **Color Scale:** Accumulated Incidence or Total Cases (Sequential Scale).
    * **Interaction:** Tooltip with specific details on hover.
* **Theoretical Justification:** Uses color saturation to allow for immediate identification of "hotspots" and geographical clusters. Unlike the bubble map, this visualization fills the entire territory of each country, facilitating the recognition of regional patterns at a global scale.