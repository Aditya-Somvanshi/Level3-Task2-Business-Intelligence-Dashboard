# Level 3 – Task 2: Business Intelligence Dashboard
**RaushByte Technologies – Data Analytics Internship**

---

## 📌 Objective
Build a complete business analytics dashboard from both datasets, covering customer insights, sales trends, profit analysis, KPI metrics, and interactive filters and charts.

---

## ✅ Requirements Completed

| # | Requirement | Status |
|---|-------------|--------|
| 1 | Customer insights | ✅ Done (Customers tab) |
| 2 | Sales trends | ✅ Done (monthly trend with Sales / Profit / Both / Margin views) |
| 3 | Profit analysis | ✅ Done (product, region, payment method, margin bands, cost split) |
| 4 | KPI metrics | ✅ Done (6 KPIs per tab, 18 in total) |
| 5 | Interactive filters and charts | ✅ Done (live chip filters, click-to-filter bars, tabs) |

---

## 📊 Datasets

| Dataset | Rows | Used for |
|---------|------|----------|
| `data_analytics_sales_dataset` | 8,000 orders (1 Jan 2024 – 15 May 2025) | Overview, Sales & Profit tabs |
| `customer_analytics_dataset` | 8,000 customers | Customers tab, Overview |

Both datasets have 0 missing values and 0 duplicate rows.

### ⚠️ The two datasets cannot be joined reliably
They share no customer ID (the sales file uses Order_ID, the customer file uses Customer_ID). Matching on name finds only 612 names in common (756 orders), and names repeat inside each file (e.g. "Michael Davis" appears 6 times in the sales data, and 404 names are duplicated in the customer file), so those matches are coincidences, not the same people. The dashboard therefore keeps the two datasets side by side, and **filters apply within each dataset** rather than across them.

---

## 📈 Key Findings

### 1. Sales and profit
| Metric | Value |
|--------|-------|
| Total sales | ₹201.8 Cr |
| Total profit | ₹60.1 Cr (29.8% margin) |
| Total expense | ₹141.6 Cr (70.2% of sales) |
| Avg order value | ₹2,52,221 |
| Jan–Apr 2025 vs Jan–Apr 2024 sales | +0.2% |

- **Sales are stable**: about ₹12 Cr a month with no significant trend. May 2025 looks like a drop only because the data stops on 15 May.
- **Margins are uniform.** Product margins range only from 29.3% (Tablet) to 30.2% (Mobile), so **profit follows sales volume**, not pricing power.
- **Profit by product:** Headphones ₹12.7 Cr, Smartwatch ₹12.3 Cr, Tablet ₹12.3 Cr, Laptop ₹11.7 Cr, Mobile ₹11.1 Cr.
- **Regions are close:** sales range from ₹49.8 Cr (North) to ₹51.5 Cr (West), a 3.4% spread.
- **Best and worst region-product cells:** North Headphones ₹3.32 Cr profit, East Mobile ₹2.49 Cr.
- **Payment methods:** Cash leads (₹52.3 Cr sales), UPI is lowest (₹49.2 Cr); margins are 29.4%–30.2%.
- **Customer rating has no link to profit:** average profit per order is ₹72K–₹78K at every rating from 1 to 5 stars.
- **Margin bands:** orders are split almost evenly across margin bands (about 2,000 each), but the 40%+ band brings 37% of profit versus 13% for the under-20% band.

### 2. Customers
| Metric | Value |
|--------|-------|
| Customers | 8,000 |
| Total customer spending | ₹200.9 Cr |
| Avg spending | ₹2,51,068 |
| Avg satisfaction | 5.51 / 10 |
| Premium customers | 2,711 (33.9%) |

**Six value segments** (built from spending, satisfaction and membership years):

| Segment | Customers | % of Spending |
|---------|-----------|---------------|
| Champions | 784 | 15% |
| Rising Value | 1,608 | 30% |
| ⚠️ At-Risk High Spenders | 1,611 | 30% |
| Loyal Mid-Spenders | 1,265 | 11% |
| Casual Mid-Spenders | 1,203 | 10% |
| Low Value | 1,529 | 4% |

- **At-Risk High Spenders (spend ₹2.5L+, satisfaction 4 or lower) hold 30% of customer spending.** They are the first group to contact.
- **Customer type does not drive spending**: New, Returning and Premium differ by only 2.5% (ANOVA p = 0.26).
- **Membership years and age have almost no effect on spending** (correlation +0.004 for membership years).

### 3. Business takeaways
1. Plan on a steady ~₹12 Cr a month; there is no growth trend to budget for.
2. Because margins are nearly identical, grow profit by **selling more volume** or **cutting expense**, not by shifting product mix.
3. Protect the 30% of customer spending that sits with unhappy high spenders.

### ⚠️ Data quality notes
- 1,570 customers labelled **New** have 5 or more membership years.
- **Feedback** labels do not follow **Satisfaction_Score** (590 customers have "Excellent" feedback with a score of 3 or lower).
- Profit equals Sales minus Expense for every order, so the sales dataset is internally consistent.

---

## 🖥️ Dashboard Features

**Three tabs:**
- **Overview:** 12 KPI cards (6 sales + 6 customer), key insights, monthly sales and profit trend, profit by product, customer segments
- **Sales & Profit:** filters for Region, Product, Payment method, Year and Customer rating; trend with a Sales / Profit / Both / Margin % toggle; profit by product (click a bar to filter); sales and profit by region; region × product profit heatmap; payment method table; rating vs profit; margin bands; expense vs profit per ₹100 of sales
- **Customers:** filters for Customer type, Segment, Age group, Membership tenure, Spending tier and Feedback; segment bars (click to filter), spending share donut, New vs Returning vs Premium table, age group, membership years, satisfaction distribution, feedback, spending tiers

Every tab has a **"What this view says"** summary that rewrites itself for the current filters. Works offline, no install, light and dark mode.

---

## 📁 Project Structure

```
Level3-Task2-Business-Intelligence-Dashboard/
│
├── dashboard.html      ← Interactive BI dashboard (both datasets embedded)
├── README.md           ← This file
└── requirements.txt    ← Python dependencies (optional)
```

---

## 🚀 How to Open

1. Download `dashboard.html`
2. Double-click it → opens in your browser (Chrome, Edge, Firefox)
3. Switch tabs at the top and use the filters on the left

---

## 🛠️ Tools Used

- **Python 3** (pandas, SciPy): data checks, dataset-join test, significance tests
- **HTML + CSS + JavaScript:** interactive dashboard with hand-built SVG charts (no external libraries)

---

*Level 3 – Task 2 | RaushByte Technologies Data Analytics Internship*
