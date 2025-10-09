# Project Title (This is a template README.md file that you can adapt to your project)
Inequality in Education-Analyzing How Socioeconomic Conditions Affect Student Achievement

> A brief description of what the project does and its purpose.
This project addresses inequality of educational opportunity in U.S. high schools. Here we will focus on average student performance on the ACT or SAT exams that students take as part of the college application process.
Do smaller schools with lower student–teacher ratios perform better on the ACT, even after controlling for socioeconomic factors such as household income and unemployment rates?
---

## Project Overview

Provide a short and concise overview of the project. Mention the problem it solves, the data used, and the key outcomes or findings.

- **Objective:** The goal of the project is to address inequality of educational opportunity in U.S. high schools
- **Domain:** Education
- **Key Techniques:** Regression

---

## Project Structure

```
├── data/                 # Raw and processed data
├── code/                 # Jupyter notebooks and Python scripts
├── reports/              # Generated reports and visualizations
├── requirements.txt      # Dependencies
└── README.md             # Project documentation
```

---

## Data

- **Source:** https://www.edgap.org/#5/37.892/-95.977
https://nces.ed.gov/ccd/pubschuniv.asp
- **Description:** Brief overview of the dataset features, size, and format
- **License:** (if applicable)

---

## Analysis

Describe the notebooks and/or scripts used to perform the analysis. Specify the order in which the code should be run to reproduce the results.

Name of the file used to clean the data-../code/education.ipynb
1. Import pandas, numpy, matplotlib,seaborn
2. Start by loading the each data sets-Edgap dataset & School_information data set
3. Explore the contents of each dataframe using .head(), .info(), .shape()
4. Make a pairplot to explore the relationships between the variables, add regression lines, plot single row that is required for analysis
5. Select relevant subsets from the school_information dataframe like ['SCHOOL_YEAR','NCESSCH','LSTATE','LZIP','SCH_TYPE_TEXT','LEVEL','CHARTER_TEXT']
6. Rename the column names of edgap and school_information dataset
7. To ensure we have matching key values in both dataframe we set the 'id' column in school_information to object using .astype()
8. Join the dataframe edgap and school_information using left join with 'id' as the key.
9. Next is the quality control. We check for out of range values and set the values to NaN. set the percent_lunch <0  to Nan and average_act < 1 to NaN.
10. Check the types, levels,and charter status of schools. Filter the school_levels to High(High Schools)
11. Check for any duplicated rows.
12. check for missing values & Calculate the percentage of missing values for each column.
13. Check for the number of states present in the data.
14. Drop the rows where the average ACT score is missing.
15. Impute missing values of sociaeconomic variables.
  - Define the predictor variables to be rate_unemployment, percent_college, percent_married,
    median_income, percent_lunch, state, and charter.
  - Use the iterative imputer to replace missing values in the columns corresponding
    to predictor variables in the analysis
  - Fit the imputer using imputer.fit()
  - Impute the missing values in the training data
16. Export the clean data set.

Name of the cleaned file-../data/education_clean.csv


---

## Results

Include a short discussion of the findings and what they imply.

---

## Authors

- Your Name - [@yourhandle](https://github.com/yourhandle)

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Acknowledgements

- Tools/libraries used
- Tutorials or papers referenced
- Inspiration or collaborators
