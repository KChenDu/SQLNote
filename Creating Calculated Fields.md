1. Concatenating Fields
	```sql
	SELECT vend_name + '(' + vend_country + ')'
	FROM Vendors
	ORDER BY vend_name;
	```
	```sql
	SELECT RTRIM(vend_name) + ' (' + RTRIM(vend_country) + ')'
	FROM Vendors
	ORDER BY vend_name;
	```
	- NOTE: The TRIM Functions
		Most DBMSs support RTRIM() (which, as just seen, trims the right side of a string), as well as LTRIM(), which trims the left side of a string, and TRIM(), which trims both the right and left.
2. Using Aliases
	```sql
	SELECT RTRIM(vend_name) + ' (' + RTRIM(vend_country) + ')' AS vend_title
	FROM Vendors
	ORDER BY vend_name;
	```
	- TIP: Other Uses for Aliases
		Aliases have other uses too. Some common uses include renaming a column if the real table column name contains illegal characters (for example, spaces) and expanding column names if the original names are either ambiguous or easily misread.
	- CAUTION: Alias Names
		Aliases may be single words or complete strings. If the latter is used, then the string should be enclosed within quotes. This practice is legal but is strongly discouraged. While multiword names are indeed highly readable, they create all sorts of problems for many client applications—so much so that one of the most common uses of aliases is to rename multiword column names to single-word names (as explained above).
3. Performing Mathematical Calculations
	```sql
	SELECT prod_id, quantity, item_price, quantity*item_price AS expanded_price
	FROM OrderItems
	WHERE order_num = 20008;
	```

[[readme|back]]