1. Understanding Data Insertion
	1. Inserting Complete Rows
		- TIP: The INTO Keyword
			In some SQL implementations, the INTO keyword following INSERT is optional. However, it is good practice to provide this keyword even if it is not needed. Doing so will ensure that your SQL code is portable between DBMSs.
		```sql
		INSERT INTO Customers(cust_id,
							  cust_name,
							  cust_address,
							  cust_city,
							  cust_state,
							  cust_zip,
							  cust_country,
							  cust_contact,
							  cust_email)
		VALUES(1000000006,
		       'Toy Land',
		       '123 Any Street',
		       'New York',
		       'NY',
		       '11111',
		       'USA',
		       NULL,
		       NULL);
		```
		- Always Use a Columns List
			As a rule, never use INSERT without explicitly specifying the column list. This will greatly increase the probability that your SQL will continue to function in the event that table changes occur.
	2. Inserting Partial Rows
		```sql
		INSERT INTO Customers(cust_id,
							  cust_name,
							  cust_address,
							  cust_city,
							  cust_state,
							  cust_zip,
							  cust_country)
		VALUES(1000000006,
			   'Toy Land',
			   '123 Any Street',
			   'New York',
			   'NY',
			   '11111',
			   'USA');
		```
		- CAUTION: Omitting Columns
			You may omit columns from an INSERT operation if the table definition so allows. One of the following conditions must exist:
			- The column is defined as allowing NULL values (no value at all).
			- A default value is specified in the table definition. This means the default value will be used if no value is specified.
		- CAUTION: Omitting Required Values
			If you omit a value from a table that does not allow NULL values and does not have a default, the DBMS will generate an error message, and the row will not be inserted.
	3. Inserting Retrieved Data
		```sql
		INSERT INTO Customers(cust_id,
							  cust_contact,
							  cust_email,
							  cust_name,
							  cust_address,
							  cust_city,
							  cust_state,
							  cust_zip,
							  cust_country)
		SELECT cust_id,
			   cust_contact,
			   cust_email,
			   cust_name,
			   cust_address,
			   cust_city,
			   cust_state,
			   cust_zip,
			   cust_country
		FROM CustNew;
		```
		- TIP: Column Names in INSERT SELECT
			This example uses the same column names in both the INSERT and SELECT statements for simplicity’s sake. But there is no requirement that the column names match. In fact, the DBMS does not even pay attention to the column names returned by the SELECT. Rather, the column position is used, so the first column in the SELECT statement (regardless of its name) will be used to populate the first specified table column, and so on.
2. Copying from One Table to Another
	```sql
	SELECT * INTO CustCopy
	FROM Customers;
	```
	- TIP: Making Copies of Tables
		The technique described here is a great way to make copies of tables before experimenting with new SQL statements. By making a copy first, you’ll be able to test your SQL on that copy instead of on live data.

[[readme|back]]