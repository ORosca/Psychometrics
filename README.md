# Validity Study for Diagnostic Mathematical Assessment using IRT in R
This repository contains an operational psychometrics project focused on the analysis of the DAACS Mathematics Assessment (v2.0) data collected between May 2022 and May 2023 from two combined college samples. The project's primary goal was to evaluate the psychometric properties of 174 math items using unidimensional Item Response Theory (IRT) models and to analyze Differential Item Functioning (DIF) across various demographic groups. The repository includes RMarkdown files documenting the entire research process, from initial data organization and cleaning to missing data analysis, IRT modeling, and logistic regression with factor scores to identify DIF. The included files provide a transparent and reproducible workflow, offering insights into the methodology used to refine the item pool and ensure the validity of the assessment for diverse student populations.

## Math1_Creating Analytic Sample Datasets.Rmd
Purpose: This document details the process of cleaning and organizing DAACS math assessment data collected from two colleges (UMGC1 and UA2) between May 2022 and May 2023. The goal was to create several analytic samples for different types of analyses.

### Key Datasets Created:

Analytic Sample 1 (AnSamp1): Includes first-attempt scores from 4460 non-speedy respondents from UMGC1 (3713) and UA2 (747). This dataset is primarily used for IRT (Item Response Theory) analyses.

Would-be-sample 2022 (sampW22): A subset of AnSamp1 with 2614 students who took the assessment in 2022. This sample is intended for missing data analysis.

Sample 2022 with Demographics (samp22D): A subset of AnSamp1 with 1606 students who took the assessment in 2022 and had at least one demographic data point.

Analytic Sample 2 (AnSamp2): A subset of Sample 22D with 1603 students who took the assessment in 2022 and had non-missing values on all five key demographic variables. This sample is used for DIF (Differential Item Functioning) and age-group comparisons.

### Data Reconciliation: 
The document details how data from the two colleges were combined, including recoding categorical variables like "Military" and "gender" to ensure consistency across the datasets. It also describes a data error fix where item Q157 was a duplicate of Q016 in the UMGC1 data.

## Math2_Items_UniModels_umgc1ua2_AnSamp1.Rmd
Purpose: This Rmd file focuses on the IRT analysis of math assessment scores using the Analytic Sample 1 (AnSamp1) to obtain valid item parameters and student theta scores. The goal was to determine how well the math items fit a unidimensional 2PL IRT model.

### Key Findings:

Model Fit: A 2PL model was found to fit the data better than a 1PL (Rasch) model.

Item Pool Refinement: Out of the initial 174 items, 15 items were removed due to poor psychometric parameters (e.g., very low or very high discrimination and difficulty). The remaining 159 items were found to have a good fit to the unidimensional 2PL IRT model.

Item Parameters: In the 174-item model, 14% of the items had poor discrimination (a-parameters < 0.5), and some had very high difficulty (b-parameters > 6), but these issues were improved in the 159-item model.

Theta Scores: Student theta scores derived from both the 174-item and 159-item models were found to be approximately normally distributed. A paired-samples t-test confirmed no significant difference between the theta scores from these two models.

Student Overlap: The analysis confirmed that different item sets were interconnected by common students, fulfilling a key requirement for a concurrent IRT analysis of multiple item sets.

## Math3_Missing Values Analyses_theta159_sampW22.rmd
Purpose: This document conducts a missing data analysis to address a key research problem: a significant portion of students, particularly from UMGC1, have missing demographic data. The analysis focuses on whether the missingness of age data is related to student theta scores.

### Key Findings:

Missingness Pattern: In the combined sampW22 (n=2614), 38.6% of demographic data was missing, with umgc1 students accounting for 52% of the missingness. In contrast, only 3.7% of ua2 students had missing demographic data. Little’s MCAR (Missing Completely at Random) test rejected the null hypothesis for both the combined sample and the college-specific subsamples, indicating that the data are not missing randomly. Instead, the missingness is systematically associated with the college variable.

Impact on Theta Scores:
Combined Sample: A Wilcoxon rank sum test showed a statistically significant difference in theta scores between students with and without age data (p < 0.001). However, the effect size (Cliff's Delta = 0.23) was "Very Small" and practically negligible. This "spurious correlation" is attributed to the systematic missingness from UMGC1, which has different student demographics.
Subsamples (UMGC1 & UA2): When analyzed separately, both college subsamples showed no statistically significant impact of missing age data on theta scores (p > 0.6 and p > 0.43, respectively). The missingness was therefore considered MCAR (Missing Completely at Random) within each college.

## Math4_DIF Analyses_theta159_AnSamp2.Rmd
Purpose: This file details the Differential Item Functioning (DIF) analysis for the DAACS Math assessment. The primary goal was to evaluate 174 math items for DIF across two age groups: "Adult Undergraduates (AUS, ≥ 24 y.o.)" and "Traditional College-age Undergraduates (TCAUS, < 24 y.o.)".

### Key Findings:

Item Pool Refinement: Out of the initial 174 items, 91 were identified as "good" items that did not exhibit DIF based on age. These items had acceptable psychometric properties (a-parameters between 0.36 and 2.5, b-parameters between -2.3 and +1.8) and showed no DIF for age groups according to logistic regression and graphical analysis.

DIF for Age: The logistic regression analysis, which serves as a statistical test for DIF, was run for both the full 174-item pool and a reduced 159-item pool. The results from the 174-item model and the 159-item model were used to identify the 91 items that did not show DIF with respect to the age variable.

Demographic Distribution: The document also includes descriptive statistics for the Analytic Sample 2, detailing the distribution of age, gender, transfer status, military status, SES, and ethnicity. For instance, the sample consists of 958 TCAUS and 645 AUS students, with males being the majority at 58.7%.

## Math5_91Valid Items_2PLUniModel_AnSamp1.Rmd 
Purpose: Documents the Item Response Theory (IRT) analysis of the DAACS Math Assessment scores from Analytic Sample 1 (n = 4460). The primary goal was to obtain accurate theta-scores (ability estimates) for students using a refined set of 91 "valid" math items. Also compared the fit of a 1PL and a 2PL model and evaluated the psychometric properties of different item pools.

### Key Findings
Model Fit: The analysis found that the 2PL model provided a better fit than the 1PL model for the 91-item pool, as indicated by a significant p-value (< 0.001) in the ANOVA for nested models.

Item Pool Performance: The 91-item pool, which was selected for having good psychometric parameters and no Differential Item Functioning (DIF) for age, showed acceptable parameters. Specifically, the a-parameters ranged from 0.16 to 3.19, and the b-parameters ranged from -2.31 to +2.06. A small percentage of items (6%) were found to have weak discrimination (a-parameter < 0.5).

Theta-Score Distribution: The theta-scores derived from the 91-item model were distributed close to a normal distribution, with a mean of 0.00019 and a standard deviation of 0.73. This distribution was statistically similar to the theta-score distributions from the larger 159-item and 174-item pools, as confirmed by an ANOVA t-test which found no significant difference.

Item Fit and Dependency: The 91-item model demonstrated good local dependency, with Q3 residuals below 0.2. This suggests that after removing items with poor psychometric properties and DIF, the remaining items function well together to measure a single, unidimensional trait.

Data Structure: The analysis confirmed that students in the analytic sample, despite taking different sets of items in an adaptive format, had sufficient overlap to meet the requirements for a concurrent IRT analysis.

## Math6_Missing Values Analyses_theta91_sampW22.rmd
Purpose: This Rmd file continues the missing data analysis, this time using theta scores derived from the 91 "good" items identified in the DIF analysis. The objective is to re-examine the research question of whether missing age data impacts theta scores, but with a refined item pool.

### Key Findings:

Missingness Pattern: The analysis confirms the same missing data pattern as the previous file. 38.9% of students in the combined sample (sampW22) had missing demographic data, with a significant systematic missingness based on college.

Impact on Theta Scores (91-item model):
Combined Sample: Similar to the 159-item model, a Wilcoxon rank sum test on the theta scores from the 91-item model showed a statistically significant difference between groups with and without missing age data (p < 0.001). However, the effect size (Cliff's Delta = -0.19) was again "Very Small," suggesting a negligible practical impact.
Subsamples (UMGC1 & UA2): When the umgc1 and ua2 samples were analyzed separately, the missingness in the age variable did not significantly impact theta scores. The null hypothesis could not be rejected for either college subsample.

### Conclusions: 
The analysis with the 91-item model corroborates the findings from the 159-item model. While there is a statistically significant correlation between missing age data and theta scores in the combined sample, this is primarily a spurious correlation driven by the systematic missingness of demographic data from UMGC1 students, who have different demographic characteristics from UA2 students.

