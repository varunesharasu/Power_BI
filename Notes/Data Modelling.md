# Data Modelling

It is the process of organizing, structuring, and connecting multiple tables in Power BI.

```
Cardinality/ Type of Relationship
	one-to-one
	one-to-many/many-to-one
	many-to-many - it will only exist in machine learning Python, it will not be there in Power BI

	customer ----> product ---> orders ---> order_items(bill)
	c_id (PK)		p_id			o_id(PK)		oi_id (PK)
							c_id(FK)		o_id (FK)
										p_id (FK)


	customer ----- product ----- orders ----- order_items
		1	   ->       n
				     1		->	n
```

Fact Table :
it consists of all the measurable and numerical information

Dimension Table :
it consists of

Star Schema

```
fact table at the center and all the dimension tables are around the fact table.

	Customers
       |
```

Products — Sales — Calendar
|
Region

Snowflake Schema
