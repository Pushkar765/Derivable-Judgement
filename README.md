# 📜 Derivable Judgement
### *A Statistical Decision Making Model*

> *"That which cannot be measured, cannot be governed — and that which cannot be governed, shall surely lead one astray."*

---

## 🏛️ Table of Contents

- [📖 Overview](#-overview)
- [🔬 Dataset](#-dataset)
- [📚 Part A — Theoretical Foundation](#-part-a--theoretical-foundation)
- [🧪 Part B — Analytical Tasks](#-part-b--analytical-tasks)
- [⚙️ Requirements](#️-requirements)
- [🚀 Usage](#-usage)
- [📊 Summary of Results](#-summary-of-results)
- [🏁 Conclusion](#-conclusion)

---

## 📖 Overview

Permit me to introduce unto thee this most distinguished scholarly undertaking — **Derivable Judgement** — a rigorous statistical decision-making model of considerable academic merit.

This notebook doth traverse the grand landscape of **Inferential Statistics**, employing the most venerable methods of hypothesis testing upon a health-related dataset of notable breadth. From the construction of confidence intervals to the formidable ANOVA examination, every endeavour herein hath been conducted with the utmost scholarly rigour and methodical precision.

---

## 🔬 Dataset

| Property | Detail |
|---|---|
| 📁 **File** | `health_dataset.csv` |
| 🏥 **Domain** | Public Health & Clinical Metrics |
| 📐 **Key Variables** | `bmi`, `blood_pressure`, `cholesterol_level`, `smoking_status`, `diabetes`, `exercise_frequency` |

The dataset doth contain a wealth of health-related observations, permitting one to investigate the intricate relationships betwixt lifestyle habits and clinical outcomes with commendable statistical power.

---

## 📚 Part A — Theoretical Foundation

Before one may embark upon the practical arts of data analysis, it is most proper and fitting that the theoretical underpinnings be thoroughly understood.

### 🎓 1. Inferential Statistics

> *The noble art of drawing conclusions about a great population by examining but a modest sample thereof.*

Inferential Statistics allows the learned scholar to make predictions about a **population** by carefully studying a representative **sample** — a most economical and elegant practice indeed.

---

### 🔍 2. Hypothesis Testing & Its Components

Hypothesis Testing is a formal statistical procedure by which one doth adjudicate the plausibility of claims concerning population parameters.

| Component | Description | Example |
|---|---|---|
| **H₀ — Null Hypothesis** | The default claim; assumes no effect or difference | H₀: μ = 10 (battery life is 10 hours) |
| **H₁ — Alternate Hypothesis** | The proposition one seeks to prove | H₁: μ ≠ 10 (battery life differs from 10 hours) |

---

### 📏 3. Confidence Interval & Critical Value

🔷 **Confidence Interval** — A range of values within which the true population parameter is believed to reside, at a stated level of confidence (e.g., 95%).

🔷 **Critical Value** — The threshold boundary of the test statistic, beyond which one doth reject the Null Hypothesis.

```
For α = 0.05 (two-tailed):
  z-critical = ±1.96
  t-critical  = depends upon degrees of freedom
```

---

### 🎯 4. The P-Value

The **p-value** (probability value) doth reveal how likely it is to observe one's data — or something yet more extreme — assuming the Null Hypothesis to be true.

```
p < 0.05  →  Reject H₀         (Evidence is compelling!)
p ≥ 0.05  →  Fail to Reject H₀ (Insufficient evidence)
```

---

### ⚠️ 5. Type I & Type II Errors

One must always remain vigilant against the twin perils of erroneous inference:

| Error Type | Common Name | Meaning |
|---|---|---|
| **Type I Error** | 🔴 False Positive | Rejecting H₀ when it is actually **TRUE** |
| **Type II Error** | 🔵 False Negative | Failing to reject H₀ when it is actually **FALSE** |

---

### 📐 6. Statistical Tests — A Brief Compendium

| Test | When to Apply | Conditions |
|---|---|---|
| **Z-Test** | Sample mean vs population mean | n > 30, σ known, Normal distribution |
| **T-Test** | Means of 1 or 2 groups | n < 30 or σ unknown, Approximately normal |
| **Chi-Square Test** | Independence of two categorical variables | Expected frequency > 5 per cell |
| **ANOVA** | Comparing means of 3 or more groups | Normal distribution, Equal variances |

---

### 🔗 7. Covariance

**Covariance** doth measure the directional relationship betwixt two variables:

- 📈 **Positive Covariance** — Both variables increase in concert
- 📉 **Negative Covariance** — One increases whilst the other decreases
- ⚖️ **Zero Covariance** — No discernible linear pattern betwixt them

---

### 🧲 8. Correlation

**Pearson Correlation** furnishes a standardised and most interpretable score of relationship strength:

```
r = +1   →  Perfect Positive Linear Relationship   📈
r = -1   →  Perfect Negative Linear Relationship   📉
r =  0   →  No Linear Relationship                 ⚪
```

---

## 🧪 Part B — Analytical Tasks

### ✅ Task 1 — Hypothesis Formulation

Two most illuminating hypotheses were formulated upon the health dataset:

#### 🔬 Hypothesis 1 — Chi-Square Test
```
H₀ : Smoking Status hath NO effect upon diabetes prevalence.
H₁ : Smoking Status SIGNIFICANTLY AFFECTS diabetes prevalence.
```

#### 🔬 Hypothesis 2 — T-Test
```
H₀ : Mean BMI is the SAME for Smokers and Non-Smokers.
H₁ : Mean BMI is DIFFERENT betwixt Smokers and Non-Smokers.
```

---

### 📏 Task 2 — Confidence Intervals

Confidence intervals were computed for the key numerical variable **BMI**, employing the following procedure:

```python
# 95% Confidence Interval for BMI
Mean  = df.sum() / n
StdDev = sqrt(Variance)
SE    = StdDev / sqrt(n)

Lower_CI = Mean - 1.96 * SE
Upper_CI = Mean + 1.96 * SE
```

One doth thereafter test whether the hypothesised mean (μ = 25) falls within or without the computed interval — a most elegant arbiter of statistical plausibility.

---

### 🎯 Task 3 — Critical Values & P-Values

Critical values were derived for each test type using `scipy.stats`, and p-values were computed to adjudicate the acceptance or rejection of each hypothesis:

```python
# Z-Critical (Two-Tailed)
Z_critical = norm.ppf(1 - alpha/2)   # ≈ ±1.96

# T-Critical (Two-Tailed)
T_critical = t.ppf(1 - alpha/2, df)

# P-Value via Z-Test
z_stat, p_value = ztest(Data['bmi'], value=25)
```

---

### ⚗️ Task 4 — Z-Test & T-Test

Both the Z-Test and the T-Test were conducted upon the BMI column, in accordance with the conditions governing each:

```
T-Test is proper when:
  • Population standard deviation is unknown
  • Sample size is small (n < 30)

Z-Test is proper when:
  • Population standard deviation is known
  • Sample size is large (n ≥ 30)
```

---

### 🔲 Task 5 — Chi-Square Tests

Two chi-square tests were conducted upon categorical variables of considerable interest:

**Goodness of Fit:**
```
H₀: All smoking categories are equally distributed
H₁: Distribution is not equal
χ² = Σ (O - E)² / E
```

**Test of Independence:**
```
H₀: Smoking Status and Diabetes are independent
H₁: Smoking Status and Diabetes are related
df = (rows - 1) × (cols - 1)
```

---

### 📊 Task 6 — ANOVA Test

One-Way ANOVA was performed to examine whether **cholesterol levels** differ significantly across groups distinguished by **exercise frequency** (`Daily`, `Weekly`, `Rarely`, `Never`):

```
H₀ : μ_Daily = μ_Weekly = μ_Rarely = μ_Never
H₁ : At least one group mean is different

F = MSB / MSW
```

---

### 🔗 Task 7 — Covariance & Correlation

The relationship betwixt **BMI** and **Blood Pressure** was subjected to both covariance and Pearson correlation analysis:

```python
# Manual Pearson Correlation
r = Σ[(X - X̄)(Y - Ȳ)] / sqrt(Σ(X-X̄)² × Σ(Y-Ȳ)²)

# Scipy Verification
r_scipy, p_value = stats.pearsonr(X, Y)
```

Strength of relationship was classified thusly:

| r Value | Interpretation |
|---|---|
| r ≥ 0.7 | Strong Positive |
| 0.4 ≤ r < 0.7 | Moderate Positive |
| 0 < r < 0.4 | Weak Positive |
| r ≤ -0.7 | Strong Negative |
| -0.7 < r ≤ -0.4 | Moderate Negative |
| -0.4 < r < 0 | Weak Negative |

---

### 📋 Task 8 — Results Summary Table

| # | Test | Variable(s) | Decision Rule |
|---|---|---|---|
| 1 | One-Sample Z-Test | BMI vs threshold = 25 | Reject H₀ if p < 0.05 |
| 2 | Two-Sample T-Test | BMI: Smokers vs Non-Smokers | Based on p-value |
| 3 | Chi-Square Test | Smoking vs Diabetes | Based on p-value |
| 4 | Chi-Square Test | Exercise vs Hypertension | Based on p-value |
| 5 | One-Way ANOVA | Cholesterol ~ Exercise Frequency | Reject H₀ if p < 0.05 |
| 6 | Pearson Correlation | BMI vs Blood Pressure | Multiple pairs |

> **General Rule:** If **p-value < 0.05** → Reject H₀ *(statistically significant)*
> If **p-value ≥ 0.05** → Fail to Reject H₀ *(insufficient evidence)*

---

## ⚙️ Requirements

The following most indispensable libraries must be installed upon one's computing apparatus:

```bash
pip install numpy pandas matplotlib seaborn scipy statsmodels
```

| Library | Purpose |
|---|---|
| `numpy` | Numerical computations |
| `pandas` | Data manipulation & loading |
| `matplotlib` | Visualisation |
| `seaborn` | Statistical graphics |
| `scipy` | Statistical tests (t, z, chi², F) |
| `statsmodels` | Z-Test via `weightstats` |

---

## 🚀 Usage

1. **Procure** the `health_dataset.csv` file and place it in the self-same directory as the notebook.
2. **Install** the required libraries as enumerated above.
3. **Open** the notebook in Jupyter:
   ```bash
   jupyter notebook A_Statistical_Decision_Making_Model.ipynb
   ```
4. **Execute** each cell in due sequence, from Part A through to Part B.
5. **Observe** the outputs with scholarly attention and draw thine own informed conclusions.

---

## 📊 Summary of Results

| Analysis | Method | Outcome |
|---|---|---|
| 🩺 BMI vs Healthy Threshold | One-Sample Z-Test | Decision based on p-value |
| 🚬 BMI by Smoking Status | Two-Sample T-Test | Decision based on p-value |
| 🔲 Smoking ↔ Diabetes | Chi-Square (Independence) | Decision based on p-value |
| 🏃 Exercise ↔ Cholesterol | One-Way ANOVA | Decision based on F-statistic |
| 📐 BMI ↔ Blood Pressure | Pearson Correlation | Direction & strength assessed |

---

## 🏁 Conclusion

This most comprehensive notebook hath traversed the full breadth of foundational inferential statistics, applied with scholarly diligence to a health dataset of considerable richness:

- 📏 **Confidence Intervals** — computed for key numerical health metrics
- ⚗️ **Z-Test** — to ascertain whether BMI departs from the healthy threshold of 25
- 🧪 **Two-Sample T-Test** — to compare BMI betwixt Smokers and Non-Smokers
- 🔲 **Chi-Square Tests** — for Smoking ↔ Diabetes and Exercise ↔ Hypertension
- 📊 **One-Way ANOVA** — examining Cholesterol Level across Exercise Frequency groups
- 🔗 **Covariance & Pearson Correlation** — for all continuous variable pairs

> *"Numbers, when properly interrogated, do not merely describe the world — they illuminate it."*

---

📜 *Crafted with scholarly diligence and statistical rigour*

**Derivable Judgement** · Statistical Decision Making Model
