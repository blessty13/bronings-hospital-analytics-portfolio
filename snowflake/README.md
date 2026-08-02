# Bronings Hospital Analytics – Snowflake Data Warehouse

## Project Overview

As part of my healthcare analytics portfolio, I built a cloud-based data warehouse in Snowflake to centralise hospital operational data. Instead of relying on local CSV files, I imported multiple healthcare datasets into Snowflake and used them as the single source of truth for my analytics solution.

After loading and validating the data, I connected the Snowflake warehouse directly to both Power BI and Tableau to build interactive dashboards. This project demonstrates my ability to work with modern cloud data platforms, integrate business intelligence tools, and build scalable analytics solutions using real-world healthcare data.

## Project Objectives

The primary objective of this project was to build a cloud-based healthcare data warehouse using Snowflake and use it as the central data source for business intelligence reporting.

During this project I:

- Created a cloud data warehouse using Snowflake.
- Imported and organised multiple hospital datasets into a structured database.
- Stored data within a centralised PUBLIC schema.
- Validated imported data to ensure successful loading and accurate table structures.
- Connected Snowflake directly to Power BI for dashboard development.
- Connected Snowflake directly to Tableau for interactive visualisations.
- Demonstrated an end-to-end cloud analytics workflow from data storage to business intelligence reporting.

- ## Dataset Overview

The Snowflake data warehouse stores operational data for a simulated NHS hospital. Each table represents a different area of hospital performance and serves as the foundation for the SQL analysis and business intelligence dashboards built in Power BI and Tableau.

| Table | Description |
|--------|-------------|
| **ED_ATTENDANCES** | Records emergency department attendances, including arrival times, triage categories, chief complaints and four-hour breach status. |
| **INPATIENT** | Contains inpatient admission data, including admission type, length of stay, discharge details and readmission status. |
| **OUTPATIENT** | Stores outpatient appointment information, including waiting days, RTT status, attendance status and clinic details. |
| **THEATRE_UTILISATION** | Captures theatre activity, including sessions available, sessions used, cancellations and completed procedures. |
| **WORKFORCE_STAFFING** | Contains workforce data including staff grades, hours worked, overtime, agency usage and ward allocation. |

## Snowflake Environment

To build a scalable cloud-based analytics solution, I created a dedicated Snowflake environment to store and manage the hospital datasets. Using Snowflake as the central data warehouse allowed me to keep all operational data in one location before connecting it to Power BI and Tableau for reporting and dashboard development.

### Database

**BRONINGS_HOSPITAL**

### Schema

**PUBLIC**

### Operational Tables

- ED_ATTENDANCES
- INPATIENT
- OUTPATIENT
- THEATRE_UTILISATION
- WORKFORCE_STAFFING

### Business Intelligence Integration

Once the datasets were loaded into Snowflake, I connected the database directly to:

- Microsoft Power BI
- Tableau Desktop

This enabled both reporting tools to access the same cloud-hosted datasets, creating a consistent and scalable workflow for data analysis and dashboard development.

## Implementation Process

To build the Snowflake data warehouse, I followed a structured workflow that transformed raw hospital datasets into a cloud-based data source ready for analysis in Power BI and Tableau.

### Step 1 – Created the Database

I created a dedicated Snowflake database named **BRONINGS_HOSPITAL** to store all hospital operational data. This provided a central location for managing the datasets used throughout the project.

### Step 2 – Organised the Data

Within the **PUBLIC** schema, I created separate tables for each hospital dataset:

- ED_ATTENDANCES
- INPATIENT
- OUTPATIENT
- THEATRE_UTILISATION
- WORKFORCE_STAFFING

Organising the data into separate tables made it easier to manage, query and connect to business intelligence tools.

### Step 3 – Imported the Data

I imported each CSV dataset into its corresponding Snowflake table using Snowflake's data loading functionality. After loading the data, I verified that each table had imported successfully and that all columns and records were available for analysis.

### Step 4 – Validated the Data

Before connecting the warehouse to my reporting tools, I reviewed each table to ensure the data had loaded correctly. This included checking the column structure, confirming the expected records were present and previewing the imported data.

### Step 5 – Connected Business Intelligence Tools

With the data successfully stored in Snowflake, I connected the warehouse directly to both Power BI and Tableau using their native Snowflake connectors. This allowed me to build interactive dashboards from a central cloud data source rather than relying on local files.

### Outcome

The completed Snowflake data warehouse became the foundation for the rest of the project, providing a scalable and centralised data source for SQL analysis, Power BI dashboards and Tableau visualisations.

## Technical Skills Demonstrated

Throughout this project, I applied a range of cloud data warehousing and business intelligence skills to build a scalable analytics solution using Snowflake.

### Cloud Data Warehousing

- Created and managed a cloud-based Snowflake database.
- Organised datasets using databases and schemas.
- Imported multiple healthcare datasets into Snowflake.
- Validated data after loading to ensure accuracy and completeness.

### Data Management

- Managed multiple operational datasets within a single data warehouse.
- Structured data to support reporting and analytics.
- Verified table structures and data quality before analysis.

### Business Intelligence Integration

- Connected Snowflake directly to Power BI.
- Connected Snowflake directly to Tableau.
- Used Snowflake as the central data source for dashboard development.

### Analytics Workflow

- Centralised hospital operational data within a cloud environment.
- Prepared datasets for reporting and visualisation.
- Supported end-to-end analytics from data storage through to executive dashboards.

## Key Skills

- Snowflake
- Cloud Data Warehousing
- Data Management
- Data Integration
- Power BI
- Tableau
- Data Validation
- Business Intelligence
- Healthcare Analytics
