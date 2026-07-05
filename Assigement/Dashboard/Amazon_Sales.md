# Amazon Sales Dashboard – Power BI Guide

## Step 1: Load the Dataset into Power BI

### 1. Open Power BI Desktop
Launch **Power BI Desktop** on your computer.

### 2. Get Data
- Click **Home** → **Get Data**.
- Select the appropriate data source (Excel, CSV, SQL Server, etc.).
- Browse to your Amazon Sales dataset.
- Click **Open**.

### 3. Navigator Window
- In the **Navigator** window, select the required worksheet or table.
- Click **Transform Data** to open the **Power Query Editor**.

### 4. Power Query Editor

Verify the following before loading the data:

| Column | Data Type |
|---------|-----------|
| Order Date | Date |
| Ship Date | Date |
| Sales | Decimal Number |
| Profit | Decimal Number |
| Quantity | Whole Number |
| Discount | Decimal Number |
| Shipping Cost | Decimal Number |

Also ensure:

- The **first row is used as headers**.
- Column names are accurate and properly formatted.

### 5. Remove Empty Rows
- Go to **Home** → **Remove Rows** → **Remove Blank Rows** (if applicable).

### 6. Check for Null Values
Review each column for missing or null values and clean the data as needed.

### 7. Rename the Table
Rename the imported table to:

```text
Amazon Sales
```

### 8. Apply Changes
After completing all transformations:

**Home → Close & Apply**

Power BI will load the cleaned dataset into the data model.




# Amazon Sales Dashboard – DAX Measures

## Step 2: Create DAX Measures

### 2.1 Create a Measures Table

Create a dedicated table to store all DAX measures.

```DAX
Measures = { BLANK() }
```

---

## 2.2 Total Sales

```DAX
Total Sales =
SUM('Amazon Sales'[Sales])
```

---

## 2.3 Total Profit

```DAX
Total Profit =
SUM('Amazon Sales'[Profit])
```

---

## 2.4 Total Quantity

```DAX
Total Quantity =
SUM('Amazon Sales'[Quantity])
```

---

## 2.5 Total Orders

```DAX
Total Orders =
DISTINCTCOUNT('Amazon Sales'[Order ID])
```

---

## 2.6 Total Customers

```DAX
Total Customers =
DISTINCTCOUNT('Amazon Sales'[Customer ID])
```

---

## 2.7 Profit Margin

```DAX
Profit Margin =
DIVIDE(
    [Total Profit],
    [Total Sales],
    0
)
```

---

## 2.8 Average Order Value

```DAX
Average Order Value =
DIVIDE(
    [Total Sales],
    [Total Orders],
    0
)
```

---

## 2.9 Average Discount

```DAX
Average Discount =
AVERAGE('Amazon Sales'[Discount])
```

---

## 2.10 Average Shipping Cost

```DAX
Average Shipping Cost =
AVERAGE('Amazon Sales'[Shipping Cost])
```

---

## 2.11 Profit per Order

```DAX
Profit per Order =
DIVIDE(
    [Total Profit],
    [Total Orders],
    0
)
```

---

## Summary of Measures

| Measure | Description |
|----------|-------------|
| Total Sales | Total revenue generated |
| Total Profit | Total profit earned |
| Total Quantity | Total units sold |
| Total Orders | Number of unique orders |
| Total Customers | Number of unique customers |
| Profit Margin | Profit as a percentage of sales |
| Average Order Value | Average revenue per order |
| Average Discount | Average discount offered |
| Average Shipping Cost | Average shipping cost per order |
| Profit per Order | Average profit earned per order |


# Step 3: Build Dashboard Visualizations

---

## 3.1 Sales Trend (Line Chart)

### Visual

**Line Chart**

### Fields

| Field | Value |
|--------|-------|
| X-axis | Order Date |
| Y-axis | Total Sales |

### Purpose

Shows how sales change over time.

---

## 3.2 Sales by Category (Donut Chart)

### Visual

**Donut Chart**

### Fields

| Field | Value |
|--------|-------|
| Legend | Category |
| Values | Total Sales |

### Purpose

Displays each product category's contribution to total sales.

---

## 3.3 Profit by State (Filled Map)

### Visual

**Filled Map** (Recommended)

If Filled Map is unavailable, use **Map**.

### Fields

| Field | Value |
|--------|-------|
| Location | State |
| Color Saturation | Total Profit |

**For Map Visual**

| Field | Value |
|--------|-------|
| Location | State |
| Bubble Size | Total Profit |

### Purpose

Shows which states generate the highest profit.

---

## 3.4 Top 10 Products by Sales

### Visual

**Clustered Bar Chart**

### Fields

| Field | Value |
|--------|-------|
| Y-axis | Product Name |
| X-axis | Total Sales |

### Filter

Apply a **Top N Filter**:

- Top **10**
- By **Total Sales**

### Purpose

Highlights the ten highest-selling products.

---

# Recommended Dashboard Layout

```
---------------------------------------------------------
| Total Sales | Total Profit | Orders | Customers |
---------------------------------------------------------
|             Sales Trend (Line Chart)              |
---------------------------------------------------------
| Sales by Category | Profit by State (Map)         |
---------------------------------------------------------
|          Top 10 Products by Sales                 |
---------------------------------------------------------
```
