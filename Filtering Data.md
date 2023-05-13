1. Using the WHERE Clause
	```sql
	SELECT prod_name, prod_price
	FROM Products
	WHERE prod_price = 3.49;
	```
	- CAUTION: WHERE Clause Position
		When using both ORDER BY and WHERE clauses, make sure that ORDER BY comes after the WHERE. Otherwise, an error will be generated.
2. The WHERE Clause Operators
	1. Checking Against a Single Value
		```sql
		SELECT prod_name, prod_price
		FROM Products
		WHERE prod_price < 10;
		```
		```sql
		SELECT prod_name, prod_price
		FROM Products
		WHERE prod_price <= 10;
		```
	2. Checking for Nonmatches
		```sql
		SELECT vend_id, prod_name
		FROM Products
		WHERE vend_id <> 'DLL01';
		```
		```sql
		SELECT vend_id, prod_name
		FROM Products
		WHERE vend_id != 'DLL01';
		```
	3. Checking for a Range of Values
		```sql
		SELECT prod_name, prod_price
		FROM Products
		WHERE prod_price BETWEEN 5 AND 10;
		```
	4. Checking for No Value
		```sql
		SELECT prod_name
		FROM Products
		WHERE prod_price IS NULL;
		```
		```sql
		SELECT cust_name
		FROM Customers
		WHERE cust_email IS NULL;
		```

[back](readme.md)