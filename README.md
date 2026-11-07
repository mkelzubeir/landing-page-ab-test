# Landing Page A/B Test

Does a redesigned landing page convert more users than the current one? This notebook analyzes an A/B test of about 290,000 users split between the old page (control) and the new page (treatment).

## Data cleaning
Before testing, I checked the data's integrity and found two problems:
- **3,893 rows** where a user's assigned group didn't match the page they actually saw (for example, control users shown the new page). These rows contaminate the comparison, so I removed them.
- **1 user** who appeared twice. I kept the first record.

That left **290,584 users**. The two groups are nearly equal in size, so the random split worked as expected.

## Method
- Hypotheses: no difference in conversion rates (null) vs. any difference (alternative), at α = 0.05
- Two-sided two-proportion z-test
- 95% confidence interval for the difference in conversion rates

## Results
| Group | Conversion rate |
|---|---|
| Control (old page) | 12.04% |
| Treatment (new page) | 11.88% |

The difference is **-0.16 percentage points** (relative lift -1.3%), with **p = 0.19** and a **95% confidence interval of -0.39 to 0.08 points**. The difference is not statistically significant, and the interval rules out any meaningful improvement.

## Recommendation
Don't launch the new page. It performs no better than the current one.

## Tools
Python, pandas, statsmodels

## Data
[A/B testing dataset on Kaggle]([https://www.kaggle.com/datasets/zhangluyuan/ab-testing])
