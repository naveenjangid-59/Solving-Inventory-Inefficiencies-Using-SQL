# 📦 Solving Inventory Inefficiencies through Advanced SQL Queries

## 📋 Project Overview
This project demonstrates how **Advanced SQL Queries** can be used to **analyze, monitor, and optimize inventory performance** by identifying inefficiencies such as:
- Overstock
- Stockouts
- High lead times
- Seasonal sales variations
- Lost revenue due to demand-supply gaps

The dataset represents **two years of daily transactional data** across multiple stores, regions, and products, enriched with details like:
- Pricing
- Discounts
- Weather
- Seasonality
- Competitor pricing
- Promotional periods

The ultimate goal is to **normalize** the data into relational tables, perform **deep analysis**, and calculate **key inventory management metrics** to support data-driven decision-making.

---

## 🗂 Dataset Details
**Database Name:** `inventory_inefficiencies_using_sql`

**Source Table:** `inventory_combined`

**Columns in `inventory_combined`:**
- `order_data` – Transaction date
- `store_id`, `region` – Store identifiers
- `product_id`, `categories` – Product details
- `inventory_level`, `units_sold`, `units_order` – Inventory movement
- `demand_forecast` – Predicted demand
- `price`, `discount` – Pricing details
- `weather_condition`, `seasonality` – Contextual conditions
- `holiday_promotion` – Holiday/promo flag
- `competitor_pricing` – Competitor price point

---

## 🏗 Data Normalization
The dataset is **normalized** into multiple relational tables to improve data quality, reduce redundancy, and enable efficient querying.

### **1. `stores` Table**
Stores and regions are assigned unique `store_number` identifiers.

### **2. `products` Table**
Holds distinct products and their categories.

### **3. `day_details` Table**
Stores date-specific attributes like seasonality.

### **4. `inventory` Table**
Fact table linking `stores`, `products`, and `day_details` with actual movement (inventory levels, sales, orders, forecast).

### **5. `pricing` Table**
Stores price, discount, competitor pricing, and promotion flags for each order.

---

## 📊 Key Analytical Queries

### **1. Descriptive Analysis**
- **Days covered:** 730 days
- **Stores:** 20 unique stores
- **Products:** 30 unique products
- **Revenue by store/year:** Identifies top revenue generators
- **Seasonal revenue trends:** Winter highest, followed by Summer, Autumn, Spring
- **Holiday/Promotion effect:** Higher average daily revenue during promotions
- **Weather impact:** Snowy weather generates the most revenue

---

### **2. Inventory Inefficiency Detection**
- **Stockout Rate:** `(units_sold > inventory_level)`
- **Overstock Rate:** `(inventory_level > demand_forecast)`
- **Lost Revenue:** Calculates missed revenue when stock < demand forecast
- **Age of Inventory:** Average inventory days before selling

---

### **3. Performance Metrics**
- **Lead Time Calculation:** Average days between ordering and receiving stock
- **Safety Stock:** Based on demand variability and average lead time
- **Reorder Point:** `(Average Daily Usage × Lead Time) + Safety Stock`
- **Low Stock Detection:** Flags SKUs needing replenishment
- **Inventory Turnover Ratio:** `Total Units Sold / Average Inventory`
- **Days of Inventory (DOI):** `365 / Inventory Turnover Ratio`

---

### **4. Sales Trends**
- **Weekly & Monthly Sales:** Time-series aggregation of sales volume
- **Category-wise Discount Effectiveness:** Evaluates discount impact on sales

---

### **5. Competitor Analysis**
- **Price Position vs. Sales:** Compares own price to competitor and measures sales impact

---

## 📈 Advanced Inventory Projections
- **Last Day Stock Level Calculation:** Predicts inventory on the next day considering:
  - Current stock
  - Expected deliveries
  - Previous day’s sales
- **Final Stock Status:** Determines if reorder is required before the next cycle

---

## 🛠 Technical Stack
- **Database:** MySQL 8.0+
- **SQL Techniques Used:**
  - `CTE` (Common Table Expressions)
  - `Window Functions` (`RANK`, `LAG`)
  - `CASE` statements
  - `JOIN` optimizations
  - `Indexing` for performance
  - Aggregate functions (`SUM`, `AVG`, `STDDEV`)
  - Subqueries

---

## 🚀 How to Run
1. Create the database:
   ```sql
   CREATE DATABASE inventory_inefficiencies_using_sql;
   USE inventory_inefficiencies_using_sql;
