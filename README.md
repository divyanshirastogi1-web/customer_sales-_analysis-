Customer Sales Data Analysis

A Python-based data cleaning and exploratory data analysis (EDA) project on a raw customer sales dataset — covering data cleaning, outlier detection, and business-focused analysis with visualizations.

Project Description

Raw, real-world business data is rarely clean. This project takes a messy customer sales dataset (~10,200 records) with inconsistent text casing, mixed data types, missing values, and duplicate records, and works through a full analysis pipeline: cleaning the data, validating it, detecting outliers, and answering practical business questions with pandas, matplotlib, and seaborn.

The goal was to practice the two things most data analyst roles actually require day to day: turning messy inputs into a trustworthy dataset, and translating that dataset into answers a business stakeholder would care about (which cities drive revenue, whether customer feedback tracks with spending, how much revenue is concentrated in top customers, and so on).

Dataset:"C:\Users\DEll\Downloads\customer_sales_data (1).csv"

Data quality issues found in the raw file:

Inconsistent casing and whitespace in Gender, City, and Country (e.g. "M", "m ", "MALE" all representing the same value)
Age stored as text, with some values like "51.0 years" mixed in with plain numbers
Missing values across nearly every column (roughly 8–10% in several fields)
Duplicate rows and duplicate Customer_IDs
Dates stored as plain text rather than proper date types
What Was Done
Data cleaning — standardized text fields (lowercased, trimmed whitespace, mapped abbreviations to full values), extracted numeric ages from mixed text using regex, filled missing values using median (for skewed numeric fields) and mode (for categorical fields), removed duplicate rows and duplicate customer IDs, and converted date columns to proper datetime types.
Outlier detection — used z-scores on Age and Purchase_Amount to flag and remove statistically extreme values (|z| > 3), visualized before/after with boxplots.
Exploratory analysis — answered a set of business questions using groupby, aggregation, and correlation, each paired with a chart (histograms, bar charts, scatter plots, a stacked bar chart, and a pie chart).
Key Findings
Kolkata drives the most total revenue (~₹5.5 crore across 2,255 customers), notably higher than the other five cities, which cluster close together (~₹3.2–3.4 crore each).
Average spend is nearly identical across cities (~₹24,000–25,200) — Kolkata's revenue lead comes from having more customers, not higher-spending ones.
Gender has almost no effect on spending — average purchase amount is ~₹24,430 (female) vs. ~₹24,840 (male), a difference small enough to be noise rather than a real pattern.
Age and Feedback_Score show virtually no correlation with Purchase_Amount (correlation coefficients of 0.004 and -0.003 respectively) — spend doesn't track with either age or satisfaction in this dataset.
Revenue is only mildly concentrated: the top 10% of customers account for about 19% of total revenue — a much flatter distribution than the "80/20 rule" often assumed for customer revenue.
On average, ~727 days pass between a customer's signup date and their last recorded purchase.
Tech Stack
Python 3
pandas — data cleaning, transformation, aggregation
numpy — numeric operations, z-score outlier detection
matplotlib / seaborn — data visualization
scipy.stats — z-score calculation
