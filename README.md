# 📊 SaaS Analytics Dashboard

> **A Power BI report on revenue, customers, subscriptions and marketing for a subscription software company**

This project uses sample data for a software company that sells monthly subscriptions. The Power BI report shows how much money comes in each month, who signs up, who cancels, and how much it costs to win new customers. Everything is on five pages, with filters for country, industry, plan and year.

![Power BI](https://img.shields.io/badge/Power%20BI-DAX%20%7C%20Power%20Query-yellow?style=flat-square&logo=powerbi)
![SQL](https://img.shields.io/badge/SQL-MS%20SQL%20Server-blue?style=flat-square&logo=microsoftsqlserver)
![Python](https://img.shields.io/badge/Python-Pandas%20%7C%20NumPy-blue?style=flat-square&logo=python)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)

---

# 📸 Dashboard Preview

<table>
<tr>
<td align="center">

### Executive Overview

<img width="587" height="330" alt="Image" src="https://github.com/user-attachments/assets/213ba3af-0b20-489d-8918-d0555134f156" />

</td>

<td align="center">

### Revenue Analytics

![Revenue Analytics](screenshots/Revenue_Analytics.png)

</td>
</tr>

<tr>
<td align="center">

### Customer Analytics

![Customer Analytics](screenshots/Customer_Analytics.png)

</td>

<td align="center">

### Subscription Health

![Subscription Health](screenshots/Subscription_Health.png)

</td>
</tr>

<tr>
<td colspan="2" align="center">

### Marketing Analytics

![Marketing Analytics](screenshots/Marketing_Analytics.png)

</td>
</tr>
</table>

---

# 📖 The Story

Imagine you run revenue operations at a growing software company.

Every month someone asks you:

- Is monthly recurring revenue (MRR) going up?
- Are new customers making up for the ones who cancel?
- Which ways of finding customers are worth the money?
- Which plans bring in the most revenue?
- Which industries and countries have the most valuable customers?

Without a report, you would have to combine customer lists, billing files and marketing sheets by hand each month. This dashboard puts all of that in one place.

---

# 🎯 What the Report Answers

### Revenue

- How much MRR and yearly revenue (ARR) do we have?
- How much did we gain from upgrades and lose from downgrades and cancellations?
- How does revenue compare with last year?

### Customers

- How many customers are active, and how many are new?
- How long do customers stay?
- What is a customer worth over their lifetime?

### Subscriptions

- How many subscriptions are active?
- How many customers do we keep?
- Do we add more than we lose?

### Marketing

- What does it cost to win one customer?
- How long does it take to earn that money back?
- Which channels give the best return?
- Which countries bring in the most revenue?

---

# 🚀 What Is in the Report

- **5 report pages** with filters for country, industry, plan and year
- **About 55 DAX measures** for revenue, customers, subscriptions and marketing
- **5 tables of data** (customers, subscriptions, events, monthly revenue, marketing spend) plus a date table
- **Sample data:** 5,000 customers over 36 months (Jan 2022 to Dec 2024)
- **Custom theme and page navigation** with a sidebar on every page

---

## 🧱 Tools Used

| Part | Tool |
|---|---|
| Loading data | Power Query |
| Calculations | DAX |
| Report | Power BI Desktop |

---

## 🗂️ Data

The data is made up, but it is set up like real billing and customer files.

| File | What is in it | Rows |
|---|---|---|
| `customers.csv` | One row per customer: company, industry, size, country, sign-up date, channel, lifetime value | 5,000 |
| `subscriptions.csv` | One row per customer: plan, monthly price, start and end date, cancelled or not, months as a customer | 5,000 |
| `subscription_events.csv` | Every new sign-up, upgrade, downgrade and cancellation | 10,706 |
| `monthly_revenue.csv` | Revenue for each customer in each month | 68,490 |
| `marketing_spend.csv` | Spend each month for each of 5 channels | 180 |

The three customer-level tables connect to the `customers` table through `customer_id`. A date table (2022–2024) is built in DAX.

---

## 📈 Main Numbers

- **Active MRR:** about $1.47M
- **Yearly revenue (ARR):** about $17.6M
- **Customers:** 5,000
- **Cancelled subscriptions:** 1,626 (32.5%)
- **Average customer lifetime value:** about $34K

**Revenue changes from events (all time)**

| Event | Count | MRR change |
|---|---|---|
| New | 5,000 | +$1,775,501 |
| Upgrade | 2,479 | +$146,315 |
| Downgrade | 1,601 | −$75,417 |
| Cancellation | 1,626 | −$378,361 |

**By plan**

| Plan | Subscriptions | Share of active MRR |
|---|---|---|
| Enterprise | 841 | 63% |
| Growth | 1,180 | 22% |
| Starter | 2,979 | 15% |

---

# 💡 What Stands Out

| Topic | What the data shows | What to do about it |
|---|---|---|
| **Plans** | Enterprise is 17% of subscriptions but 63% of active MRR. Starter is 60% of subscriptions but only 15% of MRR. | Help Starter customers move up to Growth and Enterprise. |
| **Losses** | Cancellations removed about $378K of MRR, more than double the $146K gained from upgrades. | Spend more time on keeping customers and getting upgrades, not just on finding new ones. |
| **Marketing** | Spend stays near $1.1M each year, while monthly revenue grows from $3.1M (2022) to $8.8M (2023) to $14.7M (2024). | Check which channels bring the revenue growth before moving budget around. |

---

## 🧮 How the Main Numbers Are Calculated

| Number | How it works |
|---|---|
| Total MRR | Sum of monthly price for subscriptions that have not cancelled |
| ARR | Total MRR × 12 |
| Net MRR | New + upgrades − downgrades − cancellations |
| Customer churn % | Customers lost in the month ÷ customers at the start of the month |
| Renewal rate | 1 − churn % |
| CAC | Marketing spend ÷ new customers |
| LTV:CAC | Average customer value ÷ CAC |
| CAC payback | CAC ÷ average monthly price per customer |
| Net revenue retention | (Last month's MRR + upgrades − downgrades − cancellations) ÷ last month's MRR |

---

## ⚠️ Things to Know

- The date table is not linked to the other tables in the model. Some measures use date logic, so check the results after any change.
- "Active Customers" counts every customer in the subscriptions table, including cancelled ones, unless a filter removes them.
- The report has two similar measures for customer lifetime value. The cards use the one based on average monthly revenue × average months as a customer.
- The "Last Refresh" text on each page is typed in by hand.
- The data files are read from a folder on my computer. Change the file paths in Power Query before you refresh on another computer.

---

## 📁 Project Structure

```
SaaS-Analytics-Dashboard/
├── data/
│   ├── customers.csv
│   ├── subscriptions.csv
│   ├── monthly_revenue.csv
│   ├── marketing_spend.csv
│   └── subscription_events.csv
├── powerbi/
│   └── SaaS_Analytics_Dashboard.pbix
├── screenshots/
│   ├── Executive_Overview.png
│   ├── Revenue_Analytics.png
│   ├── Customer_Analytics.png
│   ├── Subscription_Health.png
│   └── Marketing_Analytics.png
└── README.md
```

---

## 🎯 Why I Built This

I built this to practice the numbers that subscription businesses watch: recurring revenue, churn, customer value and the cost of winning customers. I also wanted to show how to set them up so that someone without a data background can read them.

---

## 👤 Author

**Tushar Jadhav**
Data Analyst | Power BI · DAX · Power Query <br>
📧 tusharjadhav1582003@gmail.com <br>
💼 [LinkedIn](https://www.linkedin.com/in/your-linkedin-name/) <br>
💻 [github.com/jtushar15](https://github.com/jtushar15)

---

# 💼 Skills Shown

- Power BI
- DAX
- Power Query
- Data modeling
- KPI design
- Dashboard design
- Data visualization
- SaaS metrics

---

If this project helped you, you can give the repository a ⭐. Feedback is welcome.
