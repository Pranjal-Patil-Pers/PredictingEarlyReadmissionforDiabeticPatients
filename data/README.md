### 1. Dataset
The analysis leverages a dataset from 130 U.S. hospitals spanning 10 years (1999–2008). This dataset contains over 50 descriptive features and includes comprehensive records of inpatient diabetic patient encounters.
#### Link to the Dataset:
https://archive.ics.uci.edu/dataset/296/diabetes+130-us+hospitals+for+years+1999-2008

## Table of Contents
1. [Overview](#overview)
2. [Dataset Features](#dataset-features)  
   2.1 [Identifiers](#identifiers)  
   2.2 [Demographic Features](#demographic-features)  
   2.3 [Admission Information](#admission-information)  
   2.4 [Medical Data](#medical-data)  
   2.5 [Medications](#medications)  
   2.6 [Target Variable](#target-variable)  
3. [Handling Missing Values](#handling-missing-values)  
4. [Feature Summary Table](#feature-summary-table)

---

## Overview
- **Dataset Source**: 130 US hospitals, data spanning from 1999 to 2008.
- **Purpose**: Predict inpatient readmissions within 30 days of discharge to improve patient care and hospital resource allocation.
- **Number of Records**: 101,766 instances.
- **Features**: Includes 47 descriptive features and 1 target variable ("readmitted").

Features are categorized into:
- Identifiers
- Demographic details
- Admission information
- Medical and procedural data
- Diabetic medications
- Target variable (readmitted within 30 days)

---

## Dataset Features

### 2.1 Identifiers
- **`encounter_id`**: Unique identifier of each hospital encounter.
- **`patient_nbr`**: Unique identifier for each patient.

### 2.2 Demographic Features
- **`race`**: Patient’s race (e.g., Caucasian, African American, Hispanic) *(may contain missing values)*.
- **`gender`**: Patient gender (`male`, `female`, `unknown/invalid`).
- **`age`**: Patient age, grouped into 10-year intervals (e.g., `[0-10)`, `[10-20)`, ..., `[90-100)`).
- **`weight`**: Patient weight in pounds *(often contains missing values)*.

### 2.3 Admission Information
- **`admission_type_id`**: Type of hospital admission (e.g., emergency, elective, urgent).
- **`discharge_disposition_id`**: Patient’s discharge state (e.g., to home, expired, or transferred).
- **`admission_source_id`**: Source of the admission (e.g., physician referral, emergency room, transfer).
- **`time_in_hospital`**: Length of stay during the hospital encounter (in days).

### 2.4 Medical Data
- **`payer_code`**: Insurance provider (e.g., Medicare, Blue Cross/Blue Shield, self-pay) *(often missing)*.
- **`medical_specialty`**: Specialty of admitting physician (e.g., cardiology, internal medicine) *(often missing)*.
- **`num_lab_procedures`**: Total number of lab procedures during the encounter.
- **`num_procedures`**: Number of non-lab procedures performed during the encounter.
- **`num_medications`**: Number of unique medications prescribed during the encounter.
- **`number_outpatient`**: Outpatient visits in the year preceding the encounter.
- **`number_emergency`**: Emergency visits in the year preceding the encounter.
- **`number_inpatient`**: Inpatient visits in the year preceding the encounter.
- **`diag_1`**: Primary diagnosis code (ICD9 codes, 848 unique values) *(may contain missing values)*.
- **`diag_2`**: Secondary diagnosis code (ICD9 codes, 923 unique values) *(may contain missing values)*.
- **`diag_3`**: Additional secondary diagnosis code (ICD9 codes, 954 unique values) *(may contain missing values)*.
- **`number_diagnoses`**: Total number of diagnoses recorded for the patient.

### 2.5 Medications
Each of the following features indicates whether the respective drug was prescribed or if there were changes in dosage:
- **`max_glu_serum`**: Glucose serum test result (`none`, `>200`, `>300`, `normal`).
- **`A1Cresult`**: Hemoglobin levels (`none`, `>7`, `>8`, `normal`).
- **`metformin`, `repaglinide`, `chlorpropamide`, etc.**: Drugs used to manage diabetes. Values: `up` (dosage increased), `down` (dosage decreased), `steady` (dosage unchanged), `no` (not prescribed).
- **`change`**: Indicates whether any diabetic medication was changed during the encounter (`change`, `no change`).
- **`diabetesMed`**: Indicates whether any diabetic medication was prescribed.

### 2.6 Target Variable
- **`readmitted`**: Target variable indicating readmission status:
  - `<30`: Readmitted within 30 days.
  - `>30`: Readmitted after 30 days.
  - `No`: No readmission occurred.

---

## 3. Handling Missing Values
- **Features with Missing Values**:
  - **`race`**, **`weight`**, **`payer_code`**, **`medical_specialty`**, **`diag_1`**, **`diag_2`**, **`diag_3`**.
- Missing values were addressed using appropriate imputation methods (e.g., replacing categorical `NaN` values with `Unknown` or the mode).

---

## 4. Feature Summary Table
| **Variable Name**         | **Role**  | **Type**        | **Demographic** | **Description**                                                                                   | **Units**   | **Missing Values** |
|----------------------------|-----------|-----------------|-----------------|---------------------------------------------------------------------------------------------------|-------------|---------------------|
| encounter_id              | ID        |                 |                 | Unique identifier of an encounter                                                                |             | No                  |
| patient_nbr               | ID        |                 |                 | Unique identifier of a patient                                                                   |             | No                  |
| race                      | Feature   | Categorical     | Race            | Patient’s race (e.g., Caucasian, African American, Hispanic)                                     |             | Yes                 |
| gender                    | Feature   | Categorical     | Gender          | Patient’s gender (male, female, or unknown/invalid)                                              |             | No                  |
| age                       | Feature   | Categorical     | Age             | Patient’s age in 10-year intervals (e.g., `[0-10)`, `[10-20)`, ..., `[90-100)`)                  |             | No                  |
| weight                    | Feature   | Categorical     |                 | Patient’s weight in pounds                                                                       |             | Yes                 |
| admission_type_id         | Feature   | Categorical     |                 | Type of hospital admission (e.g., emergency, elective, urgent)                                   |             | No                  |
| discharge_disposition_id  | Feature   | Categorical     |                 | Discharge state (e.g., to home, expired, transferred)                                            |             | No                  |
| admission_source_id       | Feature   | Categorical     |                 | Source of admission (e.g., emergency room, transfer from another hospital)                       |             | No                  |
| time_in_hospital          | Feature   | Integer         |                 | Number of days the patient spent in the hospital                                                 | Days        | No                  |
| payer_code                | Feature   | Categorical     |                 | Insurance provider (e.g., Blue Cross/Blue Shield, Medicare)                                      |             | Yes                 |
| ... (additional rows omitted for brevity)                                                                                                                        |

> **Note**: Full feature list available above in the attached Data Dictionary

---

## Summary
This dataset contains a diverse set of features enabling the prediction of early readmission for diabetic patients. Proper feature engineering, handling of missing values, and transformations are critical for building an accurate predictive model.
---
