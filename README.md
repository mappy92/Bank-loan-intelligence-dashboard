# Bank Loan Intelligence Dashboard
### *Excel-Based Portfolio Risk Analytics | Business Intelligence | Financial Reporting*

![Excel](https://img.shields.io/badge/Microsoft%20Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=for-the-badge)
![Domain](https://img.shields.io/badge/Domain-Banking%20%26%20Finance-blue?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-Intermediate-orange?style=for-the-badge)

---

## LinkedIn Series - *Learning Aloud in Public*

This project was built and shared as a 3-part LinkedIn series. Follow along:

| Post | Title | Link |
|------|-------|------|
| Day 1 | *Data Architecture & KPI Design* | [View Post →](https://www.linkedin.com/feed/update/urn:li:activity:7435393642074337280) |
| Day 2 | *Design Sheet & Overview Dashboard* | [View Post →](https://www.linkedin.com/feed/update/urn:li:activity:7435752272556539904) |
| Day 3 | *Full Walkthrough & Actionable Intelligence* | [View Post →](https://www.linkedin.com/feed/update/urn:li:activity:7436145499012853761) |

> **Free Resource (PDF):** Full dashboard filter views + Design Sheet architecture + KPI Data Dictionary → [Google Drive](https://drive.google.com/file/d/11A45KCs8jiFdKHtwwTneN7SdTmN66VZM/view?usp=sharing)

---

## 1. Audience-Friendly Description

This project transforms a raw, 38,600-row loan portfolio dataset into a fully interactive, business-ready intelligence dashboard - **built entirely in Microsoft Excel**.

No Power BI licence. No SQL server. No Python environment to configure. Just Excel and a rigorous analytical framework that mirrors how risk teams in real financial institutions monitor loan portfolio health.

If you are a **Data Analyst, BI Developer, or Data Scientist** building a portfolio for banking and financial services roles, this project demonstrates the core reporting logic that underpins loan portfolio management: KPI aggregation, month-over-month trending, good/bad loan classification, and multi-dimensional slicing by grade, purpose, and geography.

---

## 2. Business Impact

| Impact Area | Result |
|-------------|--------|
| **Portfolio Health Visibility** | Instant view of Good Loan rate (86.18%) vs Bad Loan rate (13.82%) across 38.6K applications |
| **Risk Segmentation** | Grade E loans carry a 31.31% default rate - validated against a 21.40% interest premium |
| **Funding Gap Analysis** | $435.8M funded vs $473.1M received - profitability spread surfaced at a glance |
| **Stakeholder-Ready Reporting** | Interactive slicers eliminate ad-hoc SQL queries for common business questions |
| **Month-Over-Month Tracking** | MoM + MTD calculations embedded, supporting rolling performance reviews |

**Who benefits from this analysis:**
- **Credit Risk Officers** - monitor default rates and early warning signals
- **Portfolio Managers** - track funded vs received amounts by segment
- **Product Teams** - identify high-performing loan purposes (Wedding: 90.73% good rate)
- **Executive Reporting** - single-pane KPI summary for board-level presentation

---

## 3. Project Description

### Background
Banks and lending institutions manage thousands of loan applications across multiple risk grades, purposes, and geographies. Without a structured reporting layer, identifying portfolio stress points (e.g., rising Charged Off rates in Grade E) requires significant manual querying effort.

### What Was Built
A two-dashboard Excel workbook connected to a raw 24-column dataset, featuring:

**Summary Dashboard** - KPI tiles for total applications, funded amount, amount received, avg interest rate, and avg DTI. Good Loan vs Bad Loan donut charts. Loan status breakdown by application count, funded amount, amount received, interest rate, and DTI.

**Overview Dashboard** - Monthly trend line, US state choropleth map, loan term donut (36 vs 60 months), employment length distribution, loan purpose horizontal bar chart, and home ownership treemap.

**Interactive Filtering** - All visuals are connected to Grade (A–G) and Purpose (car, credit card, debt consolidation, educational, home improvement, house, medical, moving, other, renewable energy, small business, vacation, wedding) slicers.

### Key Technical Decisions
- MoM formula: `(MTD − PMTD) / PMTD` - implemented via pivot table time intelligence
- Good/Bad Loan classification: `IF loan_status = "Fully Paid" OR "Current" → "Good Loan"` | `"Charged Off" → "Bad Loan"`
- Design Sheet architecture: All pivot tables and source charts are isolated in a hidden Design Sheet, keeping dashboard views clean
- State map using Excel's built-in Bing Maps integration with raw state abbreviation data

### Dataset
- **Source:** Simulated LendingClub-style loan portfolio (publicly available structure)
- **Size:** 38,600 loan records × 24 columns
- **Period:** Full calendar year (Jan–Dec), month-level granularity
- **See:** [`docs/Data_Dictionary.pdf`](docs/Data_Dictionary.pdf) for full column definitions

---

## 4. Folder Structure

```
bank-loan-intelligence-dashboard/
│
├── README.md                          ← You are here
│
├── docs/
│   ├── Business_Requirements_Document.docx   ← Stakeholder requirements & KPI specs
│   ├── Problem_Statement.docx                ← Business problem, objectives, success criteria
│   └── Data_Dictionary.pdf                   ← Column definitions & loan classification logic
│
├── dashboard/
│   ├── screenshots/
│   │   ├── 01_Summary_All_Grades.png
│   │   ├── 02_Summary_Grade_B.png
│   │   ├── 03_Summary_Grade_E.png
│   │   ├── 04_Summary_Educational.png
│   │   ├── 05_Summary_Wedding.png
│   │   ├── 06_Summary_Medical.png
│   │   ├── 07_Overview_All_Grades.png
│   │   ├── 08_Overview_Grade_B.png
│   │   ├── 09_Overview_Grade_E.png
│   │   ├── 10_Overview_House.png
│   │   └── 11_Overview_House_Improvement.png
│   └── design_sheets/
│       ├── Design_Sheet_1_Measures.png
│       ├── Design_Sheet_2_Loan_Status.png
│       ├── Design_Sheet_3_State_Map.png
│       └── Design_Sheet_4_Term_Purpose_Ownership.png
│
├── data/
│   └── DATA_SOURCE.md                 ← Notes on dataset
│
├── assets/
│   └── flow_diagram.png               ← End-to-end project architecture diagram
│
└── linkedin/
    └── post_series.md                 ← Full text of 3-day LinkedIn series
```

---

## 5. Flow Diagram

```
RAW DATA (38,600 rows × 24 cols)
         │
         ▼
[Data Sheet - Excel Workbook]
  • Loan ID, Member ID, State, Grade, Sub-Grade
  • Loan Amount, Interest Rate, DTI
  • Loan Status → Good/Bad Loan (derived column)
  • Issue Date → MTD / PMTD grouping
         │
         ▼
[Design Sheet - Hidden Pivot Layer]
  • Overall Measures Pivot (Total, MTD, PMTD, MoM)
  • Loan Status Pivot (Fully Paid / Charged Off / Current)
  • Good vs Bad Loan Pivot + Donut Charts
  • Monthly Trends Pivot (line chart)
  • State Map Pivot (choropleth)
  • Term Analysis (36 / 60 months donut)
  • Emp Length Pivot (horizontal bar)
  • Purpose Pivot (horizontal bar)
  • Home Ownership Pivot (treemap)
         │
         ├──────────────────────┐
         ▼                      ▼
[Summary Dashboard]      [Overview Dashboard]
  KPI Tiles (5)           Monthly Trend Line
  Good Loan Section       US State Map
  Bad Loan Section        Term Donut
  Loan Status Bars        Emp Length Bar
                          Purpose Bar
                          Home Ownership Treemap
         │                      │
         └──────────┬───────────┘
                    ▼
         [Interactive Slicers]
         Grade Filter (A–G)
         Purpose Filter (13 categories)
```

---

## 6. Demo Video

> *Dashboard walkthrough video - see LinkedIn Day 3 post for the full end-to-end video.*

**[▶ Watch the Full Walkthrough on LinkedIn](https://www.linkedin.com/feed/update/urn:li:activity:7436145499012853761)**

Covers:
- Grade B vs Grade E risk comparison (88.50% vs 68.69% Good Loan rate)
- Wedding vs Medical vs Educational purpose segmentation
- House vs Home Improvement lending comparison
- Live slicer interaction demonstrating the Design Sheet architecture
- How to frame these insights for a Director-level stakeholder meeting

---

## 7. Output - Key Dashboard Findings

### Summary Dashboard (All Grades)
| KPI | Value |
|-----|-------|
| Total Loan Applications | **38.6K** |
| Total Funded Amount | **$435.8M** |
| Total Amount Received | **$473.1M** |
| AVG Interest Rate | **12.05%** |
| AVG DTI | **13.33%** |
| Good Loan Rate | **86.18%** (33.2K applications) |
| Bad Loan Rate | **13.82%** (5.3K applications) |

### Segment Highlights
| Segment | Good Loan % | Bad Loan % | Avg Interest Rate |
|---------|-------------|------------|-------------------|
| Grade B | 88.50% | 11.50% | 11.03% |
| Grade E | 68.69% | 31.31% | 21.40% |
| Wedding | 90.73% | 9.27% | 11.89% |
| Medical | 85.01% | 14.99% | 11.57% |
| Educational | 84.13% | 15.87% | 11.65% |
| House | 0.4K apps | - | 12.38% |
| Home Improvement | 2.9K apps | - | 11.40% |

### Loan Status Breakdown
| Status | Count | Funded | Received | Avg Rate | Avg DTI |
|--------|-------|--------|----------|----------|---------|
| Fully Paid | 32.1K | $351.4M | $411.6M | 11.64% | 13.17% |
| Charged Off | 5.3K | $65.5M | $37.3M | 13.88% | 14.00% |
| Current | 1.1K | $18.9M | $24.2M | 15.10% | 14.72% |

---

## 8. How to Run & Dependencies

### Requirements
| Tool | Version | Purpose |
|------|---------|---------|
| Microsoft Excel | 2016 or later (365 recommended) | All dashboard functionality |
| Bing Maps (Excel Add-in) | Built-in with Excel 365 | State choropleth map |

### Steps to Open
```
1. Download the .xlsx file from the /dashboard/ folder (or Releases)
2. Open in Microsoft Excel - Enable Content if prompted
3. Navigate to the "Summary Dashboard" tab
4. Use the Grade and Purpose slicers on the left panel to filter all visuals
5. Click "Overview Dashboard" tab for geographic and trend views
```

### Note on the Design Sheet
The **Design Sheet** tab contains all source pivot tables. It is intentionally left visible so you can inspect the data architecture. In a production environment, this sheet would typically be hidden.

### No Python / No Power BI Required
This project is intentionally Excel-only to demonstrate that sophisticated portfolio analytics can be delivered without additional tooling - a common constraint in banking environments.

---

## 9. Contribution Guidelines

This is a portfolio project, but feedback and suggestions are welcome.

**To suggest improvements:**
1. Open an Issue describing the proposed change
2. Fork the repo and create a feature branch: `git checkout -b feature/your-improvement`
3. Commit your changes with a clear message
4. Open a Pull Request with a description of what changed and why

**Good first contributions:**
- Additional KPI cards (e.g., average loan term by grade)
- A Tableau or Power BI port of the same design
- A Python notebook replicating the KPI calculations from raw CSV

---

## 10. License & Credits

**License:** MIT License - free to use, adapt, and share with attribution.

**Dataset:** This project uses a simulated loan dataset structured after publicly available LendingClub loan data. No real borrower PII is included.

**Author:** Manpreet Singh (Mappy)
- 🔗 [LinkedIn](https://www.linkedin.com/in/manpreet-singh-ds)
- 💻 [GitHub](https://github.com/mappy92)
- 📧 Available for data science roles in Ontario banking & financial services

**Acknowledgements:** Inspired by real-world credit risk reporting frameworks used in Canadian banking, with reference to OSFI E-23 portfolio monitoring guidelines.

---

## 11. 🚀 Next Steps

| Priority | Next Step | Why It Matters |
|----------|-----------|----------------|
| 🔴 High | **Tableau Port** - Rebuild the Summary & Overview dashboards in Tableau Public | Expands the project's reach and demonstrates cross-tool fluency |
| 🔴 High | **Python EDA Notebook** - Replicate KPI calculations in pandas + matplotlib | Demonstrates that the Excel logic is reproducible in code |
| 🟡 Medium | **Predictive Layer** - Add a Logistic Regression model to predict "Good vs Bad Loan" at application time | Connects the reporting layer to an ML layer |
| 🟡 Medium | **Power BI Version** - Use DAX measures to replicate MoM and MTD logic | Common ask in Canadian bank data roles |
| 🟢 Low | **OSFI E-23 Alignment Notes** - Annotate KPIs with relevant OSFI guidelines | Demonstrates Canadian regulatory awareness |
| 🟢 Low | **Automated Refresh** - VBA or Power Query script to refresh pivots on new data load | Production-readiness demonstration |

---

<div align="center">

**⭐ If this project helped you, please give it a star - it helps others find it too.**

*Built as part of a public #LearningAloud series | London, Ontario, Canada*

</div>
