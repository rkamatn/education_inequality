# Project Title 

Inequality in Education:Analyzing how socioeconomic conditions and Student–Teacher ratios affect student achievement

## Project Overview

This project addresses inequality of educational opportunity in U.S. high schools. Here we will focus on average student performance on the ACT or SAT exams that students take as part of the college application process. The analysis also investigates whether schools with lower student–teacher ratios perform better on the ACT, even after controlling for socioeconomic factors such as household income and unemployment rates. The findings reveal that not all socioeconomic variables show a strong correlation with average ACT performance.

---

- **Objective:** The goal of the project is to address inequality of educational opportunity in U.S. high schools
- **Domain:** Education
- **Key Techniques:** Linear Regression

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

- **Source:**</br>
-[National Center for Education Statistics](https://nces.ed.gov/ccd/pubschuniv.asp)</br>
-[Edgap.org](https://www.edgap.org/#5/37.892/-95.977)

- **Description:** This project combines data from the [EdGap dataset](../data/Edgap_data.csv) and the National Center for Education Statistics (NCES) Public Elementary/Secondary School Universe Survey Data (2016–2017) [NCES School Information]((https://www.dropbox.com/s/lkl5nvcdmwyoban/ccd_sch_029_1617_w_1a_11212017.csv?dl=1)) to analyze how socioeconomic conditions affect student achievement in U.S. high schools.

The [EdGap dataset](../data/Edgap_data.csv) provides school-level academic and socioeconomic information such as NCESSH id, average ACT and SAT scores, median household income, unemployment rate, percentage of students eligible for free or reduced-price lunch, proportion of married parents and parental education levels.

The [NCES School Information]((https://www.dropbox.com/s/lkl5nvcdmwyoban/ccd_sch_029_1617_w_1a_11212017.csv?dl=1)) includes institutional details such as school year, NCESSH id, state name, ZIP code, school type, grade level, and charter school status, offering a clearer understanding of the structural and geographic characteristics of each school.

The data for teacher count and student count was downloaded from National Center for Education Statistics (NCES) website. [Teacher count](https://drive.google.com/file/d/126RI52Z1GPcnshE_0I-nYmyQdBh8lf0U/view?usp=drive_link) contains the school level count of teacher and the [Student count](https://drive.google.com/file/d/1szims8J8QZbafLDmuxogZlrFVA5Xb9Vr/view?usp=drive_link) contains the school level count of students.

The data was processed to subset the datasets, remove unnecessary columns, and rename the remaining columns for clarity. All the 4 datasets  were then combined into a single DataFrame, and missing values were handled  by imputation. This cleaned and consolidated dataset was used for the Exploratory Data analysis and Modeling


- **License:**  This project is intended solely for educational and academic purposes as part of a university course.  

---

## Analysis

Name of the file used to clean the data-../code/education.ipynb

1. Import pandas, numpy, matplotlib,seaborn
2. Start by loading the each data sets-Edgap dataset,School_information, school_staff and school_members data set
3. Explore the contents of each dataframe using .head(), .info()
4. Make a pairplot to explore the relationships between the variables, add regression lines, plot single row that is required for analysis
5. Select relevant subsets from the school_information dataframe like ['SCHOOL_YEAR','NCESSCH','LSTATE','LZIP','SCH_TYPE_TEXT','LEVEL','CHARTER_TEXT'], school_staff like ['NCESSH','TEACHERS'], school_members like ['NCESSH', 'GRADE','STUDENT_COUNT']
6. Rename the column names of edgap ,school_information, school_staff and school_members dataset
7. To ensure we have matching key values in both dataframe we set the 'id' column in school_information, school_staff and school_members to object using .astype()
8. We filtered only the Grade 9-12 students from school members data set.
9. Join the dataframe edgap and school_information using left join with 'id' as the key.
10. Join the dataframe student_staff and student_members using outer join with 'id' as the key
11. Add a new column and calculate the student teacher ratio before calculating the ratio we have converted the student and teacher counts to numeric — invalid strings become NaN
12. Join the edgap- school_information dataframe with the student teacher dataframe wusing left join with 'id' as key.
13. Next is the quality control. We check for out of range values and set the values to NaN. set the percent_lunch <0  to Nan and average_act < 1 to NaN.
14. Check the types, levels,and charter status of schools. Filter the school_levels to High(High Schools)
11. Check for any duplicated rows.
12. check for missing values & Calculate the percentage of missing values for each column.
13. Check for the number of states present in the data.
14. Drop the rows where the average ACT score is missing.
15. Impute missing values of sociaeconomic variables.
  - Define the predictor variables to be rate_unemployment, percent_college, percent_married,student_teacher_ratio,median_income, percent_lunch, state, and charter.
  - Use the iterative imputer to replace missing values in the columns corresponding
    to predictor variables in the analysis
  - Fit the imputer using imputer.fit()
  - Impute the missing values in the training data
16. Export the clean data set.

Name of the cleaned file-../data/education_clean.csv

Exploratory data analysis & Modeling:

Name of the file used to clean the data-../code/exploratory_modeling.ipynb

1. Load the cleaned data file.
2. Examine distributions and relationships,Plot the correlation matrix of the numerical variables in the training data to explore relationships between the variables.
3. Identify outliers using Box plots.
4. We start by taking only median income as the single input variable and access the relationship.
5.Fit and assess models predicting the average ACT score from each of the input variables
6.Fit the simple linear regression model
7.Display the fit summary: check the sign and significance of the coefficients.
8. Check Numerical assessment of fit accuracy by computing R-squared, Root mean squared error and mean absolute error
9. We then use a residual plot for graphical assessment of model fit.
10.We then try a quadratic model by plotting the regression curves and the scatter plot
11. Fit a quadratic linear regression model and display the summary.
12. We use an analysis of variance or an ANOVA to compare these two nested polynomial linear regression models.
13.Assess the model accuracy.
14. We perform a Multiple linear regression taking all the variables and analyse the summary.
15. We fit a reduced model with the significant predictors and access the summary.
16. Compare the accuracy between full and reduced models
17. Use an ANOVA to test the significance of difference between models
18. Scale the predictor variables in the reduced model to have mean 0 and standard deviation 1 and add them to the data frame.
19. Check the mean and standard deviation of the transformed data.
20 Fit the multiple linear regression model with the normalized predictors and access the summary.
21. Compare the accuracy between the original and normalized models.


---

## Results

This study looked at how family income, education level, unemployment and student–teacher ratio affect student achievement in U.S. high schools. The results show that economic factors, especially the percentage of students getting free lunch, have the biggest impact on ACT scores. Schools with higher household income, more college-educated parents, and lower unemployment rates usually have higher ACT scores.
Although the student–teacher ratio was statistically important, it explained only a small part of the difference in scores. This means that community and family conditions affect student success more than classroom size does.


---

## Authors

- Rashmi Kamath - [@rkamatn](https://github.com/rkamatn)

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Acknowledgements

- Libraries used: pandas,numpy,matplotlib,seaborn
- Models used: scikit-learn,statsmodels
- References : Wikipedia
- Tutorials : Dr Brian Fischer

