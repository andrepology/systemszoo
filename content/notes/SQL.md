+ SQL dialects
+ The operations are similar to pandas, so you've worked with this before.

+ Database design
	+ preferable to make sure that a particular column of data is only stored in a single location
	+ relate one table to another, using keys
		+ reduces tables to non-readable id maps, but helps with maintainability
	+ You need joins to reconcile related tables
		+ cross join
		+ innter join

### syntax for basic SQL queries
+ Creating tables/schemas
	+ `CREATE TABLE groceries (id INTEGER PRIMARY KEY, name TEXT, quantity INTEGER);`
		+ PRIMARY KEY states this is a row identifier
		+ AUTOINCREMENT does so automatically

+ Inserting data
	+ `INSERT INTO groceries VALUES (1, "Bananas", 4);`
	+ `INSERT INTO groceries VALUES (2, "Peanut Butter", 2);`

+ Querying
	+ Selecting all data
		+ `SELECT * FROM groceries`
	+ Filter 
		+ with conditions
			+ `SELECT * FROM customers WHERE age > 21;`
			+ `SELECT * FROM customers WHERE age < 21 AND state = "NY";`
		+ with IN
			+ `SELECT * FROM customers WHERE plan IN ("free", "basic");`
		+ with HAVING
			+ `SELECT type, SUM(calories) AS total_calories FROM exercise_logs`
			+ `GROUP BY type`
			+ `HAVING total_calories > 150`
	+ Select specific columns
		+ `SELECT name, age FROM customers;`
	+ Order results
		+ `SELECT * FROM customers WHERE age > 21 ORDER BY age DESC;`
	+ Transform with CASE
		+ `SELECT name, CASE WHEN age > 18 THEN "adult" ELSE "minor" END "type" FROM customers;`
+ Aggregating Data
	+ Aggregate functions
		+ `SELECT MAX(age) FROM customers;`
	+ Grouping data
		+ `SELECT gender, COUNT(*) FROM students GROUP BY gender;`
+ Joining related tables
	+ Inner
		+ `SELECT customers.name, orders.item FROM customers JOIN orders ON customers.id = orders.customer_id;`
	+ Outer
		+ `SELECT customers.name, orders.item FROM customers LEFT OUTER JOIN orders ON customers.id = orders.customer_id;`
+ Updating and Deleting Data
	+ `UPDATE customers SET age = 33 WHERE id = 73;`
	+ `DELETE FROM customers WHERE id = 73;`
+ Altering tables
	+ `ALTER TABLE groceries add AISLE INTEGER default "1"`





+ difference between a primary key and a foreign key.
-  Write a SQL query to find all client’s names and phone numbers which have 3 year (or longer) loans.
- Write a SQL query to find the total amount of loans that are in arrears.

+ Relational Databases
	+ Mapping between separate, isolated tables
+ SQL is a database access language