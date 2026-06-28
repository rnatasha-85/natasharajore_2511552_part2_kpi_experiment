## Hypothesis

### 1. Null hypothesis (H₀)
There is no significant difference in the paid conversion rate between users who experience the existing onboarding campaign (control group) and users who experience the new onboarding campaign (treatment group).

### 2. Alternate hypothesis
Users who experience the new onboarding campaign (treatment group) have a significantly higher paid conversion rate than users who experience the existing onboarding campaign (control group).

### 3. Whether the test is one-tailed or two-tailed
A one-tailed test will be used because the objective is to determine whether the new onboarding campaign increases the paid conversion rate compared to the existing onboarding experience.

### 4. Significance level used
The significance level (α) is 0.05 (5%).

### 5. Metric being tested
User Conversion Rate (Paid Conversion Rate)

Calculation:
Number of users who converted to paid ÷ Total number of users

### 6. Reason for choosing that metric
User Conversion Rate is the North Star metric for this experiment because the primary objective of the new onboarding campaign is to increase the number of users who become paying subscribers. An improvement in this metric directly contributes to subscription growth and recurring revenue.

### 7.Interpretation logic
- If the p-value < 0.05, reject the null hypothesis and conclude that the new onboarding campaign significantly improves the paid conversion rate compared to the existing onboarding experience. This provides sufficient evidence to recommend launching the new campaign to all users.

- If the p-value ≥ 0.05, fail to reject the null hypothesis and conclude that there is insufficient evidence that the new onboarding campaign improves the paid conversion rate compared to the existing onboarding experience. The existing onboarding process should be retained or the new campaign should be further evaluated.


## Hypothesis Test Result Explanantion

A hypothesis test was performed to determine whether the new onboarding campaign (treatment group) resulted in a significantly higher user conversion rate than the existing onboarding experience (control group).

### Test Performed

A [Two-Proportion Z-Test as well] as well as [Two-Sample t-Test Assuming Unequal Variances] were conducted using the User Conversion Rate (Paid Conversion Rate) as the primary metric. A one-tailed test with a significance level of 0.05 was used because the objective was to determine whether the treatment outperformed the control.

### Test Results
Control Group Conversion Rate: 3.19 %
Treatment Group Conversion Rate: 7.04 %
t-test : T Statistic = -3.290963274 , p-value one-tail = 0.000513079
Z-test : Z Statistic = 276.4390896921, p-value one-tail = 0

### Interpretation

The p-value was compared with the significance level of 0.05.

If p-value < 0.05, the null hypothesis was rejected, indicating that the new onboarding campaign significantly improved the user conversion rate compared to the existing onboarding experience.
If p-value ≥ 0.05, the null hypothesis was not rejected, indicating that there was insufficient evidence to conclude that the new onboarding campaign improved the user conversion rate.

### Business Conclusion

Based on the hypothesis test results, the statistical evidence supports launching the new onboarding campaign to all users. This recommendation should also be considered alongside the guardrail metrics, such as refund rate, support ticket rate, and user engagement, to ensure the campaign delivers sustainable business value.
