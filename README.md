# natasharajore_2511552_part2_kpi_experiment

## Business Problem Statement

The company needs to decide whether the new onboarding and activation campaign (treatment group) should be launched to all users or if the existing onboarding process (control group) should continue.

This decision will impact new users, the product team, marketing team, and the overall business, as it affects user activation, engagement, and subscription growth.

The main metric that should improve is the user conversion rate (the percentage of users who complete the desired action, such as subscribing or activating their account). Early engagement metrics should also improve.

Before making a decision, the company must monitor risks such as a decrease in user retention, higher user drop-offs, or negative user experience. These are the guardrail metrics that ensure the new campaign does not harm overall performance.

The recommendation should be based on evidence from the A/B test, including whether the treatment group performs better than the control group on the success metrics while maintaining acceptable guardrail metrics. Only if the improvement is meaningful and the risks remain low should the new campaign be launched to all users.

## North Star Metric: User Conversion Rate (Conversion to Paid Subscription)

### Why this is the North Star metric

The main objective of the onboarding campaign is to convert more new users into paying subscribers. User Conversion Rate directly measures whether the new onboarding experience helps achieve this goal. Since the company follows a subscription-based business model, increasing paid conversions has the greatest impact on business success.

### Why other metrics are supporting metrics

Metrics such as landing page visits, trial starts, onboarding completion, engagement score, and days to convert help explain why users do or do not convert. They measure different stages of the user journey but do not directly reflect business success. Similarly, revenue, support tickets, and refund requests provide additional insights into the quality and impact of the campaign but are not the primary objective of the experiment.

### How this metric connects to business growth

A higher User Conversion Rate means more paying subscribers from the same number of new users. This increases recurring subscription revenue, improves customer acquisition efficiency, and supports long-term business growth without requiring additional marketing spend.

### What could go wrong if this metric is optimized blindly

Focusing only on User Conversion Rate could lead the company to use aggressive tactics that encourage users to subscribe without ensuring they receive value from the product. This may result in lower user engagement, higher refund requests, increased support tickets, or poor long-term retention. Therefore, User Conversion Rate should always be evaluated together with guardrail metrics to ensure sustainable growth.

## Data Preparation

The following data quality checks and cleaning steps were completed:

### Missing Values
- Missing values in device_type (18 records) and traffic_source (24 records) were replaced with "Unknown" to retain all user records for analysis.
- Missing values in days_to_convert were retained because they represent users who did not convert and are expected in the dataset.
- Missing values in engagement_score (14 records) were retained, as they represent less than 1% of the dataset and were not expected to materially affect the analysis.
- No missing values were found in the remaining columns.

### Duplicate User IDs
- Duplicate user IDs were checked for conflicting information.
- No duplicate user IDs with conflicting data were found.
- A total of 16 exact duplicate records (8 duplicated pairs) were identified and removed, resulting in 8 records being deleted from the dataset.

### Group Counts
- The number of users in each experiment group was verified after the duplicate records were deleted.
   - Control Group: 690 users
   - Treatment Group: 710 users
- The groups were considered sufficiently balanced, and no adjustments were made.

### Invalid Binary Values
- The binary columns (visited_landing_page, started_trial, completed_onboarding, converted_to_paid, and refund_requested) were validated to ensure they contained only 0 or 1.
- No invalid binary values were found, so no corrections were required.

### Revenue Outliers
- Revenue outliers were identified using the Interquartile Range (IQR) method.
- Four records (Revenue: 2660.21, 3887.98, 6788.95, and 8610.72) were identified as outliers.
These records were reviewed and retained because they represent valid high-value customer transactions rather than data quality issues.

### Segment Distribution Across Groups
- Pivot tables were created to compare the distribution of region, device_type, traffic_source, and plan_type across the control and treatment groups.
- The segment distribution analysis is available in the Analysis sheet of analysis/experiment_analysis.xlsx.
- This check was performed to review the composition of the experiment groups, and no data changes were made based on the segment distribution.
