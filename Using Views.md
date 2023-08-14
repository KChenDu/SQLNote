1. Creating Views
	- NOTE: Renaming Views
		To remove a view, you use the DROP statement. The syntax is simply DROP VIEW viewname;.
		To overwrite (or update) a view, you must first DROP it and then re-create it.
	1. Using Views to Simplify Complex Joins
		```sql
		CREATE VIEW ProductCustomers AS
		SELECT cust_name, cust_contact, prod_id
		FROM Customers, Orders, OrderItems
		WHERE Customers.cust_id = Orders.cust_id AND OrderItems.order_num = Orders.order_num;
		```
	2. Using Views to Reformat Retrieved Data
		```sql
		CREATE VIEW VendorLocations AS
		SELECT RTRIM(vend_name) + ' (' + RTRIM(vend_country) + ')' AS vend_title
		FROM Vendors;
		```
	3. Using Views to Filter Unwanted Data
		```sql
		CREATE VIEW CustomerEMailList AS
		SELECT cust_id, cust_name, cust_email
		FROM Customers
		WHERE cust_email IS NOT NULL;
		```
		- NOTE: WHERE Clauses and WHERE Clauses
			If a WHERE clause is used when retrieving data from the view, the two sets of clauses (the one in the view and the one passed to it) will be combined automatically.
	4. Using Views with Calculated Fields
		```sql
		CREATE VIEW OrderItemsExpanded AS
		SELECT order_num, prod_id, quantity, item_price, quantity*item_price AS expanded_price
		FROM OrderItems
		```

[[readme|back]]