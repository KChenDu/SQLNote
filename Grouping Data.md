1. Understanding Data Grouping
	```sql
	SELECT vend_id, COUNT(*) AS num_prods
	FROM Products
	GROUP BY vend_id;
	```
	- TIP: The ALL Clause
		Some SQL implementations (such as Microsoft SQL Server) support an optional ALL clause within GROUP BY. This clause can be used to return all groups, even those that have no matching rows (in which case the aggregate would return NULL). Refer to your DBMS documentation to see if it supports ALL.
2. Filtering Groups
	```sql
	
	```