
# Healthcare Data Cleaning and Exploration Project

## Project Overview
This project focuses on cleaning and preprocessing a healthcare dataset using Python and pandas library. The dataset contains records related to patient information, including age, room number, admission, and discharge dates. The goal is to remove errors, inconsistencies, and duplicates from the dataset, and explore the data to uncover insights.

## Dataset Information
The dataset contains the following columns:
- **Name**: The name of the patient.
- **Age**: The age of the patient.
- **Gender**: The age of the patient.
- **Blood type**: The age of the patient.
- **Medical Condition**: The age of the patient.
- **Hospital**: The age of the patient.
- **Insurance Provider**: The age of the patient.
- **Billing amount**: The age of the patient.
- **Admission type**: The age of the patient.
- **Room Number**: The room number assigned to the patient.
- **Date of Admission**: The date when the patient was admitted to the hospital.
- **Discharge Date**: The date when the patient was discharged from the hospital.
- **Medication**: The a.
- **Test Results**: The age of the patient.

## Data Cleaning Steps

### 1. Reading the Dataset
```python
import pandas as pd
# read the file
data = pd.read_csv('healthcare_dataset.csv')
# display the first few rows of the data
data.head()
```

### 2. Checking for Negative Values
```python
# check for negative values in Age and Room Number
negative_values = data[(data['Age'] < 0) | (data['Room Number'] < 0)]
print(negative_values)
```

### 3. Removing Duplicate Rows
```python
# determine the duplicated data
duplicate = data.duplicated()
print(duplicate)

# drop duplicate data if any are found
if duplicate.any():
    data = data.drop_duplicates()
```

### 4. Fixing Incorrectly Capitalized Names
```python
# Fix the wrong capitalized names
data['Name'] = data['Name'].str.title()
```

### 5. Converting Dates to the Correct Format
```python
# Convert 'Date of Admission' and 'Discharge Date' to datetime format
data['Date of Admission'] = pd.to_datetime(data['Date of Admission'])
data['Discharge Date'] = pd.to_datetime(data['Discharge Date'])
```

### 6. Checking Data Types
```python
# Check data types of all columns
print(data.dtypes)
```

## Data Exploration with SQL Queries

### 1. Total Patients and Average Age
Calculate summary statistics such as total patients and the average age of patients:
```sql
   SELECT count(*) as total_patients, avg(age) as avg_age
   FROM healthcaretbl
```

### 2. Patient Count by Gender
Break down the patient count by gender to understand the gender distribution:
```sql
   SELECT gender, COUNT(*) as total_patients
   FROM healthcaretbl
   GROUP BY gender;
```

### 3. Distribution of Medical Conditions
Identify the most common medical conditions among patients:
```sql
   SELECT medical_condition, COUNT(*) as total_patients
   FROM healthcaretbl
   GROUP BY medical_condition
   ORDER BY total_patients DESC
   LIMIT 5;

```

### 4. Insurance Provider Distribution

Analyze how many patients are associated with each insurance provider:
```sql
   SELECT insurance_provider, COUNT(*) as total_patients
   FROM healthcaretbl
   GROUP BY insurance_provider;

```
### 5. Admission Type Distribution

Explore how many patients were admitted as "Emergency," "Elective," or "Urgent":
```sql
   SELECT admission_type, COUNT(*) as total_patients
   FROM healthcaretbl
   GROUP BY admission_type;
```
### 6. Trends in Admission Dates
Analyze the monthly distribution of patient admissions over time:
```sql
   SELECT 
    TO_CHAR(date_of_admission, 'YYYY-MM') as admission_month, 
    COUNT(*) as total_patients
   FROM healthcaretbl
   GROUP BY admission_month
   ORDER BY admission_month;
```
### 7. Data Range for Admission and Discharge Dates
Find the earliest and latest dates for admissions and discharges:
```sql
   SELECT 
    MIN(date_of_admission) as earliest_admission,
    MAX(date_of_admission) as latest_admission,
    MIN(discharge_date) as earliest_discharge,
    MAX(discharge_date) as latest_discharge
   FROM healthcaretbl;
```
### 8. Age Distribution by Medical Condition
Analyze the average age of patients based on different medical conditions:
```sql
   SELECT 
      AVG(age) as avg_age, 
      medical_condition
   FROM healthcaretbl
   GROUP BY medical_condition;
```
### 9. Room Occupancy Insights
Analyze the rooms that have the most patients to understand room utilization:
```sql
   SELECT 
      room_number, 
      COUNT(*) as total_patients
   FROM healthcaretbl
   GROUP BY room_number
   ORDER BY total_patients DESC
   LIMIT 10;
```

### 10. Average Billing Amount by Admission Type
Analyze billing information based on the type of admission (e.g., Emergency, Elective):
```sql
   SELECT 
      admission_type, 
      SUM(billing_amount) as total_amount
   FROM healthcaretbl
   GROUP BY admission_type;
```

### 11. Discharge Rate Trends
Track the number of patient discharges over time (by month):
```sql
   SELECT 
      TO_CHAR(discharge_date, 'YYYY-MM') as discharge_month, 
      COUNT(*) as total_patients
   FROM healthcaretbl
   GROUP BY discharge_month
   ORDER BY discharge_month;
```

### 12. Case Load by Doctor
Identify how many patients each doctor has managed to balance the workload:
```sql

```

### 13. Patients on Specific Medications
Show how many patients are taking specific medications:
```sql
   SELECT 
      medication, 
      COUNT(*) as total_patients
   FROM healthcaretbl
   GROUP BY medication;
```

## Conclusion
This project cleaned and explored the healthcare dataset by addressing common data issues like negative values, duplicates, and inconsistent data. The cleaned dataset is now ready for further analysis or machine learning tasks.
