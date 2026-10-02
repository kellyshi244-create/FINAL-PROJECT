# FINAL-PROJECT
# 💧 Kenya Water Quality Analysis (2000–2024)
### A Data-Driven Investigation of National Water Access, Regional Coverage, and Water Quality in Kenya

---

## 📖 Project Description

This project analyzes Kenya's water sector across three dimensions:

1. **National access trends** — how access to basic drinking water and sanitation has changed between 2000 and 2024
2. **Regional case study** — how the Athi River basin has managed water and sanitation coverage between 2011 and 2014
3. **Water quality reality** — chemical analysis of 493 water samples from across Kenyan counties

By combining these three perspectives, the project tells a complete story: Kenya has made significant progress in expanding water access nationally, but regional case data shows uneven delivery, and chemical testing reveals that water quality varies widely across counties. **Access is improving — but access does not always equal safety.**

The analysis is packaged as an interactive web application built with Streamlit, backed by a SQLite database, and fully reproducible through Python code.

---

## ❗ Problem Statement

Kenya faces a **dual water crisis**:

1. **Access gap**: As of 2024, only **65.6%** of Kenyans have access to basic drinking water and only **40.9%** have access to basic sanitation — leaving roughly **24 million people without safely managed sanitation**. Despite 24 years of steady improvement, the country remains far from the SDG 6 target of universal access by 2030.

2. **Quality uncertainty**: Even where water is available, its **chemical safety is not guaranteed**. Water samples across Kenya show pH values as low as **5.58** (below the WHO minimum of 6.5) and conductivity levels that exceed the KEBS drinking water limit of 1500 µS/cm in some counties.

**The core problem**: Kenya's water sector data is fragmented across national indicators, regional coverage reports, and laboratory test results. Without a unified view, policymakers cannot see the full picture — they can measure *access* but not *quality*, and they can track *national* trends but not *regional* delivery.

This project addresses that gap by bringing three data sources together into a single, explorable analysis.

---

## 🎯 Objectives

### General Objective
To analyze Kenya's water access and water quality using national, regional, and laboratory data sources, producing actionable insights for policy and infrastructure planning.

### Specific Objectives
1. **Quantify** 25 years of national progress in water and sanitation access (2000–2024)
2. **Assess** freshwater resource pressure by analyzing withdrawal rates
3. **Evaluate** water quality across Kenyan counties using pH, conductivity, and TDS measurements
4. **Compare** chemical parameters against KEBS and WHO drinking water standards
5. **Examine** the Athi River basin as a regional case study of coverage growth
6. **Visualize** findings in a user-friendly web application for non-technical audiences

---

## ❓ Research Questions

1. **How has Kenya's access to basic drinking water and sanitation changed between 2000 and 2024?**
2. **Is the gap between water access and sanitation access narrowing or widening?**
3. **What is Kenya's freshwater withdrawal as a percentage of internal resources, and is it approaching water stress levels?**
4. **What is the average pH of water across Kenyan counties, and does it fall within the KEBS acceptable range (6.5–8.5)?**
5. **How does water quality vary by source type (borehole, rain, effluent, etc.)?**
6. **In the Athi River basin, how has water and sanitation coverage progressed, and what share of the population remains unserved?**
7. **Do conductivity levels in tested water samples exceed the KEBS drinking water limit of 1500 µS/cm?**

---

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| **Python 3.12** | Core language for data processing and analysis |
| **pandas** | Data cleaning, transformation, and aggregation |
| **numpy** | Numerical operations |
| **SQLite** | Lightweight database for storing the three datasets |
| **matplotlib / seaborn** | Chart generation and statistical visualization |
| **Streamlit** | Web application framework for interactive deployment |
| **sqlite3** | Python's built-in interface for querying the database |
| **Git & GitHub** | Version control and hosting |
| **Streamlit Cloud** | Free hosting for the deployed application |

---

## 📊 Data Sources

### 1. World Bank Open Data
- **What it provides**: Annual national indicators for water, sanitation, and freshwater use
- **Indicators used**:
  - `SH.H2O.BASW.ZS` — Basic drinking water services (% of population)
  - `SH.STA.BASS.ZS` — Basic sanitation services (% of population)
  - `SH.STA.ODFC.ZS` — Open defecation (% of population)
  - `ER.H2O.FWTL.ZS` — Freshwater withdrawal (% of internal resources)
- **Coverage**: 2000–2024
- **Access**: Free public API

### 2. HDX — Humanitarian Data Exchange (Athi River Basin Coverage Data)
- **What it provides**: Water and sanitation coverage data for the Athi River basin
- **Variables**: Total population, served population, non-served population, coverage percentage
- **Coverage**: 2011–2014
- **Access**: Free public download

### 3. KEWI — Kenya Water Institute Water Test Results
- **What it provides**: 493 water sample test results from across Kenya
- **Variables**: Sample number, date, water source type, county, pH, alkalinity, conductivity, total dissolved solids
- **Coverage**: 2011–2012, spanning 50+ counties
- **Access**: Open data via HDX

---

## 👥 Target Audience

This project is designed for three primary audiences:

### 1. **Policymakers and Government Agencies**
- Ministry of Water, Sanitation and Irrigation
- County governments planning water infrastructure
- NEMA (National Environment Management Authority) and WRA (Water Resources Authority)

**What they get**: Evidence of where access gaps persist, which counties have water quality concerns, and how regional basins are performing.

### 2. **Development Organizations and NGOs**
- Water.org, UNICEF, WHO Kenya office
- Local water user associations (WRUAs)

**What they get**: Data-driven identification of priority areas for intervention, plus a replicable analysis framework.

### 3. **Researchers and Students**
- Environmental science, public health, and development studies programs
- Data analysts interested in African water sector data

**What they get**: A transparent, reproducible pipeline for combining multi-source water data — with documented methodology and limitations.

---

## 🔬 Methodology

The project follows a **five-phase pipeline**:

### Phase 1 — Data Acquisition
Pulled water-related indicators from the World Bank API, downloaded regional coverage data from HDX, and retrieved the KEWI water test dataset.

### Phase 2 — Data Cleaning
Standardized column names using fuzzy matching (ignoring case, punctuation, and special characters), converted text-stored numbers to numeric types, filled text nulls with placeholders, and preserved numeric nulls (which mean "test not performed").

### Phase 3 — Storage
Loaded all three cleaned datasets into a **SQLite database** (`kenya_water.db`) with three tables: `national_indicators`, `athi_river_coverage`, and `kewi_water_tests`.

### Phase 4 — Analysis
Queried the database for aggregations (averages per county, per source type, per year), compared pH and conductivity against KEBS/WHO limits, and computed coverage statistics for the Athi River basin.

### Phase 5 — Visualization & Deployment
Generated eight publication-quality charts, saved them as PNGs, and wrapped the analysis in a **Streamlit web application** for interactive exploration.

---

## 📈 Visualizations — Detailed Explanation

Each visualization answers a specific research question. Here's what each one shows, in plain language.

### 📊 Chart 1 — National WASH Access Trends (2000–2024)

**What it shows**: Three lines tracking water access, sanitation access, and open defecation in Kenya over 24 years.

**Why it matters**: This is the headline chart. It shows Kenya's overall progress at a glance — and reveals the persistent gap between water and sanitation.

**Key insight**: Water access rose from 45.4% to 65.6% (+20.2 percentage points). Sanitation rose from 23.6% to 40.9% (+17.3 pp). Open defecation fell from 16.9% to 5.9% (−11 pp). Despite progress, sanitation still lags water access by **~25 percentage points** in 2024.

---

### 📊 Chart 2 — Freshwater Withdrawal (% of Internal Resources)

**What it shows**: A line chart of Kenya's freshwater withdrawal rate over time, with a red dashed line marking the 25% water stress threshold.

**Why it matters**: Withdrawing more than 25% of renewable freshwater resources signals water stress. This chart tracks how close Kenya is to that threshold.

**Key insight**: Withdrawal rose from 7.5% (2000) to 19.5% (2022) — still below the stress threshold, but rising fast. If the current trend continues, Kenya could approach water stress within a decade.

---

### 📊 Chart 3 — Average pH by County (KEWI Water Tests)

**What it shows**: A horizontal bar chart ranking counties by their average water pH. Two orange dotted lines mark the KEBS acceptable range (6.5–8.5).

**Why it matters**: pH is a basic indicator of water safety. Too acidic (< 6.5) or too alkaline (> 8.5), and water can corrode pipes, harm aquatic life, and be unsafe to drink.

**Key insight**: Average pH ranges from **5.58 (Bungoma)** — below the KEBS minimum — to **8.50 (Homa Bay)**. Most counties fall within range, but a handful of outliers highlight water quality issues.

---

### 📊 Chart 4 — Average Conductivity by Water Source Type

**What it shows**: A bar chart comparing average conductivity across source types (borehole, rain, effluent, etc.). A red dashed line marks the KEBS limit of 1500 µS/cm.

**Why it matters**: High conductivity means the water contains elevated dissolved salts or minerals — which can indicate pollution.

**Key insight**: Effluent water samples show the highest conductivity, while rain water is the cleanest. This confirms that **source type is a strong predictor of water quality**.

---

### 📊 Chart 5 — Athi River Basin Coverage Over Time (2011–2014)

**What it shows**: Two lines tracking water and sanitation coverage percentages in the Athi River basin from 2011 to 2014.

**Why it matters**: This is your regional case study. It shows whether access is growing or stagnating in a specific basin that serves millions of people.

**Key insight**: Water coverage rose from 62% to 70% (+8 pp) and sanitation from 67% to 71% (+4 pp). Both sectors are progressing, but water is catching up to sanitation — a reversal of the national pattern.

---

### 📊 Chart 6 — Served vs Unserved Population (Athi River Basin)

**What it shows**: A grouped bar chart comparing served and unserved populations for water and sanitation in the Athi basin.

**Why it matters**: Even where coverage is growing, millions remain unserved. This chart quantifies the remaining gap.

**Key insight**: In the Athi basin, ~7.3 million people lack access to sanitation and ~7.7 million lack access to water — roughly **one-third of the entire basin population** remains unserved.

---

### 📊 Chart 7 — Water Tests by Source Type

**What it shows**: A pie chart showing how many KEWI water tests were performed on each source type.

**Why it matters**: It reveals testing priorities. Are regulators focusing on high-risk sources like effluent, or on safer sources like boreholes?

**Key insight**: The distribution shows which sources received the most attention — useful context for interpreting the quality results.

---

### 📊 Chart 8 — pH vs Conductivity Scatter Plot

**What it shows**: Each dot represents one water sample. X-axis is pH, Y-axis is conductivity. Dots are colored by source type. A red line marks the KEBS conductivity limit.

**Why it matters**: Scatter plots reveal patterns that averages hide. You can see clusters, outliers, and correlations between two quality parameters.

**Key insight**: Most samples cluster in the "safe" zone (pH 6.5–8.5, conductivity < 1500 µS/cm), but a visible minority falls outside — highlighting samples that need follow-up investigation.

---

## 🔑 Key Findings

1. **National access is improving but slowly** — Kenya adds ~0.85 percentage points per year to water access, far below the pace needed to reach universal access by 2030.

2. **Sanitation is the weakest link** — 59% of Kenyans still lack basic sanitation, and the gap vs. water access has barely narrowed in 24 years.

3. **Freshwater pressure is rising** — Withdrawal has nearly tripled since 2000, tracking toward the 25% water stress threshold.

4. **Water quality varies widely** — pH ranges from 5.58 to 8.50 across counties; some fall outside the KEBS acceptable range.

5. **Source type predicts quality** — Effluent samples are consistently worse than rain or borehole samples.

6. **Regional coverage is uneven** — Even in the relatively well-served Athi River basin, one-third of the population remains unserved.

7. **The data itself is a finding** — Only ~3% of Kenya's 47 counties have active, continuous water quality monitoring, revealing a major national data infrastructure gap.

---

## ⚠️ Limitations

- **Coverage bias**: KEWI testing is heavily concentrated in Nairobi, Machakos, Kiambu, and Kajiado — other counties have 1–5 tests each, limiting statistical reliability.
- **Temporal mismatch**: The three datasets span different periods (2000–2024 for national, 2011–2014 for Athi, 2011–2012 for KEWI) and cannot be merged into a single time series.
- **Missing years**: Freshwater withdrawal data ends in 2022 (2023–2024 unavailable).
- **Text-stored numbers**: Some KEWI columns were loaded as text and required coercion, which may have dropped malformed rows.
- **Non-Kenyan entries**: The KEWI dataset includes samples from Somalia, Tanzania, and South Sudan — these were retained but should be filtered for Kenya-only analysis.
- **No microbial data**: This analysis covers chemical parameters only. E. coli and coliform data, which are critical for health risk, are not available.

---

## 🚀 Running the Project Locally

```bash
git clone https://github.com/YOUR_USERNAME/kenya-water-quality.git
cd kenya-water-quality
pip install -r requirements.txt
streamlit run app.py
