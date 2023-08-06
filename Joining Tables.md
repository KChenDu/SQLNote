- Creating a Join
	```sql
	SELECT vend_name, prod_name, prod_price
	FROM Vendors, Products
	WHERE Vendors.vend_id = Products.vend_id;
	```
	- CAUTION: Don’t Forget the WHERE Clause
		Make sure all your joins have WHERE clauses; otherwise, the DBMS will return far more data than you want. Similarly, make sure your WHERE clauses are correct. An incorrect filter condition will cause the DBMS to return incorrect data.
	1. Inner Joins
		```sql
		SELECT vend_name, prod_name, prod_price
		FROM Vendors
		INNER JOIN Products ON Vendors.vend_id = Products.vend_id;
		```
	2. Joining Multiple Tables
		```sql
		SELECT prod_name, vend_name, prod_price, quantity
		FROM OrderItems, Products, Vendors
		WHERE Products.vend_id = Vendors.vend_id AND OrderItems.prod_id = Products.prod_id AND order_num = 20007;
		```
		```sql
		SELECT cust_name, cust_contact
		FROM Customers, Orders, OrderItems
		WHERE Customers.cust_id = Orders.cust_id AND OrderItems.order_num = Orders.order_num AND prod_id = 'RGAN01';
		```

[[readme|back]]