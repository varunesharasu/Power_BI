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
