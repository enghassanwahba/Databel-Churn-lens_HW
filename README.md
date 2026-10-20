# 📊 Databel Customer Churn Lens analysis
### *Developed by Hassan Wahba*

An end-to-end **Power BI Business Intelligence project** focused on analyzing and mitigating customer attrition (churn) for **DATABEL**, a leading telecom provider. 

This dashboard transforms raw operational data into actionable strategic insights, enabling retention teams to target high-risk customer segments effectively.

---

## 📝 Project Description
Interactive Power BI dashboard for **Databel** Telecom, focused on customer churn analysis. It tracks churn rates, identifies top retention risks (such as competitor threats and support issues), and provides data-driven insights to minimize revenue loss.
---
KPI Metric Name	Current Value	Operational Significance
Total Customers	6,687	Total active and churned customer base ingested into the model.
Total Charges	$7M	Cumulative gross financial billing volume across entire lifecycle.
Active Customers	4,891	Currently preserved base yielding active operational recurring revenue.
Churned Customers	1,796	Subscribers lost to competitors or churned due to dissatisfaction.
---
<img width="1457" height="901" alt="Databel-Churn-Lens_HW" src="https://github.com/user-attachments/assets/939ca75e-a1bc-468a-b37b-19ff0bc7c734" />

---
## 🎯 Project Overview & Key KPI Summary
* **Total Customer Base:** 6,687 customers analyzed.
* **Financial Footprint:** \$7M in total charges.
* **Retention Breakdown:** 4,891 Active users vs. 1,796 Churned users.
* **Critical Baseline:** Global Churn Rate stands at **26.86%**.

---

## 🛠️ Step-by-Step Development Process in Power BI

### Phase 1: Data ETL & Transformation (Power Query)
* **Data Ingestion:** Imported the raw Databel telecom dataset into Power BI Desktop.
* **Data Cleaning & Profiling:** 
  * Checked column quality, ensuring no missing values or duplicates in the unique `Customer ID` primary key.
  * Replaced binary/text flags (`Yes`/`No`) with strict logical types to optimize data compression.
* **Unpivoting & Categorization:** Standardized the churn reason categories to maintain clean textual hierarchies.

### Phase 2: Data Modeling & Star Schema
* **Star Schema Architecture:** Separated the flat dataset into a clean relational model.
  * Created a central **Fact Table** for transactional metrics (Charges, Churn Flags, Tenure Months).
  * Established **Dimension Tables** for `Geography (States)`, `Demographics`, and `Contract/Plan Types`.
* **Relationships:** Defined Active `1:Many (1->*)` relationships between Dimension tables and the Fact table using `Customer ID` and `State Code` as surrogate keys.

### Phase 3: Advanced Analytics & DAX Calculations
Engineered key performance indicators using robust **DAX (Data Analysis Expressions)** measures to maintain dynamic recalculations across filters:

* **Total Customers:**
  ```dax
  Total Customers = DISTINCTCOUNT('Databel Fact'[Customer ID])
  ```
* **Churned Customers:**
  ```dax
  Churned Customers = CALCULATE([Total Customers], 'Databel Fact'[Churn Label] = "Yes")
  ```
* **Dynamic Churn Rate (%):**
  ```dax
  Churn Rate = DIVIDE([Churned Customers], [Total Customers], 0)
  ```

### Phase 4: UI/UX & Dashboard Design Elements
* **Theme & Canvas Layout:** Adopted a custom visual strategy using a high-contrast **Premium Dark Mode Theme** (Charcoal `#1E1E24` background with Crimson Red `#E63946` structural accents) to reduce visual fatigue and highlight key risks.
* **Custom Layout Grid:** Built a structured skeleton layout inside Figma/Canva and imported it as a background canvas to keep pixel-perfect container alignments.

---
4. Dashboard Canvas Layout Mapping
The front-facing visual interface is architected utilizing a structured dark theme canvas, optimizing data density and prioritizing visual tracking:

Top Panel: Executive KPI Summary Block
Renders standalone large KPI cards displaying 'Total Customers (6,687)', 'Total Charges ($7M)', 'Active (4,891)', and 'Churned (1,796)'
to give an immediate high-level business pulse upon landing.

Left Control Panel: Global Slicers
Features quick-filter containers mapping across State, Gender, and Customer Group to instantly slice the entire analytical canvas down to localized segments.

Central Analysis Grid: Root Causes & Behavioral Profiling
Provides a side-by-side diagnostic breakdown of why and how customers are leaving:

• Top 10 Churn Reason Visual:A Horizontal Bar Chart using a Top N Filter (10) to prioritize high-impact issues. It reveals that 'Competitor made better offer' (311 cases) and 'Competitor had better devices' (297 cases) are the primary churn drivers.

• Churn Rate by Customer Service Calls:A Bar-and-Line combo chart showing a sharp upward spike in churn probability for clients interacting with customer support multiple times.

• Churn Rate by Contract Type Visual:A Horizontal Bar Chart segmenting churn counts across different contractual tiers, indicating that Month-to-Month contracts carry an extremely high churn risk (47%) compared to longer commitments.

• Churn Rate by State Map:An interactive map visual isolating geographic clusters to discover macro-regional service degradation.
## 🔍 Detailed Visualization Breakdown

1. **Executive Scorecard (Top Ribbon):** Cards instantly displaying `Total Customers`, `Total Charges`, `Active Customers`, and `Churned` counts for top-level stakeholders.
2. **Geographical Mapping (Middle Center):** A native **Power BI Shape Map** displaying *Churn Rate by State*, helping territory managers isolate regional performance dips across the United States.
3. **Pareto-Driven Attrition Reasons (Top Center):** A horizontal bar chart identifying the Top 10 Churn Reasons. **Competitor making better offers** stands out significantly as the primary churn catalyst (805 customers).
4. **Contract & Tenure Deep-Dive (Bottom Left):** A column chart illustrating Churn Rate against contract types. It reveals a critical operational vulnerability: **Month-to-Month contracts yield a staggering 47% churn rate**, which drops drastically once a customer signs a 1 or 2-year commitment.
5. **Group Dynamics (Right Column):** An analysis correlating monthly charges against customer group sizing, highlighting how bulk/family account structures affect billing margins and lifetime loyalty.
6. **Slicer Panel (Left Sidebar):** Multi-select interactive slicers for `State`, `Gender`, and `Group` enabling cross-filtering across every single visual component on the page dynamically.

---

## 💡 Strategic Business Recommendations
Based on the dashboard insights, the following data-driven strategies are recommended for DATABEL:
* **Competitor Match Campaign:** Since competitors offering better deals is the #1 churn driver, launch a proactive matching offer targeted at customers nearing the end of their contract cycles.
* **Month-to-Month Conversion Incentive:** Introduce financial discounts or loyalty points to incentivize Month-to-Month users to transition into structured 1-Year or 2-Year contracts.

---

## 🚀 Key Features
* **Subscriber Status Tracking**: Dynamic monitoring of active subscribers vs. churned customers across the Databel network.
* **Root Cause Diagnostics (Top 10 Churn Reasons)**: Advanced visual profiling isolating the top 10 specific triggers causing customer attrition (e.g., competitor promotions, technical support gaps).
* **Contract & Plan Risk Assessment**: Dissection of churn percentages across contract types (`Month-to-Month`, `One Year`, `Two Year`) to pinpoint fragile client segments.
* **Customer Service Calls Analytics**: Behavioral analysis correlating support interactions with churn rates to evaluate service quality.
* **Demographic Breakdown**: Profiling churn patterns by distinct segments such as age groups (`Under 30`, `Senior`) and gender.

## 🛠️ Tech Stack & Tools
* **Power BI Desktop**: Data modeling, advanced DAX engineering, and report canvas layout design.
* **Excel / Power Query**: Data source ingestion, text transformations, and handling missing values in churn logs.
* **DAX (Data Analysis Expressions)**: Used to write resilient, scalable business calculations and key performance metrics.

## 💡 Key Core DAX Measures
The metrics rendered on the report canvas are powered by these scalable DAX calculations:

Measure 1: Total Customers. Account for the total number of customers
Total Customers = COUNT('Databel - Data'[Customer ID])

Measure 2: Churned .Account for the total number of customers lost by using Filter Column 
Churn Label=”YES”
Churned = CALCULATE([Total Customers],FILTER('Databel - Data','Databel - Data',
'Databel - Data'[Churn Label]="YES"))

Measure 3: Active Customers .Account for the total number of Active customers by using Filter Column Churn Label= “NO”
Active Customers= CALCULATE([Total Customers],FILTER('Databel - Data','Databel - Data',
'Databel - Data'[Churn Label]="NO"))

Measure 4: Churn Percentage Rate. Determine the general proportional rate of loss against the historical base:
Churn Rate = 
[Churned]/[Total Customers]

Measure 5: Total Chages. Determine the Total Charges of all Customers.
Total Charges = 
SUM('Databel - Data'[Total Charges])

---



----
