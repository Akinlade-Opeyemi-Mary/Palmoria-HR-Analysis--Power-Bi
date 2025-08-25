# PALMORIA GROUP HR ANALYSIS  

## 📑 TABLE OF CONTENT
1. [Introduction](#introduction)
2. [Business Objective](#business-objective) 
3. [Data Source](#data-source)  
4. [Tools Used](#tools-used)  
5. [Data Cleaning & Preparation](#data-cleaning--preparation)  
6. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)  
7. [DAX Measures](#dax-measures)  
8. [Visualizations](#visualizations)  
9. [Insights & Key Findings](#insights--key-findings)  
10. [Summary of Gender-Related Insights for Management](#summary-of-gender-related-insights-for-management)  
11. [Recommendations](#recommendations)  
12. [Conclusion](#conclusion)  

# 🔹 INTRODUCTION 

Palmoria Group is a manufacturing company based in Nigeria with operations across three regions. Recently, the company has come under public scrutiny after a major news outlet described it as a *“Manufacturing Patriarchy”*. The report raised concerns about gender imbalance, unequal pay, and potential non-compliance with new salary regulations.  

This negative publicity poses a serious threat to Palmoria’s ambition of expanding its operations to other regions and eventually overseas. In response, the company’s leadership commissioned a comprehensive HR analysis to uncover the root causes of these issues and provide actionable insights.  

As part of this initiative, I was engaged as an **HR Analytics Consultant** to analyze Palmoria’s workforce data, evaluate key HR metrics, and support management in making informed, equitable, and compliant decisions.  

# 🎯 BUSINESS OBJECTIVE 

The goal of this analysis is to help Palmoria Group’s management team identify and address HR issues that could hinder gender equality, employee satisfaction, and compliance with industry regulations. Specifically, the objectives are to:  

1. **Assess Workforce Diversity**  
   - Understand the gender distribution across departments and regions.  
   
2. **Evaluate Performance Ratings**  
   - Compare ratings by gender to detect possible bias or imbalance.  

3. **Analyze Salary Structure**  
   - Investigate whether gender pay gaps exist within departments and regions.  

4. **Check Salary Compliance**  
   - Determine if employees meet the newly adopted $90,000 minimum salary regulation.  

5. **Examine Pay Distribution**  
   - Visualize employee distribution across salary bands (in $10,000 intervals), both company-wide and by region.  

6. **Allocate Bonuses Fairly**  
   - Calculate performance-based bonuses, integrate them into total compensation, and analyze payout by employee and region.  

7. **Provide Actionable Recommendations**  
   - Deliver data-driven insights to guide HR policies, improve fairness, and strengthen Palmoria’s reputation as it prepares for expansion.
  
# 📂 DATA SOURCE

The dataset was provided by **Digital Skills Africa / Incubator Hub** as part of the capstone project. It consists of two main tables:  

1. **Palmoria Group Employee Table (`Palmoria Group Emp`)**  
   - Contains employee-level HR information such as:  
     - Employee Name  
     - Department  
     - Gender  
     - Salary  
     - Region  
     - Performance Rating  

2. **Palmoria Bonus Mapping Table (`Palmoria Bonus Mapping`)**  
   - Defines bonus allocation rules based on department and performance rating:  
     - Department  
     - Very Poor  
     - Poor  
     - Average  
     - Good  
     - Very Good  

📥 **Download Dataset:** [Click here to download](https://canvas.instructure.com/files/folder/courses_11955369/DSA%20Capstone%20Project%20Files)  

## 🛠 Tools Used  

- **Microsoft Power BI** → Primary tool for data modeling, dashboard design, and storytelling.  
- **Power Query Editor** → Data cleaning, transformation, and preparation.  
- **DAX (Data Analysis Expressions)** → Creation of calculated columns and measures (e.g., Bonus Amount, Salary + Bonus, Pay Gap %, Compliance Checks).  
- **Microsoft Excel** → Initial review and understanding of dataset structure (bonus mapping rules, salary validation).  
- **GitHub** → Documentation, version control, and portfolio presentation.  

