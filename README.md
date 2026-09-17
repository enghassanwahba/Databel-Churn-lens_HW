# 📊 Databel Churn Lens
### *Developed by Hassan Wahba*

## 📝 Project Description
Interactive Power BI dashboard for **Databel** Telecom, focused on customer churn analysis. It tracks churn rates, identifies top retention risks (such as competitor threats and support issues), and provides data-driven insights to minimize revenue loss.
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

## 📂 Data Model Columns Applied
The dashboard architectures map directly to the `Databel - Data` schema using the following operational columns:
* **Churn Logs**: `Churn Label`, `Churn Category`, `Churn Reason`
* **Account Financials**: `Account Length (in months)`, `Monthly Charge`, `Total Charges`, `Contract Type`
* **Usage Metrics**: `Avg Monthly GB Download`, `Unlimited Data Plan`, `Intl Plan`
* **Demographics & Care**: `Customer Service Calls`, `Age`, `Gender`, `Senior`, `Under 30`

## 💡 Key Core DAX Measures
The metrics rendered on the report canvas are powered by these scalable DAX calculations:

### 1. Total Churned Customers Count
```dax
Churned = CALCULATE(COUNT('Databel - Data'[Customer ID]), 'Databel - Data'[Churn Label] = "Yes")
```

### 2. Canvas Performance Optimization Query (Top 10 Reasons Logic)
The visual engine utilizes centralized query blocks to isolate high-impact business bottlenecks directly on the dashboard layout:
```dax
DEFINE
    VAR __SQDS0Core = 
        SUMMARIZECOLUMNS('Databel - Data'[Churn Reason], "Churned", '_Measures'[Churned])
    VAR __SQDS0BodyLimited = 
        TOPN(10, __SQDS0Core, [Churned], 0)
```

## 💻 How to Run and Refresh
1. Clone this repository or download the `.pbix` dashboard file.
2. Launch the project inside **Power BI Desktop**.
3. To re-link the database trail: Navigate to the Home Ribbon -> `Transform Data` -> `Data Source Settings`.
4. Click `Change Source`, map the dataset directory to the local folder path on your machine, then click `Close & Apply`.
5. Select `Refresh` from the top navigation to load the synchronized metrics onto the interactive dashboard.
٦.
