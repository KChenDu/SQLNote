1. Using the WHERE Clause
	```sql
	SELECT prod_name, prod_price
	FROM Products
	WHERE prod_price = 3.49;
	```
	- CAUTION: WHERE Clause Position
		When using both ORDER BY and WHERE clauses, make sure that ORDER BY comes after the WHERE. Otherwise, an error will be generated.
1. The WHERE Clause Operators
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
3. Combining WHERE Clauses
	1. Using the AND Operator
		```sql
		SELECT prod_id, prod_price, prod_name
		FROM Products
		WHERE vend_id = 'DLL01' AND prod_price <= 4;
		```
	2. Using the OR Operator
		```sql
		SELECT prod_id, prod_price, prod_name
		FROM Products
		WHERE vend_id = 'DLL01' OR vend_id = 'BRS01';
		```
	3. Understanding Order of Evaluation
		```sql
		SELECT prod_name, prod_price FROM Products
		WHERE vend_id = 'DLL01' OR vend_id = 'BRS01' AND prod_price >= 10;
		```
		```sql
		SELECT prod_name, prod_price FROM Products
		WHERE (vend_id = 'DLL01' OR vend_id = 'BRS01') AND prod_price >= 10;
		```
4. Using the IN Operator
	```sql
	SELECT prod_name, prod_price
	FROM Products
	WHERE vend_id IN ('DLL01','BRS01')
	ORDER BY prod_name;
	```
5. Using the NOT Operator
	```sql
	SELECT prod_name FROM Products
	WHERE NOT vend_id = 'DLL01'
	ORDER BY prod_name;
	```

[[readme|back]]