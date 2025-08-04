---
layout: post
title:  "Card Transactions Dashboard"
subtitle: "A deep dive into transaction trend, user behavior, merchant activity, and credit risk using Power BI & DAX"
date:   2025-05-31T14:25:52-05:00
author: jmarielaure
categories: "Dashboard_and_reporting"
---

## 📝 Description

This Power BI report provides an in-depth analysis of **online and in-store card transactions** made by **2000 users** with several credit and debit cards **between Jan 2010 and Oct 2019**. It offers detailed insights into:

- Trends in successful transactions  
- Tracking of declined transactions and their causes  
- Geographic distribution of merchants  
- Demographic profiles of card users (age, credit score, income, etc.)  
- Individual behavioral analysis via client-specific dashboards  
- Monitoring of indebted customers by debt categories  

This dashboard could be used to support multiple business teams, for example:

- **Transaction trend analysts**  
- **CRM and marketing teams** for client segmentation  
- **Banking advisors** for personalized analysis and debt management  

---

## 🔌 Data Sources

- 📂 Excel and JSON files: `user_data`, `transaction_data`, `cards_data`, `mcc_json`  
- 📥 Import mode: **Import**  
- 📅 Data is updated **manually** 

NB: The dataset used was found on Kaggle and was initially used for a machine learning project purpose.

---

## 🔧 Data Preparation & Modeling

No other tools or software were used during this project. Therefore all the cleaning and data preparation was made using Power Query and DAX.

### ⚙️ Power Query Transformations

- Data cleaning and enrichment (filtering, removing duplicates/columns, format correction)  
- Merging of multiple Excel sources into structured tables  
- Adding time table (`Year`, `Quarter`, `Month`) for better temporal analysis  
- Creating a `merchant` table from `transaction_data`, enriched via `mcc_json` mapping  

### 🧠 Data Modeling & DAX Calculations

We opted for a **snowflake schema** for more flexibility in this exploratory project, although a star schema is often preferred for performance.

- Relationships established between tables: `clients`, `transactions`, `merchants`, `cards`  
- Creation of **bridge tables** to handle many-to-many (N:N) relationships  and calculated/parameters tables
- Use of **advanced DAX measures** for key business indicators  
- Implementation of **field parameters** to enable dynamic KPIs in visuals  

📌 **Example DAX Measure**:

```dax
Success Rate = DIVIDE([Successful Transactions], [Total Transactions])

---

## 🧭 Report Pages

The report consisted in 5 pages:

✅ **Approved Transactions** : An overview of successful transactions: trends over time, success rate, average value, etc.

❌ **Declined Transactions** : Analysis of failed transactions, highlighting the most frequent rejection causes.

🏪 **Merchants** : Geographic distribution of merchants and associated transaction amounts.

👥 **Demographics**: Aggregate view of user profiles: age groups, credit scores, income status.

🕵️ **Client Profile**: An individual client view (via slicer) displaying spending habits, segments, detailed transactions.

💸 **Debtors Table (via drill-through)**: Focus on indebted clients in the choosen debt category, categorized by risk levels and financial indicators. (This page can be accessed through the donut chart on the demographic page)

---

## 📊 Example of Key Metrics & KPIs

- 💳 **Total number of transactions**  : Over **13 095K** transactions processed across 8 years  
- ✅ **Success rate vs. failure rate**  : **98%** of all card transactions were approved
- 📉 **Rejection rate and dominant cause**: **2%** of transactions failed, with **62%** of failures due to **insufficient balance**  
- 🌍 **Geographic breakdown of merchant transactions**  : Majority of transactions occurred North America, with **50%** of total volume
- 👤 **User counts by demographic profile** (age, credit score, income)  : Most  users were aged **45–54**, with average credit scores above **710** 
- 🧾 **Average transaction amount by type or merchant country**  : Roughly **41€** per approved offline transactions and **57€** for approved online transactions
- 🕵️‍♀️ **Total spending per client**  
- 🔴 **Number of debtors by risk tier**: 95% of cthe user were listed as debtors with 80% with a debt less than 100k.

---

## 🧰 Methodology steps

1. **Business needs assessment**  
2. **Data exploration and cleaning** (Power Query)  
3. **Schema modeling and calculated tables**  
4. **DAX calculation** for KPIs and advanced indicators  
5. **UX design** of the dashboard (navigation, slicers, visuals)  


---

## 🧠 Technical Skills Applied

- **Power BI Desktop** (modeling, interface design, interactivity)  
- **Power Query (M)** for ETL and data preparation  
- **DAX**: calculated measures, columns, tables, conditionnal formatting, and dynamic KPIs  
- **UX & Data Storytelling**  
- **Business analysis** (segmentation, scoring, performance visualization)

---

## ⚠️ Known Limitations

- 📁 Manual data refresh (no automated pipeline in this version)  
- Some calculated columns in DAX could have been handled upstream  
- Dashboard not optimized for mobile/tablet display (desktop only)

---

## 🔮 Future Improvements

- Alert system integration (e.g. **spike in transaction failures**) via Power BI Service  
- Behavioral segmentation using **clustering or machine learning**  
- Additional visuals to highlight **correlations between KPIs and client behavior**

---

## 👥 Contributor

**Author**: jmarielaure — Personal project for portfolio  
✉️ **Contact**: [LinkedIn](#) | [Email](#)
