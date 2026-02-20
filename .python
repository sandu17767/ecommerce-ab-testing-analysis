# ==========================================================
# A/B Testing Analysis – E-commerce Landing Page
# ==========================================================

# Step 1: Import Required Libraries
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.stats.proportion import proportions_ztest


# Step 2: Load Dataset
df = pd.read_csv("data/ab_data.csv")

print("Initial Dataset Shape:", df.shape)


# Step 3: Validate Group and Landing Page Alignment
print("\nGroup and Landing Page Distribution:")
print(df.groupby(['group', 'landing_page']).size())


# Step 4: Remove Mismatched Group Assignments
df_clean = df[
    ((df['group'] == 'control') & (df['landing_page'] == 'old_page')) |
    ((df['group'] == 'treatment') & (df['landing_page'] == 'new_page'))
]

print("\nShape After Removing Mismatches:", df_clean.shape)


# Step 5: Remove Duplicate Users
print("\nDuplicate Users Before Cleaning:", df_clean['user_id'].duplicated().sum())

df_clean = df_clean.drop_duplicates(subset='user_id')

print("Duplicate Users After Cleaning:", df_clean['user_id'].duplicated().sum())


# Step 6: Calculate Conversion Rates
conversion_rates = df_clean.groupby('group')['converted'].mean() * 100

print("\nConversion Rates (%):")
print(conversion_rates)


# Step 7: Extract Group-Level Metrics
control_total = df_clean[df_clean['group'] == 'control'].shape[0]
treatment_total = df_clean[df_clean['group'] == 'treatment'].shape[0]

control_conversions = df_clean[df_clean['group'] == 'control']['converted'].sum()
treatment_conversions = df_clean[df_clean['group'] == 'treatment']['converted'].sum()

print("\nControl Total:", control_total)
print("Treatment Total:", treatment_total)
print("Control Conversions:", control_conversions)
print("Treatment Conversions:", treatment_conversions)


# Step 8: Perform Two-Proportion Z-Test
successes = [control_conversions, treatment_conversions]
totals = [control_total, treatment_total]

z_stat, p_value = proportions_ztest(successes, totals)

print("\nZ-statistic:", z_stat)
print("P-value:", p_value)


# Step 9: Visualization
control_rate = conversion_rates['control']
treatment_rate = conversion_rates['treatment']

plt.figure()
plt.bar(['Control', 'Treatment'], [control_rate, treatment_rate])
plt.ylabel('Conversion Rate (%)')
plt.title('A/B Test: Conversion Rate Comparison')

plt.savefig("conversion_comparison.png")
plt.show()


# Step 10: Final Interpretation
if p_value < 0.05:
    print("\nResult: Reject the null hypothesis.")
    print("There is statistically significant evidence that the new landing page changes conversion rate.")
else:
    print("\nResult: Fail to reject the null hypothesis.")
    print("There is insufficient statistical evidence to conclude that the new landing page improves conversion rate.")
