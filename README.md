# **Supermarket Chips Sales Project – Full Workflow Roadmap**

## **PHASE 1 — DATA INGESTION (Reading Files)**

**Goal:** Bring data from external files into Python for initial inspection.

### Steps Completed

1. Read CSV file using pandas:

   ```python
   purchase_df = pd.read_csv("purchase_data.csv")
   ```
2. Read Excel file:

   ```python
   transaction_df = pd.read_excel("transaction.xlsx")
   ```
3. Performed `.head()`, `.shape()`, and `.info()` to understand the structure of both datasets.
4. Cleaned and converted date columns using `pd.to_datetime()`.

### Concepts Covered

* File formats (CSV, Excel)
* DataFrames
* Data types (string, integer, float, datetime)

---

## **PHASE 2 — DATA STORAGE (Database & SQL Layer)**

**Goal:** Store structured data in a relational database for secure and scalable use.

### Steps Completed

1. Loaded environment variables containing `DATABASE_URL`.
2. Created a SQLAlchemy engine:

   ```python
   engine = create_engine(db_url)
   ```
3. Loaded DataFrames into PostgreSQL tables using:

   ```python
   df.to_sql("table_name", schema="customer_data", ...)
   ```
4. Verified that all tables are correctly stored in the database.

### Concepts Covered

* Purpose of databases
* Database schemas
* Tables and relationships
* Primary and foreign keys
* Writing pandas DataFrames to SQL

---

# **PHASE 3 — DATA PREPARATION (Cleaning & Transformation)**

**Goal:** Prepare clean, accurate, analysis-ready data for downstream use.

### Next Steps

1. Check for missing values:

   ```python
   df.isna().sum()
   ```
2. Identify and remove duplicates:

   ```python
   df.drop_duplicates()
   ```
3. Correct data types (e.g., convert DATE to datetime, ensure TOT_SALES is numeric).
4. Engineer new useful fields such as:

   * Month of purchase
   * Year
   * Brand extracted from `PROD_NAME`
   * Pack size extracted from `PROD_NAME`
5. Remove invalid or corrupted transaction records, such as negative totals or zero quantity.

### Concepts Covered

* ETL workflow (Extract → Transform → Load)
* Data wrangling
* Feature engineering

---

# **PHASE 4 — DATA ANALYSIS (Exploratory Data Analysis in Python)**

**Goal:** Answer business questions using Python, pandas, and grouped calculations.

### Analytical Steps

1. Join tables using the loyalty card number:

   ```python
   merged_df = transactions.merge(customer_behaviour, on="LYLTY_CARD_NBR")
   ```

2. Explore purchasing behavior by:

   * Life stage
   * Premium category
   * Store
   * Product brand
   * Time (monthly sales trends)

3. Calculate aggregations:

   * Total sales
   * Total quantity sold
   * Average spend per customer
   * Most popular chip brands
   * Sales by customer class

4. Apply groupby operations:

   ```python
   merged_df.groupby("LIFESTAGE")["TOT_SALES"].sum()
   ```

5. Create visualizations using Matplotlib and Seaborn:

   * Bar charts for top brands
   * Line charts for monthly sales
   * Distribution plots
   * Heatmaps for store performance

### Concepts Covered

* Table joins
* GroupBy operations
* Statistical summaries
* Visualization techniques
* Deriving insights from data

---

# **PHASE 5 — REPORTING (Narratives and Visuals)**

**Goal:** Convert analytical results into business-ready written reports.

### Reporting Steps

1. Summarize key findings such as:

   * Customer groups with the highest chip purchases
   * Top-performing brands
   * High-performing and low-performing stores
   * Time periods with highest sales activity
2. Export cleaned tables to Excel or CSV for presentation.
3. Create PDF or Word reports containing visualizations and insights.

### Concepts Covered

* Business communication
* Insight interpretation
* Structuring a data report

---

# **PHASE 6 — DASHBOARDING (Interactive Insights Delivery)**

**Goal:** Build an interactive dashboard to present insights in a dynamic and user-friendly manner.

### Recommended Tools

* Power BI
* Tableau
* Streamlit
* Excel dashboards

### Dashboard Structure

1. **Sales Overview**

   * Total sales
   * Total quantity sold
   * Average weekly or monthly figures

2. **Customer Segmentation**

   * Life stage categories
   * Premium/Mainstream/Budget groups

3. **Product Analysis**

   * Top brands
   * Top flavors
   * Most profitable chip products

4. **Store Analysis**

   * Best-performing stores
   * Underperforming stores
   * Store-by-store breakdown

5. **Time Trends**

   * Monthly sales patterns
   * Seasonal demand

### Concepts Covered

* Data modeling
* DAX (for Power BI users)
* Visual selection and placement
* KPI cards, slicers, filters

---

# **PHASE 7 — PRESENTATION & INSIGHTS DELIVERY**

**Goal:** Deliver a polished, end-to-end analytics project.

### Final Deliverables

1. Clean and structured SQL database
2. Full analysis notebook in Jupyter
3. Interactive dashboard (Power BI or Streamlit)
4. A concise insights summary (1–2 pages)
5. Recommendations such as:

   * Inventory strategy for premium chips
   * Targeting specific customer groups
   * Store-level performance improvements
