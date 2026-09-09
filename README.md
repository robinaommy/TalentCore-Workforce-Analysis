# TalentCore-Workforce-Analysis

**BUSINESS UNDERSTANDING**
TalentCore is a fictional pan-African technology services company with offices in Nairobi, Mombasa, Kisumu, Kampala, Dar es Salaam, and Kigali. With a workforce spread across six departments, TalentCore is committed to building a high-performing, engaged, and well-retained team through data-driven people decisions. 

**PROBLEM STATEMENT**
TalentCore would like to make some strategic talent decisions and wants answers on the following:
Attrition Patterns
Compensation Equity
Performance Trends

**PROJECT OBJECTIVES**
Understand attrition patterns.  Identify where and why employees are leaving.
Monitor compensation equity.  Assess whether pay is distributed fairly across gender, role, and department.
Evaluate performance trends.  Understand how performance varies across departments and levels.
Support strategic talent decisions.  Translate findings into concrete, prioritized recommendations for leadership.

**DATA UNDERSTANDING**
The source file contained 1,000 rows across 16 fields: Employee ID, Full Name, Hire Date, Exit Date, Department, Job Role, Office Location, Gender, Age, Education Level, Monthly Salary, Performance Rating, Training Hours, Overtime, Attrition Status, and Remarks.
Initial profiling revealed the dataset was far less complete than its row count suggested: 753 of the 1,000 rows contained only a Hire Date, with every other field blank, leaving 247 rows with genuine employee-level data. The data also carried widespread formatting inconsistencies typical of manual, multi-source entry: mixed date formats, inconsistent text casing, currency-prefixed numbers stored as text, and several statistically impossible values (e.g., an age of 200 and -5).


**DATA MODELING**
This phase built the analytical structure needed to answer the business questions: a star schema and a library of DAX measures 
Star Schema
Employee  — Employee ID, Job Role, Department, Location, and date foreign keys, plus measures (Salary, Performance Rating, Training Hours, Age, Overtime, Attrition Status).
Date  — full calendar with Year/Quarter/Month, linked to Hire Date.
Location  — Office Location mapped to Country and Region, enabling geographic rollups.
JobRole  — 24 job roles mapped to Function and Level (Individual Contributor / Team Lead / Manager).
Department  — departments grouped into a Function Group (Revenue-Generating / Operations & Delivery / Corporate Support).

**Calculated Columns**
Tenure (Years)  — years of service, computed to the Exit Date for leavers and to the current date for active staff.
Salary Band  — quartile-based compensation tiers (Entry / Mid / Senior / Executive), set from the actual salary distribution rather than round-number guesses.
Age Band  — four-group age segmentation (18-29, 30-39, 40-49, 50-65) for workforce composition views.

**Key Measures**
Total Employees, Exited Employees, Attrition Rate, Avg Tenure (Active/Exited), Avg and Median Monthly Salary, Avg Salary by Gender, Pay Gap %, Avg Performance Rating, Avg Training Hours, plus coverage-count companions (e.g., Rated Employee Count) so every average carries its sample size.

**INSIGHTS** (based on 243 of 1,000 source records)
Attrition is uneven, not uniform:  company-wide attrition is 15.3%, but Finance runs 6+ points above average despite being the second-highest-paid department — pay is not the likely driver.
Customer Support is the highest-priority department:  the largest team (22% of headcount) is simultaneously the lowest-paid, lowest-performing, and second-highest-attrition department — a compounding, not isolated, risk.
Attrition happens early:  leavers averaged 2.4 years of tenure vs. 5.1 for active staff, pointing to onboarding and early-tenure experience as the likely lever, not long-term burnout.
No material gender pay gap:  male vs. female average pay differs by under 1%, with a near-even gender split — no evidence of a systemic pay-equity issue at the aggregate level.
Top performers may be under-rewarded:  Sales holds the highest performance rating company-wide but is paid well below Engineering, creating retention exposure for a high-performing team.

**RECOMMENDATIONS**
Prioritize a Customer Support retention and compensation review as the highest-leverage action. In parallel: investigate Finance's elevated attrition through targeted exit interviews, strengthen onboarding and first-two-year support company-wide, and review Sales compensation relative to performance to protect top performers from external offers.









