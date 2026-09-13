<div align="center">

# 🏥 HCAHPS Patient Experience & Hospital Performance Analysis

<img src="https://img.shields.io/badge/Microsoft%20Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=000000" alt="Power BI"/>
<img src="https://img.shields.io/badge/Power%20Query-217346?style=for-the-badge&logo=powerbi&logoColor=ffffff" alt="Power Query"/>
<img src="https://img.shields.io/badge/DAX-1F4E79?style=for-the-badge" alt="DAX"/>
<img src="https://img.shields.io/badge/Healthcare%20Analytics-176B61?style=for-the-badge" alt="Healthcare Analytics"/>
<img src="https://img.shields.io/badge/Data%20Modeling-2E8B57?style=for-the-badge" alt="Data Modeling"/>
<img src="https://img.shields.io/badge/Star%20Schema-FF6B6B?style=for-the-badge" alt="Star Schema"/>

### 📊 End-to-End Business Intelligence Healthcare Analytics Project

An interactive Power BI dashboard analyzing **patient experience**, **hospital performance**, and **geographic variation** across **2015–2023**.

---

</div>

## 📸 Dashboard Preview

<div align="center">

<img src="screenshots/dashboard_overview.png" alt="HCAHPS Patient Experience Power BI Dashboard" width="1000"/>

**Interactive dashboard with KPIs, trend analysis, geographic insights, and AI-powered Q&A**

</div>

---

## 🎯 Quick Navigation

| Section | Purpose |
|---------|---------|
| [📊 Key Metrics](#-key-metrics) | High-level KPIs and performance indicators |
| [📋 Problem & Objectives](#-business-problem--objectives) | Business context and goals |
| [🗄️ Data & Model](#️-data-structure--model) | Dataset details and Star Schema |
| [⚙️ Technical Stack](#️-technical-implementation) | Tools, DAX, Power Query, data model |
| [🔍 Dashboard Analysis](#-dashboard-analysis) | Visualizations and business questions |
| [💡 Key Findings](#-analytical-findings) | Insights and discoveries |
| [🚀 Recommendations](#-business-recommendations) | Actionable next steps |
| [🛠️ Setup & Usage](#️-how-to-use) | Getting started guide |

---

## 🎯 Key Metrics

<div align="center">

### 2023 Performance Snapshot

| Metric | Value | Status |
|:---:|:---:|:---:|
| **Overall Hospital Rating** | 70% | ⚠️ -3% vs peak |
| **Willingness to Recommend** | 69% | ✅ Strong |
| **Historical Peak** | 73% | 📈 Benchmark |

</div>

### 📈 Patient Experience Dimensions (2023)

<div align="center">

| Rank | Dimension | Top-Box % | Performance |
|:---:|:---|---:|:---|
| 🥇 | Discharge Information | **86%** | ⭐⭐⭐⭐⭐ |
| 2️⃣ | Communication with Doctors | 79% | ⭐⭐⭐⭐ |
| 3️⃣ | Communication with Nurses | 79% | ⭐⭐⭐⭐ |
| 4️⃣ | Cleanliness | 72% | ⭐⭐⭐⭐ |
| 5️⃣ | Responsiveness | 65% | ⭐⭐⭐ |
| 6️⃣ | Quietness | 62% | ⭐⭐⭐ |
| 7️⃣ | Communication about Medicines | 61% | ⭐⭐⭐ |
| 🥉 | Care Transition | **51%** | ⚠️ **Needs Improvement** |

</div>

---

## 📊 Business Problem & Objectives

### ❓ The Challenge

HCAHPS (Hospital Consumer Assessment of Healthcare Providers and Systems) data contains multiple patient-experience measures that vary significantly across:
- **Time periods** (2015–2023)
- **Geographic regions** (56 states + D.C.)
- **Patient experience dimensions** (8+ measures)

Healthcare organizations need to understand **where they stand**, **where they're trending**, and **where to focus improvement efforts**.

### 🎯 Business Questions Answered

- ✅ How has overall hospital performance changed over the past 8 years?
- ✅ How does patient perception (Rating) align with willingness to recommend?
- ✅ Which patient-experience dimensions are strengths vs. weaknesses?
- ✅ Which states show the strongest/weakest performance?
- ✅ How do survey response rates vary by region and time?
- ✅ What's the top-box performance trajectory (2015 vs. 2023)?

### 🎪 Objectives

✔️ Monitor overall patient-experience KPIs  
✔️ Benchmark current performance against historical peaks  
✔️ Identify high-performing and low-performing dimensions  
✔️ Track state-level and regional variation  
✔️ Provide interactive exploration for stakeholders  
✔️ Enable data-driven recommendations  

---

## 🗄️ Data Structure & Model

### 📦 Dataset Overview

| Table | Records | Columns | Purpose |
|:---|---:|---:|:---|
| **Reports** | 9 | 4 | Reporting periods (2015–2023) |
| **States** | 56 | 3 | Geographic hierarchy |
| **Measures** | 10 | 3 | Patient-experience dimensions |
| **Questions** | 19 | 6 | HCAHPS survey questions |
| **National Results** | 90 | 8 | Aggregated national data |
| **State Results** | 4,580 | 9 | State-level performance data |
| **Responses** | 43,219 | 5 | Facility-level survey metrics |

**Total Records Analyzed:** 48,003  
**Time Span:** 9 years (2015–2023)  
**Geographic Coverage:** 56 states + D.C. + U.S. territories  

### 🏗️ Star Schema Architecture
