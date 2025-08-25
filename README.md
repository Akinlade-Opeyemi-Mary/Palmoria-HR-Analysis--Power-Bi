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

# 🛠 TOOLS USED

- **Microsoft Power BI** → Primary tool for data modeling, dashboard design, and storytelling.  
- **Power Query Editor** → Data cleaning, transformation, and preparation.  
- **DAX (Data Analysis Expressions)** → Creation of calculated columns and measures (e.g., Bonus Amount, Salary + Bonus, Pay Gap %, Compliance Checks).  
- **Microsoft Excel** → Initial review and understanding of dataset structure (bonus mapping rules, salary validation).  
- **GitHub** → Documentation, version control, and portfolio presentation.  

# 🧹 DATA CLEANING AND PREPARATION

Before analysis, the dataset was reviewed and cleaned in **Power Query Editor** to ensure accuracy and consistency.  

## Key Steps Taken:
1. **Missing Values**  
   - Employees without salary → Removed (assumed no longer employed).  
   - Blank or missing gender → Reassigned as *"Undisclosed"*.  
   - Null departments → Dropped (could not be mapped to any business unit).  

2. **Duplicate Records**  
   - Checked Employee Name & Department fields for duplicates.  
   - Retained unique entries only.  

3. **Salary Validation**  
   - Ensured all salary values were numeric.  
   - Corrected any incorrect formats.  

4. **Bonus Mapping Integration**  
   - Used `Palmoria Bonus Mapping` table.  
   - Merged with main employee dataset using **Department** and **Performance Rating**.  
   - Ensured each employee had the correct bonus allocation rule.  

5. **Data Type Standardization**  
   - Salary → Currency (NAIRA).  
   - Rating → Text/Categorical.  
   - Gender/Department/Region → Categorical.  

✅ Final dataset was clean, consistent, and ready for **Power BI modeling and visualization**.  

# 🔍 Exploratory Data Analysis (EDA)

The purpose of the EDA was to explore the workforce dataset, identify underlying patterns, and establish a foundation for meaningful Power BI insights.  

## Key Explorations Conducted

1. **Dataset Structure**  
   - Total Employees: *946 records (Palmoria Group)*  
   - Tables Analyzed:  
     - `Palmoria Group EMP` → Employee-level data (Department, Gender, Salary, Region, Rating).  
     - `Palmoria Bonus Mapping` → Bonus allocation framework (Department vs. Rating).  

2. **Gender Distribution**  
   - Employees classified as *Male, Female, or Undisclosed*.  
   - Verified accuracy of gender categories after cleaning.  

3. **Department & Regional Spread**  
   - Workforce breakdown across multiple departments.  
   - Regional presence confirmed in *Abuja, Lagos, and Kaduna*.  

4. **Salary Structure**  
   - Average salary by gender and department.  
   - Salary threshold compliance: *292 employees earn above $90K; 654 below*.  
   - Pay gap analysis revealed *male salaries are ~4% higher* on average.  

5. **Performance Ratings**  
   - Distribution across 5 categories: *Very Poor → Very Good*.  
   - Gender-based comparison highlighted rating imbalances.  

6. **Bonus Allocation Readiness**  
   - Ensured all departments mapped correctly to bonus rules.  
   - Previewed total company-level bonus allocation (~$29.7K).  

---

✅ The EDA revealed critical insights into **employee demographics, pay disparities, rating fairness, and bonus allocation structures** — forming the basis for in-depth Power BI visualization and HR decision-making.  

# 📊 DAX COLUMNS & MEASURES

---

## 🔹 DAX Columns  

Some key calculated columns created include:  

### **Total Compensation**  
```DAX
Total Compensation = 
'Palmoria Group emp-data'[Salary] + 
'Palmoria Group emp-data'[Bonus Amount]
```
### **Salary Band**  
Categorizes employees into salary ranges.  

```DAX
Salary Band =
SWITCH(
    TRUE(),
    'Palmoria Group emp-data'[Salary] < 10000, "<10K",
    'Palmoria Group emp-data'[Salary] < 20000, "10K–20K",
    'Palmoria Group emp-data'[Salary] < 30000, "20K–30K",
    'Palmoria Group emp-data'[Salary] < 40000, "30K–40K",
    'Palmoria Group emp-data'[Salary] < 50000, "40K–50K",
    'Palmoria Group emp-data'[Salary] < 60000, "50K–60K",
    'Palmoria Group emp-data'[Salary] < 70000, "60K–70K",
    'Palmoria Group emp-data'[Salary] < 80000, "70K–80K",
    'Palmoria Group emp-data'[Salary] < 90000, "80K–90K",
    'Palmoria Group emp-data'[Salary] < 100000, "90K–100K",
    "100K+"
)
```
### **Bonus Amount**
Lookup bonus by department & performance rating.
```Bonus Amount =
SWITCH(
    TRUE(),
    'Palmoria Group emp-data'[Rating] = "Very Good", 
        LOOKUPVALUE(
            'Bonus Mapping'[Very Good], 
            'Bonus Mapping'[Department], 
            'Palmoria Group emp-data'[Department]
        ),
    'Palmoria Group emp-data'[Rating] = "Good", 
        LOOKUPVALUE(
            'Bonus Mapping'[Good], 
            'Bonus Mapping'[Department], 
            'Palmoria Group emp-data'[Department]
        ),
    'Palmoria Group emp-data'[Rating] = "Average", 
        LOOKUPVALUE(
            'Bonus Mapping'[Average], 
            'Bonus Mapping'[Department], 
            'Palmoria Group emp-data'[Department]
        ),
    'Palmoria Group emp-data'[Rating] = "Poor", 
        LOOKUPVALUE(
            'Bonus Mapping'[Poor], 
            'Bonus Mapping'[Department], 
            'Palmoria Group emp-data'[Department]
        ),
    'Palmoria Group emp-data'[Rating] = "Very Poor", 
        LOOKUPVALUE(
            'Bonus Mapping'[Very Poor], 
            'Bonus Mapping'[Department], 
            'Palmoria Group emp-data'[Department]
        )
)
```
### To support deeper HR insights, several DAX measures were created:
🎯 Employee Distribution

Total Employees
```Total Employee = COUNT('Palmoria Group emp-data'[Employee])```

## 👥 Employee Distribution  
```Total Employees = COUNT('Palmoria Group emp-data'[Employee])
Employees Above 90K = CALCULATE(COUNTROWS('Palmoria Group emp-data'), 'Palmoria Group emp-data'[Salary] > 90000)
Employees Below 90K = CALCULATE(COUNTROWS('Palmoria Group emp-data'), 'Palmoria Group emp-data'[Salary] <= 90000)
Undisclosed Employees = CALCULATE(COUNTROWS('Palmoria Group emp-data'), ISBLANK('Palmoria Group emp-data'[Salary]))
```
- **Employees Above $90K**  
- **Employees Below $90K**  
- **Undisclosed Employees**  

---

## 💰 Compensation Analysis  
- **Total Compensation** = Salary + Bonus  
- **Average Salary, Bonus & Compensation**  
- **% in Each Salary Band**  
- **% of Total Employees**  

---

## 👩‍💼 Gender-Based Insights  
- **Female vs. Male Employees**  
- **Female % / Male % of Total Workforce**  
- **Average Salary: Female vs. Male**  
- **Gender Pay Gap (%)**  
- **Compensation Share: Female vs. Male**  
- **Undisclosed %**  

---

## 🎁 Bonus Insights  
- **Total Bonus Paid**  
- **Bonus as % of Salary**  
- **Bonus as % of Total Compensation**  
- **Bonus Distribution by Gender**  
- **Bonus Distribution by Region**  
- **Bonus Share Insight (dynamic measure)**  

---

## 🌍 Regional Insights  
- **Top Region by Spend**  
- **Top Region Insight (dynamic output)**  
- **Regional Spend Distribution**  

# 📊 VISUALIZATION

The Palmoria HR dashboard was designed with a **multi-page layout** to highlight workforce, compensation, gender, bonus, and regional insights.  

### Pages & Highlights  
1️⃣ **Overview** – KPI cards (Total Employees, >$90K, <$90K, Gender Split), Salary Band Distribution.  
2️⃣ **Compensation** – Avg Salary, Bonus & Total Compensation, % by Salary Band.  
3️⃣ **Gender** – Female vs Male Avg Salary & Bonus, Pay Gap %.  
4️⃣ **Bonus** – Bonus by Department, Gender, and % of Compensation.  
5️⃣ **Region** – Spend by Region, Top Region KPI.  

### 🎨 Design  
- **Color Palette:** `#FADCD5` (accent) + dark supporting shades.  
- **Style:** Rounded cards, clean fonts, minimal clutter.  
- **Storytelling Flow:** Overview → Compensation → Gender → Bonus → Region.  

![Alt text](https://github.com/Akinlade-Opeyemi-Mary/Palmoria-HR-Analysis--Power-Bi/blob/d98d43fd8605a9fc53c3e1fbdd97dd6f58160f8c/Palmoria%20Dashboard%20page%201.png)







