# How to write a query for Q7 in HW5?
# Method 1: no aggregate funtion Count()
+ then, we need to understand one concept we did not cover in our class
## DIVISION
+ DIVISION Operation, denoted by (÷)
  - The division operation is applied to two tables R and S, denoted by R(Z) ÷ S(X) where
    + Z is the set of columns of R
    + X is the set of columns of S
    + X is a subset of Z
    + Let Y be the set of columns of R that are not attributes of S, i.e, Y = Z - X
  - The result of DIVISION is a table T(Y) that includes a row t if row t<sub>R</sub> appear in R with t<sub>R</sub>[Y] = t, and with t<sub>R</sub>[X] = t<sub>S</sub> for every tuple t<sub>S</sub> in S.
  - For a row t to appear in the result T of the DIVISION, the values in t must appear in R in combination with every row in S.
  - DIVISION Examples
  
  ![division](../Resources/division1.png)
  
  
  ![division2](../Resources/division2.png)

+ Now, let's take a look at Q7 in HW5: Print supplier numbers for suppliers who ship at least all those parts shipped by supplier s3. Do not include s3 in the answer(And do not use `COUNT()`).

shipment

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

+ Let's change it into a DIVISION problem. 

![division3](../Resources/divsion3.png)

+ The next step should be how we can get the two tables.
  - table R
  ~~~~
  SELECT Sno, Pno FROM shipment Where Sno != 's3';
  ~~~~
  - table S
  ~~~~
  SELECT Pno FROM shipment WHERE Sno = 's3';
  ~~~~
+ The last step is the DIVISION in MySQL
## DIVISION of Two Queries
+ DIVISION is not part of the SQL standard. Most RDBMSs don’t provide such operator.
+ However, DIVISION can be achieved by using `NOT EXISTS` and `NOT IN`.

~~~~
SELECT DISTINCT Sno
FROM (SELECT Sno, Pno FROM shipment Where Sno != 's3') AS R
WHERE NOT EXISTS(
                 SELECT Pno
                 FROM shipment
                 WHERE Sno='s3' AND
                 Pno NOT IN(
                 SELECT Pno
                 FROM shipment
                 WHERE Sno = R.Sno)
                 );
~~~~
+ Since R and S come from the same table, we can do it in another way
~~~~
SELECT DISTINCT Sno
FROM shipment AS S1
WHERE NOT EXISTS(
                 SELECT Pno
                 FROM shipment
                 WHERE Sno='s3' AND
                 Pno NOT IN(
                 SELECT Pno
                 FROM shipment
                 WHERE Sno = S1.Sno)
                 )
      AND Sno != 's3';
~~~~
+ More examples for [DIVISION](https://www.red-gate.com/simple-talk/sql/t-sql-programming/divided-we-stand-the-sql-of-relational-division/)

# Method 2: using COUNT() function
~~~
SELECT Sno from 
(SELECT S1.Sno,S1.Pno from shipment S1 inner join shipment S2 USING (Pno) WHERE S2.Sno='s3') AS temp
GROUP BY Sno
HAVING COUNT(Pno) = (SELECT COUNT(Pno) FROM shipment Group by Sno Having Sno='s3' )
AND Sno !='s3';
~~~

or

~~~
SELECT Sno from 
(SELECT S1.Sno,S1.Pno from shipment S1 inner join shipment S2 USING (Pno) WHERE S2.Sno='s3' AND S1.Sno!='s3') AS temp
GROUP BY Sno
HAVING COUNT(Pno) = (SELECT COUNT(Pno) FROM shipment Group by Sno Having Sno='s3');
~~~

+ Let's analyze the second statement a little bit:
  - `SELECT S1.Sno,S1.Pno from shipment S1 inner join shipment S2 USING (Pno) WHERE S2.Sno='s3' AND S1.Sno!='s3'` gives us other suppliers who ship at least one part shipped by s3.
  
  |Sno|Pno|
  |---|---|
  |s1|p2|
  |s2|p2|
  |s4|p2|
  |s1|p3|
  |s4|p3|
  
 - `SELECT COUNT(Pno) FROM shipment Group by Sno Having Sno='s3'` give us the number of parts shipped by s3.
 
 |Count(Pno)|
 |---|
 |2|
 
 - the whole statement will find out Sno who ships at least one part shipped by s3 and who ships at least the same number of different parts. If we combine thest two conditions together, we can find out the information we need: other suppliers who ships at least the parts shipped by s3.
 - Note: we can write the query in this way because (Sno,Pno) is the primary key in shipment, so the values of (Sno, Pno) are unique. Suppose the values of (Sno, Pno) could be NOT unique, then we may have a result by  `SELECT S1.Sno,S1.Pno from shipment S1 inner join shipment S2 USING (Pno) WHERE S2.Sno='s3' AND S1.Sno!='s3'` like the following table, then s1 will not be included in the final result. To deal with situation like this, you need to SELECT all the columns contains in the primary key to avoid duplicates.
  |Sno|Pno|
  |---|---|
  |s1|p2|
  |s1|p2|
  |s2|p2|
  |s4|p2|
  |s1|p3|
  |s4|p3|
  
