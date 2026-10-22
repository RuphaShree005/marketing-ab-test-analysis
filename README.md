Marketing A/B Test Analysis: Did the Ad Campaign Increase Conversions?
Project Overview
This project analyzes a marketing A/B test to compare conversion rates between users assigned to an advertising group (ad) and users assigned to a public service announcement control group (psa). It uses Python and statistical methods to assess the observed difference, explore exposure and timing patterns, and estimate possible business impact under stated assumptions.
Business Questions
- Did the ad group have a higher observed conversion rate than the PSA control group?
- Is the difference statistically significant?
- How large is the absolute and relative conversion lift?
- How do observed conversion rates vary by ad exposure, day, and hour?
- What might the business impact look like under illustrative cost and revenue assumptions?
Dataset
The project uses the Marketing A/B Testing dataset from Kaggle, containing approximately 588,000 rows and these columns:
- user_id
- test_group (ad or psa)
- converted
- total_ads
- most_ads_day
- most_ads_hour
Dataset setup: Download the CSV from Kaggle and place marketing_AB.csv in the same folder as the notebook. The dataset is not bundled in this repository.
Tools and Libraries
- Python
- pandas and NumPy
- Matplotlib and Seaborn
- SciPy
- Jupyter Notebook
Workflow
1. Load the CSV and standardize column names.
2. Convert the conversion flag into a numeric binary variable.
3. Check missing values, duplicate user IDs, group sizes, and descriptive statistics.
4. Compare conversion rates between the ad and PSA groups.
5. Run a two-proportion z-test and cross-check it with a chi-square test.
6. Calculate absolute lift and a 95% confidence interval.
7. Estimate relative lift and a bootstrap confidence interval.
8. Explore conversion rates by ad-exposure bucket and by day/hour.
9. Apply a Bonferroni adjustment to day-level comparisons.
10. Estimate incremental conversions, ROI, and break-even revenue using explicitly stated assumptions.
Key Findings from the Notebook
Metric	Result
Total users	588,101
Ad-group users	564,577
PSA-group users	23,524
Ad-group conversions	14,423
PSA-group conversions	420
Ad-group conversion rate	2.555%
PSA-group conversion rate	1.785%
Absolute lift	0.769 percentage points
Relative lift	43.1%
95% CI for absolute lift	0.595 to 0.943 percentage points
Two-proportion z-test p-value	1.71 × 10⁻¹³


The observed conversion rate is higher in the ad group, and the statistical test indicates a statistically significant difference. Statistical significance alone does not prove that the ad caused the difference.
Exposure and Timing
In the ad group, observed conversion rates increase across the notebook's ad-exposure buckets, from approximately 0.25% for 1–5 ads to 17.14% for 100+ ads. This is an association, not proof that showing more ads causes higher conversion; user intent and other factors may influence both exposure and conversion.

Day-level comparisons show statistically significant differences after the notebook's Bonferroni adjustment for Monday, Tuesday, and Wednesday. The groups also have different day/hour distributions, so these comparisons should be interpreted cautiously.
Illustrative Business Impact
The notebook assumes:
- Cost per user shown an ad: 0.05 currency units
- Revenue per conversion: 25.00 currency units
Under these assumptions, the notebook estimates approximately 4,343 incremental conversions, 108,575 in incremental revenue, 28,229 in ad cost, 80,346 in net profit, and 285% ROI. These are scenario estimates, not verified financial results. Replace the assumptions with realistic campaign-specific values before making business decisions.
Important Limitations and Next Steps
- The group sizes are highly imbalanced (about 96% ad and 4% PSA). Investigate how assignment and sampling occurred.
- The notebook's day and hour balance checks return very small p-values, suggesting exposure-time distributions differ between groups.
- The notebook's README originally mentioned power analysis, but a completed power-analysis calculation is not present in the current notebook. Add and validate it before claiming achieved power, required sample size, or minimum detectable effect.
- The notebook's final narrative cell contains placeholders. Replace them with actual results or remove the unfinished template.
- Consider reporting effect sizes and confidence intervals alongside p-values, and avoid claiming causality unless randomization and experiment implementation are validated.
Repository Structure
marketing-ab-test-analysis/
├── Marketing_AB.ipynb
├── README.md
├── requirements.txt
├── .gitignore
└── marketing_AB.csv   # download separately; not included
How to Run
1. Install Python and Jupyter Notebook.
2. Download the dataset and save it as marketing_AB.csv beside the notebook.
3. Install dependencies:pip install -r requirements.txt
4. Open Jupyter Notebook and run Marketing_AB.ipynb from top to bottom.
