1. Sorting Data
	```sql
	SELECT prod_name
	FROM Products
	ORDER BY prod_name;
	```
	- CAUTION: Position of ORDER BY Clause
		When specifying an ORDER BY clause, be sure that it is the last clause in your SELECT statement. If it is not the last clause, an error will be generated.
	- TIP: Sorting by Nonselected Columns
		Although more often than not the columns used in an ORDER BY clause will be ones selected for display, this is actually not required. It is perfectly legal to sort data by a column that is not retrieved.
2. Sorting by Multiple Columns
	```sql
	SELECT prod_id, prod_price, prod_name
	FROM Products
	ORDER BY prod_price, prod_name;
	```
3. Specifying Sort Direction
	```sql
	SELECT prod_id, prod_price, prod_name
	FROM Products
	ORDER BY prod_price DESC;
	```
	```sql
	SELECT prod_id, prod_price, prod_name
	FROM Products
	ORDER BY prod_price DESC, prod_name;
	```

[back](readme.md)