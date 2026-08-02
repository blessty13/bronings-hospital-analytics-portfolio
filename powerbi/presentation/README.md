# Bronings University Hospital Analytics Dashboard (Power BI)

## Project Overview

This project showcases my ability to design and develop an end-to-end healthcare analytics solution using Microsoft Power BI and Snowflake. The objective was to transform raw hospital operational data into interactive dashboards that provide meaningful insights for executive decision-making.

Working with datasets covering inpatient admissions, outpatient appointments, emergency department attendances, theatre utilisation, workforce staffing and financial performance, I created a suite of dashboards that monitor key NHS operational metrics. The solution combines data modelling, DAX calculations and interactive visualisations to help identify trends, monitor performance against national targets and support strategic planning.

To deliver the solution, I connected Power BI to a Snowflake cloud data warehouse, created calculated measures using DAX, designed six interactive dashboard pages and implemented forecasting to predict future outpatient demand. The final dashboard enables stakeholders to monitor patient flow, hospital capacity, workforce performance and financial position through a single business intelligence solution.

This project demonstrates my skills in business intelligence, data modelling, DAX development, dashboard design and communicating data-driven insights to support operational and strategic decision-making.

## Snowflake Integration

To create a scalable and realistic business intelligence solution, I connected Power BI directly to a Snowflake cloud data warehouse rather than importing static files. Using the native Snowflake connector, I established a live connection to the hospital datasets and imported the required tables into Power BI for modelling and analysis.

The datasets included operational information across multiple hospital departments, including:

- Inpatient Admissions
- Outpatient Appointments
- Emergency Department Attendances
- Theatre Utilisation
- Workforce Staffing

After loading the data into Power BI, I validated data types, created relationships between the tables and organised all calculated measures within a dedicated Measures table. This provided a structured data model that supported accurate KPI calculations and interactive cross-filtering throughout the dashboards.

By Snowflake as the data source, it reflects how organisations manage and analyse large volumes of healthcare data within modern cloud-based analytics environments.

# Dashboard Pages

To present the data in a way that was easy to understand, I designed six interactive dashboard pages in Power BI. Each dashboard focuses on a different area of hospital performance, allowing users to monitor KPIs, identify trends and explore the data using interactive filters and visualisations.

---

## Dashboard 1 – Executive Summary

The Executive Summary dashboard provides a high-level overview of the hospital's overall performance by bringing together the most important KPIs into one place. This allows users to quickly understand how the organisation is performing before exploring the more detailed dashboards.

### What I included

- RTT Compliance: **41.98%**
- Occupancy: *Unavailable (blank due to dataset limitations)*
- Agency Spend: **16.57%**
- Theatre Utilisation: **70.75%**
- Readmission Rate: **8.95%**
- Average Length of Stay (ALOS): **3.86 days**
- RAG Status: **Red**

### Why I built it

I wanted this page to act as the landing page of the report, giving executives a quick snapshot of hospital performance and immediately highlighting areas that require attention.

---

## Dashboard 2 – Emergency Department

This dashboard focuses on Emergency Department activity and patient flow, helping users understand demand, patient presentations and waiting times.

### What I included

- Attendances by Triage Category
- Attendances by Chief Complaint
- Four-Hour Breach Trend
- Average Emergency Department Time: **183.54 minutes**

### Key insights

- The most common chief complaint recorded was **Seizure**, followed by **Vomiting** and **Abdominal Pain**.
- Most patients were triaged within **Category 3 and Category 4**, indicating that the majority of attendances were urgent rather than immediately life-threatening.

### Why I built it

I built this dashboard to monitor emergency demand, identify common patient presentations and track Emergency Department performance over time.

---

## Dashboard 3 – Outpatient Waiting

This dashboard focuses on outpatient services by analysing waiting times, referral performance and appointment attendance.

### What I included

- Average Waiting Days Trend
- RTT Status Breakdown
- Attendance Status Breakdown
- DNA Rate: **13.15%**
- Rolling 12-Week Average Waiting Time: **81 days**
- RTT Compliance: **41.98%**
- 12-week Waiting List Forecast

### Key insights

- Nearly **80%** of referrals were closed, while a smaller proportion remained open.
- The majority of appointments were attended successfully, although **13.15%** resulted in a Did Not Attend (DNA).
- RTT Compliance of **41.98%** is well below the NHS target of **92%**, highlighting delays within outpatient services.

### Why I built it

I wanted users to monitor waiting times, appointment attendance and RTT performance while using forecasting to better understand future demand.

---

## Dashboard 4 – Capacity

The Capacity dashboard focuses on inpatient admissions and hospital bed usage to support operational planning.

### What I included

- Cumulative Admissions Trend
- Admissions by Admission Type
- Average Length of Stay by Ward
- Admission Date Slicer
- Average Length of Stay: **3.86 days**
- Cumulative Admissions: **1K**
- Occupancy %

### Key insights

- Emergency admissions account for the highest number of inpatient episodes.
- The running total shows admissions increasing steadily over time.
- Average Length of Stay varies across hospital wards, helping identify areas where patient flow could potentially be improved.

### Why I built it

I built this dashboard to understand hospital capacity, monitor admission trends and support better bed management.

---

## Dashboard 5 – Finance

The Finance dashboard combines operational data with estimated financial measures to highlight where resources are being used and where costs could potentially be reduced.

### What I included

- Agency Spend by Ward
- Theatre Sessions Used vs Sessions Available
- Agency Shift Trend
- Agency Spend: **£99K**
- HRG Revenue at Risk: *Unavailable*
- Theatre Waste: **£477K**
- Theatre Utilisation: **70.75%**

### Key insights

- Ward **W-05** recorded the highest agency spend.
- Theatre utilisation was **70.75%**, indicating unused theatre capacity.
- Estimated theatre waste totalled **£477K**, highlighting a significant opportunity to improve operational efficiency.

### Why I built it

I wanted this dashboard to demonstrate how operational performance directly impacts financial performance and identify areas where costs could be reduced.

---

## Dashboard 6 – Workforce

The Workforce dashboard focuses on staffing activity and workforce planning across the hospital.

### What I included

- Agency Shifts by Ward
- Agency Shift Trend
- Hours Worked by Staff Grade
- Shift Type Distribution
- Agency Spend: **16.57%**
- Agency Shifts: **256**
- Hours Worked: **15.87K**
- Overtime Hours: **138.70**

### Key insights

- Ward **W-05** recorded the highest number of agency shifts.
- Nurses worked the highest number of hours compared to all other staff grades.
- Day shifts represented the largest proportion of all recorded shifts.
- Agency staffing accounted for **16.57%** of workforce activity.

### Why I built it

I built this dashboard to understand staffing patterns, monitor reliance on agency workers and support workforce planning across different hospital departments.

# DAX Measures

One of the main objectives of this project was to create custom DAX measures that transformed raw hospital data into meaningful KPIs. Rather than relying on existing columns, I built a dedicated **Measures** table to store all calculations and keep the data model organised.

Using DAX allowed me to calculate key NHS performance metrics, monitor trends over time and create dynamic measures that update automatically as users interact with the dashboards.

To build these measures, I used a combination of DAX functions including **CALCULATE**, **FILTER**, **COUNTROWS**, **DIVIDE**, **AVERAGEX**, **DATESINPERIOD**, **LASTDATE** and **IF**. These functions enabled me to calculate percentages, running totals, rolling averages and conditional KPI indicators across multiple hospital datasets.

The measures I created were then used throughout the six dashboard pages to power KPI cards, charts, trend analysis and executive scorecards.

| DAX Measure | How I Built It | Business Purpose |
|-------------|----------------|------------------|
| **Cumulative Admissions** | Created using `CALCULATE()` and `FILTER()` to calculate a running total of inpatient admissions over time. | Tracks admission trends and overall hospital demand. |
| **Rolling 12Wk Avg Wait** | Used `AVERAGEX()`, `DATESINPERIOD()` and `LASTDATE()` to calculate a rolling 12-week average waiting time. | Smooths short-term fluctuations and highlights long-term waiting time trends. |
| **YTD Variance** | Calculated by subtracting Budget YTD from Actual Spend YTD using DAX measures. | Monitors financial performance against budget. |
| **Occupancy %** | Used `COUNTROWS()`, `FILTER()` and `DIVIDE()` to calculate occupied beds as a percentage of total available beds. | Measures hospital bed utilisation and capacity. |
| **DNA Rate %** | Used `COUNTROWS()` and `DIVIDE()` to calculate the percentage of outpatient appointments where patients did not attend. | Helps identify appointment attendance issues and potential efficiency improvements. |
| **Readmission Rate %** | Calculated using `COUNTROWS()`, `FILTER()` and `DIVIDE()` to identify the percentage of patients who returned after discharge. | Measures quality of care and patient outcomes. |
| **Theatre Util %** | Used `SUM()` and `DIVIDE()` to compare theatre sessions used against sessions available. | Evaluates how efficiently operating theatres are being utilised. |
| **RTT Compliance %** | Used `FILTER()`, `COUNTROWS()` and `DIVIDE()` to calculate the percentage of patients meeting the NHS 18-week RTT target. | Tracks compliance with national waiting time standards. |
| **Average Length of Stay (ALOS)** | Used `AVERAGEX()` to calculate the average number of days patients stayed in hospital. | Supports capacity planning and patient flow analysis. |
| **RAG Status** | Built using nested `IF()` statements to categorise RTT performance as Green, Amber or Red. | Provides an easy-to-read performance indicator for executives. |
| **Agency Spend %** | Used `COUNTROWS()`, `FILTER()` and `DIVIDE()` to calculate the proportion of agency staff within the workforce. | Monitors reliance on temporary staffing. |
| **Waiting List Forecast** | Applied Power BI's Analytics Forecast feature to the waiting list trend line using a 12-period forecast. | Predicts future outpatient demand and supports service planning. |

### Key DAX Skills Demonstrated

- Created running totals and rolling averages.
- Built dynamic percentage-based KPIs.
- Applied time intelligence functions for trend analysis.
- Used conditional logic to create RAG performance indicators.
- Organised all calculations within a dedicated Measures table.
- Integrated DAX measures across multiple dashboards to provide consistent reporting and interactive analysis.

# Business Questions & Key Findings

The purpose of this dashboard was not only to visualise hospital data but also to answer key business questions that support operational and strategic decision-making.

| Business Question | Key Finding |
|-------------------|-------------|
| Is the hospital meeting the NHS RTT target? | RTT Compliance was **41.98%**, significantly below the 92% target, indicating delays in outpatient treatment pathways. |
| Are patients attending their outpatient appointments? | The DNA Rate was **13.15%**, showing that missed appointments continue to impact service efficiency. |
| How effectively is hospital capacity being managed? | Average Length of Stay was **3.86 days**, while cumulative admissions continued to increase, highlighting growing pressure on inpatient capacity. |
| Are operating theatres being fully utilised? | Theatre Utilisation was **70.75%**, with an estimated **£477K** in theatre waste, suggesting opportunities to improve scheduling and resource utilisation. |
| How much does the hospital rely on agency staff? | Agency staff accounted for **16.57%** of the workforce, with Ward **W-05** recording the highest agency usage. |
| What are the main financial pressures? | Agency Spend reached **£99K**, demonstrating the financial impact of temporary staffing and operational inefficiencies. |

## Key Takeaways

Through this project, I was able to transform raw healthcare data into meaningful business insights using Power BI. By combining DAX calculations, interactive dashboards and data visualisation techniques, I created a reporting solution that allows stakeholders to monitor operational performance, identify trends and make more informed decisions across the hospital.



