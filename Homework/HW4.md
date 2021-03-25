# CSCI360 Spring 2021
# Homework 4 for Chapter 6
# due: 11:59pm 03/23/2021

# Database Description: This homework is based on the well-known suppliers-and-parts database which contains three relations and the following data:
+ **supplier**: Table supplier denotes suppliers. Each supplier has one supplier number (Sno), which is unique to that supplier (and so Sno is the primary key), one name (Sname), not necessarily unique; one rating or status value (Status); and one location (City).
+ **part**: Table part denotes parts. Each kind of part has one part number (Pno), which is unique (So Pno is the primary key); one name (Pname); one color (Color); one weight (Weight); and one location where parts of that kind are stored (City).
+ **shipment**: Table shipment denotes shipments (it shows which parts are supplied by which suppliers). Each shipment has one supplier number (Sno), one part number (Pno), and one quantity (Qty), and one price (Price). For the sake of the example, (Sno, Pno) is the primary key; also Sno and Pno are both foreign keys, matching the primary keys of Suppliers and Parts, respectively). Note that the database shown below includes one supplier, supplier S5, with no shipments at all.
+ The database has the following constraints(We did not learn the `CHECK` and `UNIQUE` constraits, see documentation [here](https://www.w3resource.com/mysql/creating-table-advance/constraint.php)):
  - Sname cannot be NULL.
  - Status must be positive(he `CHECK` constraint).
  - Pname cannot be NULL
  - Weight must be between 1 and 100 inclusive (the `CHECK` constraint).
  - The combination of Pname and Color must be unique.(the `UNIQUE`c onstraint)
  - Qty has a default value of 100.
  - Price must be positive.(the `CHECK` constraint)
+ Bonus: Foreign Key(5 points)
  - Note that there exist foreign key relationship in this database, you do not need to define the foreign key relationships in your code. If you do it, you can get 5 points as the bonus.
+ A Sample of Database State

## supplier

|Sno|Sname|Status|City|
|---|---|---|---|
|s1|Smith|20|London|
|s2|Jones|10|Paris|
|s3|Black|30|Paris|
|s4|Clack|20|London|
|s5|Adams|30|NULL|
  

## part

|Pno|Pname|Color|Weight|City|
|---|---|---|---|---|
|p1|Nut|Red|12|London|
|p2|Bolt|Green|17|Paris|
|p3|Screw|NULL|17|Rome|
|p4|Screw|Red|14|London|
|p5|Cam|Blue|12|Paris|
|p6|Cong|Red|19|London|

## shipment

|Sno|Pno|Qty|Price|
|---|---|---|---|
|s1|p1|300|0.005|
|s1|p2|200|0.009|
|s1|p3|400|0.004|
|s1|p4|200|0.009|
|s1|p5|100|0.01|
|s1|p6|100|0.01|
|s2|p1|300|0.006|
|s2|p2|400|0.004|
|s3|p2|200|0.009|
|s3|p3|200|NULL|
|s4|p2|200|0.008|
|s4|p3|NULL|NULL|
|s4|p4|300|0.006|
|s4|p5|400|0.003|


# Step 1: Create the follwong four files in order:
+ CreateDB.sql: set of SQL statements to create the above three relations. (65 points)
+ LoadDB.sql: set of SQL statements to load the above database state to the database (10 points)
+ AlterDB.sql: set of SQL statements to alter the database structure.(15 points)
  - Rename City in supplier as SCity, and City in part as PCity
  - Change the default value of Qty to 200.
  - Add a new column into shipment to store the date and time information.
  - Set the combination of Sno and Pno in shipment as an index.
  - Rename shipment as ships.
+ ClearDB.sql: set of SQL statements to drop the above three Table. (10 points)
 
# Step 2: Zip the four files, name it as CSCI360_Homework4_JohnDoe(0123456).
# Step 3: Submit your work on [Blackboard](https://blackboard.sau.edu/webapps/login/)
