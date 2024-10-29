# Analysis of 2024 JAMB Result

## Table of Content
-Overview

-Tools

-Data

-Tasks

-Exploratory Data Analysis

-Hypothesis & Correlation

-Insights & Findings

-Recommendations
### Overview
This project examines the factors affecting JAMB 2024 exam performance, using a detailed dataset on student study habits, school attendance, and teacher quality. Leveraging Python libraries and data science techniques, we analyze the impact of variables such as study hours, school type, and parental education level on student scores, learning materials and extra tutorials. By exploring these elements, we aim to uncover patterns and insights into academic achievement, providing valuable information for educators and policymakers to enhance student success rates.

### Tools
PostgresSQL was used for initial merging and cleaning the data. After which the merged dataframes were exported into CSV for further analysis in Python.


```python
# Load dataset
jamb = pd.read_csv(r"C:\Users\USER\Downloads\jamb2.csv")
jamb.head()
```
### Data
The dataset was a Joint Admission Matriculation Board dataset on the result of the 2024 JAMB examination. This shows the performace of students in theexam. The dataset consists of 5001 rows of unique records including 17 unique columns withou the student ID. The datasets came in five different tables which were joined in postgreSQL.The tables include "students, academic_performance, school_factors, attendance_resources, and home_environment". The columns are student_id, Age, gender, socioeconomic_status, parent_education_level, teacher_quality, distance_to_school, school_type, school_location, parent_involvement, it_knowledge, attendance_rate, extra_tutorials, access_to_learning_materials, jamb_score, study_hours_per_week, assignments_completed.
### Tasks
There were 5 major tasks to carry out 
1. Analyze JAMB Scores Based on Study and School-Related Factors
o Objective: Analyze JAMB scores based on study hours, school attendance, teacher quality, and other    school-related factors (e.g., Study_Hours_Per_Week, Teacher_Quality, School_Type). This could help educators identify students who might need additional support.
2. Investigate the Impact of Socioeconomic Status and Parental Education on Student Performance
o Objective: Investigate how a student’s socioeconomic background and their parents’ education level influence their performance in the JAMB examination (e.g., Socioeconomic_Status, Parent_Education_Level). The findings could inform educational policies aimed at supporting students from disadvantaged backgrounds.
3. Analyze the Comparison of Performance Between Public and Private Schools
o Objective: Analyze whether students from private schools perform significantly better than those from public schools in the JAMB exam (School_Type, School_Location). This could reveal disparities in resource allocation and education quality.
4. Analyze the Effect of IT Knowledge on JAMB Performance
o Objective: Determine whether a student’s proficiency with computers (IT knowledge) impacts their performance in the computer-based JAMB exam (IT_Knowledge). This analysis could help design interventions that focus on improving IT literacy.
5. Check the Influence of Extra Tutorials on Student Success
o Objective: Evaluate whether students who receive extra tutorials or coaching sessions perform better in the JAMB exam (Extra_Tutorials). This could help parents and educators understand the importance of supplementary learning programs.

### Exploratory Data Analysis
The data was explored. There were no duplicates in the data prior to and post merging the data. The data consists of 5000 unique records of students who took part in the Joint Admission Matriculation Board Examination in the 2024. There are columns with missing values and they include:
parent_education_level          891
teacher_quality                  22
distance_to_school               77
school_type                     101
school_location                  65
parent_involvement               17
it_knowledge                      5
extra_tutorials                  36
access_to_learning_materials     15
study_hours_per_week              9

### Using Little’s MCAR to check for randomness of missing values
```python
msno.matrix(jamb, labels = True)
```

#### Treatment
The numerical columns were filled with the mean values while the categorical columns were left unfilled so as to not affect the analysis. The parents could actually be unlettered.

Findings
The Jamb Score of the students was weighted across various features

#### School-Related Factors (Features to focus on)
Study_Hours_Per_Week, Attendance_Rate, Teacher_Quality, Distance_To_School, School_Type, School_Location, Extra_Tutorials, Access_To_Learning_Materials

#### Socioeconomic Factors (Features to focus on)
Socioeconomic_Status, Parent_Education_Level, Parent_Involvement, Students that have access to learning materials, extra tutorials, went to private school, have better socioeconomic status, parent involvement and parent with high education level perform better than their counterparts. 
