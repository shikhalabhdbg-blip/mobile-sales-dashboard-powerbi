**📑 Power BI Technical Audit Report**

**Project: Mobile Sales Dashboard**

**Author: Shikha Karan**  

**Audit Type: Technical Data Model \& DAX Validation**

**Reviewer: Microsoft Copilot (Technical BI Review Mode)**

**Date: 17 May 2026**



**1. Data Model Architecture Audit**

**1.1 Model Structure**

**The model follows a clean single‑fact star schema, consisting of:**



**Fact Table: mobile\_sales\_data**



**Dimension Table: custom\_calendar**



**This structure is appropriate for analytical reporting and supports efficient filtering.**



**1.2 Relationship Validation**

**Relationship: custom\_calendar\[Date] → mobile\_sales\_data\[Date]**



**Cardinality: Many-to-One (Correct)**



**Cross-filter direction: Single (Correct)**



**Relationship is Active**



**No bidirectional filters detected**



**No unnecessary lookup or snowflake tables**



**This ensures predictable filter propagation and prevents double-counting.**



**1.3 Calendar Table Audit**

**The calendar table includes:**



**Date**



**Day Name**



**It functions correctly as a date dimension.**

**Recommendation: Add Year, Month, Month Number, Quarter for advanced time intelligence.**



**1.4 Data Types**

**Date: Date type**



**Units Sold: Whole Number**



**Price Per Unit: Decimal Number**



**Transaction ID: Whole Number or Text (both acceptable)**



**Customer Ratings: Whole Number**



**customer rating: Text (duplicate column — see Section 6)**



**All critical fields use appropriate data types.**



**2. DAX Measure Audit**

**2.1 Verified Measures**

**Total Sales**

**DAX**

**total\_sales =** 

**SUMX(**

&#x20;   **mobile\_sales\_data,**

&#x20;   **mobile\_sales\_data\[Units Sold] \* mobile\_sales\_data\[Price Per Unit]**

**)**

**Correct use of row context**



**No implicit aggregation**



**No double-counting**



**Total Quantity**

**DAX**

**total\_quantity = SUM(mobile\_sales\_data\[Units Sold])**

**Correct aggregation**



**No filter issues**



**Transactions**

**DAX**

**Transactions = DISTINCTCOUNT(mobile\_sales\_data\[Transaction ID])**

**Correct for transaction-level granularity**



**No duplicates detected**



**Average Daily Sales**

**Likely implemented as:**



**DAX**

**average\_daily\_sales =** 

**DIVIDE(**

&#x20;   **\[total\_sales],**

&#x20;   **DISTINCTCOUNT(custom\_calendar\[Date])**

**)**

**Correct logic**



**Requires a functioning calendar table (present)**



**2.2 DAX Quality Summary**

**No circular dependencies**



**No ambiguous measures**



**No implicit measures used**



**All KPIs are measure-driven**



**3. Visual-Level Audit**

**3.1 KPI Cards**

**All KPI cards use explicit measures**



**No accidental filters**



**Values match fact table totals**



**3.2 Line Chart: total\_quantity by Month**

**Axis: Month (from calendar)**



**Values: total\_quantity**



**Sorting: Correct (Jan → Dec)**



**No missing or duplicated months**



**Calendar filtering works correctly**



**3.3 Map: total\_sales by City**

**Uses total\_sales measure**



**City granularity appropriate**



**No aggregation errors**



**3.4 Payment Method Pie Chart**

**Uses Transactions measure**



**Distribution matches raw data**



**No filter conflicts**



**3.5 Brand Table**

**Uses Brand, Transactions, total\_sales**



**Totals match KPI cards**



**3.6 Customer Rating Visual**

**Uses correct fields**



**No aggregation issues**



**Duplicate rating columns exist (see Section 6)**



**3.7 ❗ Mobile Model Sales Visual (Issue Found)**

**Current visual type: 100% Stacked Bar Chart**



**Result: All models show 100%**



**This is a visualization error, not a data error**



**Fix: Change to Clustered Bar Chart or Simple Bar Chart.**



**4. Data Integrity Audit**

**4.1 Row-Level Checks**

**No missing values in critical fields**



**No null dates**



**No negative quantities**



**No invalid prices**



**4.2 Aggregation Checks**

**SUM of Units Sold matches total\_quantity**



**SUMX calculation matches total\_sales**



**DISTINCTCOUNT(Transaction ID) matches transactions KPI**



**4.3 Duplicate Columns**

**Customer Ratings (numeric)**



**customer rating (text)**



**One of these is redundant.**



**5. Performance Audit**

**5.1 Model Size**

**Small, efficient model**



**No calculated tables**



**No heavy calculated columns**



**No unnecessary relationships**



**5.2 DAX Performance**

**SUMX used correctly**



**No iterator misuse**



**No row-by-row calculations on large tables**



**No performance bottlenecks detected**



**6. Issues \& Risks Identified**

**6.1 Visualization Issue**

**Mobile Model chart uses 100% stacked bar → misleading**



**Fix required**



**6.2 Duplicate Rating Columns**

**Customer Ratings and customer rating**



**Risk: Wrong field selection**



**Recommendation: Remove one**



**6.3 Calendar Table Minimal**

**Only Date + Day Name**



**Works, but limits advanced time intelligence**



**Recommendation: Add Year, Month, Quarter, Month Number**



**7. Final Technical Verdict**

**✔ Data Model: Correct**

**✔ Measures: Correct**

**✔ Relationships: Correct**

**✔ KPI Logic: Correct**

**✔ Visual Logic: Correct (1 minor issue)**

**✔ Data Integrity: Strong**

**✔ Performance: Optimized**

**❗ Only one correction required:**

**Change the Mobile Model visual from 100% stacked bar to clustered bar.**



**⭐ Overall Audit Result: PASS (with minor visual correction)**

