# Cardiovascular Disease Analysis

## Project Overview

This project performs an exploratory analysis of cardiovascular disease (CVD) patient data using Python, Pandas, Matplotlib, and Seaborn. The goal is to understand which factors may be linked to cardiovascular disease using a dataset of 70,000 patient records from the mlcourse.ai Assignment #2.

## Dataset

The dataset contains 70,000 patient records with the following features:

### Objective Features
- **age**: Age in days (integer) - range: 10,798 to 23,713 days (30.0 to 65.0 years)
- **height**: Height in centimeters (integer) - range: 55 to 250 cm
- **weight**: Weight in kilograms (float) - range: 10.0 to 200.0 kg
- **gender**: Categorical code (1 = women, 2 = men) - gender 1: 45,530 people, gender 2: 24,470 people
- **ap_lo**: Diastolic blood pressure (integer)
- **ap_hi**: Systolic blood pressure (integer)
- **cholesterol**: Cholesterol level (integer: 1 = normal, 2 = above normal, 3 = well above normal)
- **gluc**: Glucose level (integer: 1 = normal, 2 = above normal, 3 = well above normal)

### Subjective Features
- **smoke**: Smoking status (binary: 0 = no, 1 = yes)
- **alco**: Alcohol consumption (binary: 0 = no, 1 = yes)
- **active**: Physical activity (binary: 0 = no, 1 = yes)
- **cardio**: Cardiovascular disease status (binary target variable: 0 = no, 1 = yes)

70% of patients have CVD, 30% do not.

## Tools Used

- **Python**: Programming language
- **Pandas**: Data manipulation and analysis
- **NumPy**: Numerical calculations
- **Matplotlib**: Plotting library
- **Seaborn**: Statistical data visualization

## Project Steps

### Step 1: Load the Data

Loaded the dataset `mlbootcamp5_train.csv.csv` (semicolon-separated) from the project folder. Dataset contains 70,000 records and 13 columns.

### Step 2: Preliminary Data Analysis

**Gender Distribution:** 45,530 women (gender 1) and 24,470 men (gender 2). Men are taller on average (169.9 cm vs 161.4 cm), confirming the gender code assumption.

**Alcohol Consumption:** 5.4% of both men and women report consuming alcohol (3,764 drinkers each).

**Smoker Percentages:** Men: 21.9% smoke; Women: 1.8% smoke. **Difference: 20 percentage points more men smoke than women.**

**Age Difference (Smokers vs Non-smokers):** Median age smokers: 52.0 years; Median age non-smokers: 54.0 years. **Difference: -24 months** (smokers are younger on average).

### Step 3: BMI Calculation

Calculated BMI using the formula: `BMI = weight in kg / (height in meters)^2`, where height in meters = height_cm / 100.

**BMI Results:**
- Median BMI: 26.4 (within the "overweight" range)
- Normal BMI (18.5-25): 25,804 people (36.9% of sample)
- BMI by gender: Men: median 25.9, Women: median 26.7
- BMI by CVD status: No CVD: median 25.5, With CVD: median 27.5
- Statement 1: **True** - Median BMI (26.4) is above the normal range (18.5-25)
- Statement 2: **False** - Men's BMI (25.9) is slightly lower than Women's (26.7)
- Statement 3: **False** - Healthy people (BMI 25.5) have lower BMI than people with CVD (BMI 27.5)
- Statement 4: Not assessed directly

### Step 4: Data Cleaning

Filtered out erroneous data records:

1. **Diastolic > systolic pressure:** Removed 1,234 records (1.8% of data)
2. **Height outside 2.5th-97.5th percentile:** Removed 2,907 additional records
3. **Weight outside 2.5th-97.5th percentile:** Removed 3,075 additional records

**Total data removed: 10%** of original 70,000 records. Cleaned dataset: 62,784 records.

### Step 5: Correlation Analysis

**Pearson Correlation with CVD:**
- Age: 0.2382
- BMI: 0.1656
- Cholesterol: 0.2211
- Systolic BP (ap_hi): 0.0545
- Diastolic BP (ap_lo): 0.0657
- Gluc: 0.0893
- Weight: 0.1817
- Height: -0.0108

**Spearman Correlation with CVD:**
- Age: 0.2344
- BMI: 0.1991
- Cholesterol: 0.2151
- Systolic BP (ap_hi): 0.4519
- Diastolic BP (ap_lo): 0.3626
- Gluc: 0.0915
- Weight: 0.1827
- Height: -0.0124

**Key findings:**
- Systolic blood pressure has the strongest Spearman correlation with CVD (0.4519)
- Cholesterol has strong both Pearson (0.2211) and Spearman (0.2151) correlation
- Age has moderate correlation with CVD in both Pearson (0.2382) and Spearman (0.2344)
- BMI has weak-moderate Pearson correlation (0.1656) but stronger Spearman (0.1991)

### Step 6: Age-Based Analysis

**Age distribution by CVD status:** Created count plots showing the number of people by age (in years) and CVD status.

**Smallest age where CVD outnumbers non-CVD:** **55 years** (at age 55: 815 people with CVD vs 683 without CVD).

### Step 7: Created Charts

The following charts were generated:

1. **Age distribution by CVD status** - Count plot showing two columns for each age representing CVD vs no CVD
2. **BMI distribution** - Histogram of BMI values with normal range (18.5-25) highlighted
3. **Pearson correlation heatmap** - Matrix of correlation coefficients between features
4. **Spearman correlation heatmap** - Matrix of rank correlation coefficients
5. **Height distribution by gender** - Violin plot comparing height distributions of men and women

## Key Results

| Analysis | Result |
|----------|--------|
| **Gender distribution** | 45,530 women (1) and 24,470 men (2) |
| **Alcohol consumption** | 5.4% of both genders |
| **Smoker difference** | 20 percentage points (men smoke more) |
| **Median age difference** | -24 months (smokers younger) |
| **CVD prevalence** | 50.0% (34,979 with CVD, 35,021 without) |
| **Median BMI** | 26.4 (overweight range) |
| **Normal BMI** | 25,804 people (36.9%) |
| **Data cleaned** | 10% removed (62,784 records remaining) |
| **Smallest age CVD > non-CVD** | 55 years |
| **Strongest Pearson correlation with CVD** | Age (0.2382) |
| **Strongest Spearman correlation with CVD** | Systolic BP (0.4519) |

## Charts Generated

- `age_distribution.png` - Age distribution by CVD status
- `bmi_distribution.png` - BMI histogram
- `correlation_heatmap.png` - Pearson correlation matrix

## Notes

- The dataset is from the [mlcourse.ai](https://mlcourse.ai) Open Machine Learning Course, Assignment #2
- All calculations are performed on the actual 70,000-record dataset - no synthetic data invented
- Analysis explores correlations, not causation
- These results are not intended for medical diagnosis
- Age is in days in the original dataset, converted to years (rounded) for analysis
- BMI formula: weight(kg) / (height(m))^2, where height(m) = height(cm) / 100

## Files in This Project

- `a2-demo-analyzing-cardiovascular-data.ipynb` - Original notebook template
- `a2-demo-analyzing-cardiovascular-data-final.ipynb` - Completed notebook with all code cells
- `a2-demo-analyzing-cardiovascular-data-completed.ipynb` - Earlier completed version
- `cardiovascular-disease-analysis-plan.md` - Project plan document
- `cardiovascular/` - Git subdirectory
- `mlbootcamp5_train.csv.csv` - Dataset (semicolon-separated, double-extended name)
- `README.md` - This file
- `age_distribution.png` - Age distribution chart
- `bmi_distribution.png` - BMI distribution chart
- `correlation_heatmap.png` - Correlation heatmap chart