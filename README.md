**# 📊 **Mobile Sales Dashboard — Power BI**
### *End‑to‑End Business Intelligence Project*

**Author:** Shikha Karan  
**Tools:** Power BI • DAX • Data Modeling • Visualization  
**Includes:** Custom Calendar • Explicit Measures • Technical Audit Report

---

📊 Mobile Sales Dashboard — Power BI Project
A complete end‑to‑end Power BI analytics project analyzing mobile phone sales across brands, cities, payment methods, customer ratings, and time periods.
This project includes a custom data model, explicit DAX measures, interactive visuals, and a full technical audit report validating the correctness of the dashboard.

🚀 Project Overview
This dashboard provides a comprehensive view of mobile sales performance, enabling insights into:

Total sales revenue

Total units sold

Number of transactions

Average daily sales

Brand‑wise performance

Model‑wise performance

City‑level sales distribution

Customer rating analysis

Payment method trends

Monthly and daily sales patterns

The project demonstrates strong skills in data modeling, DAX, visual analytics, and business intelligence storytelling.

🧱 Data Model
The data model follows a clean star schema:

Fact Table: mobile_sales_data

Dimension Table: custom_calendar

Relationship:

custom_calendar[Date] → mobile_sales_data[Date]

Cardinality: Many-to-One

Cross-filter direction: Single

This ensures accurate filtering, correct time intelligence, and optimized performance.

🧮 Key DAX Measures
All KPIs are built using explicit DAX measures, including:

DAX
total_sales =
SUMX(
    mobile_sales_data,
    mobile_sales_data[Units Sold] * mobile_sales_data[Price Per Unit]
)

total_quantity = SUM(mobile_sales_data[Units Sold])

Transactions = DISTINCTCOUNT(mobile_sales_data[Transaction ID])

average_daily_sales =
DIVIDE(
    [total_sales],
    DISTINCTCOUNT(custom_calendar[Date])
)
No implicit measures are used — ensuring accuracy and professional modeling standards.

📈 Dashboard Features
✔ KPI Cards
Total Sales

Total Quantity

Total Transactions

Average Daily Sales

✔ Visuals
Line chart: Monthly quantity trends

Map: City-wise sales distribution

Pie chart: Payment method breakdown

Bar charts:

Brand performance

Mobile model performance

Rating analysis: Good / Average / Poor

Daily sales trend: Day-of-week performance

Interactive slicers: Brand, Model, Payment Method, Month

✔ Interactivity
Fully filterable

Cross-highlight enabled

Slicers affect all visuals

Clean, intuitive layout

🧪 Technical Audit Report
This project includes a full technical audit, covering:

Data model validation

DAX measure correctness

Visual configuration checks

Data integrity verification

Performance analysis

Identified issues & recommendations

📄 Read the full audit report:
docs/technical_audit_report.md

This audit confirms the dashboard is accurate, optimized, and production‑ready.
📁 Repository Structure
mobile-sales-dashboard-powerbi/
│
├── powerbi/
│   └── mobile_sales_dashboard.pbix
│
├── screenshots/
│   ├── dashboard_main.png
│   └── additional_visuals.png
│
├── docs/
│   └── technical_audit_report.md
│
└── README.md
🎯 Skills Demonstrated
Power BI Desktop

Data Modeling (Star Schema)

DAX (SUMX, DISTINCTCOUNT, DIVIDE, Time Intelligence)

Data Cleaning & Transformation

Visual Analytics

Business KPI Design

Dashboard Storytelling

Technical Documentation

Quality Assurance & Audit Reporting

📌 How to Use
Download the .pbix file from the powerbi/ folder

Open in Power BI Desktop

Explore the visuals, slicers, and interactions

Review the audit report for technical validation

🧑‍💼 Author
Shikha Karan
Business Intelligence & Data Analytics
Riyadh, Saudi Arabia
**
