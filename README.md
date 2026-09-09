# E-Commerce Sales & Customer Analysis — Olist Dataset

A full data analytics project examining sales trends, product and customer behavior, and delivery performance for Olist, a Brazilian e-commerce platform — using Python, Pandas, and data visualization.

## Business Context

Olist connects small and medium sellers to major online marketplaces in Brazil. This analysis covers ~99,000 orders placed between September 2016 and September 2018, exploring what drives revenue, which customers and products matter most, and how delivery performance affects customer satisfaction — with the goal of surfacing insights a real business could act on.

## Dataset

- **Source:** [Olist Brazilian E-Commerce Public Dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) (Kaggle)
- **Size:** ~99,000 orders, ~112,000 order items, across 9 relational tables (orders, order items, customers, products, sellers, payments, reviews, category translations, geolocation)
- **Period:** September 2016 – September 2018

## Tools Used

Python · Pandas · Matplotlib · Seaborn · Jupyter Notebook

## Project Structure

```
olist-ecommerce-analysis/
├── README.md
├── data/
│   └── analysis_df.csv          (cleaned, merged dataset used by all analysis notebooks)
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_eda_sales.ipynb
│   ├── 03_eda_product_customer.ipynb
│   ├── 04_eda_delivery.ipynb
│   └── 05_key_insights.ipynb
├── images/
└── requirements.txt
```

## Key Questions Explored

**Sales**
- How have revenue and order volume changed over time?
- Which months show the strongest seasonal demand?
- What does a typical order look like (value, size)?
- Which states drive the most revenue?
- How do payment methods relate to order value?

**Product & Customer**
- Which product categories generate the most revenue?
- Which categories sell in high volume vs. command premium prices?
- Does product category relate to customer satisfaction?
- What share of customers are repeat buyers, and how much more do they spend?
- Where are customers concentrated geographically?
- Does review score relate to repeat purchase behavior?

**Delivery**
- What % of orders arrive on time, and how long does delivery typically take?
- Does delivery speed and reliability vary by region?
- Does delivery delay affect review scores?

## Key Insights

**Growth & Seasonality**
- Revenue grew steadily through 2017, peaked sharply in **November 2017 (R$1.01M)** — likely Black Friday — then plateaued at **R$850K–1M/month** through mid-2018.
- November is a clear seasonal peak (~40% above the average month); demand is otherwise fairly stable year-round.

**Revenue Concentration**
- São Paulo generates **2.8x** the revenue of the next-highest state, and the top 5 states account for **~74%** of total revenue — driven by order volume, not higher spend per order.

**Product Performance**
- The top 10 of 74 categories drive **~62%** of revenue. `watches_gifts` uniquely combines high sales volume with premium pricing.

**Customer Behavior**
- Only **3.05%** of customers are repeat buyers, but they spend **~2x more on average** (R$262 vs R$139) — the business currently relies heavily on new customer acquisition rather than retention.

**Delivery & Satisfaction (strongest finding)**
- Late delivery is the single largest driver of dissatisfaction found in this analysis: review scores drop from **4.29 (on-time)** to **2.27 (late)**.
- Delivery reliability varies by region — Alagoas (AL) stands out as both slow *and* unreliable (78.6% on-time), unlike other slow-but-reliable regions.
- Furniture categories rate poorly (e.g. `office_furniture`, 3.49 avg review), but this was **ruled out** as a delivery-speed issue — pointing instead to product-related causes.

## Business Recommendations

1. **Prioritize on-time delivery** — the strongest lever for customer satisfaction found in this analysis, with a larger effect than product category or payment method.
2. **Investigate logistics specifically in Alagoas (AL)** — a fixable regional issue, distinct from unavoidable distance-driven delays elsewhere.
3. **Review `office_furniture` fulfillment quality** (packaging, assembly, damage in transit) rather than shipping speed, since delivery isn't the cause of its low ratings.
4. **Invest in retention** — repeat customers are rare but far more valuable per customer; even a modest increase in repeat rate could meaningfully shift revenue mix.
5. **Prepare inventory and logistics capacity ahead of November** given the consistent, sharp seasonal spike.

## Limitations

- The ~2-year dataset window may understate true repeat-purchase behavior for infrequently-bought categories.
- Review comment text was not analyzed — only numeric scores — so specific causes behind low furniture ratings remain a hypothesis.
- A small number of source data inconsistencies (e.g. 8 "delivered" orders missing a delivery date) were identified and documented; negligible in scale.

## How to Run

```bash
git clone <your-repo-url>
cd olist-ecommerce-analysis
pip install -r requirements.txt
jupyter notebook
```

Run notebooks in order (`01` → `05`). `01_data_cleaning.ipynb` produces `data/analysis_df.csv`, which all subsequent notebooks load.

## What's Next

- A Power BI dashboard built on top of these findings
- A second portfolio project focused on SQL and Machine Learning, extending this analysis with a predictive angle (e.g. predicting delivery delay or review score)
