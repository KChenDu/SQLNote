1. Using Aggregate Functions
	1. The AVG() Function
		```sql
		SELECT AVG(prod_price) AS avg_price
		FROM Products;
		```
		```sql
		SELECT AVG(prod_price) AS avg_price
		FROM Products
		WHERE vend_id = 'DLL01';
		```
		- NOTE: NULL Values
			Column rows containing NULL values are ignored by the AVG() function.
	2. The COUNT() Function
		```sql
		SELECT COUNT(*) AS num_cust
	    FROM Customers;
		```
		```sql
		SELECT COUNT(cust_email) AS num_cust
		FROM Customers;
		```
		- NOTE: NULL Values
			Column rows with NULL values in them are ignored by the COUNT() function if a column name is specified, but not if the asterisk (*) is used.
	3. The MAX() Function
		```sql
		SELECT MAX(prod_price) AS max_price
		FROM Products;
		```
		- TIP: Using MAX() with Nonnumeric Data
			Although MAX() is usually used to find the highest numeric or date values, many (but not all) DBMSs allow it to be used to return the highest value in any columns including textual columns. When used with textual data, MAX() returns the row that would be the last if the data were sorted by that column.
	3. The MIN() Function
		```sql
		SELECT MIN(prod_price) AS min_price
		FROM Products;
		```
		- TIP: Using MIN() with Nonnumeric Data
			Although MIN() is usually used to find the lowest numeric or date values, many (but not all) DBMSs allow it to be used to return the lowest value in any columns including textual columns. When used with textual data, MIN() will return the row that would be first if the data were sorted by that column.
	4. The SUM() Function
		```sql
		SELECT SUM(quantity) AS items_ordered
		FROM OrderItems
		WHERE order_num = 20005;
		```
2. Aggregates on Distinct Values
	```sql
	SELECT AVG(DISTINCT prod_price) AS avg_price
    FROM Products
    WHERE vend_id = 'DLL01';
	```
3. Combining Aggregate Functions
	```sql
	SELECT COUNT(*) AS num_items, MIN(prod_price) AS price_min, MAX(prod_price) AS price_max, AVG(prod_price) AS price_avg
	FROM Products;
	```

[[readme|back]]