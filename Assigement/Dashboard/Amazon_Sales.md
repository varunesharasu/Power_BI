Step 1: Load the Dataset into Power BI

1. Open Power BI Desktop
2. Get Data
3. Navigator Window
4. Power Query Editor
   Check the following:
    First row is used as headers.
    Data types are correct:
    Order Date → Date
    Ship Date → Date
    Sales → Decimal Number
    Profit → Decimal Number
    Quantity → Whole Number
    Discount → Decimal Number
  Shipping Cost → Decimal Number
5. Remove Empty Rows (if any)
6. Check for Null Values
7. Rename the Table
8. Apply Changes
     Home → Close & Apply




Step 2: Create DAX Measures

2.1 Create a New Measures Table
2.2 Create Total Sales
2.3 Create Total Profit
   Total Profit =
SUM('Amazon Sales'[Profit])
2.4 Create Total Quantity
   Total Quantity =
SUM('Amazon Sales'[Quantity])
2.5 Create Total Orders
   Total Orders =
DISTINCTCOUNT('Amazon Sales'[Order ID])
2.6 Create Total Customers
   Total Customers =
DISTINCTCOUNT('Amazon Sales'[Customer ID])
2.7 Create Profit Margin
   Profit Margin =
DIVIDE(
    [Total Profit],
    [Total Sales],
    0
)
2.8 Create Average Order Value
   Average Order Value =
DIVIDE(
    [Total Sales],
    [Total Orders],
    0
)
2.9 Create Average Discount
   Average Discount =
AVERAGE('Amazon Sales'[Discount])
2.10 Create Average Shipping Cost
   Average Shipping Cost =
AVERAGE('Amazon Sales'[Shipping Cost])
2.11 Create Profit per Order
   Profit per Order =
DIVIDE(
    [Total Profit],
    [Total Orders],
    0
)

