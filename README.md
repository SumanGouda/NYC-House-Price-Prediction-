# 🏠 House Price Prediction using Feature Engineering & Custom Linear Regression

This project builds a **machine learning pipeline to predict house sale prices** using engineered features derived from categorical and numerical data.  
Instead of using ready-made preprocessing pipelines, this project manually implements **target encoding, log transformations, and standard scaling** to better understand how ML preprocessing works internally.

---

# 📌 Project Overview

The goal of this project is to predict **property sale prices** using important factors such as:

- Borough location
- Building class
- Land use category
- Building age

The project focuses heavily on **feature engineering and preprocessing techniques** to improve model performance and reduce noise in categorical variables.

---

# ⚙️ Features of the Project

## 1️⃣ Target Encoding for Categorical Features
Instead of using **One Hot Encoding**, categorical features are converted into numerical values using the **mean sale price of each category**.

Example:
# 🏠 House Price Prediction using Feature Engineering & Custom Linear Regression

This project builds a **machine learning pipeline to predict house sale prices** using engineered features derived from categorical and numerical data.  
Instead of using ready-made preprocessing pipelines, this project manually implements **target encoding, log transformations, and standard scaling** to better understand how ML preprocessing works internally.

---

# 📌 Project Overview

The goal of this project is to predict **property sale prices** using important factors such as:

- Borough location
- Building class
- Land use category
- Building age

The project focuses heavily on **feature engineering and preprocessing techniques** to improve model performance and reduce noise in categorical variables.

---

# ⚙️ Features of the Project

## 1️⃣ Target Encoding for Categorical Features
Instead of using **One Hot Encoding**, categorical features are converted into numerical values using the **mean sale price of each category**.

Example:
building_class → mean(sale_price)
borough → mean(sale_price)
landuse → smoothed mean(sale_price)


### Why not One Hot Encoding?

- Creates **high dimensional sparse matrices**
- Produces **0/1 distributions** which can hurt linear models
- Does not capture the **price trend within categories**

Target encoding captures **price behaviour of each category**.

---

## 2️⃣ Smoothing for Landuse Encoding

For `landuse`, **smoothed target encoding** was applied to avoid unreliable averages when categories have very few samples.

Formula used:
    
### Why not One Hot Encoding?

- Creates **high dimensional sparse matrices**
- Produces **0/1 distributions** which can hurt linear models
- Does not capture the **price trend within categories**

Target encoding captures **price behaviour of each category**.

---

## 2️⃣ Smoothing for Landuse Encoding

For `landuse`, **smoothed target encoding** was applied to avoid unreliable averages when categories have very few samples.

Formula used:

### Why not One Hot Encoding?

- Creates **high dimensional sparse matrices**
- Produces **0/1 distributions** which can hurt linear models
- Does not capture the **price trend within categories**

Target encoding captures **price behaviour of each category**.

---

## 2️⃣ Smoothing for Landuse Encoding

For `landuse`, **smoothed target encoding** was applied to avoid unreliable averages when categories have very few samples.

Formula used:
    smooth_mean = (mean * count + global_mean * k) / (count + k)


Where:

- `mean` → average sale price for category
- `count` → number of samples
- `global_mean` → overall dataset mean
- `k` → smoothing factor

This helps prevent **overfitting from small groups**.

---

## 3️⃣ Log Transformation

Some features had **right-skewed distributions**, so log transformation was applied.

Example:
    bldgclass_mean_price → log transformation
    landuse_mean_price → log transformation


Purpose:

- Reduce skewness
- Stabilize variance
- Improve model learning

---

## 4️⃣ Standard Scaling (Z-score Normalization)

Features are standardized so they have:

- Mean = 0
- Standard Deviation = 1

Formula:
    
Purpose:

- Reduce skewness
- Stabilize variance
- Improve model learning

---

## 4️⃣ Standard Scaling (Z-score Normalization)

Features are standardized so they have:

- Mean = 0
- Standard Deviation = 1

Formula:
    X_scaled = (X - μ) / σ

# 🔧 Feature Engineering Pipeline

The final preprocessing pipeline applied to the features:

### Building Class


building_class
->>
mean(sale_price)
->>
log transformation
->>
standard scaling


### Borough


borough
->>
mean(sale_price)
->>
standard scaling


### Building Age


building_age
 ->>
standard scaling


### Landuse


landuse
->>
smoothed mean(sale_price)
->>
log transformation
->>
standard scaling

