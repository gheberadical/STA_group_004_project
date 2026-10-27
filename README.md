# STA_group_004_project

This is the repository for the group project of Statistical Data Analysis for group 004.

## Group Members
- Marta Guzmán Alarcón
- Rares-Costin Haritonov
- Gabriele Bazzanella Bauer

---

## Project Scope & Objectives

The scope of the project is to analyze a Statistics Finland time-use teaching dataset for a client to answer four main research questions:

1. **Demographic Characterization:** Characterize the individuals present in the data.
2. **Time Allocation:** Estimate how much time on average Finnish households spend daily on each activity.
3. **Group Differences:** Determine with respect to which activities living environments (city, municipality, rural) or days of the week (working day vs. weekend) differ in Finland.
4. **Activity Associations:** Identify which daily activities are associated with each other in the Finnish population.

*Detailed information on how the dataset is structured and explanations of all variables can be found in the file `habits.txt`.*

---

## Dataset & Variables Overview

The dataset consists of 745 person-day observations collected across 378 unique individuals/households.

### Primary Variables
- **Demographics:** Household ID (`kohde`), Member ID (`jasen`), Sex (`sp`), Age Group (`IKAL1`), Living Environment (`ASALUE`: City, Municipality, Rural).
- **Day Type:** Day of diary entry (`pvknro`: Working day vs. Weekend).
- **Time Use (minutes/day):** Working (`A1`), Sleeping (`A2`), Reading (`A3`), Dining at a Restaurant (`A4`).
- **Binary Indicator:** Library visit within the past 12 months (`A5`: Yes / No).

---

## Analytical & Statistical Pipeline

1. **Data Preprocessing & Validation:**
   - Standardized mixed time representation formats (`HH:MM` and continuous integer minutes).
   - Validated physical daily time limits (maximum 1,440 minutes per person-day).

2. **Exploratory & Dimensionality Reduction:**
   - Evaluated distribution properties, skewness, and non-normality across activities.
   - Conducted Principal Component Analysis (PCA) on standardized activity times to analyze underlying time-allocation structures (e.g., Work vs. Rest trade-offs).

3. **Hypothesis Testing & Statistical Inference:**
   - **Day-Type Variations:** Paired Wilcoxon signed-rank tests for working day vs. weekend comparisons within households.
   - **Environment Variations:** Kruskal-Wallis tests across living environments and Pearson's Chi-Square tests for library visitation rates.
   - **Correlation Analysis:** Spearman's rank correlation matrices split by working days and weekends.
   - **Multiple Testing Correction:** Applied Benjamini-Hochberg False Discovery Rate (FDR) adjustments across test families ($q < 0.05$).

---

## Key Findings

- **Average Daily Allocation (Weighted 5/7 Weekday, 2/7 Weekend):**
  - **Sleeping:** ~8.6 hours (517.4 min/day)
  - **Working:** ~2.0 hours (122.1 min/day across general population sample)
  - **Reading:** ~46.6 min/day
  - **Dining Out:** ~45.6 min/day
- **Day of Week Effect:** Weekend time spent reading ($p_{\text{fdr}} \approx 0.022$) and dining at restaurants ($p_{\text{fdr}} \approx 0.0008$) is significantly higher than on weekdays. Working and sleeping show no statistically significant day-type difference after FDR control.
- **Living Environment:** Living environment (city, municipality, rural) shows no statistically significant impact on time allocation across activities or library visitation rates (~68.8% overall annual attendance).
- **Activity Trade-offs:** Time spent working exhibits moderate negative correlations with sleeping ($\rho \approx -0.38$ to $-0.42$) and weak negative correlations with reading ($\rho \approx -0.16$ to $-0.22$), reflecting standard time budget constraints.

---

## License & Attribution

The dataset is derived from the Time Use Survey provided by Statistics Finland under the [Creative Commons Attribution 4.0 International License (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).
