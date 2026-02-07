# Road Accident Analysis Dashboard (Tableau)

## Project Background
This project analyzes UK road accident data (2019–2022) to help **road safety stakeholders** understand how accident and casualty patterns change year over year, what conditions correlate with higher severity, and where interventions may have the biggest impact.

Insights and recommendations are provided on the following key areas:

- **Year-on-Year Performance:** Total Accidents and Total Casualties comparison between a selected Current Year (CY) and Previous Year (PY)
- **Severity Mix:** Fatal vs Serious vs Slight casualty outcomes and how the mix changes over time
- **Conditions & Context:** Weather, road surface, light conditions, and how they relate to casualties
- **Geography & Vehicle Types:** District-level casualty hot spots and vehicle categories involved

An interactive Tableau dashboard used to report and explore road safety trends can be found here: **[\[Tableau Public Link\]](https://public.tableau.com/app/profile/uma.shanker.chintha/viz/ROADACCIDENTDASHBOARD_17553127472560/Dashboard1)**  
---

## Data Structure & Initial Checks
**Source:** Kaggle dummy dataset (approx. **0.6M rows**, **14 fields**) covering **2019–2022**.

### Key fields (typical)
- `Accident Date`
- `Accident Severity`
- `Number of Casualties`
- `Number of Vehicles`
- `Weather Conditions`
- `Road Surface Conditions`
- `Light Conditions`
- `District / Location` (or equivalent geography field)
- `Vehicle Type`

### Initial checks performed
- Verified date parsing and created a **Year of Accident** field to keep the dashboard dynamic as new years are appended.
- Validated nulls / unknown categories for weather, road surface, and light conditions.
- Confirmed geography granularity (district-level) is consistent for mapping.

---

## Executive Summary

### Overview of Findings
The dashboard enables flexible **CY vs PY** comparisons to quickly reveal whether road safety is improving or deteriorating across time. Patterns generally show that **casualty trends differ by severity**, and that **conditions (weather/road surface/light) and vehicle type** provide practical clues for targeted interventions.

> **Stakeholder takeaway:** Use the CY/PY selector + severity filter to isolate where increases are happening (by month, location, and context) and prioritize the most actionable factors.



---

## Insights Deep Dive

### Year-on-Year Performance (Accidents & Casualties)
* **YoY trend tracking** is calculated as:  
  `(CY - PY) / PY`  
  used for both **Total Accidents** and **Total Casualties**.
* **Directional indicators** (↑ / ↓) are applied through **custom number formatting** to make changes obvious at a glance.
* **Monthly sparklines** compare years using a **dual-axis** setup:
  - PY as an **area chart**
  - CY as a **line chart** overlay



---

### Severity Mix (Fatal, Serious, Slight)
* A dashboard parameter, **Select Accident Severity**, drives:
  - global filtering of charts
  - dynamic titles and KPI values
  - theme changes (color/contrast choices aligned to severity)
* This makes it easy to evaluate, for example:
  - whether **fatal outcomes** are concentrated in specific months or districts
  - whether **slight casualties** dominate overall volume but hide meaningful shifts in serious/fatal trends



---

### Conditions (Weather, Road Surface, Light)
* **Donut charts** summarize categorical shares for:
  - weather conditions
  - road surface conditions  
  built using a **placeholder technique** (dual pie charts) to create the donut “hole”.
* Tooltips are designed to answer the natural follow-up:  
  “If this condition is common, does it also correspond to high casualties?”



---

### Geography & Vehicle Types
* **District map view** highlights casualty concentration using a dark basemap for contrast.
* Detailed tooltips include:
  - total casualties
  - number of vehicles involved
  - key road/condition attributes (where available)
* **Vehicle type KPIs** are enhanced with imported **custom PNG icons** (e.g., bus, van, tractor) to improve scan-ability and storytelling.



---

## Recommendations
Based on the dashboard insights, stakeholders can consider:

* **Target hotspots first.** Prioritize districts with consistently high casualties across multiple years and severity levels.
* **Separate “volume” vs “risk.”** High-count categories (e.g., slight casualties) may differ from high-risk patterns (fatal/serious). Use the severity filter to avoid misleading averages.
* **Operational interventions by context.** If specific weather/road surface/light conditions correlate with higher severity, plan targeted mitigations (signage, lighting, resurfacing, enforcement).
* **Vehicle-type focused programs.** If certain vehicle categories appear disproportionately in serious/fatal outcomes, explore training, route controls, or safety policy adjustments.

---

## Assumptions and Caveats
* Dataset is a **Kaggle dummy dataset** and may not represent official reporting standards.
* “Unknown/Other” categories for conditions may reduce interpretability for some segments.
* District-level mapping accuracy depends on consistency of the geography field in the source data.
* Performance optimizations assume Tableau **Extract (.hyper)** is used rather than Live connection due to dataset size.

---

