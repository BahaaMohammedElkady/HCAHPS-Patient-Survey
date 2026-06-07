# 🏥 HCAHPS Patient Survey — National Quality of Care Analysis

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)
![Pandas](https://img.shields.io/badge/Pandas-2.0%2B-150458?logo=pandas)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.7%2B-11557c)
![Seaborn](https://img.shields.io/badge/Seaborn-0.12%2B-4c72b0)
![License](https://img.shields.io/badge/License-MIT-green)

---

## 📋 Project Overview

This project performs a comprehensive data analysis of the **Hospital Consumer Assessment
of Healthcare Providers and Systems (HCAHPS)** survey — a national, standardized instrument
that measures patients' perspectives on hospital care across the United States.

The analysis covers **national and state-level scores from 2015 to 2023** (9 years),
examining 10 HCAHPS measures across 51 states and 4,700+ hospital facilities to answer
four core recommended questions:

> 1. Have hospitals made improvements in their quality of care over the past 9 years?
> 2. Are there specific areas where hospitals have made more progress than others?
> 3. Are there still major areas of opportunity?
> 4. What recommendations can be made to help hospitals further improve patient experience?

---

## 🗂️ Project Structure

```
HCAHPS+Patient+Survey/
│
├── 📓 HCAHPS_Patient_Survey.ipynb     ← Main analysis notebook (24 cells)
├── 📄 README.md                        ← This file
│
├── 📁 data_tables/                     ← Raw CSV data files
│   ├── reports.csv                     ← Release periods & date ranges
│   ├── measures.csv                    ← 10 HCAHPS measures & types
│   ├── questions.csv                   ← Survey questions per measure
│   ├── national_results.csv            ← National-level scores
│   ├── state_results.csv               ← State-level scores
│   ├── responses.csv                   ← Facility-level survey data
│   └── states.csv                      ← State names & Census regions
│
├── 📁 Charts/                          ← All exported visualizations (9 charts)
│   ├── 01_EDA_Overview.png
│   ├── 02_Q1_National_Trend.png
│   ├── 03_Q2_Measure_Progress.png
│   ├── 04_Q3_Opportunity_Areas.png
│   ├── 05_Q4_COVID_Impact.png
│   ├── 06_Q5_Geographic_Analysis.png
│   ├── 07_Q6_Response_Rate_Trends.png
│   ├── 08_Q7_Measure_Type_Comparison.png
│   └── 09_Final_Summary_Dashboard.png
│
├── 📁 New_Created_Tables/              ← Derived/exported tables
├── 📁 Presentations/                   ← Presentation assets
└── 📄 data_dictionary.csv              ← Full data dictionary
```

---

## 📊 Dataset

| Table | Rows | Columns | Description |
|-------|------|---------|-------------|
| `reports.csv` | 9 | 3 | Release periods from 07_2015 to 07_2023 |
| `measures.csv` | 10 | 3 | HCAHPS measures with IDs and types |
| `questions.csv` | 19 | 6 | Individual survey questions per measure |
| `national_results.csv` | 90 | 5 | National top/middle/bottom-box % |
| `state_results.csv` | 4,580 | 6 | State-level scores per measure per period |
| `responses.csv` | 43,219 | 5 | Facility-level response rates |
| `states.csv` | 51 | 3 | States with Census Bureau regions |

**Source:** [Centers for Medicare & Medicaid Services (CMS)](https://www.cms.gov/Research-Statistics-Data-and-Systems/Research/CAHPS/HCAHPS1)
**Coverage:** October 2013 – September 2022 (released July 2015 – July 2023)

---

## 🔬 Analytical Questions & Key Findings

### Q1 — Overall National Trend
> Are hospitals improving overall?

**Finding:** Overall average Top-box % declined from **71.0% (2015) → 69.4% (2023)**, a net
change of **-1.6 percentage points**. Scores peaked during COVID (72.3% in 2020–2021) then
collapsed sharply — all 10 measures declined or held flat over 9 years.

---

### Q2 — Measure-by-Measure Progress
> Where did hospitals improve most?

**Finding:** Not a single measure showed net improvement.
The worst performers were:

| Measure | Net Change | Post-Peak Drop |
|---------|-----------|----------------|
| Communication about Medicines | -4% | -5% |
| Responsiveness of Hospital Staff | -3% | -5% |
| Communication with Doctors | -3% | -3% |

The most resilient measures (0% net change) were Communication with Nurses,
Discharge Information, and Quietness of Hospital Environment.

---

### Q3 — Persistent Opportunity Areas
> Where are hospitals still struggling?

**Finding:** Five measures consistently scored below the national average across all 9 years:

| Measure | Avg Top-box % | Gap vs National Avg |
|---------|--------------|---------------------|
| Care Transition | 52.6% | -18.8pp |
| Quietness of Hospital Environment | 62.2% | -9.2pp |
| Communication about Medicines | 64.8% | -6.6pp |
| Responsiveness of Hospital Staff | 68.6% | -2.8pp |
| Willingness to Recommend | 71.3% | -0.1pp |

Care Transition is a **chronic structural crisis** — stuck at 51–54% for 9 consecutive years.

---

### Q4 — COVID-19 Impact
> Did the pandemic cause a visible dip?

**Finding:** Counterintuitively, scores **rose during COVID (+0.7%)** — likely due to patient
gratitude and lower expectations. The real damage came post-COVID:

| Period | Avg Top-box % |
|--------|--------------|
| Pre-COVID (2015–2019) | 71.6% |
| COVID (2020–2021) | 72.3% |
| Post-COVID (2022–2023) | 70.0% |

The post-COVID collapse of **-2.3%** erased 6 years of incremental gains — likely driven
by healthcare worker burnout and staffing shortages.

---

### Q5 — Geographic Analysis
> Which states and regions consistently outperform?

**Finding:** A **7.6pp gap** exists between the best and worst regions:

| Rank | Region | Avg Top-box % |
|------|--------|--------------|
| 🥇 1 | West North Central | 74.9% |
| 🥈 2 | West South Central | 73.7% |
| ⚠️ 8 | South Atlantic | 68.8% |
| ⚠️ 9 | Mid-Atlantic | 67.3% |

**South Dakota (76.8%), Nebraska (76.7%), and Louisiana (76.1%)** lead all states.
**District of Columbia (62.4%), New Jersey (65.6%), and New York (66.1%)** are at the bottom.

---

### Q6 — Response Rate Trends
> Is the survey data becoming less reliable?

**Finding:** Response rates fell continuously from **30.8% (2015) → 22.7% (2023)** — a drop
of 8.1 percentage points. A moderate positive correlation of **r = 0.593** between response
rate and Top-box scores suggests growing non-response bias. States that engage patients
most also score best.

---

### Q7 — Measure Type Comparison
> Do Composite, Individual, and Global measures improve differently?

**Finding:** All three types declined, but Composite measures fell hardest:

| Type | Start (2015) | End (2023) | Net Change |
|------|-------------|-----------|-----------|
| Composite Measure | 72.0% | 70.2% | **-1.8%** |
| Global Item | 71.0% | 69.5% | -1.5% |
| Individual Item | 68.0% | 67.0% | -1.0% |

Individual Items (environment) showed the most resilience.
Composite measures — which reflect direct staff behavior — declined fastest.

---

## 💡 Recommendations

| Priority | Recommendation | Target Measure |
|----------|---------------|----------------|
| 🔴 Critical | Redesign discharge & care transition processes with dedicated teams | Care Transition |
| 🔴 Critical | Mandate bedside pharmacist consultations & plain-language medication cards | Communication about Medicines |
| 🔴 High | Invest in post-COVID staff mental health & communication training | All Composite Measures |
| 🟡 Medium | Audit call-light response protocols & staffing ratios | Responsiveness |
| 🟡 Medium | Commission best-practice studies from top Midwest states | Geographic gap |
| 🟢 Opportunity | Implement SMS/multilingual post-discharge survey outreach | Response Rate |

---

## 🛠️ Technical Stack

| Library | Version | Purpose |
|---------|---------|---------|
| `pandas` | 2.0+ | Data loading, cleaning, merging, aggregation |
| `numpy` | 1.24+ | Numerical operations |
| `matplotlib` | 3.7+ | All chart creation and styling |
| `seaborn` | 0.12+ | Heatmaps and statistical plots |
| `jupyter` | 6.0+ | Interactive notebook environment |

---

## ⚙️ Setup & Usage

### 1. Clone or download the project
```bash
cd /home/pharmacy/HCAHPS+Patient+Survey
```

### 2. Install required libraries
```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 3. Launch the notebook
```bash
jupyter notebook HCAHPS_Patient_Survey.ipynb
```

### 4. Run all cells
Use **Kernel → Restart & Run All** to execute the full analysis from scratch.
All 9 charts will be saved automatically to the `/Charts/` directory.

---

## 📁 Output Charts

| # | File | Content |
|---|------|---------|
| 01 | `01_EDA_Overview.png` | Measure distribution, score histogram, trend, response rate |
| 02 | `02_Q1_National_Trend.png` | All measures over time + overall average trend |
| 03 | `03_Q2_Measure_Progress.png` | Net change, 2015 vs 2023 bars, post-peak drop |
| 04 | `04_Q3_Opportunity_Areas.png` | Ranked averages + Top-box & Bottom-box heatmaps |
| 05 | `05_Q4_COVID_Impact.png` | Pre/during/post COVID comparison by measure |
| 06 | `06_Q5_Geographic_Analysis.png` | Regional rankings, top/bottom states, regional trends |
| 07 | `07_Q6_Response_Rate_Trends.png` | Response rate trend, volume distribution, correlation |
| 08 | `08_Q7_Measure_Type_Comparison.png` | Composite vs Individual vs Global type analysis |
| 09 | `09_Final_Summary_Dashboard.png` | Executive summary — all 7 analyses in one dashboard |

---

## 📌 Data Limitations

- `Completed Surveys` volume categories are only populated for the 2015 release period;
  subsequent years show "Not Available" only.
- Response rates below 25% (post-2020) increase the risk of non-response bias.
- State-level results reflect averages across all facilities within each state —
  facility-level variation is not captured in this analysis.
- The 2 null values in `questions.csv` (Middle-box Answer for H_COMP_6) are expected,
  as those questions use a Yes/No scale with no middle response category.

---

## 👨‍💻 Author

**Dr. Bahaa**
Pharmacist & Data Analyst
Bahaa Pharmacy, Dirout, Egypt

---

## 📄 License

This project is licensed under the MIT License.
HCAHPS data is publicly available via the Centers for Medicare & Medicaid Services (CMS).

---

*Built with Python & Jupyter Notebook | Analysis period: 2015–2023*
