# Customer Shopping Behavior Analysis

## Overview

This project is an end-to-end **Data Analytics project** focused on analyzing customer shopping behavior and identifying patterns related to customer demographics, purchasing habits, subscriptions, discounts, shipping methods, and product performance.

The project follows a complete analytics workflow:

**Python → EDA & Data Cleaning → PostgreSQL → SQL Analysis → Power BI Dashboard → Business Report → Presentation**

The dataset contains **3,900 customer purchase transactions**.

---

## Dataset

The dataset contains customer shopping and transaction information, including:

* Customer ID
* Age
* Gender
* Item Purchased
* Category
* Purchase Amount
* Location
* Size
* Color
* Season
* Review Rating
* Subscription Status
* Shipping Type
* Discount Applied
* Promo Code Used
* Previous Purchases
* Payment Method
* Frequency of Purchases

Additional analytical columns were created during data preparation:

* `age_group`
* `purchase_frequency_days`

---

## Tools & Technologies

| Tool                      | Purpose                                     |
| ------------------------- | ------------------------------------------- |
| **Python**                | Data loading, exploration and preprocessing |
| **Pandas**                | Data manipulation and cleaning              |
| **PostgreSQL**            | Database storage and SQL analysis           |
| **SQL**                   | Business and customer analysis              |
| **SQLAlchemy / Psycopg2** | Python–PostgreSQL connection                |
| **Power BI**              | Interactive dashboard and visualization     |
| **Gamma**                 | Business presentation / PPT                 |
| **Jupyter Notebook**      | Python analysis and documentation           |

---

## Project Steps

### 1. Load Dataset

The dataset was loaded into Python using Pandas.

```python
import pandas as pd

df = pd.read_csv("customer_shopping_behavior.csv")
```

Initial inspection was performed using:

```python
df.head()
df.info()
df.describe(include="all")
df.isnull().sum()
```

---

### 2. Exploratory Data Analysis (EDA)

EDA was performed to understand:

* Dataset structure
* Data types
* Missing values
* Customer demographics
* Purchase behavior
* Product categories
* Subscription behavior
* Discounts and promotions
* Shipping preferences
* Customer ratings

---

### 3. Data Cleaning & Transformation

The data was cleaned and transformed before database analysis.

Key activities included:

* Handling missing review ratings
* Standardizing column names
* Converting column names to lowercase
* Replacing spaces with underscores
* Renaming `purchase_amount_(usd)` to `purchase_amount`
* Creating customer age groups
* Converting purchase frequency into numerical days
* Removing the redundant `promo_code_used` column

Missing review ratings were filled using the **median review rating of the corresponding product category**.

Example:

```python
df['Review Rating'] = df.groupby('Category')['Review Rating'].transform(
    lambda x: x.fillna(x.median())
)
```

---

### 4. PostgreSQL Database

The cleaned dataset was loaded into a PostgreSQL database.

The Python workflow uses:

* PostgreSQL
* SQLAlchemy
* Psycopg2

The cleaned DataFrame was uploaded to a PostgreSQL table named:

```text
customer
```

---

### 5. SQL Analysis

SQL queries were used to analyze customer and transaction data from PostgreSQL.

The analysis focused on areas such as:

* Customer purchasing behavior
* Revenue analysis
* Customer segmentation
* Subscription performance
* Discount usage
* Product/category performance
* Shipping behavior
* Customer demographics
* Purchase frequency

SQL was used to convert the cleaned transactional data into business-focused insights.

---

### 6. Power BI Dashboard

An interactive Power BI dashboard was created to visualize the analysis.

The dashboard provides insights into:

* Total revenue
* Customer demographics
* Purchase behavior
* Customer segments
* Subscription status
* Product categories
* Discounts
* Shipping methods
* Customer ratings

The dashboard allows users to explore customer behavior through interactive visualizations and filters.

---

### 7. Business Report

A business-focused report was created to summarize the major findings and translate the analysis into actionable insights.

Some key findings include:

* Male customers generated approximately **67.7% of total portfolio spend**.
* The dataset contains a strong loyal customer base, with **3,116 loyal customers**.
* There are **701 returning customers** and **83 new customers**.
* Subscribers spend slightly less per order than non-subscribers.
* **839 purchases** exceeded the average purchase amount while using a discount.
* Express shipping had an average purchase amount of **$60.48**, compared with **$58.46** for standard shipping.
* Revenue was relatively balanced across different age groups.

---

## Dashboard

The Power BI dashboard converts the SQL analysis into an interactive visual analytics experience.

### Key Dashboard Areas

* Customer demographics
* Revenue analysis
* Customer loyalty
* Subscription analysis
* Discount analysis
* Product/category performance
* Shipping analysis
* Purchase behavior

**Power BI File:**
`Customer Behavior Dashboard.pbix`

---

## Results & Business Insights

The analysis highlights several potential business opportunities:

### Customer Loyalty

The customer base is heavily concentrated among loyal customers. This indicates that retention and repeat-purchase strategies are important areas for analysis.

### Subscription

Subscription customers are a relatively small portion of the customer base and have slightly lower average spending than non-subscribers.

### Discounts

A significant number of high-value purchases were made with discounts, indicating that promotional strategies can be analyzed based on product/category demand rather than applying discounts universally.

### Products

Several highly rated products also show strong sales activity, providing opportunities for product-focused marketing and merchandising.

### Shipping

Express shipping has a modestly higher average purchase amount than standard shipping, providing a potential area for further testing.

---

## Project Workflow

```text
Customer Dataset
       ↓
Python / Pandas
       ↓
EDA
       ↓
Data Cleaning & Transformation
       ↓
PostgreSQL Database
       ↓
SQL Analysis
       ↓
Power BI Dashboard
       ↓
Business Report
       ↓
Gamma Presentation
```

---

## Project Files

```text
Customer-Shopping-Behavior-Analysis/
│
├── Customer_Shopping_Behavior_Analysis.ipynb
├── Customer_Shopping_Behavior_SQL.sql
├── Customer Behavior Dashboard.pbix
├── Customer-shopping-behavior-analysis.pdf
├── customer_shopping_behavior.csv
└── README.md
```

---

## How to Run

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd Customer-Shopping-Behavior-Analysis
```

### 2. Install Python Libraries

```bash
pip install pandas sqlalchemy psycopg2-binary jupyter
```

### 3. Run the Jupyter Notebook

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open:

```text
Customer_Shopping_Behavior_Analysis.ipynb
```

Run the notebook from beginning to end to:

* Load the dataset
* Perform EDA
* Clean the data
* Create new analytical columns
* Connect to PostgreSQL
* Upload the cleaned dataset

### 4. Set Up PostgreSQL

Create a PostgreSQL database:

```text
customer_behavior
```

Configure your PostgreSQL connection in the Python notebook.

**For security, do not store database passwords directly in the GitHub repository. Use environment variables or a `.env` file instead.**

### 5. Run SQL Analysis

Open:

```text
Customer_Shopping_Behavior_SQL.sql
```

Run the queries against the PostgreSQL `customer` table.

### 6. Open Power BI Dashboard

Open:

```text
Customer Behavior Dashboard.pbix
```

Refresh the data connection if required.

### 7. Review the Report & Presentation

The final business findings are documented in:

```text
Customer-shopping-behavior-analysis.pdf
```

A presentation was also created using **Gamma** to communicate the project findings in a business-friendly format.

---

## Key Skills Demonstrated

* Python
* Pandas
* Exploratory Data Analysis
* Data Cleaning
* Data Transformation
* SQL
* PostgreSQL
* Database Integration
* Business Analytics
* Power BI
* Data Visualization
* Business Reporting
* Presentation & Storytelling

---

## Conclusion

This project demonstrates an end-to-end approach to solving a business analytics problem — from **raw customer transaction data to cleaned data, SQL analysis, interactive Power BI visualization, and business recommendations**.

It showcases practical skills in **Python, SQL, PostgreSQL, Power BI, data cleaning, EDA, and business intelligence**, making it suitable as a portfolio project for Data Analyst and entry-level Data Engineer roles.
