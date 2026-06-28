# natasharajore_2511552_part2_kpi_experiment

## Business Problem Statement

The company needs to decide whether the new onboarding and activation campaign (treatment group) should be launched to all users or if the existing onboarding process (control group) should continue.

This decision will impact new users, the product team, marketing team, and the overall business, as it affects user activation, engagement, and subscription growth.

The main metric that should improve is the user conversion rate (the percentage of users who complete the desired action, such as subscribing or activating their account). Early engagement metrics should also improve.

Before making a decision, the company must monitor risks such as a decrease in user retention, higher user drop-offs, or negative user experience. These are the guardrail metrics that ensure the new campaign does not harm overall performance.

The recommendation should be based on evidence from the A/B test, including whether the treatment group performs better than the control group on the success metrics while maintaining acceptable guardrail metrics. Only if the improvement is meaningful and the risks remain low should the new campaign be launched to all users.

## Dataset Description

The dataset (campaign_experiment_data) contains user-level information collected during the A/B test, including:

- User and experiment information (user ID, signup date, experiment group)
- User segments (region, device type, traffic source, plan type)
- User journey metrics (landing page visit, trial start, onboarding completion, paid conversion)
- Business metrics (30-day revenue, refund requests, support tickets)
- User behaviour metrics (days to convert, engagement score)

The dataset was reviewed and prepared before analysis by checking missing values, duplicate user IDs, invalid binary values, revenue outliers, experiment group counts, and segment distribution across groups.

## North Star Metric Selected

### User Conversion Rate (Conversion to Paid Subscription)

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


## Guardrail Metrics Evaluation

The guardrail metrics were evaluated to ensure that the improvement in user conversion did not negatively impact the overall user experience or business performance.

### 1. Refund Rate
Control: 0.00%
Treatment: 0.42%

Evaluation:
The treatment group recorded a small increase in refund requests compared to the control group. Although the increase is minimal, it suggests that a few additional users were dissatisfied after converting. At the current level, this does not represent a significant business risk but should continue to be monitored.

### 2. Support Ticket Rate
Control: 14.78%
Treatment: 24.79%

Evaluation:
The support ticket rate increased considerably in the treatment group. This indicates that users required more assistance while using the new onboarding experience. This is the primary guardrail risk, as it may increase customer support workload and indicate usability or onboarding issues.

### 3. Average Days to Convert
Control: 8.86 days
Treatment: 6.40 days

Evaluation:
Users in the treatment group converted more quickly than those in the control group. A shorter conversion time indicates a more effective onboarding process and does not create a business risk.

### 4. Revenue Quality
Average Revenue per User: Increased from 51.97 to 54.25
Average Revenue per Converted User: Decreased from 1630.10 to 770.41

Evaluation:
Although the treatment group generated slightly higher average revenue per user, the average revenue per converted user decreased substantially. This suggests that the increase in conversions was accompanied by lower revenue from each converted customer. This represents a potential risk to revenue quality and should be investigated further.

### Overall Guardrail Risk Assessment

The treatment group achieved improvements in user conversion and reduced the average time required to convert. However, two guardrail metrics require attention. The higher support ticket rate indicates a potential decline in the onboarding experience, while the lower average revenue per converted user suggests a possible reduction in revenue quality. The refund rate increased only slightly and does not currently indicate a major business risk. These guardrail metrics should be considered alongside the improvement in user conversion before deciding on a full rollout of the new onboarding campaign.

## KPI Tree Summary

The KPI tree was built around User Conversion Rate as the North Star Metric.

Primary KPI drivers:
- User Acquisition Quality
- Onboarding Effectiveness
- User Engagement

Supporting metrics included:
- Landing Page Visit Rate
- Trial Start Rate
- Onboarding Completion Rate
- Engagement Score
- Days to Convert

Guardrail metrics evaluated separately included:
- Refund Rate
- Support Ticket Rate
- Average Days to Convert
- Revenue Quality

### Experiment Analysis Approach

The experiment compared the performance of the Control and Treatment groups using key business metrics.

The analysis included:
- Overall comparison of experiment metrics
- Segment-level analysis by Region, Device Type, Traffic Source, and Plan Type
- Hypothesis testing using User Conversion Rate as the primary metric
- Evaluation of guardrail metrics before making a business recommendation

### Hypothesis Test Summary

A one-tailed hypothesis test was conducted using User Conversion Rate (Paid Conversion Rate) as the primary metric to determine whether the new onboarding campaign significantly improved conversion compared to the existing onboarding experience.

The hypothesis test results indicated that the treatment group achieved a significantly higher paid conversion rate than the control group, providing evidence that the new onboarding campaign improved user conversion.

### Guardrail Metrics Considered

The following guardrail metrics were evaluated to ensure that improvements in user conversion did not negatively impact the business:
- Refund Rate
- Support Ticket Rate
- Average Days to Convert
- Revenue Quality (Average Revenue per User and Average Revenue per Converted User)

While the treatment group converted users faster and increased overall revenue per user, it also showed a higher support ticket rate and lower average revenue per converted user. These metrics were considered before making the final recommendation.

### Final Recommendation

Recommendation: Continue Testing

Although the treatment group significantly improved user conversion, engagement, and conversion speed, the increase in support ticket rate and the decline in average revenue per converted user indicate potential business risks. These findings suggest that the onboarding experience should be refined and re-tested before being launched to all users.

### Assumptions and Limitations

Assumptions
- Users were randomly assigned to the Control and Treatment groups.
- The experiment groups are representative of the target user population.
- Revenue and conversion data accurately reflect user behaviour during the experiment period.
- Missing values retained in days_to_convert represent users who did not convert.

Limitations
- The analysis is based only on the available experiment data.
- Long-term user retention and customer lifetime value were not included in the dataset.
- Revenue outliers were retained because they represented valid customer transactions.
- Missing engagement scores were excluded only from analyses involving engagement score.

### Screenshots Included

The following supporting screenshots are included with the submission:
- screenshots/kpi_tree.png
- screenshots/summary_metrics.png
- screenshots/segment_analysis.png
- screenshots/hypothesis_test_output.png
