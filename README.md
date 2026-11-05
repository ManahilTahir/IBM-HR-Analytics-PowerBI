# IBM HR Employee Attrition & Performance Dashboard 📊

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=power-bi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Analytics-blue?style=for-the-badge)
![Data Analysis](https://img.shields.io/badge/HR_Analytics-Data_Visualization-green?style=for-the-badge)

## 📌 Executive Summary
This end-to-end Power BI analytics project transforms raw HR data (1,470 records) into an executive-level interactive reporting interface. The primary objective is to analyze key drivers of employee turnover, evaluate risk across demographic groups and job roles, and surface actionable insights for executive leadership.

---

## 🖼️ Dashboard Preview

![IBM HR Dashboard](Screenshots/dashboard_preview.png)

---

## 🔑 Key Core Metrics (KPIs)
* **Total Employees:** 1,470
* **Attrition Count:** 237 employees
* **Attrition Rate:** 16.1%
* **Average Monthly Income:** $6,503

---

## 💡 Key Business Insights
1. **High-Risk Job Roles:** **Sales Representatives** exhibit the highest attrition rate (~40%), followed by **Laboratory Technicians** (~24%) and **Human Resources** (~23%).
2. **Age Demographic Vulnerability:** Employee turnover heavily concentrates in early career stages. The **26–35 age group** accounts for the highest volume of attrition (116 employees lost), followed by the **18–25 age group**.
3. **Departmental Breakdown:** While Research & Development holds the largest headcount, the **Sales Department** experiences disproportionately higher percentage turnover relative to team size.

---

## 🛠️ Technical Data Pipeline & Modeling

### 1. Data Cleaning & Transformation (Power Query)
* **Age Group Categorization:** Created conditional age buckets (`18-25`, `26-35`, `36-45`, `46-55`, `>55`).
* **Chronological Sorting Logic:** Built a custom numerical index column (`AgeGroupSortOrder` from `1` to `5`) to ensure true chronological left-to-right sorting across all visual charts.

### 2. Core DAX Calculations
```dax
// Total Employee Count
Total Employees = COUNTROWS('WA_Fn-UseC_-HR-Employee-Attrition-Data')

// Total Attrition Count
Attrition Count = 
CALCULATE(
    COUNTROWS('WA_Fn-UseC_-HR-Employee-Attrition-Data'),
    'WA_Fn-UseC_-HR-Employee-Attrition-Data'[Attrition] = "Yes"
)

// Attrition Percentage
Attrition Rate = DIVIDE([Attrition Count], [Total Employees], 0)
