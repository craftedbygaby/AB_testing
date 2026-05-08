![Logo](logo/logo.png)
# Vanguard Project 


**Vanguard Project** is an A/B testing analysis project developed as part of the **IronHack Data Analytics Bootcamp**. The project evaluates whether Vanguard’s redesigned digital interface improved client process completion compared with the traditional interface by analysing completion, speed, friction, and user progression through the online journey. 

---

## Team
- Gabriela Cascioness
- Hina Haq
- Jorge Barrios Hurtado


---

## Project Context

Vanguard launched a digital experiment to test whether a more modern interface with in-context prompts could improve the client experience and increase the number of users who completed the online process. The A/B test ran from March 15, 2017 to June 20, 2017, comparing a **Control** group using the old interface with a **Test** group using the redesigned version. 

---

## Data Sources

The analysis was based on four provided datasets that were cleaned, explored, and merged to build the final analysis tables. 

| Dataset | Description | Notes |
|---|---|---|
| `df_final_demo` | Client demographic data including age, gender, tenure, number of accounts, balance, calls, and logons | 70,609 rows |
| `df_final_experiment_clients` | Group assignment data indicating whether a client belonged to the Control or Test group | 70,609 rows |
| `df_final_web_data_pt_1` | First part of Vanguard web interaction data | 343,141 rows|
| `df_final_web_data_pt_2` | Second part of Vanguard web interaction data | 412,264 rows|

After merging the two web datasets, the combined digital footprint table contained 755,405 rows before duplicate removal. 

---

## Data Cleaning

The data preparation stage focused on making the four datasets consistent, analysis-ready, and suitable for A/B testing. 

### Steps Applied

- Merged the two web datasets into one combined table. 
- Joined web data with demographic and experiment assignment datasets. 
- Converted `date_time` fields into datetime format. 
- Standardised the process-step labels and mapped them into numeric order. 
- Removed duplicate rows from the merged web data. 
- Identified rows without group assignment and excluded them from experiment comparison. 
- Filtered sessions longer than 30 minutes as inactive outliers. 
- Created derived variables including `step_num`, `time_spent`, `prev_step_num`, and `is_error`. 

### Key Result

The cleaned experiment dataset used for KPI analysis and hypothesis testing contained 317,235 rows. 

---

## KPI Definitions

- **KPI 1 — Completion Rate:** Completion rate measured the percentage of visits that reached the `confirm` step. 
- **KPI 2 — Average Time Spent per Step:** Average time spent per step measured the average time users spent on each stage of the process. 
- **KPI 3 — Error Rate:** Error rate measured the percentage of backward movements made by users during the process. 
- **KPI 4 — Drop-Off Rate by Step:** Drop-off rate by step measured the percentage of users who left the process at each stage before confirmation. (dropped)
- **KPI 5 — Average Steps Reached:** Average steps reached measured how far users progressed on average through the process. (dropped)

---

## KPI Findings

- **Completion Rate:** The Control group achieved a completion rate of 51.91%, while the Test group reached 65.54%, producing an improvement of 13.63 percentage points and exceeding Vanguard’s 5% success threshold. 
- **Average Time Spent per Step:** The Test group was faster at the beginning of the process, especially at Step 1, but users spent more time at the `confirm` step in the redesigned interface. 
- **Error Rate:** The Test group had higher error rates at Steps 1 and 2, but a much lower error rate at Confirm., indicating that the new UI did not reduce friction. 
- **Drop-Off Rate by Step:** The Test group experienced lower drop-off at important stages of the funnel, especially from `step_3` to `confirm`, where drop-off was 2.1% compared with 12.3% in the Control group. 
- **Average Steps Reached:** The Test group reached an average furthest step of 3.90, compared with 3.51 in the Control group, showing deeper progression through the process. 

---

## Hypothesis Testing

### H1 — Completion Rate

- **Null Hypothesis (H0):** The completion rate of the Test group is less than or equal to the completion rate of the Control group. 
- **Alternative Hypothesis (H1):** The completion rate of the Test group is greater than the completion rate of the Control group. 
- **Test Used:** One-sided two-proportion z-test. 
- **Result:** `z = 35.04`, `p < 0.000001`. 
- **Conclusion:** The null hypothesis was rejected, showing that the redesigned interface significantly improved completion rate. 

### H2 — Time Spent per Step

- **Null Hypothesis (H0):** The Test group time is greater than or equal to the Control group time. 
- **Alternative Hypothesis (H1):** The Test group time is less than the Control group time. 
- **Test Used:** Step-level comparison of average time spent. 
- **Result:** Start, Step 2, and Step 3 showed statistically significant improvements, while Step 1 and Confirm did not.
- **Conclusion:** The redesigned interface did not consistently reduce time across the entire process. 

### H3 — Error Rate

- **Null Hypothesis (H0):** The error rate of the Test group is greater than or equal to the error rate of the Control group. 
- **Alternative Hypothesis (H1):** The error rate of the Test group is lower than the error rate of the Control group. 
- **Test Used:** One-sided two-proportion z-test.
- **Conclusion:** The null hypothesis could not be rejected because the Test group showed a higher error rate than the Control group. 

---

## Experiment Evaluation 

### Design Effectiveness

The experiment used a clear Control versus Test structure, and rows without valid group assignment were removed to keep comparisons clean. The presentation notes that the groups were not perfectly equal in size, with roughly 3,000 more observations in the Test group, and the assignment method was not documented, which leaves a small risk of bias. 

### Demographic Balance

No strong demographic bias was detected across age, gender, tenure, balance, or number of accounts according to the presentation and supporting analysis. 

### Duration

The experiment ran for roughly three months, which was considered adequate for gathering insights, although seasonal effects cannot be completely ruled out. 

### Additional Data Needs

More detailed step-flow rules, clearer app context, and better information about user goals would support stronger recommendations in future analyses. 

---

## Client Behaviour Analysis

The project also included a behavioural analysis to better understand how users moved through the online process and how far they progressed before dropping off or confirming. This helped connect the KPI results to actual user behaviour rather than looking only at final completion outcomes. 

---

## Tools Used

- **Python** — data cleaning, KPI analysis, and hypothesis testing. 
- **Pandas** — data manipulation and merging. 
- **SciPy / statistical testing tools** — hypothesis testing. 
- **Jupyter Notebook** — project notebooks and analysis workflow. 
- **Tableau** — dashboard and visual presentation of experiment results. 
- **Git / GitHub** — version control and project collaboration. 
- **Trello** — task management and team coordination. 

---

## How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/Hina-Haq/AB_testing.git
   cd AB_testing
   ```
2. Open the Jupyter notebooks used for cleaning, KPI analysis, and hypothesis testing. 
3. Run the notebooks in sequence after making sure the required datasets are stored in the expected project folders. 
4. Use the cleaned outputs for Tableau visualisation and final presentation work. 

---

## Links

- GitHub repository: https://github.com/Hina-Haq/AB_testing.
- Slides: Add your final online slide link here(revise).
- Trello / Kanban board: https://trello.com/invite/b/69ef923173719181b9143496/ATTI3b9cd3871ebfec777a2d1cf64cf0bd974EBB3361/vanguard-a-b-test-analysis-slytherin.
-Tableau dashboard link: https://public.tableau.com/app/profile/jorge.barrios.hurtado/viz/Vanguard_ABTest_Dashboard/Dashboard1?publish=yes

---
**For a more detailed discussion of the project’s strengths, limitations, recommendations, and next steps, please refer to the presentation file.** 

---

**This project was developed for educational and portfolio purposes as part of the IronHack Data Analytics Bootcamp.** 
