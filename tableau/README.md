# Bronings Hospital Analytics | Tableau Dashboard

## Project Overview

This project showcases my Tableau skills by transforming raw NHS operational data into interactive dashboards that support executive decision-making across Bronings Hospital.

Using Tableau Desktop connected to Snowflake, I designed six dashboards that monitor key hospital performance indicators across Emergency Care, Outpatients, Capacity, Finance and Workforce. The aim of the project was to turn complex healthcare data into clear visual insights that help identify operational challenges, monitor performance against NHS targets and support data-driven decisions.

Throughout the project I focused on building dashboards that were interactive, easy to navigate and suitable for senior management reporting. I also used Tableau calculations, filters, parameters and dashboard actions to create a dynamic user experience while maintaining a clean and professional layout.

## Skills Demonstrated

- Tableau Desktop
- Snowflake Cloud Data Warehouse
- Interactive Dashboard Design
- Healthcare Analytics
- Executive Reporting
- Data Visualisation
- Tableau Calculated Fields
- Dashboard Actions
- Filters & Parameters
- KPI Monitoring

# Snowflake Integration

To simulate a real-world business intelligence workflow, I connected Tableau Desktop directly to a Snowflake cloud data warehouse using Tableau's native Snowflake connector. Rather than working with standalone files, I queried the hospital datasets stored in Snowflake, demonstrating how Tableau can integrate with modern cloud-based data platforms.

After connecting to Snowflake, I imported the five core operational datasets required for the project:

- Emergency Department Attendances
- Inpatient Admissions
- Outpatient Appointments
- Theatre Utilisation
- Workforce Staffing

Using these datasets, I created the data model within Tableau and built six interactive dashboards that analyse hospital performance across emergency care, outpatient services, capacity planning, finance and workforce management.

This workflow reflects how Tableau is commonly used in industry, where dashboards are connected to cloud-hosted data warehouses to provide scalable reporting and support data-driven decision-making.

# Dashboard 1 – Executive Summary

The Executive Summary dashboard provides a high-level overview of the hospital's key performance indicators in a single interactive view. I designed this dashboard to give hospital executives an instant snapshot of operational performance before exploring the more detailed dashboards.

### What I Built

I created KPI cards to display the hospital's most important performance measures, allowing users to quickly identify areas performing below target.

### KPIs Included

- RTT Compliance – **41.22%**
- Occupancy – **8.16%**
- Agency Spend – **16.57%**
- Theatre Utilisation – **70.75%**
- Readmission Rate – **8.95%**
- Average Length of Stay (ALOS) – **3.863 days**
- RAG Status – **Red**

### Key Finding

The Executive Summary highlights an overall **Red** performance status, primarily driven by an RTT Compliance rate of **41.22%**, which is significantly below the NHS operational target.

# Dashboard 2 – Emergency Department

The Emergency Department dashboard analyses emergency activity by monitoring patient demand, triage levels, chief complaints and Four Hour Breach performance. I designed this dashboard to help identify operational pressures within A&E.

### What I Built

I combined multiple visualisations to monitor emergency attendances, patient acuity and waiting performance while allowing users to analyse trends over time.

### Dashboard Highlights

- Average ED Time
- Triage Distribution
- Chief Complaint Analysis
- Four Hour Compliance Trend

### Key Finding

The dashboard reported an **Average Emergency Department Time of 183.5 minutes**, while the Four Hour Compliance Trend allows managers to monitor periods where breach performance begins to increase.

# Dashboard 3 – Outpatient Waiting

The Outpatient Waiting dashboard focuses on outpatient performance by monitoring waiting times, attendance behaviour and RTT compliance. I designed this dashboard to identify delays across the referral-to-treatment pathway.

### What I Built

I created interactive visualisations to analyse waiting time trends, appointment attendance and RTT performance while allowing users to filter activity by appointment date.

### Dashboard Highlights

- DNA Rate KPI
- RTT Compliance KPI
- RTT Status Breakdown
- Rolling 12 Week Average Waiting Time
- Attendance Status Distribution
- Appointment Date Filter

### Key Finding

The dashboard reported a **DNA Rate of 13.15%** alongside an **RTT Compliance rate of 41.22%**, highlighting that outpatient performance remains significantly below the NHS target of 92%.

# Dashboard 4 – Capacity

The Capacity dashboard provides insight into inpatient demand and hospital utilisation by analysing admissions, occupancy and average length of stay. I designed this dashboard to help monitor patient flow and bed capacity across the organisation.

### What I Built

I developed visualisations that monitor cumulative admissions, admission types and ward-level average length of stay while allowing users to analyse activity using interactive date filters.

### Dashboard Highlights

- Occupancy KPI
- Average Length of Stay (ALOS)
- Cumulative Admissions Trend
- Admissions by Admission Type
- Average Length of Stay by Ward

### Key Finding

The dashboard reported an **Average Length of Stay of 3.863 days** while cumulative admissions increased steadily over time, providing insight into overall inpatient demand and hospital capacity.

# Dashboard 5 – Finance

The Finance dashboard combines operational and financial metrics to estimate the financial impact of hospital activity. I designed this dashboard to identify opportunities for improving efficiency and reducing operational costs.

### What I Built

I created KPI cards alongside operational visualisations to monitor agency spending, theatre utilisation and estimated financial waste across the organisation.

### Dashboard Highlights

- Agency Spend % – **16.57%**
- HRG Revenue at Risk – **£51,800**
- Theatre Waste – **£477,000**
- Theatre Utilisation – **70.75%**
- Agency Spend by Ward
- Sessions Used vs Sessions Available
- Agency Shift Trend

### Key Finding

The dashboard estimated **£477,000 in theatre waste** together with **£51,800 of HRG revenue at risk**, highlighting significant opportunities to improve operational efficiency and reduce financial losses.

# Dashboard 6 – Workforce

The Workforce dashboard analyses staffing activity across the hospital by monitoring agency usage, staff grades, workforce hours and shift patterns. I designed this dashboard to support workforce planning and identify departments relying heavily on agency staff.

### What I Built

I developed interactive visualisations showing workforce distribution, agency trends and staffing hours while allowing users to filter activity by shift date.

### Dashboard Highlights

- Agency Spend % – **16.57%**
- Staff Grade Distribution
- Hours Worked vs Hours Rostered
- Agency Trend by Ward
- Agency Trend Over Time
- Shift Date Filter

### Key Finding

The dashboard showed an **Agency Spend rate of 16.57%**, with **Ward W-05** recording the highest agency usage, helping identify areas where permanent staffing could reduce reliance on agency workers.




