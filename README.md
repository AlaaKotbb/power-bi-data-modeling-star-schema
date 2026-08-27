![Power BI Data Modeling — Star Schema](<img width="1376" height="768" alt="Gemini_Generated_Image_n8vzljn8vzljn8vz" src="https://github.com/user-attachments/assets/c131e852-74ec-4a4d-aacd-e9c5e08bfc8b" />
)

# Power BI Data Modeling — Star Schema

> Turning a large set of messy, unrelated source tables into a clean, well-structured star schema in Power BI — with proper fact/dimension separation, clear relationships, and a dedicated measures table.

## 📌 Overview
This project was built while following **[Data with Baraa](https://www.youtube.com/@DataWithBaraa)**'s Data Modeling course on YouTube ([watch here](https://www.youtube.com/watch?v=0A2k62YEbfI)). The goal was to take a raw, disconnected set of business tables (orders, payments, invoices, campaigns, inventory, customers, etc.) and rebuild them into a proper **star schema** — the foundation every reliable Power BI report is built on.

## 🎯 Objectives
- Understand the real difference between **fact tables** and **dimension tables** (not just "connecting tables together").
- Apply **data normalization** to avoid repeated, redundant data.
- Design clean, direct **relationships** between fact and dimension tables (proper cardinality, no unnecessary complexity).
- Separate **DAX measures** into their own dedicated table for a cleaner, more maintainable model.
- Understand *why* a star schema makes queries faster and results more reliable.

## 🛠️ Tools & Techniques
- **Power BI** — data modeling, relationships, DAX measures.
- **Power Query** — data cleaning and transformation before loading into the model.
- **Dimensional Modeling** — Star Schema design (Kimball approach).

## 🔍 Approach

### 1. Starting point — a messy, unrelated set of tables
The raw source data was a large collection of independent tables with no clear structure — orders from different years, shipments, invoices, payments, campaign logs, inventory, security, and more — all loosely and inconsistently connected.

![Messy Source Tables](<img width="1545" height="961" alt="image" src="https://github.com/user-attachments/assets/625a0ef3-cf77-4d22-9aef-7ce7774d7add" />
)

### 2. Data cleaning in Power Query
Before any modeling, the raw tables were cleaned and shaped in Power Query — fixing data types, standardizing column names, and preparing each table to play its correct role (fact or dimension) in the final model.

![Power Query Cleaning](<img width="1320" height="952" alt="image" src="https://github.com/user-attachments/assets/471f4cee-6838-4469-b809-635d18745b0b" />
)

### 3. Rebuilding as a clean Star Schema
The cleaned tables were restructured into a proper star schema:
- **Fact tables** at the center — `fact_sales`, `fact_order_process`, `fact_inventory`, `fact_campaign`, `fact_sales_targets`, `fact_promotion_voverge` — holding the measurable, transactional data (quantities, revenue, clicks, spend, etc.).
- **Dimension tables** surrounding them — `dim_customer`, `dim_products`, `dim_date`, `dim_geo`, `dim_orders_flags`, `dim_campaign` — holding the descriptive attributes (who, what, where, when).
- A dedicated **`_measures`** table to hold all DAX measures separately from the data tables, following Power BI best practice.
- A **`security`** table to manage row-level access.

Each fact table connects to its relevant dimensions through simple, direct **one-to-many relationships** — the defining shape of a star schema.

![Final Star Schema Model](<img width="1844" height="932" alt="image" src="https://github.com/user-attachments/assets/e5c765fa-6ca3-42d1-bb64-681df3f16782" />
)

## 🧠 Key Concepts Learned

Before this project, "data modeling" meant one thing to me: connecting tables together. This project changed that.

**🔹 Fact Tables vs. Dimension Tables**
Not all tables are the same, and the difference is the key to avoiding redundancy:
- **Fact Table** — a central table that records repeated business events and numbers only (e.g. sales transactions, orders).
- **Dimension Tables** — descriptive tables that hold the attributes of an entity. Instead of repeating a customer's name, age, or address on every single sales row, that data lives once in a `dim_customer` table and is linked to the fact table through an ID.

**🔹 Data Normalization**
Organizing data to prevent redundancy and preserve data integrity. Instead of repeating customer details on every row, they're stored once in a dimension table and connected via **PK / FK** relationships to the fact table.

**🔹 Star Schema**
The fact table sits at the center, surrounded by dimension tables through direct **one-to-many** relationships. This structure makes the model easier to read and reduces complexity in DAX later on.

**🔹 Relationships & Cardinality**
Choosing the correct relationship type and **single-directional filter flow** prevents ambiguity and the performance issues caused by relationships like many-to-many.

**🔹 A Separate Measures Table**
Grouping all explicit DAX measures into one dedicated table keeps the model cleaner and much easier to maintain going forward.

**The goal throughout:**
**Simpler relationships 👉 Faster queries 👉 More accurate results**, aligned with real business requirements.

**The result:** a simpler model, faster performance, and more accurate results — proof that data modeling isn't just "connecting tables." It's the foundation every analysis or dashboard is built on afterward.

## 📁 Repository Structure
```
├── power_bi/              # .pbix file with the full data model
├── power_query/            # M queries used for data cleaning (if exported separately)
├── assets/                 # images used in this README
└── README.md
```

## 🚀 How to Run
Open `power_bi/data_modeling_project.pbix` in Power BI Desktop to explore the full data model, relationships, and measures.

## 🙏 Credit
Built while following **[Data with Baraa](https://www.youtube.com/@DataWithBaraa)**'s free Data Modeling course on YouTube.
🔗 [Watch the course](https://www.youtube.com/watch?v=0A2k62YEbfI)

## 👤 Author
**Alaa Alkotb** — Data Analyst
[LinkedIn](https://linkedin.com/in/alaa-kotb-5359a42a4) • [GitHub](https://github.com/AlaaKotbb)
