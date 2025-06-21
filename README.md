# Bank Loan Analysis Dashboard 📊💰

Welcome to the **Bank Loan Analysis Dashboard** project! 🚀 This exciting data analytics endeavor leverages **MS SQL Server** 🗄️ and **Power BI** 📈 to create a comprehensive, interactive dashboard that provides deep insights into loan performance, borrower profiles, and lending trends. Let’s dive into this data-driven journey! 🌟

---

## Project Overview 🎯

This project is designed to analyze bank loan data to empower stakeholders with actionable insights. By combining the power of SQL queries in **MS SQL Server** 🔍 and dynamic visualizations in **Power BI** 🎨, this can be used to monitor key performance indicators (KPIs), track loan trends, and assess portfolio health. The dashboard is divided into three main sections: **Summary**, **Overview**, and **Details**, each packed with metrics and visuals to support data-driven decisions. 💡

---

![Screenshot 2025-06-21 130813](https://github.com/user-attachments/assets/a6c58886-5ca5-4ef4-892b-a6980b017178)
---
![Screenshot 2025-06-21 130843](https://github.com/user-attachments/assets/c425cda7-8471-4483-b101-c27bda8dc349)
---
![Screenshot 2025-06-21 130916](https://github.com/user-attachments/assets/23f8d8ea-d310-4be8-9614-f4383125df9c)

## Objectives 🥅

- 📊 **Track Loan Performance**: Monitor total loan applications, funded amounts, and repayments with month-to-date (MTD) and month-over-month (MoM) comparisons.
- ✅ **Assess Loan Quality**: Analyze good vs. bad loans based on loan status to understand repayment risks.
- 🌍 **Explore Trends**: Visualize lending patterns by issue date, region, loan term, purpose, employment length, and home ownership.
- 🔎 **Provide Detailed Insights**: Offer a consolidated view of loan data for in-depth analysis.
- 🛠️ **Showcase Technical Skills**: Demonstrate proficiency in SQL, Power BI, data modeling, and visualization.

---

## Tools & Technologies 🛠️

- **MS SQL Server ** 🗄️: For data storage, database creation, and query execution.
- **SQL Server Management Studio (SSMS)** 🔍: To write and manage SQL queries.
- **Power BI** 📈: For data visualization, dashboard creation, and interactive reporting.
- **MS Excel** 📑: For supplementary data analysis and validation.
- **Power Query** 🧹: For data cleaning and transformation.
- **DAX** 📝: For creating calculated measures and KPIs in Power BI.

---

## Project Structure 🏗️

### Part 1: MS SQL Server 🗄️🔍

1. **Database Creation** 🏠:
   - Created a database to store loan data.
   - Designed tables to hold attributes like `ID`, `LOAN_AMOUNT`, `TOTAL_PAYMENT`, `ISSUE_DATE`, `LOAN_STATUS`, `INT_RATE`, `DTI`, and more.

2. **Data Import** 📥:
   - Loaded loan data into the database for analysis.

3. **SQL Queries** ✍️:
   - Wrote queries to compute KPIs such as:
     - Total Loan Applications: `COUNT(ID)`
     - Total Funded Amount: `SUM(LOAN_AMOUNT)`
     - Total Amount Received: `SUM(TOTAL_PAYMENT)`
     - Average Interest Rate: `ROUND(AVG(INT_RATE*100),2)`
     - Average DTI: `ROUND(AVG(DTI*100),2)`
   - Calculated MTD and PMTD metrics using `WHERE MONTH(ISSUE_DATE)` filters.
   - Analyzed good loans (`Fully Paid`, `Current`) vs. bad loans (`Charged Off`) with `CASE` statements.
   - Grouped data by `MONTH`, `ADDRESS_STATE`, `TERM`, `EMP_LENGTH`, `PURPOSE`, and `HOME_OWNERSHIP` for trend analysis.

   Example Query for Good Loan Percentage:
   ```sql
   SELECT 
       (COUNT(CASE WHEN LOAN_STATUS IN ('Fully Paid','Current') THEN id END)*100)/
       COUNT(ID) AS GOOD_LOAN_PERCENTAGE
   FROM bank_loan_data
   ```

4. **Query Validation** ✅:
   - Compared SQL results with Power BI, Tableau, and Excel outputs to ensure accuracy.

---

### Part 2: Power BI 📈🎨

1. **Data Connection** 🔗:
   - Connected Power BI to MS SQL Server to import query results.

2. **Data Cleaning & Modeling** 🧹:
   - Used **Power Query** to clean and transform data.
   - Created relationships between tables for efficient analysis.
   - Built a **Date Table** for time intelligence functions.

3. **DAX Measures** 📝:
   - Developed DAX formulas for KPIs, e.g., `SUM`, `SUMX`, `CALCULATE`, and date-based calculations.
   - Example: MTD Loan Applications = `CALCULATE(COUNT(bank_loan_data[ID]), MONTH(bank_loan_data[ISSUE_DATE]) = 12)`

4. **Dashboards** 📊:
   - **Dashboard 1: Summary** 📋:
     - KPIs: Total Loan Applications (38.6K), Total Funded Amount ($439.8M), Total Amount Received ($479.1M), Avg Interest Rate (12.0%), Avg DTI (13.39%).
     - Good vs. Bad Loan Metrics: Good Loan Percentage (86%), Bad Loan Funded Amount ($65.5M).
     - Loan Status Grid: Metrics by `LOAN_STATUS` (e.g., Fully Paid: $351.4M funded).
   - **Dashboard 2: Overview** 🌍:
     - Charts:
       - **Monthly Trends** (Line Chart): Loan metrics by issue date.
       - **Regional Analysis** (Filled Map): Lending by state (e.g., CA: $78.5M funded).
       - **Loan Term** (Donut Chart): 36 months (73%) vs. 60 months (27%).
       - **Employee Length** (Bar Chart): Distribution by employment duration.
       - **Loan Purpose** (Bar Chart): Debt consolidation ($232.5M funded).
       - **Home Ownership** (Tree Map): Mortgage ($219.3M) vs. Rent ($185.8M).
   - **Dashboard 3: Details** 🔎:
     - Comprehensive grid with all loan metrics for deep dives.

5. **Visual Formatting** 🎨:
   - Used **New Card Visuals**, filters, and navigation for a user-friendly experience.

---

## Key Metrics & Insights 📊🔍

- **Total Loan Applications**: 38,576, with 4,314 in December 2021 (MTD).
- **Total Funded Amount**: $439.8M, with $53.98M MTD.
- **Total Amount Received**: $479.1M, with $58.07M MTD.
- **Good Loans**: 86% of applications, $370.2M funded, $435.8M received.
- **Bad Loans**: 13% of applications, $65.5M funded, $37.3M received.
- **Top State**: California ($78.5M funded).
- **Top Purpose**: Debt consolidation ($232.5M funded).
- **Avg Interest Rate**: 12.05%, with MTD at 12.36%.
- **Avg DTI**: 13.33%, with MTD at 13.67%.

---

## Functionalities Learned 🧠

- **SQL** 🗄️: Database creation, `SELECT`, `GROUP BY`, `ORDER BY`, `COUNT`, `SUM`, `AVG`, `ROUND`, `CASE`, `DATENAME`, `MONTH`, CTEs, and partitions.
- **Power BI** 📈: Data connections, Power Query, DAX, time intelligence, KPI creation, chart design, and visual formatting.
- **Data Analysis** 📊: Cleaning, modeling, processing, and validation across SQL, Power BI, and Excel.

---

## How to Run the Project 🏃‍♂️

1. **Set Up MS SQL Server** 🗄️:
   - Install MS SQL Server and SSMS.
   - Create a database and import loan data.
   - Run SQL queries from the provided query document.

2. **Set Up Power BI** 📈:
   - Install Power BI Desktop.
   - Connect to MS SQL Server and import query results.
   - Load the `.pbix` file (if available) or recreate visuals using the provided dashboard structure.

3. **Validate Results** ✅:
   - Cross-check SQL outputs with Power BI visuals and Excel calculations.

---

## Future Enhancements 🚀

- 📡 **Real-Time Data**: Integrate live data feeds for up-to-date insights.
- 🤖 **Predictive Analytics**: Add machine learning to predict loan defaults.
- 📱 **Mobile Optimization**: Enhance Power BI dashboards for mobile access.
- 🌐 **Web Deployment**: Publish dashboards to Power BI Service for broader access.

---

## Conclusion 🎉

This **Bank Loan Analysis Dashboard** project is a testament to the power of combining **MS SQL Server** 🗄️ and **Power BI** 📈 to transform raw data into meaningful insights. From crafting complex SQL queries to designing interactive dashboards, this project showcases a full spectrum of data analytics skills. Explore the repository, run the dashboards, and uncover the story behind the loans! 📊💸

## Made with ❤ by [Karan Saxena](https://www.linkedin.com/in/karan1saxena/)
Happy analyzing! 😄
