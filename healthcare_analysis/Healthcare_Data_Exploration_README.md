
# Healthcare Data Cleaning and Exploration Project

## Project Overview
This project focuses on cleaning and preprocessing a healthcare dataset using Python and pandas library. The dataset contains records related to patient information, including age, room number, admission, and discharge dates. The goal is to remove errors, inconsistencies, and duplicates from the dataset, and explore the data to uncover insights.

## Dataset Information
The dataset contains the following columns:
- **Name**: The name of the patient.
- **Age**: The age of the patient.
- **Room Number**: The room number assigned to the patient.
- **Date of Admission**: The date when the patient was admitted to the hospital.
- **Discharge Date**: The date when the patient was discharged from the hospital.

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

```

### 2. Patient Count by Gender
Break down the patient count by gender to understand the gender distribution:
```sql

```

### 3. Distribution of Medical Conditions
Identify the most common medical conditions among patients:
```sql

```

### 4. Insurance Provider Distribution

Analyze how many patients are associated with each insurance provider:
```sql

```
### 5. Admission Type Distribution

Explore how many patients were admitted as "Emergency," "Elective," or "Urgent":
```sql

```
### 6. Trends in Admission Dates
Analyze the monthly distribution of patient admissions over time:
```sql

```
### 7. Data Range for Admission and Discharge Dates
Find the earliest and latest dates for admissions and discharges:
```sql

```
### 8. Age Distribution by Medical Condition
Analyze the average age of patients based on different medical conditions:
```sql

```
### 9. Room Occupancy Insights
Analyze the rooms that have the most patients to understand room utilization:
```sql
SELECT MIN(Date_of_Admission) AS earliest_admission, MAX(Discharge_Date) AS latest_discharge
FROM healthcare_data;
```

### 10. Average Billing Amount by Admission Type
Analyze billing information based on the type of admission (e.g., Emergency, Elective):
```sql

```

### 11. Discharge Rate Trends
Analyze the rooms that have the most patients to understand room utilization:
```sql

```

### 12. Case Load by Doctor
Identify how many patients each doctor has managed to balance the workload:
```sql

```

### 13. Patients on Specific Medication

Show how many patients are taking specific medications:
```sql

```
## Project Files

- **healthcare_dataset.csv**: The raw healthcare dataset that contains the patient records.
- **data_cleaning_script.py**: The Python script that performs all the data cleaning steps.
- **README.md**: This file, explaining the steps taken in the project.

## How to Run the Project

1. Install the required dependencies by running:
   ```bash
   pip install pandas
   ```

2. Run the Python script:
   ```bash
   python data_cleaning_script.py
   ```

## Conclusion
This project cleaned and explored the healthcare dataset by addressing common data issues like negative values, duplicates, and inconsistent data. The cleaned dataset is now ready for further analysis or machine learning tasks.
