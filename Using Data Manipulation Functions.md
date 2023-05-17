1. Text Manipulation Functions
	```sql
	SELECT vend_name, UPPER(vend_name) AS vend_name_upcase
    FROM Vendors
    ORDER BY vend_name;
	```
	```sql
	SELECT cust_name, cust_contact
	FROM Customers
	WHERE SOUNDEX(cust_contact) = SOUNDEX('Michael Green');
	```
2. Date and Time Manipulation Functions
	```sql
	SELECT order_num
	FROM Orders
	WHERE DATEPART(yy, order_date) = 2020;
	```

[[readme|back]]