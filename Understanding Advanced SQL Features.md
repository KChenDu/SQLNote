1. Understanding Constraints
	- NEW TERM: Constraints
		Rules that govern how database data is inserted or manipulated.
	1. Primary Keys
		```sql
		CREATE TABLE Vendors
		(
			vend_id      CHAR(10) NOT NULL PRIMARY KEY,
			vend_name    CHAR(50) NOT NULL,
			vend_address CHAR(50) NULL,
			vend_city    CHAR(50) NULL,
			vend_state   CHAR(5)  NULL,
			vend_zip     CHAR(10) NULL,
			vend_country CHAR(50) NULL
		);
		```
		```sql
		ALTER TABLE Vendors
		ADD CONSTRAINT PRIMARY KEY (vend_id);
		```
	2. Foreign Keys
		```sql
		CREATE TABLE Orders
		(
			order_num  INTEGER  NOT NULL PRIMARY KEY,
			order_date DATETIME NOT NULL,
			cust_id    CHAR(10) NOT NULL REFERENCES Customers(cust_id)
		);
		```
		```sql
		ALTER TABLE Orders ADD CONSTRAINT
		FOREIGN KEY (cust_id) REFERENCES Customers (cust_id);
		```
		- TIP: Foreign Keys Can Help Prevent Accidental Deletion
			As noted in Lesson “[[Updating and Deleting Data]]”, in addition to helping enforce referential integrity, foreign keys serve another invaluable purpose. After a foreign key is defined, your DBMS does not allow the deletion of rows that have related rows in other tables. For example, you are not allowed to delete a customer who has associated orders. The only way to delete that customer is to first delete the related orders (which in turn means deleting the related order items). Because they require such methodical deletion, foreign keys can help prevent the accidental deletion of data.
	3. Check Constraints
		```sql
		CREATE TABLE OrderItems
		(
			order_num  INTEGER  NOT NULL,
			order_item INTEGER  NOT NULL,
			prod_id    CHAR(10) NOT NULL,
			quantity   INTEGER  NOT NULL CHECK (quantity > 0),
			item_price MONEY    NOT NULL
		);
		```
		```sql
		ADD CONSTRAINT CHECK (gender LIKE '[MF]');
		```
2. Understanding Indexes
	```sql
	CREATE INDEX prod_name_ind
	ON Products (prod_name);
	```
3. Understanding Triggers
	```sql
	CREATE TRIGGER customer_state
	ON Customers
	FOR INSERT, UPDATE AS
	UPDATE Customers
	SET cust_state = Upper(cust_state)
	WHERE Customers.cust_id = inserted.cust_id;
	```
	- TIP: Constraints Are Faster Than Triggers
		As a rule, constraints are processed more quickly than triggers, so whenever possible, use constraints instead

[[readme|back]]