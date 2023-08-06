1. Creating Groups
	```sql
	SELECT vend_id, COUNT(*) AS num_prods
	FROM Products
	GROUP BY vend_id;
	```
	- TIP: The ALL Clause
		Some SQL implementations (such as Microsoft SQL Server) support an optional ALL clause within GROUP BY. This clause can be used to return all groups, even those that have no matching rows (in which case the aggregate would return NULL). Refer to your DBMS documentation to see if it supports ALL.
2. Filtering Groups
	```sql
	SELECT cust_id, COUNT(*) AS orders
	FROM Orders
	GROUP BY cust_id
	HAVING COUNT(*) >= 2;
	```
	- NOTE: The Difference Between HAVING and WHERE
		Here’s another way to look it: WHERE filters before data is grouped, and HAVING filters after data is grouped. This is an important distinction; rows that are eliminated by a WHERE clause will not be included in the group. This could change the calculated values, which in turn could affect which groups are filtered based on the use of those values in the HAVING clause.
	```sql
	SELECT vend_id, COUNT(*) AS num_prods
	FROM Products
	WHERE prod_price >= 4
	GROUP BY vend_id
	HAVING COUNT(*) >= 2;
	```
	```sql
	SELECT vend_id, COUNT(*) AS num_prods
	FROM Products
	GROUP BY vend_id
	HAVING COUNT(*) >= 2;
	```
	- NOTE: Using HAVING and WHERE
		HAVING is so similar to WHERE that most DBMSs treat them as the same thing if no GROUP BY is specified. Nevertheless, you should make that distinction yourself. Use HAVING only in conjunction with GROUP BY clauses. Use WHERE for standard row-level filtering.
3. Grouping and Sorting
	- TIP: Don’t Forget ORDER BY
		As a rule, anytime you use a GROUP BY clause, you should also specify an ORDER BY clause. That is the only way to ensure that data will be sorted properly. Never rely on GROUP BY to sort your data.
	```sql
	SELECT order_num, COUNT(*) AS items
	FROM OrderItems
	GROUP BY order_num
	HAVING COUNT(*) >= 3
	ORDER BY items, order_num;
	```

[[readme|back]]