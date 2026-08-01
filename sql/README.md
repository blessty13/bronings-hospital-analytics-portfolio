# SQL Investigation – Bronings University Hospital Group

## Overview

In this phase of the Bronings Hospital Analytics Portfolio, I used T-SQL in SQL Server Management Studio (SSMS) to investigate operational performance and data quality across the hospital database.

I analysed data from the outpatient, inpatient, emergency department, theatre utilisation and workforce tables to answer key business questions that support hospital decision-making. Along the way, I also identified data quality issues that could affect reporting and KPI calculations.

To complete the investigation, I used a range of SQL techniques including joins, aggregate functions, CASE statements, window functions and common table expressions (CTEs). Each query was written to answer a specific business question and includes comments explaining the purpose of the query, any filters applied and why certain records were excluded.

## Business Questions

The investigation was designed to answer 12 business questions covering operational performance, patient pathways and data quality across the hospital.

| Query | Business Question |
|-------|-------------------|
| Query 1 | Which specialties have patients waiting more than 18 weeks (open pathways only)? |
| Query 2 | Which consultants have the highest Trust-initiated cancellation rate? |
| Query 3 | Which clinics have the highest DNA rate? |
| Query 4 | Which wards regularly have more than 10 concurrent patients? |
| Query 5 | Which specialties have the longest average waiting times for open RTT pathways? |
| Query 6 | Are there any duplicate patient records in the outpatient dataset? |
| Query 7 | Which patients have an open RTT pathway but no corresponding inpatient admission or ED attendance? |
| Query 8 | How much revenue is potentially at risk because of missing HRG codes? |
| Query 9 | Which specialties are performing better than the Trust DNA target? |
| Query 10 | Which admission types and specialties have the highest readmission counts? |
| Query 11 | Which wards have the highest agency staffing costs? |
| Query 12 | Are there any patterns in theatre cancellations by week or specialty? |

## Data Quality Findings

As part of the investigation, I checked the data for issues that could affect the accuracy of the analysis before answering the business questions.

The main data quality checks included:

- Identifying duplicate patient records using NHS Numbers.
- Checking for missing HRG codes that could impact revenue reporting.
- Excluding blank or NULL values where calculations could not be performed.
- Removing non-standard attendance status values when calculating DNA rates.
- Identifying incomplete patient pathways and missing linked records across datasets.
- Excluding test records where appropriate to ensure the analysis reflected genuine operational activity.

These checks helped improve the reliability of the results and ensured that the findings were based on consistent and valid data.

## Analytical Decisions

To make sure my analysis was accurate and consistent, I applied several business rules throughout the investigation.

These included:

- Excluding blank or NULL values where they would affect calculations or produce misleading results.
- Filtering out non-standard attendance status values when calculating DNA rates.
- Removing test records (such as **ST-99**) from workforce analysis to avoid skewing the results.
- Using the Trust's 18-week (126-day) RTT standard when identifying patients breaching waiting time targets.
- Estimating agency staffing costs using **£385 per agency shift**, as provided in the project brief.
- Estimating revenue at risk using **£1,850 per inpatient episode** with a missing HRG code.
- Adding comments throughout my SQL queries to explain the purpose of each query, filters used, and any exclusions that were applied.

These decisions helped ensure that the results were consistent, easy to understand, and aligned with the business rules provided in the project brief.

## Skills Demonstrated

Throughout this investigation, I strengthened my SQL skills by solving real-world healthcare business problems using T-SQL in SQL Server Management Studio (SSMS).

The investigation demonstrates my ability to:

- Write complex T-SQL queries
- Use joins to combine data from multiple tables
- Apply aggregate functions and GROUP BY for reporting
- Use CASE statements to create business logic
- Build Common Table Expressions (CTEs)
- Use window functions for ranking and analysis
- Identify and investigate data quality issues
- Apply business rules to produce meaningful insights
- Analyse operational healthcare data to support decision-making
- Document SQL queries with clear comments and explanations


Query 1 – RTT Breach by Specialty

Business Question:
Which specialties have patients waiting more than
18 weeks (open pathways only)?

Purpose:
I wrote this query to identify which specialties have
the highest number of patients waiting longer than the
18-week RTT target. It returns the total number of
open pathways, the number of RTT breaches and the
overall compliance percentage for each specialty.

Business Rules:
- RTT breach = Waiting_Days greater than 126 days.
- Only open RTT pathways are included.
- Records with missing waiting times are excluded because
  RTT compliance cannot be calculated without them.

  Key Finding:
I found that Orthopaedics had the biggest RTT issue,
with only 61.36% compliance and 17 patients waiting
longer than the 18-week target. Emergency Medicine and GEN had no RTT breaches and achieved 100% compliance.


Query 2 – Consultant Cancellation Rate

Business Question:
Which consultants have the highest Trust-initiated
cancellation rate?

Purpose:
I wrote this query to identify consultants with the
highest Trust-initiated cancellation rates and rank
them within each specialty using a window function.
This helps highlight where appointment cancellations
may be affecting patient access.

Business Rules:
- Only Trust-initiated cancellations are included.
- Ranking is calculated within each specialty.
- Records with missing consultant information are excluded.

 Key Finding:
Orthopaedics recorded the highest number of missed
appointments (17 DNA records), followed by Urology (11)
 and Ophthalmology (10), indicating these specialties may
 benefit from targeted appointment reminder initiatives.


Query 3 – Clinic DNA Rate

Business Question:
Which clinics have the highest DNA (Did Not Attend)
rate?

Purpose:
I wrote this query to calculate the DNA rate for each
clinic by comparing the total number of appointments
with the number of patients who did not attend.
This helps identify clinics where attendance could
be improved.

Business Rules:
- Only valid attendance status values are included.
- Non-standard attendance statuses are excluded.
- DNA Rate = DNA Appointments ÷ Total Appointments.

 Key Finding:
Orthopaedics recorded the longest average outpatient
waiting time at 151 days, significantly higher than
Ophthalmology (97 days) and Urology (86 days),
highlighting a potential capacity and demand issue.


Query 4 – Ward Occupancy by Week

Business Question:
Which wards regularly have more than 10 patients
admitted at the same time?

Purpose:
I wrote this query to calculate ward occupancy by
counting patients who were admitted on or before a
given date and had not yet been discharged. This
helps identify wards experiencing sustained pressure
on bed capacity.

Business Rules:
- Include patients with no discharge date or a future
  discharge date.
- Occupancy is based on patients still admitted.

 Key Finding:
 GP referrals were the main source of outpatient
 appointments, generating 434 referrals. Consultant
 referrals (65) and ED referrals (59) were the next
 largest sources, while self-referrals and other
 referral routes contributed very little to the overall
 referral volume.

Query 5 – Departmental Waiting Times

Business Question:
Which specialties have the longest waiting times for
open RTT pathways?

Purpose:
I wrote this query to calculate the average, median
(approximate) and maximum waiting time for each
specialty. This helps identify departments with the
greatest patient waiting times.

Business Rules:
- Only open RTT pathways are included.
- Records with missing waiting times are excluded.
- Results are ordered by average waiting time.

Key Finding:
I found that Orthopaedics (OR) had the highest average
waiting time at 151 days, with the longest wait reaching
423 days. Emergency Medicine (EM) had the shortest
average waiting time at 41 days. This showed that some
specialties are experiencing much longer patient waits
than others and could benefit from targeted improvements.


Query 6 – Duplicate Patient Records

Business Question:
Are there any duplicate patient records in the
outpatient dataset?

Purpose:
I wrote this query to identify NHS Numbers that appear
more than once and check whether duplicate records
contain consistent patient demographic information.

Business Rules:
- Duplicate records are identified using NHS Number.
- Appointment counts are calculated for each patient.

  
Key Finding:
I found several duplicate NHS Numbers in the outpatient
dataset. The highest duplicate count was 5 appointments
for a single NHS Number, while many others appeared
3 or 4 times. These records should be reviewed to
improve data quality and reduce duplicate patient records.


Query 7 – Lost Referrals

Business Question:
Which patients have an open RTT pathway but no
corresponding inpatient admission or emergency
department attendance?

Purpose:
I wrote this query to identify patients whose referral
pathway appears not to have progressed. This helps
highlight potential gaps in patient pathways.

Business Rules:
- Only open RTT pathways are included.
- Patients with matching inpatient or ED activity are
  excluded.

Key Finding:
I found several patients who had an outpatient referral
but no matching inpatient admission or ED attendance.
The patient with the longest wait had been waiting
423 days without progressing further in their care pathway.
This could indicate delayed or lost referrals that should
be investigated to improve patient flow.

Query 8 – Revenue Leakage (HRG)

Business Question:
How much revenue is potentially at risk because of
missing HRG codes?

Purpose:
I wrote this query to identify inpatient episodes with
missing HRG codes and estimate the potential revenue
at risk by specialty.

Business Rules:
- Blank HRG codes are treated as missing.
- Revenue at risk is estimated at £1,850 per episode.

Key Finding:
I found 28 inpatient episodes with a missing
HRG code. Based on an estimated value of
£1,850 per episode, this could put around
£51,800 of hospital revenue at risk.
Completing these missing codes would help
improve reporting accuracy and reduce
potential income loss.


Query 9 – Services Exceeding Target

Business Question:
Which specialties are performing better than the
Trust DNA target?

Purpose:
I wrote this query to identify specialties with a DNA
rate below the Trust target of 8%. These services may
represent examples of good practice that could be
shared across the organisation.

Business Rules:
- DNA target = Less than 8%.
- Only valid attendance statuses are included.


Key Finding:
I found five specialties that are performing
better than the Trust target of 8% DNA rate.
Emergency Medicine (EM) and General Medicine
(GEN) recorded a 0% DNA rate, while GM, GS
and RHE all remained below the target. These
services could be used as examples of good
practice to help reduce DNA rates elsewhere.

Query 10 – Readmission Pattern

Business Question:
Which admission types and specialties have the
highest readmission counts?

Purpose:
I wrote this query to analyse readmission patterns
using a Common Table Expression (CTE). The results
highlight specialties and admission types with the
highest number of readmissions.

Business Rules:
- Only records flagged as readmissions are included.
- Readmission_Flag = 'Y'.


Key Finding:
Emergency admissions in General Surgery (GS) and
Urology (URO) recorded the highest number of
readmissions, with 9 cases each. This suggests
these services may benefit from reviewing discharge
planning and post-discharge follow-up.



Query 11 – Agency Spend by Ward

Business Question:
Which wards have the highest agency staffing costs?

Purpose:
I wrote this query to calculate the number of agency
shifts worked in each ward and estimate the total cost
using the standard agency rate.

Business Rules:
- Exclude blank Agency_Flag values.
- Exclude ST-99 test records.
- Estimated cost = £385 per agency shift.


Key Finding:
Ward W-05 had the highest agency staffing cost,
with 43 agency shifts costing an estimated £16,555.
This suggests W-05 is the most reliant on temporary
staffing and may benefit from workforce planning to
reduce agency spend.


Query 12 – Theatre Cancellation Pattern

Business Question:
Are there any patterns in theatre cancellations by
week or specialty?

Purpose:
I wrote this query to identify trends in theatre
cancellations by analysing the week ending date and
specialty. The results help identify periods or
services with higher cancellation activity.

Business Rules:
- Analysis uses Week_Ending and Specialty_Code.
- Results are grouped by week and specialty.

Key Finding:
General Surgery (GS) and Orthopaedics (OR)
recorded the highest number of theatre
cancellations, with a peak of 11 cancellations
during a single reporting week. These services
may require further investigation to identify
whether cancellations were caused by capacity,
staffing or patient-related factors.





