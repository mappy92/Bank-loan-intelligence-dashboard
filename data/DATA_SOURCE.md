# 📂 Data Source Information

## Dataset: Bank Loan Portfolio (financial_loan.csv)

### Origin
This dataset is a structured personal loan portfolio dataset distributed as a flat CSV file (`financial_loan.csv`). It follows the schema and structure of publicly available LendingClub-style loan origination data and is used here strictly for portfolio analytics demonstration. **No real borrower PII is included.**

---

### Dataset Summary
| Attribute | Detail |
|-----------|--------|
| File Name | `financial_loan.csv` |
| Total Records | **38,576 loan records** |
| Total Columns | **24 columns** |
| Date Format | DD-MM-YYYY (e.g., `11-02-2021`) |
| Application Type | INDIVIDUAL only (all records) |
| Geographic Coverage | All 50 US states |
| Loan Grades | A, B, C, D, E, F, G (7 levels) |
| Loan Terms | 36 months, 60 months |
| Loan Statuses | Fully Paid, Charged Off, Current |

---

### Good vs Bad Loan Breakdown (Derived)
| Classification | Count | Percentage |
|----------------|-------|------------|
| **Good Loan** (Fully Paid + Current) | 33,243 | **86.18%** |
| **Bad Loan** (Charged Off) | 5,333 | **13.82%** |
| **Total** | **38,576** | 100% |

*Fully Paid: 32,145 · Current: 1,098 · Charged Off: 5,333*

---

### Full Schema (24 Columns)

| Column | Data Type | Description | Range / Examples |
|--------|-----------|-------------|------------------|
| `id` | Integer | Unique loan identifier | e.g., 1077430 |
| `member_id` | Integer | Unique borrower identifier | e.g., 1314167 |
| `address_state` | Text (Categorical) | Borrower's US state (2-letter code) | 50 unique states; CA highest volume |
| `application_type` | Text (Categorical) | Individual or joint application | `INDIVIDUAL` (all records) |
| `emp_length` | Text (Categorical) | Borrower's employment length | `< 1 year`, `1 year` … `10+ years` (11 buckets) |
| `emp_title` | Text | Borrower's self-reported job title | 563+ unique titles |
| `grade` | Text (Categorical) | Primary credit risk grade | `A`, `B`, `C`, `D`, `E`, `F`, `G` |
| `sub_grade` | Text (Categorical) | Granular sub-grade | e.g., `C4`, `E1` |
| `home_ownership` | Text (Categorical) | Homeownership status | `RENT`, `OWN`, `MORTGAGE`, `NONE`, `OTHER` |
| `issue_date` | Date (Text) | Loan origination date | Format: DD-MM-YYYY |
| `last_credit_pull_date` | Date (Text) | Most recent credit pull date | Format: DD-MM-YYYY |
| `last_payment_date` | Date (Text) | Most recent payment received | Format: DD-MM-YYYY |
| `next_payment_date` | Date (Text) | Scheduled next payment date | Format: DD-MM-YYYY |
| `loan_status` | Text (Categorical) | Current loan state | `Fully Paid`, `Charged Off`, `Current` |
| `purpose` | Text (Categorical) | Borrower's stated loan reason | 14 categories (see below) |
| `term` | Text (Categorical) | Loan repayment term | `36 months`, `60 months` |
| `verification_status` | Text (Categorical) | Income verification status | `Not Verified`, `Source Verified`, `Verified` |
| `annual_income` | Numeric (Currency) | Self-reported annual income | $4,000 — $6,000,000; avg $69,645 |
| `dti` | Numeric (Ratio) | Debt-to-Income ratio (decimal) | 0.00 — 0.30; avg **0.1333** (13.33%) |
| `installment` | Numeric (Currency) | Fixed monthly payment amount | $15.69 — $1,305.19; avg $326.86 |
| `int_rate` | Numeric (Decimal) | Annual interest rate (decimal) | 0.0542 — 0.2459; avg **0.1205** (12.05%) |
| `loan_amount` | Numeric (Currency) | Total funded loan amount | $500 — $35,000; avg $11,296 |
| `total_acc` | Integer | Total credit lines in borrower's file | e.g., 4, 12, 28 |
| `total_payment` | Numeric (Currency) | Total payments received to date | $34 — $58,564; avg $12,263 |

---

### Loan Purpose Categories (14 Values)
`Debt consolidation` · `car` · `credit card` · `educational` · `home improvement` · `house` · `major purchase` · `medical` · `moving` · `other` · `renewable_energy` · `small business` · `vacation` · `wedding`

---

### Key Field Notes for Excel Dashboard

| Field | Dashboard Note |
|-------|----------------|
| `int_rate` | Stored as **decimal** in CSV (e.g., `0.1527` = 15.27%). Excel pivot displays as percentage — formatted × 100 |
| `dti` | Stored as **decimal** (e.g., `0.1333` = 13.33%). Same formatting required |
| `issue_date` | Stored as text string `DD-MM-YYYY`. Must be parsed as date in Excel for MTD/PMTD pivot grouping |
| `loan_status` | Source for the derived **Good v Bad Loan** column: `Fully Paid` + `Current` = Good; `Charged Off` = Bad |
| `loan_amount` | This is the **Total Funded Amount** KPI source column |
| `total_payment` | This is the **Total Amount Received** KPI source column |

---

### Derived Column (Created in Excel — Not in CSV)

| Column Name | Formula Logic | Result |
|-------------|---------------|--------|
| `Good v Bad Loan` | `IF loan_status = "Fully Paid" OR "Current" → "Good Loan"` / `IF loan_status = "Charged Off" → "Bad Loan"` | Good Loan: 86.18% · Bad Loan: 13.82% |

---

### Dashboard KPI Validation Against Raw CSV

| Dashboard KPI | Raw CSV Value | Match |
|---------------|---------------|-------|
| Total Loan Applications | 38,576 (displays as ~38.6K) | ✅ |
| AVG Interest Rate | 12.05% (0.1205 × 100) | ✅ |
| AVG DTI | 13.33% (0.1333 × 100) | ✅ |
| Good Loan % | 86.18% | ✅ |
| Bad Loan % | 13.82% | ✅ |
| Good Loan Applications | 33,243 (displays as 33.2K) | ✅ |
| Bad Loan Applications | 5,333 (displays as 5.3K) | ✅ |
| Fully Paid count | 32,145 (displays as 32.1K) | ✅ |
| Charged Off count | 5,333 (displays as 5.3K) | ✅ |
| Current count | 1,098 (displays as 1.1K) | ✅ |
