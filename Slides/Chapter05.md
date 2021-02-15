# CSCI 360 Spring 2021
# Chapter 5: Basic SQL
+ SQL is the only database language in widespread use.
  - It was first proposed in the early 1970s.
  - The latest standard is SQL-2003.
  - MySQL supports most of the features of SQL-1992 and many from the newer SQL standards, but it also includes many non- standard features that give more control over the database server and how it evaluates queries and returns results.
+ Objectives
  - **SELECT** to read
  - **INSERT** to add
  - **UPDATE** to change
  - **DELETE** to remove
## Use the **music** database
+ You need to understand the batch mode example we leart in [Chapters 1, 2, and 3](../Slides/Chapter010203.md) to create the **music** database
+ It is also very important to understand the ER model of the **music** database in [Chapter 4](../Slides/Chapter04.md)
+ It is also very important to understand the ER model of the **music** database in [Chapter 4](../Slides/Chapter04.md)

![music er model](../Resources/4-music.png)
    

    
+ Start the MySQL Monitor and choose the **music** database, and you can check that this is the active database by typing in the SELECT DATABASE( );
  
![5usemusic](../Resources/5-usemusic.png)

+ explore what tables make up the music database

![shwotables](../Resources/5-showtables.png)

+ explore the columns in a table

![showcolumns](../Resources/5-showcolumns.png)

  - You can try to show the columns of the other tables.
  - To have a better understanding of the results, you can compare the results of the **SHOW COLUMNS FROM** with the ER model and the code.
  
    
# The SELECT Statement and Basic Querying Techniques
## Single Table SELECTs

![select1](../Resources/5-select1.png)

+ A simple SELECT statement has four components:
  - The keyword SELECT.
  - The columns to be displayed. In our first example, we asked for all columns by using the asterisk (*) symbol as a wildcard character.
  - The keyword FROM.
  - The table name; in this example, the table name is artist.
## Choosing Columns
+ Choose one column

![select2](../Resources/5-select2.png)

+ Choose more than one columns and display in order

![select3](../Resources/5-select3.png)

+ You can even list columns more than once, this is useful when combined with aliases in more advanced queries in [Chapter 7](../Slides/Chapter07.md)

![select4](../Resources/5-select4.png)

+ Specify databases, tables, and column names in a SELECT statement
  - to avoid the USE command
  - to helps resolve ambiguities, as we show later in “Joining Two Tables”

![select5](../Resources/5-select5.png)





## Choosing Rows with the WHERE Clause
### WHERE basics
+ Used to return rows that match a condition
+ Example
  - find out the details of the artist with the name “New Order.”

  ![where1](../Resources/5-where1.png)
  
  - find out the name of the artist with an artist_id value of 4.
  
  ![where2](../Resources/5-where2.png)
  
  - more where conditions
  
  ~~~~
  SELECT track_name FROM track WHERE track_id = 13;
  SELECT artist_name FROM artist WHERE artist_id < 5;
  SELECT album_name FROM album WHERE album_id <> 2;
  ~~~~

+ Operators
  - equals (=)
  - greater than (>)
  - less than (<)
  - less than or equal (<=)
  - greater than or equal (>=)
  - not equal (<> or !=)
+ Note: you can us the operators both for numbers and strings.

~~~~
SELECT artist_name FROM artist WHERE artist_name < 'M';
~~~~

+ String match/wild cards
  - percentage character (%): zero or more characters
  
  ![like](../Resources/5-like.png)
  
  - underscore character (\_): exactly one character
    + Note that there are two underscores and one spacebar in the following example.

  ![like2](../Resources/5-lik2.png)



### Combining conditions with AND, OR, NOT, and XOR

~~~~
SELECT album_name FROM album WHERE album_name > "C" AND album_name < "M";

SELECT album_name FROM album WHERE album_name LIKE "L%" OR album_name LIKE "S%" OR album_name LIKE "P%";
~~~~
~~~~
SELECT album_name FROM album WHERE album_name LIKE "L%" OR album_name LIKE "S%" AND album_name LIKE "%g";

SELECT album_name FROM album WHERE album_name LIKE "L%" OR (album_name LIKE "S%" AND album_name LIKE "%g");

SELECT album_name FROM album WHERE (album_name LIKE "L%" OR album_name LIKE "S%") AND album_name LIKE "%g";
~~~~
~~~~
SELECT * FROM album WHERE NOT (album_id = 1 OR album_id = 3);

SELECT * FROM album WHERE NOT (album_id = 1) AND NOT (album_id = 3);

SELECT * FROM album WHERE album_id != 1 AND album_id != 3;

SELECT * FROM album WHERE album_id != 1 AND NOT (album_id = 3);
~~~~
## ORDER BY Clauses
## The LIMIT Clause
## Joining Two Tables
# The INSERT Statement

# The DELETE Statement

# The UPDATE Statement
