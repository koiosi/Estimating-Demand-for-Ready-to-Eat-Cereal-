# 🥣 EP_Cereal — Econometric Analysis of the Breakfast Cereal Market

**A collaborative econometrics project exploring consumer demand and pricing behavior in the U.S. breakfast cereal market.**

---

## 🎯 Overview
This project investigates how **price and nutritional characteristics** (such as calories, fat, and sugar content) influence consumer choices in the cereal market.  
Using econometric modeling techniques in **R**, we estimate demand equations, address **price endogeneity**, and test the **validity of instrumental variables**.

Developed collaboratively with **Canberk Atak** and team members as part of an industrial organization course.

---

## 🧩 Objectives
- Describe and visualize the U.S. cereal market structure  
- Estimate demand models using **OLS** and **IV regression**  
- Evaluate **instrument strength and validity**  
- Explore model improvements and **relaxation of IIA assumptions**

---

## 📊 Dataset
The dataset (`Cereal_Data.xls`) contains detailed information on cereal brands and product features, including:

| Variable | Description |
|-----------|-------------|
| `Name` | Cereal product name |
| `Brand` | Brand (e.g., GM, KG, NB) |
| `Sgmnt` | Market segment (Adult, Family, Kids) |
| `Avg Shelf Price` | Average shelf price |
| `Avg Trans Price` | Average transaction price |
| `Avg Ad Expn` | Average advertising expenditure |
| `Cals`, `Fat`, `Sugar` | Nutritional content |
| `Mkt Share` | Market share (%) |

---

## 🧠 Methodology

### 🔹 Task 1 — Market Description
- Data cleaning, handling missing values with `naniar`
- Descriptive statistics via `modelsummary`
- Visualization of price and nutritional patterns with `ggplot2`

### 🔹 Task 2 — OLS Estimation
Estimated mean utility using OLS under different specifications:

\[
\text{Mean Utility} = \log(\text{Market Share}) - \log(\text{Outside Share})
\]

- Included brand fixed effects  
- Compared standard and clustered standard errors  

### 🔹 Task 3 — Instrumental Variable (IV) Estimation
Addressed **price endogeneity** using instruments such as:
- Advertising × Brand  
- Transaction Price × Brand  

Evaluated using **Wald**, **F-statistics**, and **Sargan tests**.

### 🔹 Task 4 — Alternative Instruments
Developed new instruments based on:
- Average brand and segment prices  
- Discounts and coupons  
- Combined instrument sets for robustness checks  

### 🔹 Task 5 — Model Refinement
- Added a **high-sugar dummy** variable  
- Explored approaches to **relax IIA**, e.g., nested logit models  

---

## 🧮 Tools & Libraries
Built entirely in **R**, using the following packages:

```r
library(readxl)
library(dplyr)
library(tidyverse)
library(ggplot2)
library(fixest)
library(lfe)
library(modelsummary)
library(naniar)
library(corrplot)
library(lmtest)
library(sandwich)

```


## 📈 Key Insights & Takeaways

| **Aspect** | **Insight** |
|-------------|-------------|
| **Price Elasticity** | Prices show a negative and statistically significant relationship with demand — confirming that cereal consumers are price-sensitive. |
| **Brand Effects** | Brand reputation plays a major role; including brand fixed effects significantly improves model fit. |
| **Nutritional Preferences** | High-sugar products attract more demand, especially in kid-targeted segments. |
| **Advertising Influence** | Advertising expenditure is positively correlated with demand, highlighting its role in maintaining brand loyalty. |
| **Endogeneity Correction** | Instrumental variables (Ad × Brand, Transaction Price × Brand) effectively correct for price endogeneity. |

---

## 💼 Business Insights

**1. Pricing Strategy**  
Consumers react strongly to price changes — indicating **limited pricing power** for most brands.  
Premium brands, however, can sustain higher prices due to strong loyalty and perceived quality advantages.  

**2. Product Positioning**  
Health-oriented cereals (low sugar, low fat) appeal more to adult and family segments.  
High-sugar cereals remain profitable among children but depend heavily on advertising exposure and promotions.  

**3. Advertising Efficiency**  
Marketing budgets are most effective when aligned with **price sensitivity** — e.g., targeted discounts and loyalty campaigns can boost high-elasticity segments.  

**4. Market Segmentation**  
The analysis confirms clear differentiation between **demographic and taste-based segments**, suggesting that companies should adopt **segment-specific pricing and marketing** approaches.  

**5. Brand Strategy**  
Established brands benefit from strong baseline demand.  
Investing in **brand reputation, familiarity, and trust** generates measurable returns through reduced price sensitivity.  

---

## 🧾 Summary of Main Results

| **Model** | **Instruments** | **Brand FE** | **Main Finding** |
|------------|-----------------|---------------|------------------|
| OLS | None | No | Baseline relationship between price and demand |
| IV | Ad × Brand | No | Corrects for endogeneity and reduces bias |
| IV | Trans Price × Brand | Yes | Improves model precision and fit |
| OLS + New Var | None | Yes | Adding sugar dummy enhances explanatory power |
