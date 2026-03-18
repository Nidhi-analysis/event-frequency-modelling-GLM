# Motor Insurance Claim Frequency Modelling

A statistical modelling project to predict motor insurance claim frequency using GLMs, demonstrating the transition from Poisson to Negative Binomial due to overdispersion.

**Keywords:** Actuarial Science, GLM, Risk Modelling, Insurance Analytics, Machine Learning, Python

![Driver Age Risk](visuals/driver_age_risk.png)

## Table of Contents

- Problem Statement
- Project Objectives
- Dataset
- Methodology
- Model Results
- Key Findings
- Visualisations
- Project Structure
- How to Run the Project
- Tools & Libraries

## Key Results (Quick Summary)

- Overdispersion detected (Dispersion ≈ 2.77)
- Negative Binomial model outperforms Poisson
- AIC improved by ~910 points
- RMSE ≈ 0.55 indicating reasonable predictive accuracy
- Bonus-Malus is the strongest predictor of claim frequency


This project performs an actuarial analysis of motor insurance claim frequency using the **freMTPL2 dataset**.
The objective is to identify key risk factors influencing claim frequency and to build statistical models used in insurance pricing.

The analysis focuses on **exposure-adjusted claim frequency**, risk segmentation, and **Generalized Linear Models (GLM)** commonly used in actuarial practice.

---

# Problem Statement

Motor insurance companies must estimate the expected number of claims in order to price policies accurately and manage risk effectively.

Claim frequency depends on several policyholder and vehicle characteristics such as driver age, vehicle age, bonus-malus level, and geographic density. Understanding how these factors impact claim frequency is a key component of actuarial risk modelling.

This project aims to analyse motor insurance claim data and build statistical models to estimate claim frequency while accounting for policy exposure using actuarial modelling techniques.

---

# Project Objectives

- Perform data-driven risk analysis using statistical and machine learning concepts

The main objectives of this project are:

* Explore motor insurance claim data
* Calculate exposure-adjusted claim frequencies
* Identify important risk factors affecting claims
* Perform risk segmentation across policyholder characteristics
* Fit statistical models for claim frequency
* Evaluate model performance and assumptions


---

# Dataset

The project uses the **freMTPL2 dataset**, a widely used motor insurance dataset for actuarial modelling research.

Key variables include:

* **ClaimNb** – number of claims
* **Exposure** – policy exposure period
* **DriverAge** – age of the driver
* **VehAge** – age of the vehicle
* **VehPower** – vehicle power category
* **BonusMalus** – bonus-malus level
* **Density** – population density of the area

Claim frequency is calculated as:

```
Claim Frequency = Claims / Exposure
```

---

# Methodology

The analysis follows a typical actuarial modelling workflow.

### 1. Exploratory Data Analysis

Initial exploration of the dataset to understand the distribution of claims and key policy characteristics.

### 2. Risk Segmentation

Claim frequencies are analysed across multiple rating factors:

* Driver age bands
* Vehicle age bands
* Vehicle power categories
* Bonus-malus levels
* Population density groups

This helps identify how claim risk varies across different policyholder segments.

### 3. Claim Frequency Modelling

A Poisson regression model is first fitted under the assumption that mean = variance. This assumption is later tested using an overdispersion test.

### 4. Model Validation

Predicted claim frequencies are compared with observed frequencies across risk segments to evaluate model performance.

### 5. Overdispersion Testing

An overdispersion test is conducted to check whether the Poisson assumption *(variance = mean)* holds.

### 6. Alternative Model

Due to detected overdispersion, a **Negative Binomial regression model** is fitted as a more flexible alternative.

Model performance is compared using the **Akaike Information Criterion (AIC)**.

The Negative Binomial model relaxes the restrictive Poisson assumption by allowing variance to exceed the mean.
---

# Model Results

Two statistical models were fitted to estimate claim frequency and their performance was compared.

| Model | AIC |
|------|------|
| Poisson Regression | 288817 |
| Negative Binomial Regression | 287907 |

Model validation using the RMSE metric produced:

RMSE (Observed vs Predicted Frequency): **0.5457**

This indicates that the model captures overall claim frequency patterns reasonably well despite inherent variability in insurance data.

Since the **Negative Binomial model has a lower AIC**, it provides a better fit for the claim frequency data.

This improvement is expected because the Negative Binomial model accounts for **overdispersion**, which is commonly observed in insurance claim data.

---

# Key Findings

* Young drivers (18–25) exhibit the highest claim frequency.
* Claim frequency generally decreases with increasing driver age.
* Higher bonus-malus levels are strongly associated with increased claim risk.
* Policies located in high-density areas tend to have higher claim frequencies.
* The Poisson model showed evidence of **overdispersion**.
* The **Negative Binomial model** provided a better fit than the Poisson model.

- Model results align with actuarial intuition, increasing confidence in model reliability.
---

## Visualisations

Example visual outputs generated in this project.

### Claim Count Distribution

This plot shows the distribution of claim counts across policies.  
Most policies have zero claims, while higher claim counts occur much less frequently, resulting in a highly skewed distribution typical in insurance datasets.

![Claim Count Distribution](visuals/claim_count_distribution.png)

### Claim Frequency by Driver Age

This plot illustrates how claim frequency varies across driver age groups. Younger drivers typically exhibit higher claim frequencies, reflecting increased risk associated with limited driving experience.

![Driver Age Risk](visuals/driver_age_risk.png)

### Observed vs Predicted Claim Frequency

This chart compares observed claim frequencies with the frequencies predicted by the GLM model across driver age bands.

![Observed vs Predicted Claim Frequency](visuals/model_validation_driver_age.png)

Most predicted values align closely with observed values, indicating good model calibration across driver age segments.
---

## Limitations

- The GLM framework assumes independence between observations
- Interaction effects between variables are not explicitly modelled
- The dispersion parameter is not directly estimated in the current implementation


## Future Improvements

- Estimate dispersion parameter explicitly
- Explore interaction effects between risk factors
- Apply regularization or machine learning models for comparison
- Extend analysis to claim severity modelling


# Project Structure

```
Motor-Insurance-Risk-Modelling
│
├── data
│   └── freMTPL2.csv
│
├── notebooks
│   └── motor_claim_frequency_analysis.ipynb
│
├── visuals
│   └── *.png
│
├── requirements.txt
├── .gitignore
└── README.md
```

---

# How to Run the Project

Clone the repository

```
git clone https://github.com/Nidhi-analysis/motor-insurance-risk-modelling.git
```

Install dependencies

```
pip install -r requirements.txt
```

Open the notebook

```
notebooks/motor_claim_frequency_analysis.ipynb
```

Run the notebook cells to reproduce the analysis.

---

# Tools & Libraries

This project was implemented using Python with the following libraries:

* pandas
* numpy
* matplotlib
* seaborn
* statsmodels

---

# Author

**Nidhi Sharma**

Aspiring Actuarial Analyst with strong interest in risk modelling, GLMs, and insurance analytics. Skilled in translating statistical insights into business-relevant conclusions.