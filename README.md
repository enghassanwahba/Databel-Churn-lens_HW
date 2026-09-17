# 📊 Databel Churn Lens
### *Developed by Hassan Wahba*

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

6. Business Analytics Checklist
Before pushing changes to production or publishing to Power BI Service, complete the following data integrity verification checks:

1.Confirm cross-filtering interactions (Edit Interactions) between Churn Category and Top 10 Reasons render accurate synchronized subsets.

2.Verify that all currency fields map directly to Fixed Decimal numeric data types to eliminate round-off calculation drift.

3.Ensure any added slicer automatically triggers a re-evaluation of the Churn Rate gauge to preserve true dynamic slicing capability.
----
