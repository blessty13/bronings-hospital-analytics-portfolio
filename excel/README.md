# Excel Phase — Data Quality & KPI Investigation

## Project Overview

This phase focused on investigating the quality and reliability of five operational datasets from Bronings University Hospital Group before they were used for further SQL analysis, KPI development and dashboarding.

The investigation was completed using **Google Sheets**, where I performed data quality checks, cleaned and standardised inconsistent values, validated key fields and calculated healthcare performance KPIs across outpatient, inpatient, emergency department, theatre and workforce data.

The objective was to identify data quality issues that could affect operational and financial reporting, establish reliable KPI figures, and document issues requiring further investigation before the data was used for decision-making.

## Datasets Investigated

| Dataset | Analysis Area |
|---|---|
| `03_outpatient_appointments.csv` | Attendance status, DNA rates, waiting times and RTT performance |
| `04_inpatient_admissions.csv` | Admissions, discharge dates, HRG coding and readmissions |
| `05_ed_attendances.csv` | Emergency Department activity and frequent attenders |
| `06_theatre_utilisation.csv` | Theatre utilisation, unused sessions and wasted capacity |
| `07_workforce_staffing.csv` | Workforce staffing, agency flags and agency expenditure |

## Tools & Techniques

**Primary analysis tool:** Google Sheets

Techniques used during the investigation included:

- Pivot tables
- COUNTIF and COUNTIFS
- XLOOKUP
- LEN
- ISNUMBER
- IF statements
- Conditional formatting
- Filters and sorting
- Helper columns
- Data cleaning and standardisation
- Duplicate detection
- Cross-sheet reconciliation
- Percentile analysis
- KPI calculations
- Best-case and worst-case financial analysis

-## Data Quality Findings

A structured Data Quality Issue Log was created to document issues identified during the investigation, their severity, business impact and recommended corrective action.

| Issue | Dataset | Affected Rows | Severity | Recommended Action |
|---|---|---:|---|---|
| Non-standard Attendance_Status | Outpatient | 1 | Major | Standardise attendance value and investigate N/A |
| NHS Number cross-sheet gap | Inpatient / Outpatient | 1 | Major | Investigate identifier consistency at source |
| Blank HRG_Code | Inpatient | 28 | Critical | Complete missing clinical coding |
| Blank Discharge_Date | Inpatient | 31 | Critical | Investigate missing discharge events |
| Duplicate Appointment_ID check | Outpatient | 0 | Information | No corrective action required |
| Impossible Waiting_Days | Outpatient | 1 | Major | Validate against source data |
| Retired GEN specialty code | Multiple datasets | 24 | Major | Replace GEN with GM |
| Blank Agency_Flag | Workforce | 15 | Major | Investigate and complete missing flags |

### Highest-Priority Data Quality Issues

**Missing HRG Codes — Critical**

28 inpatient records contained blank HRG codes. Using an estimated value of £1,850 per episode, this represented **£51,800 of potential revenue at risk**.

**Missing Discharge Dates — Critical**

31 inpatient records contained blank Discharge_Date values. These records require investigation because they could affect Length of Stay and bed occupancy calculations.

**Retired Specialty Codes — Major**

24 occurrences of the retired `GEN` specialty code were identified across multiple datasets. These were standardised to `GM` to improve consistency in specialty-level reporting.

**Agency Flag Uncertainty — Major**

15 workforce records contained blank Agency_Flag values, creating uncertainty in calculated agency expenditure. The resulting cost was therefore reported as a range of **£98,560 best case to £104,335 worst case**.

## KPI Analysis

Following the data quality investigation, I calculated key operational performance indicators across outpatient, inpatient, emergency department and theatre activity.

| KPI | Result | Performance |
|---|---:|---|
| Overall DNA Rate | **13.15%** | Operational concern |
| Highest Specialty DNA Rate | **Orthopaedics — 36.17%** | Highest DNA specialty |
| 90th Percentile Open RTT Wait | **267 days (38.1 weeks)** | Above 18-week target |
| Readmission Rate | **9.04%** | Within 10% target |
| Wasted Elective Theatre Sessions | **499** | Capacity opportunity |
| Average Monthly Theatre Waste | **£31,187.50** | Financial impact |
| Annual Theatre Waste | **£374,250** | Financial impact |
| Frequent ED Attenders (>3 visits) | **91 patients** | Operational concern |

### DNA Rate by Specialty

The overall outpatient DNA rate was **13.15%**, with 76 DNA appointments from 578 appointments included in the calculation.

The three specialties with the highest DNA rates were:

1. **Orthopaedics (OR) — 36.17%**
2. **Ophthalmology (OPH) — 16.39%**
3. **Cardiology (CS) — 15.39%**

Orthopaedics had the highest DNA rate and represents the clearest opportunity for targeted investigation into outpatient non-attendance.

### RTT Performance

The 90th percentile waiting time for Open RTT pathways was **267 days (38.1 weeks)**, substantially above the **18-week target**.

Nine specialties analysed were below the **92% RTT compliance target**, indicating significant elective waiting-time pressure.

### Readmission Rate

The calculated readmission rate was **9.04%**, based on **39 readmissions from 432 records with a known Y/N readmission status**.

A further **44 records with blank Readmission_Flag values were excluded** from the calculation because their readmission status could not be reliably determined.

The resulting **9.04% rate was within the 10% target**.

### Theatre Wasted Capacity

The emergency/trauma theatre (`T4`) was excluded from the elective theatre analysis.

After data quality checks, the analysis identified **499 wasted elective theatre sessions** across the 12-month period.

Using a cost of **£750 per wasted session**, this produced:

- **Average monthly wasted cost: £31,187.50**
- **Annual wasted cost: £374,250**

### Frequent ED Attenders

**91 patients** attended the Emergency Department more than three times during the quarter.

This group represents an opportunity for further investigation into repeat ED utilisation and whether alternative care pathways could reduce avoidable attendances.

## Methodology & Analytical Decisions

### DNA Rate

DNA appointments were used as the numerator, with `DNA`, `ATT`, `CAN` and `REF` appointment statuses included in the denominator.

Non-standard attendance values were investigated separately rather than automatically included in the calculation. This ensured that the reported DNA rate was based on clearly defined appointment outcomes.

### Readmission Rate

Only records containing a valid `Y` or `N` Readmission_Flag were included in the readmission rate calculation.

The 44 blank records were excluded because their readmission status was unknown. Classifying these records as either readmitted or not readmitted would have introduced an unsupported assumption into the KPI.

### Theatre Wasted Capacity

The emergency/trauma theatre (`T4`) was excluded because the analysis focused on elective theatre capacity.

Wasted sessions were calculated as:

`Sessions Available - Sessions Used`

Where this calculation produced a negative value, the record was treated as zero wasted capacity so that over-utilisation did not offset unused capacity elsewhere.

A non-standard theatre identifier (`Theatre One`) was also standardised to `T1` before the final calculation.

### Agency Expenditure

15 records contained a blank Agency_Flag, meaning a definitive agency expenditure figure could not be calculated without making an assumption.

Rather than presenting a single figure with false precision, agency expenditure was reported as a range:

- **Best case: £98,560**
- **Worst case: £104,335**
- **Financial uncertainty: £5,775**

This approach makes the impact of the unresolved data quality issue transparent to decision-makers.

## Recommendations

1. **Resolve missing HRG codes as a priority**  
   Investigate and complete the 28 missing HRG codes to address approximately **£51,800 of revenue at risk**.

2. **Strengthen source-system data validation**  
   Introduce validation controls for attendance statuses, discharge dates, specialty codes, waiting times and agency flags to prevent known data quality issues entering future extracts.

3. **Implement routine data quality monitoring**  
   Develop a recurring data quality monitoring process to identify missing values, invalid codes, duplicate identifiers and other exceptions before operational and financial reports are produced.

4. **Investigate outpatient non-attendance**  
   Prioritise Orthopaedics, which recorded the highest specialty DNA rate at **36.17%**, and assess opportunities to reduce missed appointments.

5. **Review elective waiting-time performance**  
   Investigate the specialties below the **92% RTT compliance target**, particularly in light of the **267-day 90th percentile Open RTT waiting time**.

6. **Improve elective theatre utilisation**  
   Review the causes of the **499 wasted elective theatre sessions**, representing an estimated **£374,250 annual cost**.
