# TechnoEcom-Digital-Transformation-Project

## 🚀 Project Overview

Business Context:
TechnoEcom is embarking on a digital transformation initiative to better understand its order and customer satisfaction patterns, with the goal of improving operational efficiency and the customer experience.

Problem Statement:
- What drives revenue variations across warehouses?
- How are orders distributed over time?
- Which payment methods correlate with customer satisfaction?, Etc.

Objectives:
1. Load and clean the TechnoEcom transactional dataset.
2. Perform exploratory data analysis (EDA) to surface key patterns.
3. Visualize revenue by warehouse, order distribution by month, and satisfaction by payment type.
4. Summarize actionable insights for the TechnoEcom operations team.

---

## 📂 Repository Structure
```pgsql
README.md
technoecom_project_learner_notebook.html  
data/
  └─ technoecom.csv          ← main transaction dataset  
notebooks/
  └─ technoecom_analysis.ipynb  
scripts/
  └─ eda.py                   ← standalone EDA script  
images/                       ← plots generated by notebook 
```
---

## 🛠️ Setup & Dependencies
1. **Python version**
  - Tested on Python 3.8+
2. **Required libraries**
```bash
pip install pandas numpy matplotlib seaborn jupyterlab
```

3. **Dataset**
  - Place `technoecom.csv` in the `data/` folder.

## 📥 Data Import
In a Jupyter/Colab environment, run:
```python
import pandas as pd

# When prompted in Colab, upload techneocom.csv
```python
df = pd.read_csv("technoecom.csv")
df.head()
```

---

## 🔍 Exploratory Data Analysis (EDA)
1. **Revenue by Warehouse**
```python
revenue_by_warehouse = tech_df.groupby("warehouse_name")["total_bill"].sum()
print(revenue_by_warehouse)
```
Outputs total billed revenue per warehouse. 

2. **Order Distribution by Month**
```python
tech_df["order_date"] = pd.to_datetime(tech_df["order_date"])
tech_df["month"] = tech_df["order_date"].dt.month
orders_by_month = tech_df["month"].value_counts().sort_index()
orders_by_month.plot(kind="bar")
```

3. **Customer Satisfaction vs. Payment Method**
```python
ct = pd.crosstab(tech_df["order_payment"], tech_df["customer_satisfaction"])
ct_pct = ct.div(ct.sum(axis=1), axis=0) * 100
ct_pct.plot(kind="bar", stacked=True)
```
Reveals that cash‐on‐delivery customers show higher dissatisfaction, likely due to delayed deliveries.

---

## 📈 Findings & Insights
- **Revenue**: Thompson warehouse leads with the highest total billing, followed by Nickolson and Bakers. 
- **Temporal Demand**: Order volumes peak in months X, Y, Z.
- **Payment Satisfaction**: Customers using COD report ~ % dissatisfaction vs. prepayment. 

## 🚧 How to Run
1. Clone the repo:
```bash
git clone https://github.com/yourusername/technoecom-analysis.git
cd technoecom-analysis
```
2. Launch Jupyter Lab and open the notebook:
```bash
jupyter lab
```
3. Follow the notebook cells in technoecom_project_learner_notebook.html to reproduce analysis.

---

## 🤝 Contributing
- Suggestions and pull requests are welcome!
- For major changes, please open an issue first to discuss what you’d like to change.







