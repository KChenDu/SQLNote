1. Creating Tables
	1. Basic Table Creation
		```sql
		CREATE TABLE Products
		(
			prod_id    CHAR(10)      NOT NULL,
			vend_id    CHAR(10)      NOT NULL,
			prod_name  CHAR(254)     NOT NULL,
			prod_price DECIMAL(8,2)  NOT NULL,
			prod_desc  VARCHAR(1000) NULL
		);
		```
	2. Working with NULL Values
		```sql
		CREATE TABLE Orders
		(
			order_num  INTEGER  NOT NULL,
			order_date DATETIME NOT NULL,
			cust_id    CHAR(10) NOT NULL
		);
		```
		```sql
		CREATE TABLE Vendors
		(
			vend_id      CHAR(10) NOT NULL,
			vend_name    CHAR(50) NOT NULL,
			vend_address CHAR(50),
			vend_city    CHAR(50),
			vend_state   CHAR(5),
			vend_zip     CHAR(50),
			vend_country CHAR(10),
		);
		```
		- TIP: Primary Keys and NULL Values
			You learned that primary keys are columns whose values uniquely identify every row in a table. Only columns that do not allow NULL values can be used in primary keys. Columns that allow no value at all cannot be used as unique identifiers.
		- CAUTION: Understanding NULL
			Don’t confuse NULL values with empty strings. A NULL value is the lack of a value; it is not an empty string. If you were to specify '' (two single quotes with nothing in between them), that would be allowed in a NOT NULL column. An empty string is a valid value; it is not no value. NULL values are specified with the keyword NULL, not with an empty string.
	3. Specifying Default Values
		```sql
		CREATE TABLE OrderItems
		(
			order_num  INTEGER      NOT NULL,
			order_item INTEGER      NOT NULL,
			prod_id    CHAR(10)     NOT NULL,
			quantity   INTEGER      NOT NULL DEFAULT 1,
			item_price DECIMAL(8,2) NOT NULL
		);
		```
2. Updating Tables
	```sql
	ALTER TABLE Vendors
	ADD vend_phone CHAR(20);
	```
	```sql
	ALTER TABLE Vendors
	DROP COLUMN vend_phone;
	```
3. Deleting Tables
	```
	DROP TABLE CustCopy;
	```

[[readme|back]]