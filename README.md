# School_District_Analysis.

Module 4
Ashley Mayes

## Challenge

Analysis available in the Jupyter Notebook - **PyCitySchools_Challenge.ipynb**

### Background

The grades of the ninth graders at Thomas High School have been changed. While administrators do not know the full extent of this academic dishonesty, they want to uphold the standards of state testing and have turned to you for help.
After assessing the situation with the school superintendent and Maria, you decide the best approach is to:
- Replace the ninth-grade math and reading scores from Thomas High School.
- Keep all other data associated with the ninth-grade students and Thomas High School intact.

### Objectives

The goals of this challenge are for you to:
- Filter DataFrames using logical operators.
- Replace the incorrect values with NaN.
- Explain how your PyCitySchools analysis changes after you handle the incorrect data.  

### Instructions

1. Create a duplicate of PyCitySchools.ipynb and rename it PyCitySchools_Challenge.ipynb.
2. Correct the students' names so there are no professional prefixes or suffixes.
3. Replace the reading and math scores for ninth graders at Thomas High School with NaN.
    - Use loc on the student\_data_df DataFrame to select the columns by condition.
    - Set the column you want equal to "NaN" by using np.nan for the reading and math scores separately. 
        - To use np.nan, you’ll need to import Numpy with the following: import numpy as np.
    - After you replace the reading and math scores for ninth graders at Thomas High School with NaN, your DataFrame should look like the following (See Challenge original for image).
4. Merge the clean student data with the school dataset. The column order for all the DataFrames and number formatting should be the same as what was covered in this module.
5. After replacing the reading and math scores, complete the following steps and answer the questions for each step.
    - Recreate the district and school summary DataFrames.
        - **How is the district summary affected?**
            - **BEFORE DATA CLEANUP**
            - Average Math Score, Average Reading Score, % Passing Math, % Passing Reading, % Overall Passing
            - 79.0, 81.9, 75, 86, 65
            - **AFTER DATA CLEANUP**
            - Average Math Score, Average Reading Score, % Passing Math, % Passing Reading, % Overall Passing
            - 78.9, 81.9, 74, 85, 64
            - **OBSERVATION:** Slight downward change in district averages
        - **How is the school summary affected?**
            - BEFORE CLEANUP: Thomas High School's % Overall Passing = 91, placing second
            - AFTER CLEANUP: % Overall Passing = 65, placing eighth!
            - **OBSERVATION:** Overall ranking order change due to THOMAS HS, which slipped from 2ND to 13TH position, with the other intervening schools moving up.
    - Recalculate the high- and low-performing schools.
        - **How does replacing the ninth graders’ math and reading scores affect Thomas High School’s performance, relative to the other schools?**
            - **OBSERVATION:** Relative ranking for THOMAS HS changed from 2ND to 8TH, as it's % OVERALL PASSING number decreased from 91% to 65%.
    - Recalculate the scores by grade, scores by school spending, scores by school size, and scores by school type.
        - **How does replacing the ninth-grade scores affect the following?**
            - **Math and Reading Scores by Grade**
                - Thomas HS 9th grade math & reading scores set to "nan" and equivalent to 0
                - Totals for passing math & reading across grades are reduced as all of 9th grade scores are equivalent to failing
                - Average scores calculation not significantly affected by removal of 9th grade scores, seems due to count() function NOT including 9th grade scores = nan
                - Cacluate number of students with a math grade - use "student\_school\_math.groupby(["school_name"]).count()""
                - BEFORE cleanup: Thomas High School       1635
                - AFTER cleanup: Thomas High School       1174
                - "%age passing" score is reduced as Total number of students (denominator) remains unchanged, but total passing value (numerator) is reduced by the number of removed 9th grade scores.
            - **Scores by School Spending**
                - Thomas HS is in the spending bucket "$630-644"
                - Removing 9th grade scores reduces the "% Passing Math", "% Passing Reading" and "% Overall Passing" scores for spending bucket "$630-644" as follows
                - BEFORE: 73, 84, 63
                - AFTER: 67, 77, 56
            - **Scores by School Size**
                - Thomas HS is in the "Medium (1000-2000)" size bucket
                - Removing 9th grade scores reduces the "% Passing Math", "% Passing Reading" and "% Overall Passing" scores for size bucket "Medium (1000-2000)" as follows
                - BEFORE:94, 97, 91 
                - AFTER: 88, 91, 85
            - **Scores by School Type**
                - Thomas HS is in the "CHARTER" type bucket
                - Removing 9th grade scores reduces the "% Passing Math", "% Passing Reading" and "% Overall Passing" scores for type bucket "CHARTER" as follows
                - BEFORE:94, 97, 90 
                - AFTER: 90	93	87
