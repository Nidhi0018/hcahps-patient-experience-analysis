<div align="center">

# HCAHPS Patient Experience & Hospital Performance Analysis

### Power BI Healthcare Analytics Project

An end-to-end Business Intelligence project analyzing patient experience, hospital performance, survey response rates, and geographic variation across reporting periods, states, and regions.

<br>

<img src="https://img.shields.io/badge/Microsoft%20Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=000000" alt="Microsoft Power BI"/>
<img src="https://img.shields.io/badge/Power%20Query-217346?style=for-the-badge&logo=powerbi&logoColor=ffffff" alt="Power Query"/>
<img src="https://img.shields.io/badge/DAX-12345B?style=for-the-badge" alt="DAX"/>
<img src="https://img.shields.io/badge/M%20Query-176B61?style=for-the-badge" alt="M Query"/>
<img src="https://img.shields.io/badge/Star%20Schema-5B6B73?style=for-the-badge" alt="Star Schema"/>
<img src="https://img.shields.io/badge/Healthcare%20Analytics-0F766E?style=for-the-badge" alt="Healthcare Analytics"/>

</div>

---

<div align="center">

## Dashboard Preview

<img src="screenshots/dashboard_overview.png"
     alt="HCAHPS Patient Experience Power BI Dashboard"
     width="1000"/>

<br>

<strong>Interactive Power BI dashboard combining patient-experience KPIs, trend analysis, measure comparison, geographic analysis, response-rate analysis, and Q&A.</strong>

</div>

---

# 1. Project Overview

This project analyzes HCAHPS healthcare survey data to understand patient experience and hospital performance across reporting periods, states, regions, and patient-experience dimensions.

Multiple related source tables were prepared and modeled in Power BI before building the analytical layer and dashboard.

The project follows an end-to-end Business Intelligence workflow:

> **Data Preparation → Data Transformation → Data Modeling → DAX → Visualization → AI-Assisted Analysis → Business Insights**

### Project Scope

| Area | Details |
|:---|:---|
| **Domain** | Healthcare / Patient Experience |
| **BI Platform** | Microsoft Power BI |
| **Data Preparation** | Power Query |
| **Transformation Language** | M Query |
| **Analytical Language** | DAX |
| **Data Modeling** | Star Schema |
| **Analysis Period** | 2015–2023 |
| **Geographic Scope** | National, Regional & State |
| **Primary Performance Metric** | Top-Box Percentage |
| **AI Feature** | Power BI Q&A |
| **Advanced Visuals** | Gauge, Funnel, Shape Map, Decomposition Tree |

---

# 2. Business Context

HCAHPS data contains multiple measures representing different aspects of the patient experience.

These measures are available across reporting periods and geographic levels, making it possible to examine both historical and geographic patterns.

The dashboard was designed to turn these datasets into a structured analytical view that allows performance to be explored through KPIs, trends, comparisons, geographic visualization, and hierarchical analysis.

---

# 3. Analytical Questions

The dashboard was developed around specific business questions rather than simply displaying the available fields.

### Patient Experience

- How has Overall Hospital Rating changed over time?
- How does Overall Hospital Rating compare with Willingness to Recommend?
- Which patient-experience dimensions show stronger or weaker Top-Box performance?

### Geographic Performance

- How does Overall Hospital Rating vary across states?
- Are there visible differences between geographic regions?

### Survey Participation

- How does reported survey response rate vary across regions?
- How does response rate vary between states?
- How does reported response rate change across reporting periods?

### Historical Performance

- How has Top-Box performance changed between 2015 and 2023?
- How does current Overall Hospital Rating compare with its historical peak?

---

# 4. Key Performance Indicators

Two primary KPIs are used for the high-level patient-experience view.

<div align="center">

<table>
<tr>

<td align="center" width="250">

## 70%

<strong>Overall Hospital Rating</strong>

2023 Top-Box

</td>

<td align="center" width="250">

## 69%

<strong>Willingness to Recommend</strong>

2023 Top-Box

</td>

<td align="center" width="250">

## 73%

<strong>Historical Peak</strong>

Overall Hospital Rating

</td>

</tr>
</table>

</div>

### KPI Definitions

| KPI | Definition | Dashboard Use |
|:---|:---|:---|
| **Overall Hospital Rating Top Box** | Percentage of patients providing the highest overall hospital rating | Primary KPI |
| **Willingness to Recommend Top Box** | Percentage of patients providing the highest recommendation response | Primary KPI |
| **Historical Peak Overall Rating** | Highest recorded Overall Hospital Rating Top-Box score | Benchmark |

---

# 5. Dataset

The project uses seven related HCAHPS tables.

| Table | Rows | Columns | Analytical Role |
|:---|---:|---:|:---|
| **Reports** | 9 | 4 | Reporting-period dimension |
| **States** | 56 | 3 | Geographic dimension |
| **Measures** | 10 | 3 | Patient-experience measure dimension |
| **Questions** | 19 | 6 | Question-level supporting information |
| **National Results** | 90 | 8 | National-level performance fact |
| **State Results** | 4,580 | 9 | State-level performance fact |
| **Responses** | 43,219 | 5 | Facility response-rate fact |

### Dataset Grain

The source tables have different grains.

| Table | Grain |
|:---|:---|
| **Reports** | One reporting period |
| **States** | One geographic entity |
| **Measures** | One HCAHPS measure |
| **Questions** | One survey question |
| **National Results** | One reporting period × measure |
| **State Results** | One reporting period × state × measure |
| **Responses** | One reporting period × state × facility |

Maintaining these tables separately avoids combining data with different levels of detail into a single table.

---

# 6. HCAHPS Result Structure

The results tables contain three response categories:

| Result Category | Description |
|:---|:---|
| **Bottom-Box** | Lower response category |
| **Middle-Box** | Middle response category |
| **Top-Box** | Highest response category |

The analysis primarily uses **Top-Box Percentage** for performance comparisons.

This allows the dashboard to focus on the highest response category across measures, states, and reporting periods.

---

# 7. Data Preparation

Data preparation was performed using **Power Query**.

The objective was to make the source tables consistent and suitable for analysis while preserving important identifiers and handling mixed-value fields.

## Key Transformations

| Transformation | Table(s) | Purpose |
|:---|:---|:---|
| **Promote Headers** | Source tables | Converted source rows into column headers |
| **Change Data Types** | Multiple tables | Assigned appropriate data types |
| **Add Custom Column** | Responses | Created numeric response-rate values |
| **Percentage Validation** | National Results, State Results | Validated percentage distributions |
| **Facility ID as Text** | Responses | Preserved alphanumeric identifiers and leading zeros |

### Response Rate Transformation

The original response-rate field contained both numeric and non-numeric values.

A custom numeric field was created using a safe conversion approach so valid values could be analyzed while unavailable values remained blank.

### Identifier Handling

Facility IDs were retained as **Text** because some identifiers contain letters and leading zeros.

This prevents incorrect conversion of identifiers into numeric values.

<div align="center">

<img src="screenshots/power_query.png"
     alt="Power Query Data Preparation"
     width="900"/>

<br>

<sub>Power Query transformations used to prepare the HCAHPS source tables.</sub>

</div>

---

# 8. Data Model

The Power BI model follows a **Star Schema-oriented structure**.

## Dimension Layer

### Reports

Provides reporting-period information used for time-based analysis.

### States

Provides state, state-code, and regional information used for geographic analysis.

### Measures

Provides the HCAHPS measure names and identifiers used to categorize patient-experience results.

---

## Fact Layer

### National Results

Contains national-level HCAHPS results by reporting period and measure.

### State Results

Contains state-level HCAHPS results by reporting period, state, and measure.

### Responses

Contains facility-level survey counts and reported response rates.

---

## Supporting Table

### Questions

Contains question-level information mapped to the corresponding HCAHPS measures.

---

## Relationship Design

The model uses:

- One-to-many relationships
- Active relationships
- Single-direction filtering
- No many-to-many relationships

The main analytical relationships connect:

**Reports → Results / Responses**

**States → State Results / Responses**

**Measures → Results**

<div align="center">

<img src="screenshots/data_model.png"
     alt="HCAHPS Power BI Star Schema Data Model"
     width="900"/>

<br>

<sub>Power BI model showing the relationships between dimension and fact tables.</sub>

</div>

---

# 9. DAX Analytical Layer

DAX was used to create reusable analytical measures rather than relying only on raw columns.

The measures support KPI cards, benchmarking, national comparisons, state analysis, response-rate analysis, and period comparisons.

## Core Measures

| Measure | Purpose |
|:---|:---|
| **Overall Hospital Rating Top Box** | Returns the latest national Overall Hospital Rating Top-Box value |
| **Willingness to Recommend Top Box** | Returns the latest national recommendation Top-Box value |
| **Historical Peak Overall Rating** | Identifies the highest recorded Overall Hospital Rating |
| **Average Response Rate** | Calculates the average of valid reported response-rate values |
| **State Top Box %** | Supports state-level Top-Box analysis |
| **National Top Box %** | Supports national measure comparison |
| **Top Box Change 2015 to 2023** | Calculates the change between the 2015 and 2023 reporting periods |

### Additional Analytical Fields

A **Release Year** calculated column was created from the reporting-period field to support chronological visualization.

Period-specific measures were also used for 2015 and 2023 comparisons.

<div align="center">

<img src="screenshots/dax_measures.png"
     alt="DAX Analytical Measures"
     width="900"/>

<br>

<sub>DAX measures used for KPI reporting and analytical comparisons.</sub>

</div>

---

# 10. Dashboard Design

The dashboard was designed to combine high-level monitoring with detailed exploration.

## Dashboard Components

| Component | Purpose |
|:---|:---|
| **KPI Cards** | Monitor current patient-experience performance |
| **Line Chart** | Analyze historical trends |
| **Gauge** | Compare current performance with historical benchmark |
| **Funnel** | Compare patient-experience dimensions |
| **Shape Map** | Analyze geographic variation |
| **Decomposition Tree** | Explore response-rate hierarchy |
| **Q&A** | Perform natural-language analysis |

### Interactive Filters

The dashboard includes filters for:

- Release Year
- State
- Region
- Measure

These allow users to explore the data from different analytical perspectives.

---

# 11. Trend Analysis

## Overall Rating vs Recommendation

The line chart compares:

- Overall Hospital Rating
- Willingness to Recommend

across reporting periods from **2015 to 2023**.

### Observed Values

| Reporting Period | Overall Rating | Recommend |
|:---|---:|---:|
| 2015 | 71% | 71% |
| 2016 | 72% | 71% |
| 2017 | 73% | 72% |
| 2018 | 73% | 72% |
| 2019 | 73% | 72% |
| 2020 | 73% | 72% |
| 2021 | 73% | 72% |
| 2022 | 72% | 71% |
| 2023 | 70% | 69% |

This provides a direct view of how the two headline patient-perception indicators move across the reporting period.

---

# 12. Current Performance vs Historical Benchmark

The gauge compares the latest Overall Hospital Rating with the highest value recorded in the available data.

| Metric | Value |
|:---|---:|
| **Current Overall Hospital Rating** | **70%** |
| **Historical Peak** | **73%** |

This benchmark provides context for interpreting the latest result.

---

# 13. Patient Experience Dimension Analysis

The funnel focuses on eight supporting HCAHPS measures for 2023.

| Measure | Top Box |
|:---|---:|
| **Discharge Information** | **86%** |
| Communication with Doctors | 79% |
| Communication with Nurses | 79% |
| Cleanliness | 72% |
| Responsiveness | 65% |
| Quietness | 62% |
| Communication about Medicines | 61% |
| **Care Transition** | **51%** |

### Analytical Focus

The comparison highlights the relative difference between stronger and weaker patient-experience dimensions.

Overall Hospital Rating and Willingness to Recommend are excluded from this supporting-measure comparison because they are treated as headline indicators.

---

# 14. Geographic Analysis

The Shape Map focuses on:

**Overall Hospital Rating → 2023 → State Level**

### Analytical Question

> Which states show stronger or weaker Overall Hospital Rating performance in 2023?

The map uses a continuous color scale based on state-level Top-Box performance.

This allows geographic differences to be identified visually rather than relying only on tabular comparisons.

---

# 15. Survey Response Rate Analysis

The Decomposition Tree analyzes:

**Average Response Rate**

through the hierarchy:

**Region → State → Reporting Period**

### Analytical Purpose

This allows the user to start from a regional view and progressively examine state-level and reporting-period variation.

The response-rate analysis provides additional context when interpreting survey results.

---

# 16. AI-Assisted Analysis

Power BI **Q&A** was used as the AI feature.

### Natural-Language Query

```text
Top Box Change 2015 to 2023 by Measure
```

The query uses the DAX measure:

```text
Top Box Change 2015 to 2023
```

to compare performance between the beginning and end of the analysis period.

<div align="center">

<img src="screenshots/qna_analysis.png"
     alt="Power BI Q&A Analysis"
     width="900"/>

<br>

<sub>Power BI Q&A used to explore Top-Box changes by patient-experience measure.</sub>

</div>

---

# 17. 2023 Performance Summary

<div align="center">

<table>
<tr>
<th>Indicator</th>
<th>2023 Result</th>
</tr>

<tr>
<td><strong>Overall Hospital Rating</strong></td>
<td><strong>70%</strong></td>
</tr>

<tr>
<td><strong>Willingness to Recommend</strong></td>
<td><strong>69%</strong></td>
</tr>

<tr>
<td><strong>Discharge Information</strong></td>
<td><strong>86%</strong></td>
</tr>

<tr>
<td><strong>Communication with Doctors</strong></td>
<td><strong>79%</strong></td>
</tr>

<tr>
<td><strong>Communication with Nurses</strong></td>
<td><strong>79%</strong></td>
</tr>

<tr>
<td><strong>Care Transition</strong></td>
<td><strong>51%</strong></td>
</tr>

</table>

</div>

---

# 18. Key Analytical Findings

### Overall Hospital Rating

The 2023 Overall Hospital Rating Top-Box result is **70%**, compared with a historical peak of **73%**.

### Willingness to Recommend

The 2023 Willingness to Recommend Top-Box result is **69%**.

### Stronger Supporting Dimension

**Discharge Information** records the highest 2023 Top-Box value among the eight supporting measures at **86%**.

### Lower Supporting Dimension

**Care Transition** records the lowest 2023 Top-Box value among the eight supporting measures at **51%**.

### Geographic Variation

State and regional analysis demonstrates variation in patient-experience performance across geographic areas.

### Survey Response Rates

Response-rate analysis demonstrates variation across regions, states, and reporting periods.

---

# 19. Business Recommendations

The dashboard identifies several areas that can be considered for continued monitoring.

## Care Transition

Potential areas of focus include:

- Post-discharge communication
- Follow-up information
- Next-step guidance
- Ongoing care instructions

## Communication About Medicines

Potential areas of focus include:

- Clear medication instructions
- Consistent communication
- Patient understanding checks

## Responsiveness

Potential areas of focus include:

- Staff response time
- Patient request handling
- Communication around expected response times

## Performance Monitoring

The dashboard can be used to monitor changes in:

- Overall Hospital Rating
- Willingness to Recommend
- Patient-experience dimensions
- State-level performance
- Survey response rates
- Historical Top-Box performance

---

# 20. Technical Implementation

## Power BI

- Interactive dashboard development
- KPI cards
- Trend analysis
- Geographic analysis
- Advanced visualizations
- Interactive slicers
- Report tooltips

## Power Query

- Data cleaning
- Header promotion
- Data type correction
- Mixed-value handling
- Response-rate transformation
- Percentage validation

## M Query

- `Promote Headers`
- `Changed Type`
- `Added Custom`
- `try Number.From()` for response-rate conversion

## DAX

- KPI calculations
- Historical benchmarking
- Top-Box calculations
- Period comparisons
- National-level metrics
- State-level metrics
- Average response-rate calculation

## Data Modeling

- Star Schema
- Fact and dimension tables
- One-to-many relationships
- Active relationships
- Single-direction filtering
- Geographic dimensions
- Reporting-period dimensions

## Advanced Visualizations

- Gauge
- Funnel
- Shape Map
- Decomposition Tree
- Line Chart
- KPI Cards
- Power BI Q&A

---

# 21. Data Quality Considerations

Several characteristics of the source data required attention during preparation.

| Data Issue | Handling Approach |
|:---|:---|
| Mixed response-rate values | Created a separate numeric field |
| Non-available response-rate entries | Preserved as blank in numeric analysis |
| Alphanumeric Facility IDs | Maintained as Text |
| Leading zeros in identifiers | Preserved through text data type |
| Multiple analytical grains | Maintained separate source tables |
| Percentage distributions | Validated during preparation |

These steps helped prepare the source data for reliable modeling and visualization.

---

# 22. Analytical Design Decisions

### Why Top-Box?

Top-Box percentages provide a consistent basis for comparing the highest response category across patient-experience measures.

### Why Separate Fact Tables?

National results, state results, and facility response data represent different grains. Keeping them separate avoids mixing unrelated levels of detail.

### Why Star Schema?

The model separates descriptive dimensions from analytical facts, allowing controlled filtering and reusable measures.

### Why DAX Measures?

Measures allow calculations to respond dynamically to the Power BI filter context rather than relying only on static calculated values.

### Why Multiple Visualization Types?

Each visual answers a different analytical question:

**Trend → Comparison → Benchmark → Geography → Hierarchy → Natural Language**

---

# 23. Repository Structure

```text
hcahps-patient-experience-analysis/
│
├── README.md
│
├── dashboard/
│   ├── HCAHPS_Patient_Experience_Dashboard.pbix
│   └── HCAHPS_Patient_Experience_Dashboard.pdf
│
├── data/
│   ├── reports.csv
│   ├── states.csv
│   ├── measures.csv
│   ├── questions.csv
│   ├── national_results.csv
│   ├── state_results.csv
│   └── responses.csv
│
├── screenshots/
│   ├── dashboard_overview.png
│   ├── power_query.png
│   ├── data_model.png
│   ├── dax_measures.png
│   └── qna_analysis.png
│
└── report/
    └── HCAHPS_PowerBI_Report.pdf
```

---

# 24. Project Workflow

<div align="center">

<table>
<tr>
<td align="center"><strong>01</strong><br>Source Data</td>
<td>→</td>
<td align="center"><strong>02</strong><br>Power Query</td>
<td>→</td>
<td align="center"><strong>03</strong><br>Validation</td>
</tr>

<tr>
<td align="center"><strong>04</strong><br>Star Schema</td>
<td>→</td>
<td align="center"><strong>05</strong><br>DAX</td>
<td>→</td>
<td align="center"><strong>06</strong><br>Dashboard</td>
</tr>

<tr>
<td align="center"><strong>07</strong><br>Q&A</td>
<td>→</td>
<td align="center"><strong>08</strong><br>Analysis</td>
<td>→</td>
<td align="center"><strong>09</strong><br>Insights</td>
</tr>
</table>

</div>

---

# 25. Skills Demonstrated

<table>
<tr>
<th>Business Intelligence</th>
<th>Data Analytics</th>
<th>Data Modeling</th>
</tr>

<tr>
<td>Microsoft Power BI</td>
<td>DAX</td>
<td>Star Schema</td>
</tr>

<tr>
<td>Power Query</td>
<td>Trend Analysis</td>
<td>Fact Tables</td>
</tr>

<tr>
<td>KPI Development</td>
<td>Geographic Analysis</td>
<td>Dimension Tables</td>
</tr>

<tr>
<td>Dashboard Development</td>
<td>Comparative Analysis</td>
<td>Relationship Design</td>
</tr>

<tr>
<td>Advanced Visualizations</td>
<td>Performance Benchmarking</td>
<td>Filter Propagation</td>
</tr>

<tr>
<td>Power BI Q&A</td>
<td>Healthcare Analytics</td>
<td>Data Validation</td>
</tr>

</table>

---

# 26. Files Included

### Dashboard

**`.pbix`**  
Complete Power BI source file containing the data model, Power Query transformations, DAX measures, visuals, slicers, and dashboard design.

**`.pdf`**  
Exported dashboard for quick viewing without opening Power BI Desktop.

### Data

The `data/` directory contains the seven source CSV tables used by the Power BI model.

### Screenshots

The `screenshots/` directory contains selected views of:

- Dashboard
- Power Query
- Data Model
- DAX
- Q&A

### Report

The `report/` directory contains the project documentation/report.

---

# 27. How to Explore the Project

To explore the Power BI solution:

1. Download the `.pbix` file from the `dashboard/` folder.
2. Open it using Microsoft Power BI Desktop.
3. Review the model in **Model View**.
4. Review transformations in **Power Query Editor**.
5. Review analytical calculations in the **Data / Model view**.
6. Open the dashboard page.
7. Use the available slicers to explore the analysis.
8. Review the Q&A visual for natural-language analysis.

---

# 28. Project Outcome

This project demonstrates an end-to-end Business Intelligence workflow for transforming multiple related healthcare datasets into an interactive Power BI analytical solution.

The final solution combines:

**Data Preparation**

↓

**Data Modeling**

↓

**DAX**

↓

**Interactive Visualization**

↓

**AI-Assisted Analysis**

↓

**Business Insights**

The result is a structured analytical dashboard that brings together patient-experience KPIs, historical performance, measure-level comparison, geographic variation, and survey response-rate analysis.

---

# 29. Disclaimer

This project is intended for educational and portfolio purposes.

The analysis is not intended to provide clinical advice, evaluate individual patients, or make healthcare treatment decisions.

---

<div align="center">

### HCAHPS Patient Experience & Hospital Performance Analysis

**Microsoft Power BI · Power Query · M Query · DAX · Healthcare Analytics**

</div>
