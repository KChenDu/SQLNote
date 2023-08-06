1. Filtering by Subquery
	```sql
	SELECT cust_id
	FROM Orders
	WHERE order_num IN (SELECT order_num
						FROM OrderItems
						WHERE prod_id = 'RGAN01');
	```
	```sql
	SELECT cust_name, cust_contact
	FROM Customers
	WHERE cust_id IN (SELECT cust_id
					  FROM Orders
					  WHERE order_num IN (SELECT order_num
										  FROM OrderItems
										  WHERE prod_id = 'RGAN01'));
	```
	- CAUTION: Single Column Only
		Subquery SELECT statements can only retrieve a single column. Attempting to retrieve multiple columns will return an error.
2. Using Subqueries as Calculated Fields
	```sql
	SELECT cust_name, cust_state, (SELECT COUNT(*)
								   FROM Orders
								   WHERE Orders.cust_id = Customers.cust_id) AS orders
	FROM Customers
	ORDER BY cust_name;
	```

[[readme|back]]