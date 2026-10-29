# A/B Testing Analysis: Landing Page Experiment
### Project Overview

This project analyzes an A/B testing experiment conducted by an e-commerce company to evaluate whether a newly designed landing page improves user conversion rates. Users were randomly assigned to either the control group (old landing page) or the treatment group (new landing page). The analysis determines whether the new page leads to a statistically significant increase in conversions.

### Business Problem

Does the new landing page increase the conversion rate compared to the existing page?

### Dataset

- ab_data.csv: experiment data per user (group assignment, landing page shown, conversion status)
- countries.csv: country for each user

Source: the e-commerce landing page A/B test dataset from Udacity's Data Analyst Nanodegree ("Analyze A/B Test Results" project).

Post-cleaning dataset size: **290,584 users**. I removed 3,893 rows where the group and page didn't match first, then the 1 remaining duplicate user. (Removing duplicates first would wrongly drop about 2,000 valid users.)

### Analysis Approach

The project follows a structured data analysis workflow:

- Data loading, exploration, and cleaning
- Experiment validation — checking group and page assignment consistency
- Conversion rate calculation for control vs. treatment groups
- Hypothesis testing using a two-proportion Z-test (two-tailed)
- Country-level segmentation with statistical validation
- Logistic regression to control for geography and confirm page effect
- Statistical power and minimum detectable effect

### Key Results

The control group (old landing page) had a conversion rate of 12.04%, while the treatment group (new landing page) had a conversion rate of 11.88%, a difference of −0.16 percentage points. A two-proportion Z-test (two-tailed) returned a Z-statistic of −1.31 and a p-value of 0.190. Since the p-value exceeds the 0.05 significance threshold, the difference is not statistically significant. The 95% confidence interval for the difference is [−0.39 pp, +0.08 pp], which includes zero, further confirming the result.

Country-level Z-tests showed no significant difference across US (p = 0.132), CA (p = 0.195), or UK (p = 0.635). Logistic regression confirmed that neither the page variant nor user geography is a statistically significant predictor of conversion.

With about 145,000 users per group, the test could reliably detect (80% power) a change of about 0.34 percentage points. The observed difference is smaller than that, so any real effect of the new page is very small.


### Conclusion

There is no statistical evidence that the new landing page improves conversion rates. Results are consistent across the Z-test, confidence interval, and logistic regression. The recommendation is to retain the existing landing page or pursue alternative design changes in future experiments.


### Visualizations
Conversion Rate by Group

![Conversion Rate by Group](visuals/conversion_rate_by_group.png)


Conversion Rate by Country

![Conversion Rate by Country](visuals/conversion_rate_by_country.png)


### Tools Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Statsmodels
- Jupyter Notebook

### Project Structure

```
ab-test-landing-page-analysis
│
├── data
│   ├── ab_data.csv
│   └── countries.csv
│
├── notebooks
│   └── ab_test_analysis.ipynb
│
├── visuals
│   ├── conversion_rate_by_group.png
│   └── conversion_rate_by_country.png
│
├── requirements.txt
└── README.md
```

### How to Run

```bash
git clone https://github.com/GouthamMantena/ab-testing-landing-page-analysis.git
cd ab-testing-landing-page-analysis
pip install -r requirements.txt
cd notebooks
jupyter notebook ab_test_analysis.ipynb
```

Run all cells from top to bottom.

---

