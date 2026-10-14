# Logistics Analytics

Delivery performance analytics for CresMart: SQL, Excel and Power BI.

**Owner:** Data Analyst, Precious Mojolaoluwa OJO  **Reviewer:** Edwin Sunday UMANA
**Dataset:** Olist Brazilian E-Commerce, https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce

Your job in this repo is to measure how well deliveries perform, find where and why they run late, and hand your findings to the data science team. Read the Phase 1 notice in `company-handbook` first.

---

## Repo structure

| Folder | What goes in it |
| --- | --- |
| `sql/` | Your SQL queries, one file per question |
| `excel/` | Cleaning workbooks and pivot analysis |
| `powerbi/` | Power BI files and dashboard exports |
| `reports/` | Written findings and weekly reports |

---

## Phase 1 tasks (Weeks 1 to 4)

### Task 0: Set up (Week 1, first 2 days)
1. Install Git, Power BI Desktop and PostgreSQL (SQLite is acceptable to start, but tell me so we keep queries compatible).
2. Create a Kaggle account and download the dataset. Unzip it into a folder called `data/raw/` on your computer.
3. Clone this repo and make sure `data/` is listed in `.gitignore`. **Never commit the raw CSV files.**

### Task 1: Learn the data (Week 1)
The dataset has nine tables. You document these four in the data dictionary: `orders`, `order_items`, `order_payments` and `order_reviews`. The data scientist documents the rest.

For each table, record: number of rows, each column and its meaning, the key that links it to other tables, the share of missing values, and anything odd you notice. Save it in `data-platform/data-dictionary/` through a pull request.

### Task 2: Clean and join (Weeks 1 to 2)
Using Excel (Power Query) or SQL:
1. Keep only orders with the status `delivered` for delivery analysis.
2. Convert all date columns to proper dates.
3. Join `orders` with `order_items`.
4. Create these new fields:
   - `delivery_days`: customer delivery date minus purchase date
   - `estimated_days`: estimated delivery date minus purchase date
   - `delay_days`: customer delivery date minus estimated delivery date
   - `is_late`: 1 if `delay_days` is above 0, otherwise 0
5. Write down every cleaning step and every decision (for example, how you handled missing dates) in `reports/cleaning_log.md`.

**Deliverable:** the cleaned data steps in `excel/` and the cleaning log. Commit a workbook only if it is small (under about 25 MB). Otherwise commit the steps and a 100-row sample.

### Task 3: KPI queries (Weeks 2 to 3)
Write SQL queries in `sql/` for each KPI in the handbook: on-time delivery rate, average delivery days, late rate by state, by seller and by product category, and freight share of order value. Name files clearly, for example `02_late_rate_by_state.sql`, and add a comment at the top explaining the question.

### Task 4: Pivot analysis and first findings (Week 3)
In Excel, build pivot tables of late deliveries by state, by product category and by month. Write a one-page note in `reports/` with your top five observations.

### Task 5: Power BI dashboard v1 (Weeks 3 to 4)
Build "Delivery Performance Overview" with three pages:
1. **Overview:** headline KPIs and trend over time
2. **Geography:** late rate by state
3. **Sellers and categories:** the best and worst performers

Export a PDF copy into `powerbi/` and commit the `.pbix` file only if it is reasonably small.

### Task 6: Phase 1 report (Week 4)
Write a two-page report in `reports/`: what the data shows, your KPIs, and **three hypotheses about what causes late deliveries** (for example, distance between seller and customer, product weight, or time of year). The data scientist will test these hypotheses in the model. This is your handoff.

---

## How to work
1. Pick up an issue from the project board and move it to In Progress.
2. Create a branch, for example `analytics/12-late-rate-by-state`.
3. Do the work and commit often with clear messages.
4. Open a pull request and request a review. Wait for approval before merging.
5. Post a short update in GitHub Discussions each working day.
6. Show your progress at the Friday demo.

## Definition of Done
The work meets the issue's description, is documented, has been reviewed and merged, and the issue is closed.

## If you get stuck
Post the problem in the daily update or message me. Say what you tried and what you expected. Asking within 24 hours is the rule.
