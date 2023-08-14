1. Executing Stored Procedures
	```sql
	EXECUTE AddNewProduct('JTS01',
						  'Stuffed Eiffel Tower',
						  6.49,
						  'Plush stuffed toy with the text La Tour Eiffel in red white and blue');
	 ```
2. Creating Stored Procedures
	```sql
	CREATE PROCEDURE MailingListCount
	AS
	DECLARE @cnt INTEGER
	SELECT @cnt = COUNT(*)
	FROM Customers
	WHERE NOT cust_email IS NULL;
	RETURN @cnt;
	```
	```sql
	DECLARE @ReturnValue INT
	EXECUTE @ReturnValue=MailingListCount;
	SELECT @ReturnValue;
	```
	```sql
	CREATE PROCEDURE NewOrder @cust_id CHAR(10)
	AS
	-- Declare variable for order number
	DECLARE @order_num INTEGER
	-- Get current highest order number
	SELECT @order_num=MAX(order_num)
	FROM Orders
	-- Determine next order number
	SELECT @order_num=@order_num+1
	-- Insert new order
	INSERT INTO Orders(order_num, order_date, cust_id)
	VALUES(@order_num, GETDATE(), @cust_id)
	-- Return order number
	RETURN @order_num;
	```
	```sql
	CREATE PROCEDURE NewOrder @cust_id CHAR(10)
	AS
	-- Insert new order
	INSERT INTO Orders(cust_id)
	VALUES(@cust_id)
	-- Return order number
	SELECT order_num = @@IDENTITY;
	```

[[readme|back]]