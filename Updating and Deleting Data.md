1. Updating Data
	- CAUTION: Don’t Omit the WHERE Clause
		Special care must be exercised when using UPDATE because it is all too easy to mistakenly update every row in your table. Please read this entire section on UPDATE before using this statement.
	```sql
	UPDATE Customers
	SET cust_email = 'kim@thetoystore.com'
	WHERE cust_id = 1000000005;
	```
	```sql
	UPDATE Customers
	SET cust_contact = 'Sam Roberts', cust_email = 'sam@toyland.com'
	WHERE cust_id = 1000000006;
	```
	- TIP: Using Subqueries in an UPDATE Statement
		Subqueries may be used in UPDATE statements, enabling you to update columns with data retrieved with a SELECT statement. Refer to Lesson “[[Working with Subqueries]]” for more information on subqueries and their uses.
	```sql
	UPDATE Customers
	SET cust_email = NULL
	WHERE cust_id = 1000000005;
	```
2. Deleting Data
	- CAUTION: Don’t Omit the WHERE Clause
		Special care must be exercised when using DELETE because it is all too easy to mistakenly delete every row from your table. Please read this entire section on DELETE before using this statement.
	```sql
	DELETE FROM Customers
	WHERE cust_id = 1000000006;
	```
	 - TIP: Foreign Keys Are Your Friend
		Joins were introduced in Lesson 12, “Joining Tables,” and as you learned then, to join two tables, you simply need common fields in both of those tables. But you can also have the DBMS enforce the relationship by using foreign keys. (These are defined in Appendix A, “Sample Table Scripts.”) When foreign keys are present, the DBMS uses them to enforce referential integrity. For example, if you tried to insert a new product into the Products table, the DBMS would not allow you to insert it with an unknown vendor ID because the vend_id column is connected to the Vendors table as a foreign key. So what does this have to do with DELETE? Well, a nice side effect of using foreign keys to ensure referential integrity is that the DBMS usually prevents the deletion of rows that are needed for a relationship. For example, if you tried to delete a product from Products that was used in existing orders in OrderItems, that DELETE statement would throw an error and would be aborted. That’s another reason to always define your foreign keys.
	- NOTE: Table Contents, Not Tables
		The DELETE statement deletes rows from tables, even all rows from tables. But DELETE never deletes the table itself.
	- TIP: Faster Deletes
		If you really do want to delete all rows from a table, don’t use DELETE. Instead, use the TRUNCATE TABLE statement, which accomplishes the same thing but does it much quicker (because data changes are not logged).
3. Guidelines for Updating and Deleting Data
	- Never execute an UPDATE or a DELETE without a WHERE clause unless you really do intend to update and delete every row.
	- Make sure every table has a primary key (refer to Lesson [[Joining Tables]] if you have forgotten what this is), and use it as the WHERE clause whenever possible. (You may specify individual primary keys, multiple values, or value ranges.)
	- Before you use a WHERE clause with an UPDATE or a DELETE, first test it with a SELECT to make sure it is filtering the right records; it is far too easy to write incorrect WHERE clauses.
	- Use database-enforced referential integrity (refer to Lesson [[Joining Tables]] for this one too) so that the DBMS will not allow the deletion of rows that have data in other tables related to them.
	-  Some DBMSs allow database administrators to impose restrictions that prevent the execution of UPDATE or DELETE without a WHERE clause. If your DBMS supports this feature, consider using it.

[[readme|back]]