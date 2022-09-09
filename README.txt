## Treatment Groups
Note that treatment and control groups vary between years.

| Year | Control | Treatment |
| ---  | ---     | ---       |
| 2017 | Late    | Early     |
| 2018 | Late    | Early     |
| 2019 | Early   | Late      |

## Data Workflow

1. Preprocess
    1. 01 Preprocess Grades - Extracts grades for relevant assignments
        * Up to 10 points are added to student grades on invididual assignments to
            adjust for bonuses given to grades on teamwork assignments.
        * Input: grades csv
        * Input: data/grades/yyy/Working groups and pairings/group_assignments.csv
        * Output: preprocessed/grades_yyyy.csv
    2. 01 Preprocess Students - Extracts year and program
        * Input: data/students/yyyy_year.csv
        * Output: preprocessed/student_yyyy_year.csv
    3. 01 Preprocess Survey - Convert responses to numeric likert
        * Input: data/SI301 Fall YYYY Feedback Form (TREATMENT Teamwork Group)
        * Output: preprocessed/SI301 Fall YYYY Feedback Form (TREATMENT Teamwork Group)
2. Survey Analysis
    1. 02_plot_histograms_yyyy.ipynb - Analyze survey for each year
        * Input: preprocessed/SI301 Fall YYYY Feedback Form (TEATMENT Teamwork Group)
        * Output: Mann-Whitney U test and histogram images
    2. 02_plot_histograms_all.ipynb - Analyze all surveys together
        * Only includes 2017-2018 because treatment group in 2019 was after the survey
3. Grade Analysis
    1. 03_analyze_grades_yyyy.ipynb
        * Input: preprocessed/grades_yyyy.csv
        * Output: histograms and t-tests for midterm and final
    2. 03_analyze_grades_all.ipynb
        * Input: preprocessed/grades_yyyy.csv
        * Output: histograms and t-tests for final
4. Regression
    1. 04 Regression.ipynb
        * Input: preprocessed/grades_yyyy.csv
        * Input: preprocessed/student_yyyy_year.csv
        * Output OLS regressions
        * Currently includes controls for year, grade level, degree program.

## TODO

* Is the bonus point adjustment in Preprocess Grades correct?
* Confirm 2019 treatment group was the late teamwork group and this year should be
    excluded from survey analysis.
* Are points deducted for late assignments?