# Statistical Methods in Biomedical Engineering

Coursework for **IBEHS 3S03 — Statistical Methods in Biomedical Engineering** at McMaster University: probability theory, statistical inference, regression, correlation, and design of experiments (DOE), applied to biomedical and engineering datasets.

**Author:** Muhammad Ullah 

---

## Repo structure

```
Statistical-Methods-Biomedical-Engineering/
├── Assignment/
│   ├── Assignment1/   Probability, distributions, EDA
│   ├── Assignment2/   Hypothesis testing (one-sample, two-sample, paired)
│   └── Assignment3/   Correlation & multiple linear regression
├── Tutorial/
│   ├── tutorial 1/    Data cleaning fundamentals
│   ├── tutorial 2/    Probability distributions (Poisson, Normal)
│   ├── tutorial 3/    Estimation & confidence intervals
│   ├── tutorial 4/    Two-sample t-tests
│   ├── tutorial 5/    ANOVA
│   ├── tutorial 6/    Simple linear regression
│   ├── tutorial 7/    Multiple linear regression
│   ├── tutorial 8/    DOE — 2³ factorial screening
│   └── tutorial 9/    DOE — 2² factorial with blocking
└── DOE/               Final Design of Experiments project (2³ factorial + RSM)
```

## Tools used across the repo

| Tool | Used for |
|---|---|
| `pandas` | Data loading, cleaning, grouping, pivot tables |
| `numpy` | Numerical calculations, array operations |
| `matplotlib` | Plotting — histograms, boxplots, cube/contour/surface plots, interaction plots |
| `seaborn` | Statistical plots — pairplots, distribution plots, boxplots |
| `scipy.stats` | Hypothesis tests (t-test, Mann-Whitney U, Shapiro-Wilk), probability distributions |
| `statsmodels` | OLS regression, ANOVA tables, factorial DOE models, regression diagnostics (Durbin-Watson, influence plots, ACF) |
| `scikit-learn` | Train/test splitting, `LinearRegression`, `mean_squared_error`, `r2_score` |

---

## Assignments

### Assignment 1 — Probability, Distributions & Exploratory Data Analysis
**What it is:** Foundational probability and descriptive-statistics assignment using a real public dataset alongside by-hand probability problems.

**Problems solved:**
- Sourced and cleaned a real-world dataset (Ontario white-tailed deer harvest data): handled missing values and removed aggregate/non-unit rows, then summarized and visualized the distribution (histogram, boxplot) and commented on skew and outliers
- Joint/conditional probability from a contingency table (multiplication rule, addition rule, independence testing) for an engineering reaction dataset
- Diagnostic test performance (sensitivity, specificity, false positive rate) for a clinical screening tool, including plotting and interpreting a point on the ROC plane
- Poisson and Binomial probability models for interruption events in a neural network, verified by hand and in Python
- Normal distribution problems on systolic blood pressure (z-scores, percentile cutoffs, the Empirical Rule)

**Tools:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy.stats`

### Assignment 2 — Inferential Statistics & Hypothesis Testing
**What it is:** A simulated clinical-device validation study plus two real hypothesis-testing problems, covering one-sample, independent two-sample, and paired tests.

**Problems solved:**
- Simulated a clinical measurement study (core body temperature, n=50, reproducible RNG seed) and ran a two-sided one-sample t-test against a nominal clinical value, with a 95% confidence interval and full biomedical interpretation
- Independent two-sample t-test comparing resting heart rate estimates from two wearable-device algorithms, including an EDA/assumption check (normality, equal variance via F-test) and a non-parametric Mann-Whitney U cross-check
- Paired one-sided t-test on arsenic contamination levels in water tanks before/after a storm (by hand and in Python), a 99% CI on the mean difference, and a comparison against an (incorrectly) unpaired Welch's t-test to demonstrate the statistical power lost by ignoring pairing

**Tools:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy.stats`, `statsmodels`

### Assignment 3 — Correlation & Multiple Linear Regression
**What it is:** A regression-modeling assignment predicting `DEVICELOSS` (gas-transfer efficiency loss) in a portable membrane oxygenator from benchtop test data (`DeviceLoss.csv`).

**Problems solved:**
- 70/30 train/test split (fixed random state) and a full pairplot/correlation analysis to identify the predictor most linearly associated with the response
- Simple linear regression on the strongest single predictor
- Forward selection to build a multiple linear regression model, testing whether additional predictors meaningfully improved fit
- Full assumption review (residual diagnostics) and final model interpretation in the context of device efficiency

**Tools:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `statsmodels` (OLS, `anova_lm`), `scikit-learn` (`train_test_split`)

---

## Tutorials

### Tutorial 1 — Introduction to Working with Engineering and Health Data
**What it is:** A first pass through the standard data-cleaning workflow: import, inspect, identify quality issues, clean, and re-check.

**Problems solved:** Built and cleaned a small synthetic dataset — fixed datatype mismatches, handled missing/implausible values — then described the cleaned data and reflected on reproducibility.

**Tools:** `pandas`, `numpy`, `matplotlib`, `seaborn`

### Tutorial 2 — Probability Distributions
**What it is:** Discrete vs. continuous probability modeling using simulated hospital and clinical data.

**Problems solved:**
- Simulated Poisson-distributed hospital admissions for a remote clinic; compared empirical vs. theoretical PMF and computed sample/empirical probabilities
- Simulated Normally-distributed adult blood pressure data; computed sample statistics, z-scores, and probability estimates, and compared against theoretical values

**Tools:** `pandas`, `numpy`, `matplotlib`, `seaborn`

### Tutorial 3 — Estimation and Confidence Intervals
**What it is:** Estimating mean HbA1c from two different measurement systems and quantifying the uncertainty in that estimate.

**Problems solved:** EDA and QQ-plots on both measurement methods, by-hand calculation of standard error and the critical t-value, construction of 95% (and 85%) confidence intervals for each method (verified in Python/SciPy), and a graphical comparison of the two CIs.

**Tools:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy.stats`

### Tutorial 4 — Two-Sample T-Tests
**What it is:** A full independent two-sample t-test workflow comparing two HbA1c testing methods, from assumption-checking through to a non-parametric cross-check.

**Problems solved:** Normality (Jarque-Bera) and equal-variance (Levene's) assumption checks with QQ-plots, by-hand pooled standard deviation / standard error / t-statistic calculations, decision-making by both the critical-value and p-value methods, a 95% CI for the difference in means, and verification against `scipy` and `statsmodels` t-tests plus a Mann-Whitney U test.

**Tools:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy.stats`, `statsmodels`

### Tutorial 5 — ANOVA
**What it is:** One-way ANOVA comparing antioxidant capacity across chocolate groups.

**Problems solved:** Visual group comparison, hypothesis setup, linear-model formulation and assumption review, running a one-way ANOVA in Python and building the ANOVA table by hand, and Fisher's LSD post-hoc pairwise comparisons at α = 0.05 with plotted estimates and 95% CIs.

**Tools:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy.stats`, `statsmodels` (OLS, `anova_lm`)

### Tutorial 6 — Simple Linear Regression
**What it is:** End-to-end simple linear regression on energy-use data, from the closed-form OLS solution through to a train/test prediction model.

**Problems solved:** EDA, closed-form OLS coefficient derivation (matched against `statsmodels`), hypothesis testing and a 95% CI on the slope, full regression-assumption diagnostics (residual plots, Durbin-Watson autocorrelation test, ACF plot, influence plot, Shapiro-Wilk normality test), and a train/test split comparison to discuss over- vs. under-fitting.

**Tools:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy.stats`, `statsmodels`, `scikit-learn` (`train_test_split`, `LinearRegression`, `mean_squared_error`, `r2_score`)

### Tutorial 7 — Multiple Linear Regression
**What it is:** Extends Tutorial 6 to multiple predictors of energy use, including model selection and 3D response-surface visualization.

**Problems solved:** Correlation matrix and best-single-predictor SLR baseline, a 2-predictor OLS multiple regression model with full ANOVA table, an assumption review for the MLR model, a 3D response-surface plot of the fitted model, and forward step-wise selection compared by adjusted R².

**Tools:** `pandas`, `numpy`, `matplotlib` (incl. `mpl_toolkits.mplot3d`), `seaborn`, `statsmodels`

### Tutorial 8 — Design of Experiments: 2³ Factorial Screening
**What it is:** Phase 1 (screening) of a hands-on DOE project — a paper-airplane experiment with 3 two-level factors (wingspan, nose weight, launch angle) and time-of-flight as the response.

**Problems solved:** Built and randomized a coded 2³ factorial design, physically ran and recorded all 8 experimental throws, fit the full factorial model and ANOVA table, produced a cube plot, a Pareto plot of absolute effects, and pairwise interaction plots, reduced the model to its significant factors, related the regression coefficients back to factorial effects by hand, and previewed Phase 2 (optimization) with a response surface and contour plot.

**Tools:** `pandas`, `numpy`, `matplotlib` (incl. `mpl_toolkits.mplot3d`), `statsmodels` (`ols`, `anova_lm`), `itertools`

### Tutorial 9 — Design of Experiments: 2² Factorial with Blocking
**What it is:** A 2² factorial paper-airplane experiment (wingspan × launch angle, flight distance as the response) demonstrating why and how to block a nuisance factor.

**Problems solved:** Ran the full factorial with a single thrower (4 runs, no residual degrees of freedom), then replicated it with a second thrower to recover error degrees of freedom and interpret SSError/MSE, then refit the model treating "thrower" as a formal block effect to isolate that nuisance variance from the residual error rather than letting it inflate it — visualized with boxplots comparing blocks.

**Tools:** `pandas`, `numpy`, `matplotlib`, `statsmodels` (`ols`, `anova_lm`), `itertools`

---

## DOE — Final Design of Experiments Project

**What it is:** The capstone DOE project (write-up: `Ullah_Muhammad_DoEProject (1).pdf`), applying the full screening → analysis → optimization workflow from Tutorials 8–9 to an independently designed experiment (3 two-level factors, including a stretch and radius parameter, with flight/throw distance as the response), replicated across two experimental blocks (AM/PM sessions).

**Problems solved:**
- Built a coded 2³ full factorial design and fit the full model (`Distance ~ A*B*C`) with a complete ANOVA table
- Extended to a 16-run replicated design across two blocks (AM/PM) to absorb session-to-session nuisance variance
- Cube plot of mean response at each factorial corner
- Pareto plot converting regression coefficients to factorial effects and ranking them by magnitude
- Interaction plots for all three pairwise factor combinations
- Reduced the model to its significant two-factor subset and re-fit
- 3D response-surface plot and a filled contour plot of predicted response over the reduced factor space, with observed design points overlaid

**Tools:** `pandas`, `numpy`, `matplotlib` (incl. `mpl_toolkits.mplot3d`), `statsmodels` (`ols`, `anova_lm`), `itertools`

Full write-up: [`DOE/Ullah_Muhammad_DoEProject (1).pdf`](DOE/Ullah_Muhammad_DoEProject%20%281%29.pdf)
