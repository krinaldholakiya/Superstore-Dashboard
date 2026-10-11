<div align="center">

# -- ! Superstore Sales & Profit Dashboard ! --
### *Interactive Power BI Dashboard for Sales, Profit & Regional Performance Analysis*

[![Power BI](https://img.shields.io/badge/Power%20BI-Desktop-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![DAX](https://img.shields.io/badge/DAX-Measures%20%26%20Aggregations-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)](https://learn.microsoft.com/en-us/dax/)
[![Power Query](https://img.shields.io/badge/Power%20Query-Data%20Cleaning%20(M)-217346?style=for-the-badge&logo=microsoftexcel&logoColor=white)](https://learn.microsoft.com/en-us/power-query/)
[![Dataset](https://img.shields.io/badge/Dataset-Sample%20Superstore-9C27B0?style=for-the-badge&logo=databricks&logoColor=white)](https://www.kaggle.com/)                  
VIDEO LINK     
https://drive.google.com/file/d/1LqgBDHLf3PaPpDXAaER-0PdB0Szcqe_m/view?usp=sharing

<br/>

> *"Data tells you what happened — a dashboard tells you what to do next."*

</div>

---

## 📋 Table of Contents

- [📌 Overview](#-overview)
- [🎯 Problem Statement](#-problem-statement)
- [✨ Key Features](#-key-features)
- [🏗️ Project Structure](#️-project-structure)
- [🔄 Project Workflow](#-project-workflow)
- [🧹 Part A — Data Preparation (Power Query)](#-part-a--data-preparation-power-query)
- [📊 Part B — Dashboard & Visuals](#-part-b--dashboard--visuals)
- [🛠️ Tech Stack](#️-tech-stack)
- [📈 Results & Insights](#-results--insights)
- [🏆 Advantages](#-advantages)
- [🚀 How to Open the Project](#-how-to-open-the-project)
- [📄 License](#-license)
- [👤 Author](#-author)
- [🙏 Acknowledgements](#-acknowledgements)

---

## 📌 Overview

The **Superstore Sales & Profit Dashboard** is a beginner-friendly, interactive **Power BI** report built on the popular *Sample – Superstore* retail dataset. It demonstrates core business-intelligence concepts such as **data cleaning with Power Query**, **DAX measures**, **KPI cards**, **clustered bar charts**, and **slicer-driven filtering**.

This project is designed to:
- Practice importing, cleaning and shaping raw CSV data in Power Query
- Build KPI cards and charts that answer real business questions
- Use slicers and page-level filters for interactive exploration
- Turn raw numbers into short, readable business insights

---

## 🎯 Problem Statement

> **Objective:** Build an interactive dashboard to analyze sales, profit, quantity and discounts of a retail store across regions and product categories.

You are building a reporting tool for a retail business owner. The dashboard must answer questions such as *Which category sells the most? Which region earns the most profit? Where should the business focus next?*

| 📂 Component | 📄 Type | 🔍 Description |
|--------------|---------|----------------|
| Total Sales | KPI Card | Sum of all sales for the current filter |
| Total Profit | KPI Card | Sum of profit for the current filter |
| Total Quantity | KPI Card | Total units sold |
| Average Discount | KPI Card | Average discount given on orders |
| Sales by Category | Bar Chart | Compares Technology, Furniture and Office Supplies |
| Profit by Region | Bar Chart | Compares West, East, South and Central |
| Region & Category | Slicers | Interactive filters for the whole page |
| Order Details | Table | Row-level drill-down of orders on a second page |

The goal is to demonstrate **fundamental Power BI skills** through a clean, insight-driven dashboard.

---

## ✨ Key Features

| Feature | Description |
|--------|-------------|
| 🧮 **4 KPI Cards** | Total Sales, Total Profit, Total Quantity and Average Discount at a glance |
| 📊 **2 Clustered Bar Charts** | *Sales by Category* and *Profit by Region* with colour-coded categories |
| 🎛️ **Slicers** | Region and Category slicers filter every visual on the page |
| 🚚 **Page-Level Filter** | Dashboard focuses on *Standard Class* and *Second Class* shipping |
| 💡 **Insight Callouts** | Three text boxes highlight the key business takeaways |
| 📄 **Order Details Page** | Detailed table with customer, product, region, sales, profit and more |
| 🧹 **Clean Data Model** | Columns renamed, unused fields removed, Order ID split into useful parts |
| 🖥️ **Custom Canvas** | 1920 × 1080 layout with a custom background and the Fluent 2 theme |

---

## 🏗️ Project Structure

```
📦 superstore-powerbi-dashboard/
│
├── 📄 Project_1.pbix        ← Power BI report (data model + dashboard)
│
└── 📄 README.md             ← Project documentation
```

**Inside the report:**

```
📑 Page 1 — DASHBOARD       ← KPIs, charts, slicers, insights
📑 Page 2 — Order Details   ← Row-level table of orders
🗃️ Table  — Sample - Superstore (8,211 rows × 20 columns)
```

---

## 🔄 Project Workflow

```
Raw CSV (Sample - Superstore.csv)
              │
              ▼
┌─────────────────────────────┐
│   Import into Power BI      │  ← Csv.Document + Promote Headers
└────────────┬────────────────┘
             │
             ▼
┌─────────────────────────────┐
│   Clean in Power Query      │  ← Types, filters, split, rename, remove
└────────────┬────────────────┘
             │
             ▼
┌─────────────────────────────┐
│   DAX Measures              │  ← Total Sales, Sum / Average aggregations
└────────────┬────────────────┘
             │
     ┌───────┴────────┐
     ▼                ▼
┌─────────────┐   ┌──────────────────┐
│  DASHBOARD  │   │  Order Details   │
│  KPIs+Charts│   │  Detail Table    │
└──────┬──────┘   └────────┬─────────┘
       │                   │
       ▼                   ▼
┌─────────────────────────────┐
│  Slicers & Filters Applied  │
└────────────┬────────────────┘
             │
             ▼
   Insights & Business Decisions ✅
```

---

## 🧹 Part A — Data Preparation (Power Query)

### 📝 1. Source Data

The data comes from the **Sample – Superstore** CSV file (21 original columns) loaded with `Csv.Document` and headers promoted to the first row.

---

### 🗺️ 2. Transformation Steps

| Step | Transformation | Purpose |
|------|----------------|---------|
| 1️⃣ | **Change data types** | Dates → `date`, Sales/Profit → number, Quantity → whole number |
| 2️⃣ | **Rename column** | `Sub-Category` → `Sub Category` |
| 3️⃣ | **Filter rows** | Remove the `Home Office` segment (`Segment <> "Home Office"`) |
| 4️⃣ | **Split column** | Split `Order ID` by `-` into three parts |
| 5️⃣ | **Rename split columns** | `Order Region Code`, `ORDER YEAR`, `Order Number` |
| 6️⃣ | **Remove columns** | Drop `Row ID`, `Country` and `Postal Code` |

---

### 🔀 3. Order ID Split

> One messy ID becomes three useful columns.

**Example:**
```
Order ID:  CA-2015-135545
              │     │      │
              ▼     ▼      ▼
   Order Region Code   ORDER YEAR   Order Number
          CA              2015         135545
```

---

### 🧮 4. DAX Measure

```dax
Total Sales = SUM('Sample - Superstore'[Sales])
```

The remaining cards use Power BI's built-in aggregations: **Sum** of Profit, **Sum** of Quantity and **Average** of Discount.

---

## 📊 Part B — Dashboard & Visuals

### 🖼️ 5. Page 1 — DASHBOARD

| Visual | Type | Fields Used |
|--------|------|-------------|
| 💰 **Total Sales** | Card | `Sales` (Sum) |
| 📈 **Total Profit** | Card | `Profit` (Sum) |
| 📦 **Total Quantity** | Card | `Quantity` (Sum) |
| 🏷️ **Average Discount** | Card | `Discount` (Average) |
| 📊 **Sales by Category** | Clustered Bar Chart | `Category`, `Region`, `Sales` |
| 📊 **Profit by Region** | Clustered Bar Chart | `Region`, `Category`, `Profit` |
| 🌍 **Region Slicer** | Slicer | `Region` |
| 🗂️ **Category Slicer** | Slicer | `Category` |
| 💡 **3 Insight Text Boxes** | Text Box | Static business takeaways |

**Page-level filter:** `Ship Mode` = *Second Class* and *Standard Class*

---

### 🗒️ 6. Page 2 — Order Details

> A detailed table for drilling down into individual orders.

| Column | Description |
|--------|-------------|
| `Order Date` / `Ship Date` | When the order was placed and shipped |
| `Order Number` | Numeric part of the original Order ID |
| `Customer ID` / `Customer Name` | Who placed the order |
| `Segment` | Consumer or Corporate |
| `State` / `Region` | Where the order was delivered |
| `Category` / `Sub Category` / `Product Name` | What was ordered |
| `Sales` / `Quantity` / `Discount` / `Profit` | Order measures |

---

### 🎨 7. Design Choices

| Element | Choice |
|---------|--------|
| 📐 **Canvas size** | 1920 × 1080 (Fit to Page) |
| 🎨 **Theme** | Fluent 2 base theme with a custom background image |
| 🔤 **Fonts** | Segoe UI Bold for titles and KPI labels |
| 🌈 **Category colours** | Technology (teal), Office Supplies (pink), Furniture (yellow) |

---

## 🛠️ Tech Stack

| Tool | Version | Purpose |
|------|---------|---------|
| 📊 **Power BI Desktop** | Latest | Report building and visualization |
| 🧹 **Power Query (M)** | Built-in | Data import, cleaning and shaping |
| 🧮 **DAX** | Built-in | Measures and aggregations |
| 📄 **CSV** | — | Source data format (Sample – Superstore) |
| 🎨 **Fluent 2 Theme** | Built-in | Consistent report styling |

---

## 📈 Results & Insights

With the default page filter (*Second Class* and *Standard Class* shipping), the dashboard shows:

| KPI | Value |
|-----|-------|
| 💰 **Total Sales** | ≈ $1.50 M |
| 📈 **Total Profit** | ≈ $178.6 K |
| 📦 **Total Quantity** | ≈ 24,936 units |
| 🏷️ **Average Discount** | ≈ 15.7 % |

**Key takeaways (also shown on the dashboard):**

- 🏆 **Technology Leads** — Technology is the top-selling category, and it drives strong profitability in every region.
- 🌍 **West Performs Best** — The West region delivers the highest profit (≈ $65.7 K), followed by East, South and Central.
- 🪑 **Furniture Needs Focus** — Furniture earns the lowest profit and even runs at a loss in the Central region.
- 📉 **Central Is Weakest** — Central records the lowest profit of all four regions.

> 📝 *Figures are calculated from the data model using the page's default filters. They will change when you use the Region or Category slicers.*

---

## 🏆 Advantages

| Advantage | Detail |
|-----------|--------|
| 🎓 **Beginner Friendly** | Covers import, cleaning, DAX and visuals in one project |
| 🔄 **Interactive** | Slicers update every visual instantly |
| 📚 **Educational** | Shows a full BI workflow from raw CSV to insights |
| 💡 **Actionable** | Insight callouts point to where the business should focus |
| 🧼 **Clean Model** | Tidy column names and removed unused fields |
| 🧪 **Extensible** | Easy to add Time-Series, Map or Segment analysis |
| 🖥️ **Polished Layout** | Custom canvas, theme and consistent colours |
| 📖 **Well Documented** | Every transformation and visual is explained here |

---

## 🚀 How to Open the Project

1. Install **[Power BI Desktop](https://powerbi.microsoft.com/desktop/)** (free, Windows).
2. Download or clone this repository.
3. Double-click **`Project_1.pbix`** to open it.
4. If prompted, update the CSV path in **Transform data → Source** so it points to your local copy of `Sample - Superstore.csv`.
5. Click **Refresh** to reload the data, then explore using the slicers.

---

# img
## Dashboard img

<img src= "img/Dashboard img.png">

---
## Table img

<img src= "img/Table img.png">


## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for full details.

```
MIT License — Free to use, modify, and distribute with attribution.
```

---

## 👤 Author

<div align="center">

### KRINAL DHOLAKIYA



> *"Every dashboard starts with a single question — just like every insight starts with a single row of data."*

**🎓 Role:** Junior Data Analyst | Power BI Enthusiast \
**📍 Location:** India\
**🛠️ Skills:** Power BI · Power Query · DAX · Data Cleaning · Dashboard Design

</div>

---

## 🙏 Acknowledgements

Special thanks to the following resources and communities that made this project possible:

- 📚 [Microsoft Power BI Docs](https://learn.microsoft.com/en-us/power-bi/) — Official Power BI documentation
- 🧮 [DAX Guide](https://dax.guide/) — Complete DAX function reference
- 🧹 [Power Query M Reference](https://learn.microsoft.com/en-us/powerquery-m/) — M language documentation
- 🛒 [Tableau Sample Superstore](https://www.tableau.com/learn/training) — Source of the Sample Superstore dataset
- 🎥 [Guy in a Cube](https://www.youtube.com/@GuyInACube) — Power BI tutorials
- 💬 [Power BI Community](https://community.powerbi.com/) — Problem-solving support
- 📖 [Kaggle Learn](https://www.kaggle.com/learn) — Data analysis courses

---

<div align="center">

---

*Made with ❤️ — Last updated: 8 October, 2026*

</div>
