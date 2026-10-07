# 🏦 Retail Bank Transaction Analysis

An end-to-end **Power BI** business intelligence project that turns raw retail banking data into an interactive report covering customers, accounts, transactions, loans, cards, and product engagement.

---

## 📌 Project Overview

Retail banks hold large volumes of data across customers, accounts, branches, cards, loans, and transactions. Raw tables make it hard for management to spot patterns or compare performance. This project, built from the perspective of a **BI Analyst supporting the Retail Banking team**, delivers a clear, interactive dashboard that answers key business questions.

### 🎯 Objectives
- Understand customer profiles and segmentation
- Analyze account usage and branch activity
- Analyze transaction patterns
- Evaluate loan performance and repayment behavior
- Understand card usage and product engagement
- Provide an executive summary of the most important KPIs

---

## 📂 Repository Structure

```
Retail_banking-Transaction-analysis/
│
├── Retail_banking_Transaction_analysis.pbix            # Power BI report (data, model, DAX, dashboards)
├── Retail_Bank_Transaction_Analysis_Documentation.docx # Full project documentation
│
├── Customer profile.png                                # Dashboard: Customer profile & segmentation
├── Account usage.png                                   # Dashboard: Account usage & branch activity
├── transaction parttern.png                            # Dashboard: Transaction patterns
├── loan performance.png                                # Dashboard: Loan performance & repayment
└── card Usage.png                                      # Dashboard: Card usage & product engagement
```

---

## 🗃️ Dataset

Seven banking tables plus a date table, loaded into Power BI Desktop and cleaned in Power Query.

| Table | Rows | Purpose |
|---|---|---|
| Customers | 500 | Customer demographics, KYC, tenure |
| Accounts | 700 | Account type, balances, interest rates, status |
| Branches | 40 | Branch information |
| Cards | 600 | Card type, network, limits, reward points |
| Loans | 300 | Loan type, purpose, amount, outstanding balance |
| Loan Payments | 2,000 | Repayment status, method, days late |
| Transactions | 5,000 | Amounts, types, channels, status |
| Date Table | 6,940 | Calendar for time-based analysis (2010–2028) |

---

## 🔄 Project Workflow

```
Raw CSV Files → Data Loading → Power Query Cleaning → Data Modeling → KPI Identification
→ DAX Measures → Dashboard Design → Business Insights → Executive Summary
```

### Sprint Structure

| Sprint | Activity |
|---|---|
| 1 | Business Understanding |
| 2 | Data Loading, Cleaning & Data Modeling |
| 3 | KPI Identification |
| 4 | DAX Measures & Calculated Columns |
| 5 | Objective-Based Dashboard Design |

---

## 🧹 Data Cleaning & Modeling

- Validated data types (IDs as text, dates as date, amounts/rates as decimals)
- Trimmed spaces, removed unwanted characters, standardized capitalization
- Handled missing customer segments with an explicit **"Unspecified"** category instead of dropping records
- Built relationships: Customers → Accounts → Transactions / Cards / Loans → Loan Payments, and Branches → Accounts
- Connected a Date table for monthly and yearly trend analysis
- Validated relationships to avoid duplicated or inflated totals

> **Note:** 301 of 700 accounts (~43%) have no card. This is a realistic feature of the data, not an error, so visuals mixing accounts and cards may show blank card categories.

---

## 📐 Key KPIs

| Category | KPIs |
|---|---|
| Customer & Account | Total Customers, Total Accounts, Active Accounts, Total Balance, Average Balance |
| Transactions | Total Transactions, Total / Average Transaction Amount |
| Loans | Total Loans, Total Loan Amount, Outstanding Balance, Late Payments, Delinquency Rate |
| Cards | Total Cards, Active Cards, Avg. Credit Limit, Reward Points |

---

## 🧮 Sample DAX Measures

```DAX
Total Customers = COUNTROWS(Customers)

Active Accounts =
CALCULATE(COUNTROWS(Accounts), Accounts[status] = "Active")

Total Account Balance = SUM(Accounts[current_balance])

Late Payments =
CALCULATE(COUNTROWS(Loan_Payments), Loan_Payments[days_late] > 0)

Loan Delinquency Rate =
DIVIDE([Late Payments], COUNTROWS(Loan_Payments), 0)

Payment Delay Category =
SWITCH(
    TRUE(),
    Loan_Payments[days_late] = 0, "On Time",
    Loan_Payments[days_late] <= 30, "1–30 Days Late",
    "30+ Days Late"
)
```

---

## 📊 Dashboard Pages

### 1. Customer Profile & Segmentation
Customers by segment, gender, city/state, activity status, and KYC status.

<img width="1321" height="742" alt="Customer profile" src="https://github.com/user-attachments/assets/20eeed15-cb7e-4d4b-babd-171b30cf53da" />


### 2. Account Usage & Branch Activity
Accounts and balances by type and branch, active vs closed accounts.

<img width="1320" height="740" alt="Account usage" src="https://github.com/user-attachments/assets/34287699-9557-49aa-912e-d71b7799514f" />

### 3. Transaction Patterns
Transactions by type, channel, description, and month.

<img width="1330" height="741" alt="transaction parttern" src="https://github.com/user-attachments/assets/8bc94cf9-493c-46b2-8e2e-08b7bbf2e9f3" />


### 4. Loan Performance & Repayment Behavior
Loan types, purposes, outstanding balances, late payments, and payment methods.

<img width="1322" height="731" alt="loan performance" src="https://github.com/user-attachments/assets/139b9993-f2e1-4c52-9b2e-2648144db216" />


### 5. Card Usage & Product Engagement
Card types, networks, active vs inactive cards, credit limits, and reward points.

<img width="1320" height="742" alt="card Usage" src="https://github.com/user-attachments/assets/a19e2b93-1d73-47ed-9527-92b708195f56" />


---

## ▶️ How to Use

1. Clone the repository
   ```bash
   git clone https://github.com/<your-username>/Retail_banking-Transaction-analysis.git
   ```
2. Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (Windows)
3. Open `Retail_banking_Transaction_analysis.pbix`
4. Use the slicers (segment, gender, state, account type, branch, loan type, etc.) to explore the data

---

## 🛠️ Tools & Skills

- **Microsoft Power BI Desktop**
- **Power Query** for data cleaning
- **Data modeling** (relationships, cardinality, date table)
- **DAX** (measures and calculated columns)
- **Dashboard design** and business storytelling

---

## 🔮 Future Scope

- Automated data refresh and scheduled reporting
- Advanced customer segmentation
- Predictive loan-risk analysis
- Role-based dashboards for different banking teams
- Additional financial and customer-service datasets

---

## 👤 Author

**Kothapalli Ganesh

---

## 📄 License

This project is for educational purposes.
