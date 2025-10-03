# 📊 Bivariate Analysis – Data Preprocessing & Exploratory Data Analysis

Welcome to the **Bivariate Analysis** part of the *Data Preprocessing and Exploratory Data Analysis (EDA)* project!  
This notebook explores how **two variables relate to each other**, which is one of the most important steps in understanding your data before building any machine learning model.

We’ll use built-in datasets from **scikit-learn** to learn key concepts with real examples.

---

## 📘 What Is Bivariate Analysis?

**Bivariate analysis** means studying **two variables at the same time** to see if they are related and how strong that relationship is.

It helps you answer questions like:

- 📈 Do two numerical variables change together?  
- 📊 Are two categories connected or independent?  
- 🧪 Are some features too closely related, causing multicollinearity?

---

## 📚 Topics Covered

| 🔍 Scenario | 📊 Technique | 🧠 Purpose |
|------------|--------------|------------|
| Continuous ↔ Continuous | Correlation Matrix | Measure linear relationships |
| Continuous ↔ Continuous | VIF (Variance Inflation Factor) | Detect multicollinearity |
| Categorical ↔ Categorical | Chi-Square Test | Test if variables are dependent |

---

## 📂 Datasets Used

We use two well-known datasets available directly in scikit-learn:

- 🌸 **Iris dataset** – used for classification tasks.  
- 🏠 **California Housing dataset** – used for regression and correlation studies.

---

## 🛠️ How to Use

1. Open the notebook:  
   `Bivariate Analysis/bivariate analysis.ipynb`
2. Run all cells step by step.
3. Watch how relationships between variables are discovered through code, visuals, and statistical tests.

---

## 📊 Continuous vs Continuous

We start by studying relationships between continuous (numerical) variables.  
A **correlation matrix heatmap** shows how strongly each pair of features is related:

```python
sns.heatmap(california_pd.corr(method="pearson"), annot=True, cmap="Blues")
```

📌 **How to read it:**  
- Values close to **1** → strong positive correlation  
- Values close to **-1** → strong negative correlation  
- Values near **0** → little or no linear relationship

---

### 🧠 Variance Inflation Factor (VIF)

**VIF** helps detect **multicollinearity** — when two or more features are too strongly related, which can harm regression models.

```python
from statsmodels.stats.outliers_influence import variance_inflation_factor

def calc_vif(X):
    vif = pd.DataFrame()
    vif["variables"] = X.columns
    vif["VIF"] = [variance_inflation_factor(X.values, i) for i in range(X.shape[1])]
    return vif
```

✅ **Tip:** A VIF above 5 or 10 suggests the feature might be redundant.

---

## 📊 Categorical vs Categorical

For categorical variables, we use the **Chi-Square Test** to see if two variables are related or independent.

```python
from scipy.stats import chi2_contingency

chi2, p, dof, ex = chi2_contingency(pd.crosstab(df['col1'], df['col2']))
```

📌 **How to interpret:**  
- **p < 0.05** → significant relationship (variables are dependent)  
- **p ≥ 0.05** → no significant relationship (variables are independent)

---

## 📈 Visuals You’ll See

✨ Correlation heatmaps – to visualize numeric relationships  
📉 Scatterplots – to observe variable patterns  
📊 Chi-Square summary tables – to check categorical associations  

All of these help you **see relationships clearly** rather than just reading numbers.

---

## 🧠 Key Takeaways

- **Correlation** helps identify how continuous features are related.  
- **VIF** detects multicollinearity and improves model quality.  
- **Chi-Square Test** reveals whether categorical variables depend on each other.  

Together, these tools give you a deeper understanding of your dataset and guide better feature selection before modeling.

---

