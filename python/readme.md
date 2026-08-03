# Bronings Hospital Analytics – Python Automation

## Project Overview

This project demonstrates how I used Python to automate a manual NHS waiting list exception reporting process for Bronings University Hospital Group.

Using **Python**, **pandas**, and **NumPy**, I developed an automation workflow that loads, cleans, validates, and analyses outpatient appointment data before generating a formatted Excel report for operational teams.

The notebook automates key reporting tasks, including calculating DNA (Did Not Attend) rates by specialty, identifying RTT (Referral to Treatment) breaches, generating a Data Quality (DQ) Score, and exporting the results into a structured Excel workbook.

By replacing a manual reporting process with an automated solution, this project demonstrates how Python can improve reporting efficiency, reduce manual effort, and produce consistent, auditable outputs for healthcare analytics.

---

## Skills Demonstrated

- Python
- pandas
- NumPy
- Data Cleaning and Validation
- Data Quality Assessment
- Data Analysis
- Data Automation
- Exception Reporting
- Excel Report Generation
- Healthcare Analytics
- Workflow Automation
- KPI Reporting

---

## Business Problem

At Bronings University Hospital Group, the weekly waiting list exception report was produced manually using outpatient appointment data.

The reporting process required an analyst to extract the data, identify duplicate and missing records, calculate DNA (Did Not Attend) rates by specialty, identify RTT (Referral to Treatment) breaches, assess data quality, and manually compile the results into an Excel report for operational teams.

This manual workflow was repetitive, time-consuming, and susceptible to human error. It also created inconsistencies in reporting and reduced the time available for analysts to focus on higher-value activities such as identifying performance trends and supporting operational decision-making.

To improve efficiency and reporting reliability, the reporting process needed to be automated using Python.

---

## Solution

To automate the weekly waiting list exception reporting process, I developed an end-to-end Python workflow using **pandas** and **NumPy**.

The notebook imports outpatient appointment data, performs data cleaning and validation, calculates key NHS performance indicators, generates a Data Quality (DQ) Score, and exports the results into a structured Excel report.

The automated workflow includes:

- Loading outpatient appointment data from a CSV file.
- Cleaning and validating the dataset by removing duplicate records, handling missing values, and converting data into appropriate formats.
- Calculating DNA (Did Not Attend) rates by specialty.
- Identifying Referral to Treatment (RTT) breaches where patients have waited more than 18 weeks.
- Generating an automated Data Quality (DQ) Score to assess dataset completeness.
- Exporting the cleaned data and summary analysis to a formatted Excel workbook for operational reporting.

By automating these tasks, the reporting process becomes faster, more reliable, and fully repeatable, reducing manual effort while providing consistent outputs that support operational decision-making.

## Key Findings

The Python automation successfully transformed the manual waiting list exception reporting process into a repeatable workflow that cleans, analyses, and exports outpatient appointment data in seconds.

Key findings from the analysis include:

- **RTT Breach Count:** The notebook identified **109** patients who had exceeded the NHS Referral to Treatment (RTT) standard of **18 weeks**, highlighting cases that require operational attention.

- **Data Quality Score:** The automated data quality assessment returned a score of **95.48%**, indicating that the outpatient appointments dataset was highly complete and suitable for reporting and analysis.

- **DNA Rate by Specialty:** The notebook calculated DNA rates for each clinical specialty, allowing performance to be compared across departments. The analysis showed that:
  - **OR** recorded the highest DNA rate at **36.17%**.
  - **URO** recorded a DNA rate of **18.97%**.
  - **OPH** recorded a DNA rate of **16.39%**.
  - **EM** and **GEN** recorded **0.00%**, indicating no missed appointments within the analysed dataset.

- **Automated Excel Reporting:** The workflow successfully exported both the cleaned dataset and the DNA summary into a structured Excel workbook, providing an immediately usable report for operational teams without requiring any manual formatting or copying.

Overall, the notebook demonstrates how Python can automate routine NHS reporting tasks, improve consistency, reduce manual effort, and produce reliable outputs that support operational decision-making.

## Summary

This project demonstrates how Python can be used to automate routine NHS operational reporting by replacing manual spreadsheet-based processes with a repeatable and auditable workflow.

Using **pandas** and **NumPy**, I developed a Python notebook that loads and cleans outpatient appointment data, calculates key operational metrics, measures data quality, and exports the results into a structured Excel report. The automation identified **109 RTT breaches**, calculated DNA rates across multiple specialties, achieved a **95.48% Data Quality Score**, and generated a reusable report that can be produced consistently with minimal manual intervention.

This project strengthened my practical experience with Python for healthcare analytics while demonstrating how automation can improve reporting accuracy, reduce manual effort, and support evidence-based decision-making within NHS organisations.

