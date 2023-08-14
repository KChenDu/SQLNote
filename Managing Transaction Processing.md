1. Understanding Transaction Processing
	- TIP: Which Statements Can You Roll Back?
		Transaction processing is used to manage INSERT, UPDATE, and DELETE statements. You cannot roll back SELECT statements. (There would not be much point in doing so anyway.) You cannot roll back CREATE or DROP operations. These statements may be used in a transaction block, but if you perform a rollback, they will not be undone.
2. Controlling Transactions
	```sql
	BEGIN TRANSACTION
	...
	COMMIT TRANSACTION
	```
	1. Using ROLLBACK
		```sql
		DELETE FROM Orders;
		ROLLBACK;
		```
	2. Using COMMIT
		```sql
		BEGIN TRANSACTION
		DELETE OrderItems
		WHERE order_num = 12345
		DELETE Orders
		WHERE order_num = 12345
		COMMIT TRANSACTION
		```
	3. Using Savepoints
		```sql
		SAVE TRANSACTION delete1;
		```
		```sql
		ROLLBACK TRANSACTION delete1;
		```
		```sql
		BEGIN TRANSACTION  
		INSERT INTO Customers(cust_id, cust_name)
		VALUES(1000000010, 'Toys Emporium');  
		SAVE TRANSACTION StartOrder;  
		INSERT INTO Orders(order_num, order_date, cust_id)
		VALUES(20100,'2020/12/1',1000000010);  
		IF @@ERROR != 0
		ROLLBACK TRANSACTION StartOrder;
		INSERT INTO OrderItems(order_num, order_item, prod_id, quantity, item_price)
		VALUES(20100, 1, 'BR01', 100, 5.49);  
		IF @@ERROR != 0
		ROLLBACK TRANSACTION StartOrder;
		INSERT INTO OrderItems(order_num, order_item, prod_id, quantity, item_price)
		VALUES(20100, 2, 'BR03', 100, 10.99);  
		IF @@ERROR != 0
		ROLLBACK TRANSACTION StartOrder;
		COMMIT TRANSACTION
		```

[[readme|back]]