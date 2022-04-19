### Database Normalisation
+ Deletion Anomaly
+ Update Anomaly
+ Insert Anomaly
+ Searching and Sorting
	+ Require chainging together queries over multiple columns

### Progressive Normalisation 
+ First Normal Form
	+ The information is stored in a relational table with each column containing atomic values. There are no repeating groups of columns.
	+ ![[Screenshot 2022-03-02 at 1.16.29 PM.png]]
		+ Atomic Values
		+ Repeating Values
+ Second Normal Form
	+ The table is in first normal form and all the columns depend on the table’s primary key.
	+ ![[Screenshot 2022-03-02 at 1.22.12 PM.png]]
+ Third Normal Form
	+ Transitive Dependence