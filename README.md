# 🏭US_Candy-Distribution_SQL🍭
![ Cover](Assets/Profile.jpg)

## 📌 About the Project
This project explores a real-world dataset about the US candy industry. We uploaded the CSV files into VS Code, created a PostgreSQL database, and established a connection between them. Also we build a clean database foundation and prepare the data to answer key business questions about candy sales, factory efficiency, and regional trends.

---
## 🎯 Objectives
In this project, our main objectives are:

- ✅ Understand and structure the US Candy sales data.  
- ✅ Solve real business problems by identifying profitable products, comparing sales to targets, and providing advanced data analysis.
- ✅ Explore seasonality and regional trends in candy sales.  
- ✅ Compare product performance against division targets.  
- ✅ Build a maintainable, clean database schema with a clear ER diagram.
- ✅ Uncover data trends and hidden insights using advanced SQL techniques.
---

## 🗂️ Data Source & Context
**_Source👉_**: [**Maven Analytics “US Candy Distributor”**](https://www.mavenanalytics.io/data-playground?order=date_added%2Cdesc&search=candy%20distributor)



**Why This Candy Dataset?**
 
- **Balanced Size:** Ideal for both complex SQL queries and rapid iteration.
- **Geospatial & Time Series Data:** Includes latitude/longitude coordinates, order dates, and shipping information, ideal for joins, distance calculations, and time-based analyses.
- **Business Relevance:** SKU-level sales data, factory origins, customer locations, and division targets mirror real-world retail/distribution analytics scenarios.
- **Well-Organised CSV Files:** Multiple files represent distinct tables in a relational model.


_**Here is a short description for each CSV file & its columns**_:

1.**Sales.csv**  
   - **Columns**: `row_id`, `order_id`, `order_date`, `ship_date`, `customer_id`,  
     `division`, `product_id`, `units`, `gross_profit`, `cost`, etc.  
   - **Describes**: Individual sales transactions linking customers, products, and financials.

2.  **Factories.csv**  
   - **Columns**: `factory_name`, `latitude`, `longitude`  
   - **Describes**: Candy factory names and their geographic locations.

3. **Targets.csv**  
   - **Columns**: `division`, `Target_Count`  
   - **Describes**: Sales targets for each division (Chocolate, Sugar, Other).

4.  **Products.csv**  
   - **Columns**: `product_id`, `product_name`, `division`, `factory_name`, `unit_cost`, `unit_price`  
   - **Describes**:  type of candy and  its division, factory origin, and cost/price.

5. **us_zips.csv**  
   - **Columns**: `zip`, `lat`, `lng`, `city`, `state_id`, `state_name`,  
     `zcta`, `population`, `density`, `county_fips`, `county_name`, `timezone`  
   - **Describes**: ZIP-level geographic and demographic data for mapping customers.

6. **Dictionary.csv**
   
    _Lists descriptions for the tables & their columns._

---

> **_Now let's move into the deep work🕵️‍♂️_**

## 📑 Phase 1: Business & Data Understanding
- ✅ **Created** the PostgreSQL database and defined tables matching our CSV structures.  
- ✅ **Uploaded** CSV data into those tables using VS Code’s SQL editor.
- ✅ Verified row counts for each table matched CSV sources.  
- 🧹 Dropped unused columns from `us_zips` to keep only zip, zcta, state, county, population, density, timezone.   
- ✅ **Clarified** the business questions we’ll answer by analysing our dataset:

 **General Analysis**

1. Which products or categories generate the highest profits?  
2. What are the top-selling products by quantity?  
3. Which shipping routes are the most expensive?

**Geographic & Optimization**

1. Which customer–factory pairs are least efficient (long distance + low margin)?  
2. Are there specific states/regions with higher return on sales?

**Time-Based Trends**

1. How do monthly/quarterly sales trends look?  
2. Are there specific weekdays or weekends with higher volume or profit?

**Advanced Insights**

1. Which customers rank in the top 5 spenders each month?  
2. How has profit changed over time for each product category?


### 🔗 ERD Diagram
    FACTORIES ||--o{ PRODUCTS       : factory_name
    TARGETS   ||--o{ PRODUCTS       : division
    TARGETS   ||--o{ SALES          : division
    PRODUCTS  ||--o{ SALES          : product_id
    US_ZIPS   ||--o{ SALES          : postal_code


### ERD Explained

- **FACTORIES → PRODUCTS** (`products.factory_name` → `factories.factory_name`)  
  One factory can produce many products.

- **TARGETS → PRODUCTS** (`products.division` → `targets.division`)  
  Each product belongs to a division that has a sales target.

- **TARGETS → SALES** (`sales.division` → `targets.division`)  
  Each sale is classified under a division with an associated target.

- **PRODUCTS → SALES** (`sales.product_id` → `products.product_id`)  
  A product can appear in many sales records.

- **US_ZIPS → SALES** (`sales.postal_code` → `us_zips.zip`)  
  Each sale’s customer ZIP links to geographic data.


---

## 🛠️ Tools Used

- **PostgreSQL** – Relational database for storing and querying data.  
- **VS Code** – IDE for writing SQL, managing CSVs, and connecting to the database.  
- **Git & GitHub** – Version control and documentation of the entire process.  
- **Sider AI** –  Explored multiple AI models for the data analysis journey. 
- **DeepSeek** – Automated code review & best-practice suggestions.  
- **Perplexity** – Contextual search for technical guidance & fact-checking.
- **GPT**–  Drafted and refined narrative content
- **Grammarly** – Writing assistant to polish documentation.  

---

✅ **Phase 1 is complete!🎉**  


Next up: **Phase 2 – Data Cleaning & Transformation**, where we’ll refine, normalise, and enrich our tables for analysis.  

## 🧠 SQL_Skills_Used

- **Joins** across multiple tables  
- **CASE** statements for conditional logic  
- **Common Table Expressions (CTEs)** for modular queries  
- **Window Functions** for running totals and rankings  
- **Data Cleaning:** null handling, formatting  
- **Pivoting** via CASE for cross-tabs  
- **Date/Time Functions** for extracting year/quarter/week  
- **Views** to encapsulate reusable queries  
- **Query Optimization** with indexes and EXPLAIN  

---

