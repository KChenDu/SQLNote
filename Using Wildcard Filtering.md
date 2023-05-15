1. Using the LIKE Operator、
	1. The Percent Sign (%) Wildcard
		```sql
		SELECT prod_id, prod_name
		FROM Products
		WHERE prod_name LIKE 'Fish%';
		```
		```sql
		SELECT prod_id, prod_name
		FROM Products
		WHERE prod_name LIKE '%bean bag%';
		```
		```sql
		SELECT prod_name
		FROM Products
		WHERE prod_name LIKE 'F%y';
		```
	2. The Underscore (\_) Wildcard
		```sql
		SELECT prod_id, prod_name
		FROM Products
		WHERE prod_name LIKE '__ inch teddy bear';
		```
	3. The Brackets ([]) Wildcard
		```sql
		SELECT cust_contact
		FROM Customers
		WHERE cust_contact LIKE '[JM]%'
		ORDER BY cust_contact;
		```
2. Tips for Using Wildcards
	- Don’t overuse wildcards. If another search operator will do, use it instead.

[[readme|back]]