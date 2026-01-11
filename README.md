# PySpark Student Performance Analysis
This repository contains a PySpark project analyzing student performance data from exams. The goal is to practice **DataFrame operations, aggregations, joins, and UDFs** in PySpark.
## Dataset
- **Source:** [Kaggle - Students Performance in Exams](https://www.kaggle.com/datasets/spscientist/students-performance-in-exams)
- **Columns:**
  - `gender`
  - `race/ethnicity`
  - `parental level of education`
  - `lunch`
  - `test preparation course`
  - `math score`
  - `reading score`
  - `writing score`
## Features
- Basic DataFrame operations: `select`, `filter`, `describe`
- Aggregations: average, count, max, min
- Joins between students, grades, and departments
- User Defined Functions (UDFs) for grading and categorizing performance

## Project structure
```
analysis-of-student-performance-tp
+
+---data
|       StudentsPerformance.csv
|       
+---docs
|   +---subject
|           tp01.md
|
|   .gitignore
|   analysis_of_student_performance.ipynb
|   README.md
|   requirements.txt
```

## Environment
- Python 3.10
- Java 11
- Spark 3.5.7
- Jupyter

## Author
J.SAIDI