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

## Project Overview

This project analyzes HCAHPS healthcare survey data to understand patient experience and hospital performance across reporting periods, states, regions, and patient-experience dimensions.

Multiple related source tables were prepared, transformed, and modeled in Microsoft Power BI. The analytical layer was developed using DAX, followed by interactive dashboard development and AI-assisted exploration using Power BI Q&A.

### Project Scope

| Area | Details |
|:---|:---|
| **Domain** | Healthcare / Patient Experience |
| **BI Platform** | Microsoft Power BI |
| **Data Preparation** | Power Query |
| **Transformation** | M Query |
| **Analytical Language** | DAX |
| **Data Model** | Star Schema |
| **Analysis Period** | 2015–2023 |
| **Geographic Scope** | National, Regional & State |
| **Primary Metric** | Top-Box Percentage |
| **AI Feature** | Power BI Q&A |
| **Advanced Visuals** | Gauge, Funnel, Shape Map, Decomposition Tree |

---

## Business Context

HCAHPS data contains multiple measures describing different aspects of the patient experience across reporting periods and geographic areas.

The project transforms these related datasets into an interactive Business Intelligence solution that makes it easier to identify performance patterns, compare patient-experience dimensions, analyze geographic variation, and monitor changes over time.

---

## Business Questions

The dashboard was designed around the following analytical questions:

1. How has Overall Hospital Rating changed over time?
2. How does Overall Hospital Rating compare with Willingness to Recommend?
3. Which patient-experience dimensions perform strongly or weakly?
4. Which states show stronger or weaker Overall Hospital Rating performance?
5. How does reported survey response rate vary across regions, states, and reporting periods?
6. How has Top-Box performance changed between 2015 and 2023?

---

## Business Objectives

- Evaluate overall patient-experience performance
- Monitor Overall Hospital Rating
- Analyze Willingness to Recommend
- Compare patient-experience dimensions
- Track performance across reporting periods
- Identify state-level variation
- Explore regional differences
- Analyze reported survey response rates
- Compare Top-Box performance between 2015 and 2023
- Provide an interactive analytical solution

---

# Key Performance Indicators

| KPI | 2023 Result | Purpose |
|:---|---:|:---|
| **Overall Hospital Rating Top Box** | **70%** | High-level indicator of overall patient perception |
| **Willingness to Recommend Top Box** | **69%** | Indicator of patients' willingness to recommend |
| **Historical Peak Overall Rating** | **73%** | Benchmark for current performance |

The two primary KPIs are Overall Hospital Rating and Willingness to Recommend. The historical peak is used as a supporting benchmark.

---

# Dataset

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

### Data Coverage

The model supports analysis across:

**National → Region → State → Reporting Period → Facility Response**

The source tables remain separate because they represent different analytical grains and serve different roles within the model.

---

# HCAHPS Result Structure

HCAHPS results contain three response categories:

| Category | Analytical Role |
|:---|:---|
| **Bottom-Box** | Lower response category |
| **Middle-Box** | Middle response category |
| **Top-Box** | Highest response category |

The dashboard primarily uses **Top-Box Percentage** when comparing patient-experience performance.

---

# Data Preparation

Data preparation was performed using **Power Query**.

### Key Transformations

| Transformation | Table(s) | Purpose |
|:---|:---|:---|
| **Promote Headers** | Multiple tables | Converted source rows into column headers |
| **Change Data Types** | Multiple tables | Assigned appropriate data types |
| **Add Custom Column** | Responses | Created a numeric response-rate field |
| **Percentage Validation** | National Results, State Results | Validated percentage distributions |
| **Facility ID as Text** | Responses | Preserved alphanumeric identifiers and leading zeros |

### Response Rate Handling

The original response-rate field contained both numeric and non-numeric values.

A separate numeric field was created to allow valid response-rate values to be analyzed while unavailable values remained blank.

### Identifier Handling

Facility ID was retained as a **Text** field because some identifiers contain letters and leading zeros.

This prevents identifiers from being incorrectly interpreted as numeric values.

---

# Data Model

The Power BI solution follows a **Star Schema-oriented relational model**.

## Dimension Tables

- Reports
- States
- Measures

## Fact Tables

- National Results
- State Results
- Responses

## Supporting Table

- Questions

### Relationship Design

The model uses:

- One-to-many relationships
- Active relationships
- Single-direction filtering
- No many-to-many relationships

### Model Relationships

| Dimension | Related Fact / Supporting Tables |
|:---|:---|
| **Reports** | National Results, State Results, Responses |
| **States** | State Results, Responses |
| **Measures** | National Results, State Results |
| **Measures** | Questions |

This structure provides controlled filter propagation across reporting periods, geography, and patient-experience measures.

---

# DAX & Analytical Layer

DAX was used to create reusable analytical measures for KPI reporting, historical benchmarking, geographic analysis, and period comparisons.

## Core DAX Measures

| Measure | Purpose |
|:---|:---|
| **Overall Hospital Rating Top Box** | Calculates the latest national Overall Hospital Rating |
| **Willingness to Recommend Top Box** | Calculates the latest national recommendation performance |
| **Historical Peak Overall Rating** | Identifies the highest recorded Overall Hospital Rating |
| **Average Response Rate** | Calculates the average of valid reported response rates |
| **State Top Box %** | Supports state-level Top-Box analysis |
| **National Top Box %** | Supports national measure comparisons |
| **Top Box Change 2015 to 2023** | Calculates change between 2015 and 2023 |

### Additional DAX Fields

A **Release Year** calculated column was created from the reporting-period field to support chronological analysis.

Additional period-specific measures were used for 2015 and 2023 comparisons.

---

# Power Query & M Query

The project uses Power Query for source preparation and M Query transformations.

### Main M Query Operations

| M Query Operation | Purpose |
|:---|:---|
| **Promote Headers** | Establishes source column headers |
| **Changed Type** | Assigns appropriate data types |
| **Added Custom** | Creates transformed analytical fields |
| **try Number.From()** | Safely converts response-rate values to numeric format |

These transformations prepare the source data before it enters the analytical model.

---

# Dashboard Architecture

The dashboard combines multiple analytical perspectives rather than relying on a single visualization.

| Component | Analytical Purpose |
|:---|:---|
| **KPI Cards** | Current performance monitoring |
| **Line Chart** | Historical trend analysis |
| **Gauge** | Current vs historical benchmark |
| **Funnel** | Patient-experience measure comparison |
| **Shape Map** | Geographic performance analysis |
| **Decomposition Tree** | Response-rate hierarchy |
| **Q&A** | Natural-language analysis |

---

# Interactive Filters

The dashboard provides interactive filtering through:

- **Release Year**
- **State Name**
- **Region**
- **Measure**

These filters allow users to explore the data from different analytical perspectives.

---

# Trend Analysis

## Overall Rating vs Recommendation

The line chart compares Overall Hospital Rating and Willingness to Recommend across reporting periods from 2015 to 2023.

| Reporting Period | Overall Rating | Willingness to Recommend |
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

This comparison provides a direct view of how the two headline patient-perception measures changed over the analysis period.

---

# Current Performance vs Historical Peak

The gauge compares the latest Overall Hospital Rating with the highest recorded value.

| Metric | Value |
|:---|---:|
| **Current Overall Hospital Rating** | **70%** |
| **Historical Peak** | **73%** |

The historical peak is used as a benchmark for interpreting current performance.

---

# 2023 Patient Experience Performance

The funnel compares eight supporting patient-experience measures using Top-Box percentages.

| Rank | Measure | Top Box |
|---:|:---|---:|
| 1 | **Discharge Information** | **86%** |
| 2 | Communication with Doctors | 79% |
| 3 | Communication with Nurses | 79% |
| 4 | Cleanliness | 72% |
| 5 | Responsiveness | 65% |
| 6 | Quietness | 62% |
| 7 | Communication about Medicines | 61% |
| 8 | **Care Transition** | **51%** |

Overall Hospital Rating and Willingness to Recommend are treated as headline indicators and are analyzed separately.

---

# Geographic Analysis

The Shape Map focuses on:

**Overall Hospital Rating → 2023 → State Level**

### Business Question

> Which states show stronger or weaker Overall Hospital Rating performance in 2023?

The map uses state-level Top-Box performance to visualize geographic variation.

This complements the national and historical analysis by providing a geographic perspective.

---

# Survey Response Rate Analysis

The Decomposition Tree analyzes:

**Average Response Rate**

through the hierarchy:

**Region → State → Reporting Period**

### Purpose

This allows the analysis to move from a regional-level view to state-level and reporting-period detail.

Response-rate analysis provides additional context for interpreting survey participation.

---

# AI-Assisted Analysis

Power BI **Q&A** was used to support natural-language exploration.

### Query Used

```text
Top Box Change 2015 to 2023 by Measure
```

The query uses the `Top Box Change 2015 to 2023` measure to compare patient-experience performance between 2015 and 2023.

### Q&A Configuration

A synonym was added for the Measure field to support natural-language interpretation of patient-experience dimensions.

The Q&A visual was then used to compare Top-Box changes across measures.

---

# Key Results

| Indicator | Result |
|:---|---:|
| **Overall Hospital Rating — 2023** | **70%** |
| **Willingness to Recommend — 2023** | **69%** |
| **Historical Peak Overall Rating** | **73%** |
| **Discharge Information — 2023** | **86%** |
| **Care Transition — 2023** | **51%** |

---

# Key Findings

### Overall Performance

Overall Hospital Rating reached **70% in 2023**, compared with a historical peak of **73%**.

### Willingness to Recommend

Willingness to Recommend was **69% in 2023**.

### Stronger Supporting Dimension

Discharge Information recorded the highest supporting-measure Top-Box result at **86%** in 2023.

### Lower Supporting Dimension

Care Transition recorded the lowest supporting-measure Top-Box result at **51%** in 2023.

### Geographic Variation

State and regional analysis revealed variation in Overall Hospital Rating performance across geographic areas.

### Survey Response Rates

Response-rate analysis showed variation across regions, states, and reporting periods.

---

# Business Recommendations

The analysis highlights several areas for continued performance monitoring.

## Care Transition

Potential areas of focus:

- Post-discharge communication
- Follow-up information
- Next-step guidance
- Ongoing care instructions

## Communication About Medicines

Potential areas of focus:

- Clear medication instructions
- Consistent communication
- Patient understanding checks

## Responsiveness

Potential areas of focus:

- Staff response time
- Patient request handling
- Communication around expected response times

## Continuous Monitoring

The dashboard can be used to monitor:

- Overall Hospital Rating
- Willingness to Recommend
- Patient-experience dimensions
- State-level performance
- Survey response rates
- Historical Top-Box changes

---

# Data Quality Considerations

Several characteristics of the source data required attention during preparation.

| Data Consideration | Handling |
|:---|:---|
| Mixed response-rate values | Created a separate numeric field |
| Non-available response-rate values | Preserved as blank in numeric analysis |
| Alphanumeric Facility IDs | Maintained as Text |
| Leading zeros | Preserved through Text data type |
| Multiple analytical grains | Maintained separate tables |
| Percentage distributions | Validated during preparation |

---

# Analytical Design Decisions

## Why Top-Box?

Top-Box Percentage provides a consistent basis for comparing the highest response category across patient-experience measures.

## Why Separate Fact Tables?

National results, state results, and facility response data represent different levels of detail. Keeping them separate prevents mixing different analytical grains.

## Why Star Schema?

The model separates descriptive dimensions from analytical facts, allowing controlled filtering and reusable DAX measures.

## Why DAX Measures?

DAX measures allow calculations to respond dynamically to the Power BI filter context.

## Why Multiple Visualization Types?

Each visualization was selected for a specific analytical purpose:

**Trend → Benchmark → Comparison → Geography → Hierarchy → Natural Language**

---

# Technical Implementation

| Area | Technologies / Techniques |
|:---|:---|
| **BI Platform** | Microsoft Power BI |
| **Data Preparation** | Power Query |
| **Transformation** | M Query |
| **Analytics** | DAX |
| **Data Modeling** | Star Schema |
| **Visualization** | Gauge, Funnel, Shape Map, Decomposition Tree, Line Chart |
| **AI** | Power BI Q&A |
| **Domain** | Healthcare Analytics |

---

# Skills Demonstrated

### Business Intelligence

- Microsoft Power BI
- Interactive Dashboard Development
- KPI Development
- Interactive Reporting
- Data Visualization

### Data Preparation

- Power Query
- M Query
- Data Cleaning
- Data Transformation
- Data Validation
- Data Type Management

### Data Analytics

- DAX
- Trend Analysis
- Geographic Analysis
- Comparative Analysis
- Performance Benchmarking
- Healthcare Analytics

### Data Modeling

- Star Schema
- Fact Tables
- Dimension Tables
- One-to-Many Relationships
- Single-Direction Filtering
- Relationship Design

### Advanced Power BI

- Power BI Q&A
- Shape Map
- Decomposition Tree
- Funnel
- Gauge
- Interactive Slicers
- Report Tooltips

---

# Repository Structure

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

> The `screenshots/` folder is maintained as supporting project documentation. Images are not embedded in this README.

---

# Project Workflow

<div align="center">

**01 — Source Data**

↓  

**02 — Power Query / M Query**

↓  

**03 — Data Cleaning & Validation**

↓  

**04 — Star Schema Data Model**

↓  

**05 — DAX Analytical Layer**

↓  

**06 — Interactive Dashboard**

↓  

**07 — Q&A Analysis**

↓  

**08 — Business Insights**

</div>

---

# Files Included

### Dashboard

**HCAHPS_Patient_Experience_Dashboard.pbix**

Complete Power BI source file containing the model, transformations, DAX measures, visuals, filters, and dashboard design.

**HCAHPS_Patient_Experience_Dashboard.pdf**

Exported dashboard for quick review without opening Power BI Desktop.

### Data

The `data/` directory contains the seven source CSV tables used by the Power BI model.

### Screenshots

The `screenshots/` directory contains supporting views of the dashboard, Power Query transformations, data model, DAX calculations, and Q&A analysis.

### Report

The `report/` directory contains the project documentation.

---

# How to Explore the Project

1. Download the `.pbix` file from the `dashboard/` folder.
2. Open the file using Microsoft Power BI Desktop.
3. Review the relationships in **Model View**.
4. Review data transformations in **Power Query Editor**.
5. Review analytical measures created using DAX.
6. Open the dashboard page.
7. Use the available slicers to explore the analysis.
8. Review the Q&A visual for natural-language analysis.

---

# Project Outcome

This project demonstrates an end-to-end Business Intelligence workflow for transforming multiple related healthcare datasets into an interactive Power BI analytical solution.

The solution brings together:

**Data Preparation → Data Modeling → DAX → Visualization → AI-Assisted Analysis → Business Insights**

It provides a structured view of:

- Patient-experience KPIs
- Historical performance
- Patient-experience dimensions
- State-level performance
- Regional variation
- Survey response rates
- Top-Box performance changes

---

# Disclaimer

This project is intended for educational and portfolio purposes.

The analysis is not intended to provide clinical advice, evaluate individual patients, or make healthcare treatment decisions.

---

<div align="center">

### HCAHPS Patient Experience & Hospital Performance Analysis

**Microsoft Power BI · Power Query · M Query · DAX · Healthcare Analytics**

</div>
