# 📜 Derivable Judgement — A Statistical Decision Making Model

> *"In matters of great consequence, one ought never to proceed upon conjecture alone,*
> *but to arm oneself with the full weight of evidence and rigorous enquiry."*

---

## 🎩 Preface

It is with considerable distinction and scholarly devotion that this notebook, entitled **"Derivable Judgement: A Statistical Decision Making Model"**, hath been composed and presented herein. This work undertakes the noble pursuit of applying the most esteemed principles of **Inferential Statistics** upon a **Health Dataset**, so as to extract meaningful conclusions and render sound, evidence-based judgements of the highest academic calibre.

The analysis is divided into two principal parts — a **Theoretical Foundation** and a **Practical Data Analysis** — together forming a most comprehensive and methodical enquiry into the nature of human health indicators.

---

## 🗂️ Table of Contents

1. [Dataset Overview](#-dataset-overview)
2. [Part A — Theoretical Foundation](#-part-a--theoretical-foundation)
3. [Part B — Data Analysis & Testing Tasks](#-part-b--data-analysis--testing-tasks)
4. [Technologies Employed](#%EF%B8%8F-technologies-employed)
5. [Key Findings & Conclusions](#-key-findings--conclusions)
6. [Project Structure](#-project-structure)

---

## 📊 Dataset Overview

The dataset upon which all analyses are conducted is drawn from a **Health Domain** (`health_dataset.csv`), comprising numerous observations pertaining to the physical constitution and medical conditions of individuals. The principal variables of interest are as follows:

| Variable | Nature | Description |
|---|---|---|
| `age` | Continuous | Age of the individual in years |
| `weight` | Continuous | Body weight measurement |
| `bmi` | Continuous | Body Mass Index |
| `blood_pressure` | Continuous | Systolic blood pressure reading |
| `cholesterol_level` | Continuous | Serum cholesterol level |
| `glucose_level` | Continuous | Blood glucose measurement |
| `smoking_status` | Categorical | Smoking habit classification |
| `diabetes` | Categorical | Presence or absence of diabetes |
| `exercise_frequency` | Categorical | Frequency of physical exercise |

---

## 📚 Part A — Theoretical Foundation

This section layeth the intellectual groundwork upon which all subsequent analysis doth rest. The following concepts have been most diligently examined and explained:

### 1. 🔬 Inferential Statistics
The branch of statistics that permitteth one to draw conclusions about a **population** through the careful examination of a **sample** — a most powerful instrument of scientific reasoning.

### 2. 🧪 Hypothesis Testing
A formal statistical procedure by which one evaluateth assumptions about population parameters. Its principal components are:

- **Null Hypothesis (H₀)** — The default claim, presuming no effect or difference.
- **Alternate Hypothesis (H₁)** — The proposition one seeketh to establish through evidence.

### 3. 📐 Confidence Interval & Critical Value
- A **Confidence Interval** furnisheth a range of plausible values for the true population parameter at a stated level of certainty (e.g., 95%).
- A **Critical Value** marketh the boundary beyond which the Null Hypothesis is to be rejected (z = ±1.96 at α = 0.05, two-tailed).

### 4. 📉 P-Value
The probability of observing the given data — or data more extreme — under the assumption that H₀ is true.
- **p < 0.05** → Reject H₀ *(statistically significant)*
- **p ≥ 0.05** → Fail to Reject H₀ *(insufficient evidence)*

### 5. ⚠️ Type I & Type II Errors

| Error | Also Called | Meaning |
|---|---|---|
| **Type I** | False Positive | Rejecting H₀ when it is, in truth, **correct** |
| **Type II** | False Negative | Failing to reject H₀ when it is, in truth, **false** |

### 6. 🧮 Statistical Tests at a Glance

| Test | When to Apply |
|---|---|
| **Z-Test** | Large samples (n > 30), known population σ |
| **T-Test** | Small samples (n < 30) or unknown σ |
| **Chi-Square Test** | Independence between two categorical variables |
| **ANOVA** | Comparing means across three or more groups |

### 7. 🔗 Covariance & Correlation
- **Covariance** measureth the directional relationship between two variables (+, −, or near zero).
- **Pearson Correlation (r)** furnisheth a standardised, interpretable score ranging from −1 to +1, quantifying both the direction and the strength of the linear association.

---

## 🔬 Part B — Data Analysis & Testing Tasks

### ✅ Task 1 — Hypothesis Formulation

Two hypotheses of clinical significance were formulated for empirical testing:

**Hypothesis 1 — Chi-Square Test**
> H₀: Smoking status hath *no* bearing upon the prevalence of diabetes.
> H₁: Smoking status *doth significantly* affect diabetes prevalence.

**Hypothesis 2 — T-Test**
> H₀: The mean BMI of Smokers and Non-Smokers is the *same*.
> H₁: The mean BMI of Smokers and Non-Smokers is *different*.

---

### 📏 Task 2 — Confidence Intervals

Confidence Intervals were computed for key numerical health metrics, with particular attention given to **BMI**, following the classical methodology:

1. Computation of the **sample mean** and **standard deviation** from first principles.
2. Derivation of the **Standard Error (SE)**.
3. Application of the **z-critical value (1.96)** at 95% confidence.
4. Determination as to whether the hypothesised population mean (μ = 25) doth fall within the computed interval.

---

### 🎯 Task 3 — Critical Values & P-Values

Critical values were derived via `scipy.stats` for both the **Z-distribution** and the **T-distribution**, encompassing:
- Two-tailed, Right-tailed, and Left-tailed configurations.
- P-values computed via `statsmodels` Z-test on the BMI variable against the benchmark of μ = 25.

---

### ⚖️ Task 4 — Z-Test & T-Test

Both tests were applied upon the `bmi` column with full transparency of computation:

**One-Sample T-Test** *(population σ unknown)*
> Compared sample mean BMI against the healthy benchmark threshold of **25**.

**One-Sample Z-Test** *(population σ assumed known, σ = 2.5)*
> Compared mean BMI against a population mean of **70** — serving as a didactic demonstration of z-test application on large samples.

In each instance, the test statistic, p-value, and critical value were presented alongside a clear Accept/Reject decision.

---

### 🔢 Task 5 — Chi-Square Tests

Two chi-square procedures were executed upon the categorical variables:

**Goodness of Fit Test**
> Examined whether the `smoking_status` categories are uniformly distributed across the dataset.

**Test of Independence**
> Examined whether `smoking_status` and `diabetes` are statistically independent.
> The contingency table, expected frequencies, χ² statistic, degrees of freedom, and p-value were all meticulously calculated — both by manual formula and by `scipy.stats`.

---

### 📊 Task 6 — One-Way ANOVA

ANOVA was employed to determine whether **cholesterol levels** differ significantly across groups defined by **exercise frequency** (Daily, Weekly, Rarely, Never).

Computed from first principles:
- **Sum of Squares Between (SSB)** and **Within (SSW)** groups
- **Mean Square** values, **F-statistic**, and **Critical F-value**
- Confirmed using `scipy.stats.f_oneway`

> H₀: μ_Daily = μ_Weekly = μ_Rarely = μ_Never
> H₁: At least one group mean differeth significantly.

---

### 🔗 Task 7 — Covariance & Correlation

**Covariance Analysis** was conducted between `bmi` and `blood_pressure`, computed both manually and via `numpy`. A full **Covariance Matrix** was then constructed for all six continuous variables and rendered as a **Seaborn heatmap**.

**Pearson Correlation Analysis** was similarly executed — manually, via `numpy.corrcoef`, and via `scipy.stats.pearsonr` — with interpretation of both the correlation coefficient and its associated p-value. A comprehensive **Correlation Matrix heatmap** was produced for visual inspection.

---

### 📋 Task 8 — Summary of Results

A consolidated summary table of all statistical tests was produced, presenting:

| # | Test | Variables | Decision Rule |
|---|---|---|---|
| 1 | One-Sample Z-Test | BMI vs μ = 25 | p < 0.05 → Reject H₀ |
| 2 | Two-Sample T-Test | BMI: Smokers vs Non-Smokers | Based on p-value |
| 3 | Chi-Square Test | Smoking vs Diabetes | Based on p-value |
| 4 | Chi-Square Test | Exercise vs Hypertension | Based on p-value |
| 5 | One-Way ANOVA | Cholesterol ~ Exercise Frequency | p < 0.05 → Reject H₀ |
| 6 | Pearson Correlation | Age, BMI, BP, Glucose, etc. | Multiple variable pairs |

> **General Rule of Decision:** If p-value < 0.05 → Reject H₀ (statistically significant). If p-value ≥ 0.05 → Fail to Reject H₀ (insufficient evidence).

---

## 🛠️ Technologies Employed

```python
import numpy as np           # Numerical computation
import pandas as pd          # Data manipulation
import matplotlib.pyplot as plt  # Visualisation
import seaborn as sns        # Statistical heatmaps
import scipy                 # Statistical testing
from scipy import stats
from statsmodels.stats.weightstats import ztest
```

| Library | Version | Purpose |
|---|---|---|
| `NumPy` | Latest | Array operations & manual statistics |
| `Pandas` | Latest | Data ingestion & manipulation |
| `Matplotlib` | Latest | Plotting & visualisation |
| `Seaborn` | Latest | Correlation & covariance heatmaps |
| `SciPy` | Latest | Z, T, Chi-Square, ANOVA & F-distributions |
| `Statsmodels` | Latest | Z-test via `weightstats` |

---

## 🏁 Key Findings & Conclusions

This notebook doth stand as a thorough and commendable demonstration of applied inferential statistics upon real-world health data. The following accomplishments merit particular note:

- 🎯 **Confidence Intervals** were rigorously computed for key numerical health metrics, grounding all subsequent inference in sound probability theory.
- ⚖️ **Z-Test & T-Test** were applied with complete transparency, distinguishing their appropriate conditions of use and yielding clear Accept/Reject decisions.
- 🔢 **Chi-Square Tests** illuminated the relationship between smoking behaviour and diabetes — a matter of genuine public health significance.
- 📊 **One-Way ANOVA** examined whether exercise frequency is associated with measurable differences in cholesterol, a question of considerable clinical import.
- 🔗 **Covariance & Pearson Correlation** matrices revealed the directional and strength-based relationships amongst all continuous health indicators, visualised with elegance through heatmap representations.

In summation, the work exemplifieth the principled application of statistical reasoning — from the formulation of hypotheses to the drawing of evidence-based conclusions — and shall serve as a most valuable reference for any scholar engaged in data-driven enquiry into matters of health and wellbeing.

---

## 📁 Project Structure

```
📦 Statistical_Decision_Making_Model/
├── 📓 A_Statistical_Decision_Making_Model.ipynb   ← Main Analysis Notebook
├── 📊 health_dataset.csv                          ← Source Dataset
└── 📜 README.md                                   ← This very document
```

---

*"The facts speak most eloquently when one hath taken the trouble to listen with rigour."*

**Crafted with scholarly diligence | Statistical Decision Making | Inferential Analysis**
