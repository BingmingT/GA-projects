# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 1: Standardized Test Analysis

### Problem Statement

Resources allocation for education in the USA can often be limited. When additional funding is provided, determining which areas of education to target to provide the most improvement can help streamline and optimise the process to ensure the best return.

In this project, we seek to look at the performance by students across the USA to determine if performance in English or Math is poorer and which may benefit from more funding.

---

### Datasets

* [`act_2017.csv`](./data/act_2017.csv): 2017 ACT Scores by State ([source](https://blog.prepscholar.com/act-scores-by-state-averages-highs-and-lows))
* [`sat_2017.csv`](./data/sat_2017.csv): 2017 SAT Scores by State ([source](https://blog.collegevine.com/here-are-the-average-sat-scores-by-state/))
* [`sat_2018.csv`](./data/sat_2018.csv): 2018 SAT Scores by State ([source](https://blog.collegevine.com/here-are-the-average-sat-scores-by-state/))

---

### Data Dictionary
|Feature|Type|Dataset|Description|
|---|---|---|---|
|**state**|*object*|SAT 2017/2018|States of the US in 2 letter state abbreviations (AL = Alabama)|
|**sat_2017_participation**|*float*|SAT 2017|Number of students in their cohort who took part in the 2017 SATs (units in decimal approximations of percentages 0.80 means 80% |
|**sat_2017_english**|*int*|SAT 2017|Mean score for the Evidence-Based Reading and Writing portion of the 2017 cohort within the state (min of 200, max of 800)|
|**sat_2017_math**|*int*|SAT 2017|Mean score for the Math portion of the 2017 cohort within the state (min of 200, max of 800)|
|**sat_2017_total**|*int*|SAT 2017|Mean total SAT score of the 2017 cohort within the state (min of 200, max of 800)|
|**sat_2018_participation**|*float*|SAT 2018|Number of students in their cohort who took part in the 2018 SATs (units in decimal approximations of percentages 0.80 means 80% |
|**sat_2018_english**|*int*|SAT 2018|Mean score for the Evidence-Based Reading and Writing portion of the 2018 cohort within the state (min of 200, max of 800)|
|**sat_2018_math**|*int*|SAT 2018|Mean score for the Math portion of the 2018 cohort within the state (min of 200, max of 800)|
|**sat_2018_total**|*int*|SAT 2018|Mean total SAT score of the 2018 cohort within the state (min of 200, max of 800)|
|**act_2017_participation**|*float*|ACT 2017|Number of students in their cohort who took part in the 2017 ACTs (units in decimal approximations of percentages 0.80 means 80% |
|**act_2017_english**|*float*|ACT 2017|Mean score for the English portion of the 2017 cohort within the state (min of 1, max of 36)|
|**act_2017_math**|*float*|ACT 2017|Mean score for the Math portion of the 2017 cohort within the state (min of 1, max of 36)|
|**act_2017_read**|*float*|ACT 2017|Mean score for the Reading portion of the 2017 cohort within the state (min of 1, max of 36)|
|**act_2017_science**|*float*|ACT 2017|Mean score for the Science portion of the 2017 cohort within the state (min of 1, max of 36)|
|**act_2017_composite**|*float*|ACT 2017|Mean Composite score of the 2017 cohort within the state, calculated by taking mean of the 4 individual sections (min of 1, max of 36)|

---

### Analysis

The data was combined and reviewed for correlations to determine any initial areas of interest.

Due to the ambiguity of the read section for the ACT and its relatedness to the subject of English, an aggregate mean of the ACT English, and the ACT Reading scores were used to determine English scores for States.

Relationships between participation rates, SAT English and Math scores, and ACT English and Math scores were explored.

Dominance by States in English and Math were examined based on each examination and within each year.

Lastly, scores were normalised according to the highest and lowest mean scores achieved that year by States, to determine performance and volatility within the exams. A normalisation by highest and lowest mean score, rather than the maximum and minimum score, was chosen in order to account for cohort differences, as well as exam difficulty for the years and exams.

---

### Conclusion

States scored poorer in Math than in English almost all across the board through the USA. This is in particular more true, in the States that performed poorer, which is important as those States tended to be the ones with higher participation and larger sample pools.

There was also clear difference between States that perform well in Examinations for English, versus a slight more continuous distribution for Maths. However, this may be primarily due to the spread of English results, versus the more tightly grouped Maths scores.

States should almost all consider allocating more funds to their Math programmes, over their English programmes, if there is a new influx with some exceptions. The lower scores, along with the tight grouping suggests that there is improvement to be had across the board and that even well performing states are not performing as well as they could be, in comparison to English.

However, this may not be true across the board, and we do see a number of States with trailing English scores that are far below mean and in these States, funding the English programme would probably provide higher returns.

Observations were also made on the preference of SATs and ACTs between States. In general, States preferred to take the ACTs, however, this may also be attributed to the recent change in the SAT format in 2016 leading to uncertainty in the grading rubric and a push towards the more reliable exam.

Lastly, observations were made on participation rates and its heavy influence on the State means in the two subjects. More accurate experiments were suggested based on increasing the amount of data about the sample of the study.
