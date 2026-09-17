
# 🌍 Global Service Business Analytics

## 📌 Project Overview

**Global Service Business Analytics** is a data analytics project designed to analyze service operations, branch performance, revenue, working hours, clients, and service activities across different regions and countries.

The project uses **SQL Server** to transform and analyze the underlying data through reusable SQL Views, preparing a clean analytical layer that can be connected to **Power BI** for interactive business dashboards and decision-making.

---

## 🎯 Business Objective

The main objective is to transform raw service data into meaningful business insights that help answer questions such as:

* Which branches generate the highest revenue?
* Which countries and regions contribute the most to overall performance?
* What is the total number of services delivered?
* How many working hours are being generated?
* What is the average hourly rate?
* What is the revenue generated per service hour?
* Which service types and departments generate the most revenue?
* Which clients contribute the highest revenue?
* How does service performance vary across branches and regions?

---

## 🗂️ Dataset

The project is based on two main tables:

### `services_data`

Contains detailed information about delivered services, including:

* `service_id`
* `service_type_id`
* `client_name`
* `hours`
* `service_date`
* `service_time`
* `hourly_rate`
* `total_revenue`
* `branch_id`
* `department`
* `service_description`

### `Branch_data`

Contains branch and geographic information:

* `Branch_ID`
* `Country`
* `Region`

The tables are connected through:

```text
services_data.branch_id
        ↓
Branch_data.Branch_ID
```

---

# 🛠️ Tools & Technologies

* **SQL Server**
* **T-SQL**
* **Power BI**
* **Data Modeling**
* **Data Cleaning & Transformation**
* **KPI Analysis**
* **Business Intelligence**
* **Data Visualization**

---

# 🧠 SQL Analysis

SQL was used to create reusable analytical Views instead of performing the same calculations repeatedly.

## 1. Service Details View

### `vw_Service_Details`

Combines service-level information with branch and geographic information.

The view provides:

* Service details
* Client information
* Hours
* Revenue
* Hourly rate
* Department
* Branch
* Country
* Region

This creates a unified dataset suitable for detailed analysis and Power BI reporting.

---

## 2. Branch Performance View

### `vw_Branch_Performance`

Measures the operational and financial performance of each branch.

### Key Metrics

* Total Services
* Total Hours
* Total Revenue
* Average Hourly Rate
* Revenue per Hour

### Revenue per Hour

```sql
SUM(s.total_revenue) / NULLIF(SUM(s.hours), 0)
```

This metric helps evaluate revenue generation relative to the number of service hours delivered.

---

## 3. Service Performance View

### `vw_Service_Performance`

Analyzes performance by:

* Department
* Service Description

### Key Metrics

* Total Services
* Total Hours
* Total Revenue
* Average Hourly Rate

This view can be used to identify high-revenue services and compare service activity across departments.

---

## 4. Client Performance View

### `vw_Client_Performance`

Analyzes client contribution across regions and countries.

### Key Metrics

* Total Services
* Total Hours
* Total Revenue

A Top 10 analysis is also performed to identify the clients generating the highest revenue.

```sql
SELECT TOP 10 *
FROM vw_Client_Performance
ORDER BY total_revenue DESC;
```

---

# 📊 Power BI Dashboard

The SQL Views provide the analytical foundation for the Power BI dashboard.

### Main Dashboard Analysis

The dashboard focuses on:

* 💰 Revenue Performance
* 📦 Service Volume
* ⏱️ Total Service Hours
* 💵 Revenue per Hour
* 🌍 Regional Performance
* 🏢 Branch Performance
* 👥 Client Analysis
* 🛠️ Service & Department Analysis

### Suggested Dashboard Structure

**Executive Overview**

* Total Revenue
* Total Services
* Total Hours
* Revenue per Hour
* Revenue by Region
* Revenue by Branch
* Revenue Trend

**Branch & Regional Analysis**

* Country → Region → Branch performance
* Revenue comparison
* Service volume
* Hours
* Revenue per Hour

**Service Analysis**

* Revenue by service
* Services by department
* Hours by service
* Average hourly rate

**Client Analysis**

* Top clients by revenue
* Client service volume
* Client hours
* Revenue contribution by region

---

# 🔍 Key Analytical Questions

This project is designed around practical business questions rather than simply displaying data.

### What Happened?

* How much revenue was generated?
* How many services were delivered?
* How many hours were worked?
* Which branches, services, and clients generated the most revenue?

### Why?

The analysis can be further explored by breaking down performance by:

```text
Region
   ↓
Country
   ↓
Branch
   ↓
Department
   ↓
Service
   ↓
Client
```

This allows users to move from overall performance into the underlying drivers.

---

# 📁 Project Structure

```text
Global_service/
│
├── SQL/
│   ├── vw_Service_Details.sql
│   ├── vw_Branch_Performance.sql
│   ├── vw_Service_Performance.sql
│   └── vw_Client_Performance.sql
│
├── Power BI/
│   └── Global Service Business Analytics.pbix
│
├── Images/
│   └── Dashboard screenshots
│
└── README.md
```

---

# 🚀 Analytical Workflow

```text
Raw Data
   ↓
SQL Server
   ↓
Data Validation & Transformation
   ↓
SQL Views
   ↓
Analytical Metrics
   ↓
Power BI
   ↓
Interactive Dashboard
   ↓
Business Insights
```

---

# 💡 Business Value

The project demonstrates how raw operational data can be transformed into a structured analytical solution.

By combining **SQL analysis** with **Power BI visualization**, decision-makers can examine revenue, service activity, branch performance, client contribution, and operational efficiency from multiple perspectives.

The approach also makes the analysis more scalable by separating data preparation and business logic in SQL from visualization and interactive exploration in Power BI.

---

# 👩‍💻 Author

**Aldrda Ali**
Data Analyst

### Connect with me

* **GitHub:** https://github.com/aldrda
* **LinkedIn:** https://www.linkedin.com/in/aldrda-ali-0217b023b
* **Portfolio:** https://data-analyst.aldrda.workers.dev/

---

## ⭐ Project Focus

**SQL Server • T-SQL • Power BI • Data Analysis • Business Intelligence • KPI Development • Data Visualization**
