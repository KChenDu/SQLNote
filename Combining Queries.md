1. Using UNION
	```sql
	SELECT cust_name, cust_contact, cust_email
	FROM Customers
	WHERE cust_state IN ('IL','IN','MI')
	UNION
	SELECT cust_name, cust_contact, cust_email
	FROM Customers
	WHERE cust_name = 'Fun4All';
	```
2. UNION Rules
	- A UNION must be composed of two or more SELECT statements, each separated by the keyword UNION (so, if you’re combining four SELECT statements, you would use three UNION keywords).
	- Each query in a UNION must contain the same columns, expressions, or aggregate functions (and some DBMSs even require that columns be listed in the same order).
	- Column datatypes must be compatible. They need not be the same name or the exact same type, but they must be of a type that the DBMS can implicitly convert (for example, different numeric types or different date types).
	- NOTE: UNION Column Names
		If SELECT statements that are combined with a UNION have different column names, what name is actually returned? For example, if one statement contained SELECT prod_name and the next used SELECT productname, what would be the name of the combined returned column?
		The answer is that the first name is used, so in our example the combined column would be named prod_name, even though the second SELECT used a different name. This also means that you can use an alias on the first name to set the returned column name as needed.
		This behavior has another interesting side effect. Because the first set of column names are used, only those names can be specified when sorting. Again, in our example, you could use ORDER BY prod_name to sort the com- bined results, but ORDER BY productname would display an error message because there is no column productname in the combined results.
3. Including or Eliminating Duplicate Rows
	```sql
	SELECT cust_name, cust_contact, cust_email
	FROM Customers
	WHERE cust_state IN ('IL','IN','MI')
	UNION ALL
	SELECT cust_name, cust_contact, cust_email
	FROM Customers
	WHERE cust_name = 'Fun4All';
	```
	- TIP: UNION Versus WHERE
		At the beginning of this lesson, I said that UNION almost always accomplishes the same thing as multiple WHERE conditions. UNION ALL is the form of UNION that accomplishes what cannot be done with WHERE clauses. If you do, in fact, want all occurrences of matches for every condition (including duplicates), you must use UNION ALL and not WHERE.
3. Sorting Combined Query Results
	```sql
	SELECT cust_name, cust_contact, cust_email
	FROM Customers
	WHERE cust_state IN ('IL','IN','MI')
	UNION
	SELECT cust_name, cust_contact, cust_email
	FROM Customers
	WHERE cust_name = 'Fun4All'
	ORDER BY cust_name, cust_contact;
	```
	- TIP: Working with Multiple Tables
		For simplicity’s sake, the examples in this lesson have all used UNION to com- bine multiple queries on the same table. In practice, UNION is really useful when you need to combine data from multiple tables, even tables with mismatched column names, in which case you can combine UNION with aliases to retrieve a single set of results.

[[readme|back]]