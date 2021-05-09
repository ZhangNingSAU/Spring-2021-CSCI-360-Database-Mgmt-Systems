# CSCI360 Spring 2021
# Homework 7 for Chapter 9
# due: 11:59pm 05/04/2021

# In the following questions, we are going to use the `music` database in the textbook.
+ Q1: Can we use the following statements to retrieve the artist information? Why?

~~~~
-- log in as 'root'@'localhost' and execute the following statement
GRANT ALL ON music.track TO 'user1'@'localhost' IDENTIFIED BY 'the_password';
GRANT SELECT(album_id, album_name) ON music.album TO 'user1'@'localhost'
-- log in as 'user1'@'localhost' and execute the following statement
SELECT * FROM music.artist
~~~~

+ Q2: What is the previlidge level of `ON music.track`?
A. Global level<br>
B. Database level<br>
C. Table level<br>
D. Column level<br>

+ Q3. After creating `user1` in Q1, can we use the following statement to create a new user? Why?

~~~~
-- log in as 'user1'@'localhost' and execute the following statement
GRANT ALL ON music.track* TO 'user2'@'localhost' IDENTIFIED BY 'the_password';
~~~~

+ Q4. Which is **NOT** a local user?
A. `'user3'@'localhost'`<br>
B. `'user4'@'127.0.0.1'`<br>
C. `@'localhost'`<br>
D. `'user5'@'192.168.1.100'`<br>

+ Q5. Suppose there are four users in `mysql` database(listed in the following table), which user will be used when you try to establish a connection by using the following statemtn?

|user|
|----|
|'dave'@'localhost'|
|'dave'@'%'|
|'dave'@'192.168.1.100'|
|''@'localhost'|

~~~~
-- suppose '123456' is the password for all the users
mysql --user=dave --host='192.168.1.200' --password=123456
~~~~

A. `'dave'@'localhost'`<br>
B. `'dave'@'%'`<br>
C. `'dave'@'192.168.1.100'`<br>
D. `''@'localhost`<br>

+ Q6. After creating `user1` in Q1, can we use the following statements to retrieve the album information? Why?

~~~~~
-- log in as 'root'@'localhost' and execute the following statement
REVOKE SELECT (album_name) ON music.album FROM 'user1'@'localhost';
-- log in as 'user1'@'localhost' and execute the following statement
SELECT album_id, album_name FROM music.album
~~~~~

+ Q7. Which command does **NOT** need to use the `FLUSH PRIVILEGES` instruction to tell the server to read in the updated data(we log in as `'root'@'localhost'`).
A. `DROP USER user1`<br>
B. `DELETE FROM mysql.user WHERE user='user1'`<br>
C. `UPDATE mysql.user SET user='new_user' WHERE user='user1'`<br>
D. `SELECT user, host, password FROM mysql.user`<br>

+ Q8. We can use the following statment to change the password of the current user to `123456`.
~~~~
SET PASSWORD='123456';
~~~~
A. True<br>
B. False<br>

# Step 1: Save your answers in a PDF file, name it as CSCI360_Homework7_JohnDoe(0123456).pdf


# Step 2: Submit your work on [Blackboard](https://blackboard.sau.edu/webapps/login/)
