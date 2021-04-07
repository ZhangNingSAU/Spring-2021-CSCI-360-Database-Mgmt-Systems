# CSCI360 Spring 2021
# Homework 5 for Chapter 7
# due: 11:59pm 04/01/2021

# Database Description: This homework is based on the suppliers-and-parts database you created in [HW4](../Homework/HW4.md).
+ Note: Please run CreateDB.sql and LoadDB.sql to create the database and insert rows. Do NOT run AlterDB.sql.




# Step 1: Write Queries:
1. Print part numbers for all parts shipped by more than one supplier.(hint: count())<br>
2. Print the total number of suppliers (regardless of whether they are currently shipping any parts).<br>
3. For each supplier currently shipping parts, print the total number of parts (i.e. `sum of qty`) it has shipped.<br>
4. Print all information of the part(s) with the highest weight.<br>
5. Print all information of the part(s) that doesn’t have the lowest weight.<br>
6. Print supplier numbers for suppliers who are located in the same city as supplier S1. Do not include S1 in the answer.<br>
7. Print supplier numbers for suppliers who ship at least all those parts shipped by supplier S3. Do not include S3 in the answer(And do not use `COUNT()`).<br>
8. Print supplier numbers for suppliers who ship at least one type of red part.<br>
9. Print supplier numbers for suppliers who do not ship any red parts.<br>
10. Print supplier numbers for suppliers who ship ONLY red parts.<br>
11. Print supplier names for suppliers who do not currently ship any parts.<br>
12. Print supplier names for suppliers who ship at least one part that is also shipped by supplier S2. Do not include S2 in the answer.<br>
13. Print supplier numbers for suppliers with status value less than the current average status value of all suppliers.<br>
14. Print all the shipment information for the shipment(s) with the highest unit cost (i.e. `price`).<br>
15. Print all the shipment information for the shipment(s) with the highest total cost, (i.e. `price*Qty`).<br>
16. Print all the supplier information for the supplier(s)making the most money. The supplier money is determined by the sum of all shipment cost. Each shipment cost is found by the number of units being shipped times the price per unit.<br>
17. For each supplier (including the one who doesn’t ship any parts), print the supplier number and how many different parts shipped. For example, S1 6; S2 2, ...<br>
18. For each supplier (including the one who doesn’t ship any parts), print the supplier number, supplier name, total cost of all shipments, and how many different parts shipped.<br>
 
# Step 2: Save your queries in a file, name it as CSCI360_Homework5_JohnDoe(0123456).sql
+ Note: 
  - Place comments before each query(use “--” (double minus) to comment one line), e.g.:
  ~~~~
  -- 1. Print part numbers for all parts shipped by more than one supplier.
  your query here
  ~~~~
  - 100 points as long as you get 15 correct answers.
  - bonus: 5 points for one more correct answer.
# Step 3: Submit your work on [Blackboard](https://blackboard.sau.edu/webapps/login/)
