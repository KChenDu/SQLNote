1. Retrieving Individual Columns
	```sql
	SELECT prod_name
	FROM Products;
	```
2. Retrieving Multiple Columns
	```sql
	SELECT prod_id, prod_name, prod_price
	FROM Products;
	```
3. Retrieving All Columns
	```sql
	SELECT *
	FROM Products;
	```
	- CAUTION: Using Wildcards
		As a rule, you are better off not using the * wildcard unless you really do need every column in the table. Even though use of wildcards may save you the time and effort needed to list the desired columns explicitly, retrieving unnecessary columns usually slows down the performance of your retrieval and your application.
	- TIP: Retrieving Unknown Columns
		There is one big advantage to using wildcards. As you do not explicitly specify column names (because the asterisk retrieves every column), it is possible to retrieve columns whose names are unknown.
4. Retrieving Distinct Rows
	```sql
	SELECT DISTINCT vend_id
	FROM Products;
	```
	- CAUTION: Can’t Be Partially DISTINCT
		The DISTINCT keyword applies to all columns, not just the one it precedes. If you were to specify SELECT DISTINCT vend_id, prod_price, six of the nine rows would be retrieved because the combined specified columns produced six unique combinations.
5. Limiting Results
	```sql
	SELECT TOP 5 prod_name
	FROM Products;
	```
6. Using Comments
	- inline comments:
	```sql
	SELECT prod_name -- this is a comment
	FROM Products;
	```
	- multiline comments:
	```sql
	/* SELECT prod_name, vend_id
	FROM Products; */
	SELECT prod_name
	FROM Products;
	```

[back](readme.md)