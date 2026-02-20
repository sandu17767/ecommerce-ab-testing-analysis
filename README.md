# 🧪 A/B Testing Analysis – E-commerce Landing Page

## 📌 Project Overview

This project analyzes the impact of introducing a new landing page design for an e-commerce platform.  
The objective was to determine whether the new landing page improves user conversion compared to the existing version.

The primary metric used in this experiment is **conversion rate**, defined as the percentage of users who completed a desired action after visiting the landing page.

Statistical hypothesis testing was applied to determine whether any observed difference in conversion rates is statistically significant or due to random variation.

---

## 🎯 Business Problem

Conversion rate is a critical metric in e-commerce because it directly impacts revenue. Even small improvements in conversion can lead to substantial increases in sales when applied at scale.

Before rolling out a new landing page to all users, the business must validate whether the redesign genuinely improves user behavior. Implementing design changes without statistical validation may result in unnecessary costs without measurable business impact.

---

## 🧪 Hypothesis

To evaluate the effectiveness of the new landing page, the following hypotheses were defined:

**Null Hypothesis (H₀):**  
The new landing page does not change the conversion rate compared to the old landing page.

**Alternative Hypothesis (H₁):**  
The new landing page results in a different conversion rate compared to the old landing page.

The test was conducted using a two-proportion z-test at a 5% significance level (α = 0.05).

---

## 🧹 Data Cleaning

To ensure the integrity of the experiment, the following data cleaning steps were performed:

- Removed rows where the assigned group did not match the landing page shown (e.g., control group shown the new page).
- Removed duplicate users to ensure each user was counted only once.
- Verified that control and treatment groups were balanced in size after cleaning.

Final dataset size after cleaning: **290,584 users**

---

## 📊 Exploratory Analysis

After cleaning the dataset, conversion rates were calculated for both groups:

- **Control Group:** 12.04%
- **Treatment Group:** 11.88%

The observed difference between groups was small (approximately 0.16 percentage points). Statistical testing was required to determine whether this difference was meaningful or due to random variation.

---

## 📈 Statistical Testing

A two-proportion z-test was conducted to compare conversion rates between the control and treatment groups.

- **Test Used:** Two-proportion z-test  
- **Z-statistic:** 1.31  
- **P-value:** 0.19  
- **Significance Level (α):** 0.05  

Since the p-value (0.19) is greater than the significance level (0.05), we fail to reject the null hypothesis.

This indicates that the observed difference in conversion rates is likely due to random variation rather than a statistically significant effect of the new landing page.

---

## 📊 Visualization

A bar chart was created using Matplotlib to visually compare conversion rates between the control and treatment groups.

The visualization confirms that the difference between groups is minimal and aligns with the statistical test results.

---

## 💡 Business Recommendation

Based on the statistical analysis, the new landing page does not demonstrate a significant improvement in conversion rate.

Rolling out the new design without further evidence may result in implementation costs without measurable business benefit.

It is recommended that the company either retain the existing landing page or conduct further experimentation with more impactful design changes aimed at meaningfully improving conversion performance.

---

## 🛠 Tools & Technologies Used

- Python
- Pandas (data manipulation)
- Statsmodels (statistical testing)
- Matplotlib (data visualization)
- Jupyter Notebook

---

## 📌 Key Takeaways

- Proper experiment validation is critical before making business decisions.
- Small differences in metrics require statistical testing to determine significance.
- Data cleaning and experiment integrity directly impact the reliability of results.
- Statistical thinking combined with business reasoning leads to better decision-making.
