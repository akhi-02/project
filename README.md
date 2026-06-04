# 📊 Customer Churn Prediction & Segmentation

> **IBM Telco Customer Churn Dataset | Python · Scikit-learn · Power BI**

---

## 🔍 Project Overview

Customer churn is one of the costliest problems for telecom companies. This project analyzes **7,043 Telco customers** to:

- Identify the key drivers of customer churn
- Build a machine learning model to predict which customers are likely to leave
- Segment customers into actionable risk groups using clustering
- Visualize insights in an interactive **Power BI dashboard**

---

## 🎯 Business Questions Answered

| # | Question | Finding |
|---|----------|---------|
| 1 | Does contract type affect churn? | Month-to-month customers churn at **3x the rate** of annual contract holders |
| 2 | Do high monthly charges drive churn? | Churners pay significantly **higher monthly charges** on average |
| 3 | Do new customers churn more? | Customers with **< 6 months tenure** are the highest risk group |
| 4 | Does internet service type matter? | Fiber optic users show **higher churn rates** than DSL users |
| 5 | What is the overall churn rate? | **26.5%** of customers churned |

---

## 📁 Project Structure

```
churn_project/
├── data/
│   └── telco_churn.csv                  # IBM Telco dataset (Kaggle)
├── notebooks/
│   └── Customer_churn_prediction.ipynb  # Full analysis notebook
├── outputs/
│   └── figures/                         # All EDA & model plots
├── dashboard/
│   └── churner_customer_dashboard.pbix  # Power BI dashboard
├── requirements.txt
└── README.md
```

---

## 🛠️ Tools & Technologies

| Category | Tools Used |
|----------|-----------|
| Language | Python 3 |
| Data manipulation | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Machine learning | Scikit-learn |
| Dashboard | Power BI Desktop |
| Environment | Jupyter Notebook |

---

## 📊 Dataset

- **Source:** [IBM Telco Customer Churn – Kaggle](https://www.kaggle.com/datasets/vedatgul/telco-churn-dataset)
- **Rows:** 7,043 customers
- **Columns:** 33 features including demographics, services, billing, and churn labels
- **Target variable:** `Churn Value` (1 = churned, 0 = retained)

**Key columns used:**

| Column | Description |
|--------|-------------|
| `Tenure Months` | How long the customer has been with the company |
| `Monthly Charges` | Monthly billing amount |
| `Total Charges` | Total amount billed |
| `Contract` | Month-to-month / One year / Two year |
| `Internet Service` | DSL / Fiber optic / No |
| `Churn Value` | Target variable (1 = churned) |
| `CLTV` | Customer Lifetime Value |
| `Churn Reason` | Reason for leaving (available for churned customers) |

---

## 🔄 Project Workflow

```
Raw Data → EDA → Cleaning → Feature Engineering → Modeling → Clustering → Dashboard
```

### 1. Exploratory Data Analysis (EDA)
- Churn rate distribution
- Churn by contract type, internet service, tenure, monthly charges
- Correlation heatmap of numeric features
- Top churn reasons analysis

### 2. Data Cleaning & Preprocessing
- Fixed `Total Charges` column (object → numeric)
- Dropped leakage columns: `Churn Label`, `Churn Score`, `Churn Reason`
- Dropped identifier/location columns: `CustomerID`, `Zip Code`, `Lat Long`
- One-hot encoded all categorical variables
- Scaled numeric features using `StandardScaler`

### 3. Feature Engineering
- Created `avg_monthly_spend` (TotalCharges / Tenure)
- Created `is_new_customer` (tenure < 6 months)
- Created `num_services` (count of subscribed add-on services)

### 4. Machine Learning Models

| Model | Accuracy | AUC-ROC |
|-------|----------|---------|
| Logistic Regression | ~80% | ~0.84 |
| Random Forest | ~85% | ~0.88 |

> **Random Forest** selected as the final model for higher accuracy and built-in feature importance.

### 5. Customer Segmentation (K-Means Clustering)
- Used Elbow Method to determine optimal K = 3
- Segmented customers into 3 risk groups:

| Segment | Label | Characteristics | Churn Rate |
|---------|-------|----------------|-----------|
| 0 | High-value loyalists | Long tenure, high spend, many services | Low |
| 1 | At-risk new customers | Short tenure, mid charges, month-to-month | High |
| 2 | Budget churners | Low charges, no add-ons, minimal engagement | Medium |

---

## 📈 Key Findings

- **Month-to-month contract** customers have the highest churn — offering annual plan discounts could reduce this significantly
- **Fiber optic internet** users churn more despite paying more — possible service quality issue worth investigating
- **The first 6 months** are the most critical retention window — customers who survive past month 12 rarely churn
- **Customers with no add-on services** (Online Security, Tech Support etc.) churn at a higher rate — upselling services improves retention

---

## 💡 Business Recommendation

> Customers on **month-to-month contracts** with **tenure < 6 months** and **monthly charges > ₹65** represent the highest-risk segment with a **~42% churn rate**.
>
> **Recommended action:** Proactively offer a 10–15% loyalty discount or upgrade incentive to this segment at the 3-month mark. Estimated retention improvement: **8–12%** in the high-risk group.

---

## ⚙️ How to Reproduce

1. Clone this repository
   ```bash
   git clone https://github.com/akhi-02/project.git
   cd customer-churn-prediction
   ```

2. Install dependencies
   ```bash
   pip install -r requirements.txt
   ```

3. Download the dataset from [Kaggle](https://www.kaggle.com/datasets/vedatgul/telco-churn-dataset) and place it in the `data/` folder

4. Open and run the notebook
   ```bash
   jupyter notebook notebooks/Customer_churn_prediction.ipynb
   ```

5. Open `dashboard/churner_customer_dashboard.pbix` in **Power BI Desktop** to explore the dashboard

---

## 📦 Requirements

```
pandas
numpy
matplotlib
seaborn
scikit-learn
jupyter
```

Install all at once:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

---

## 👩‍💻 Author

**Akhila**
- 📍 Hyderabad, India
- 🎓 B.Tech Computer Science — 2023
- 💼 Aspiring Data Analyst
- 🔗 [LinkedIn](https://www.linkedin.com/in/akhila-v-75667a269?) | [GitHub](https://github.com/akhi-02/project.git)

---

## 📌 Acknowledgements

- Dataset: [IBM Telco Customer Churn via Kaggle](https://www.kaggle.com/datasets/vedatgul/telco-churn-dataset)
- Inspired by real-world churn reduction strategies used in the telecom industry

---

*This project was built as part of my data analytics portfolio to demonstrate end-to-end analytical thinking — from raw data to business recommendations.*
