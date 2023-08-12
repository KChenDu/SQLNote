1. Using Table Aliases
	```sql
	SELECT cust_name, cust_contact
    FROM Customers AS C, Orders AS O, OrderItems AS OI
    WHERE C.cust_id = O.cust_id AND OI.order_num = O.order_num AND prod_id = 'RGAN01';
	```
2. Using Different Join Types
	1. Self Joins
		```sql
		SELECT c1.cust_id, c1.cust_name, c1.cust_contact
		FROM Customers AS c1, Customers AS c2
		WHERE c1.cust_name = c2.cust_name AND c2.cust_contact = 'Jim Jones';
		```
	2. Natural Joins
		```sql
		SELECT C.*, O.order_num, O.order_date, OI.prod_id, OI.quantity, OI.item_price
		FROM Customers AS C, Orders AS O, OrderItems AS OI
		WHERE C.cust_id = O.cust_id AND OI.order_num = O.order_num AND prod_id = 'RGAN01';
		```
	3. Outer Joins
		```sql
		SELECT Customers.cust_id, Orders.order_num
		FROM Customers
		LEFT OUTER JOIN Orders ON Customers.cust_id = Orders.cust_id;
		```
		```sql
		SELECT Customers.cust_id, Orders.order_num
		FROM Customers
		RIGHT OUTER JOIN Orders ON Customers.cust_id = Orders.cust_id;
		```
		- TIP: Outer Join Types
			Remember that there are always two basic forms of outer joins—the left outer join and the right outer join. The only difference between them is the order of the tables that they are relating. In other words, a left outer join can be turned into a right outer join simply by reversing the order of the tables in the FROM or WHERE clause. As such, the two types of outer join can be used interchangeably, and the decision about which one is used is based purely on convenience.
		```sql
		SELECT Customers.cust_id, Orders.order_num
		FROM Customers
		FULL OUTER JOIN Orders ON Customers.cust_id = Orders.cust_id;
		```
3. Using Joins with Aggregate Functions
	```sql
	SELECT Customers.cust_id, COUNT(Orders.order_num) AS num_ord
	FROM Customers
	INNER JOIN Orders ON Customers.cust_id = Orders.cust_id
	GROUP BY Customers.cust_id;
	```
	```sql
	SELECT Customers.cust_id, COUNT(Orders.order_num) AS num_ord
	FROM Customers
	LEFT OUTER JOIN Orders ON Customers.cust_id = Orders.cust_id
	GROUP BY Customers.cust_id;
	```

[[readme|back]]