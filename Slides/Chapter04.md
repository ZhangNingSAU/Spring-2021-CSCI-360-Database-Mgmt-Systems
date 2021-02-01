# CSCI 360 Spring 2021
# Chapter 4: Modeling and Designing Databases
# How NOT to develop a database
+ Q: quick design vs. good design
+ Example:
  - Version 1
  
  |GivenNames|Surname|CourseName|Pctg|
  |---|---|---|---|
  |John Paul|Bloggs|Web Database Applications|72|
  |Sarah|Doe|Programming 1|87|
  |John Paul|Bloggs|Computing Mathematics|43|
  |John Paul|Bloggs|Computing Mathematics|65|
  |Sarah|Doe|Web Database Applications|65|
  |Susan|Smith|Computing Mathematics|75|
  |Susan|Smith|Programming 1|55|
  |Susan|Smith|Computing Mathematics|80|
  
    + Problem: students with the same name
    + Solution: unique ID
  
  - Version 2
  
  |StudentId|GivenNames|Surname|CourseName|Pctg|
  |---|---|---|---|---|
  |12345678|John Paul|Bloggs|Web Database Applications|72|
  |12345121|Sarah|Doe|Programming 1|87|
  |12345678|John Paul|Bloggs|Computing Mathematics|43|
  |12345678|John Paul|Bloggs|Computing Mathematics|65|
  |12345121|Sarah|Doe|Web Database Applications|65|
  |12345876|Susan|Smith|Computing Mathematics|75|
  |12345876|Susan|Smith|Programming 1|55|
  |12345303|Susan|Smith|Computing Mathematics|80|
  
    + Problem: no order
    + Solution: more column(s)
    
  - Version 3
  
  |StudentId|GivenNames|Surname|CourseName|Year|Sem|Pctg|
  |---|---|---|---|---|---|---|
  |12345678|John Paul|Bloggs|Web Database Applications|2004|2|72|
  |12345121|Sarah|Doe|Programming 1|2006|1|87|
  |12345678|John Paul|Bloggs|Computing Mathematics|2005|2|43|
  |12345678|John Paul|Bloggs|Computing Mathematics|2006|1|65|
  |12345121|Sarah|Doe|Web Database Applications|2006|1|65|
  |12345876|Susan|Smith|Computing Mathematics|2005|1|75|
  |12345876|Susan|Smith|Programming 1|2005|2|55|
  |12345303|Susan|Smith|Computing Mathematics|2006|1|80|
  
    + Problem: bloated
    + Solution: split up the information
  - Version 4
  
  |StudentId|GivenNames|Surname|
  |---|---|---|
  |12345678|John Paul|Bloggs|
  |12345121|Sarah|Doe|
  |12345876|Susan|Smith|
  |12345303|Susan|Smith|
  
  |StudentId|CourseName|Year|Sem|Pctg|
  |---|---|---|---|---|
  |12345678|Web Database Applications|2004|2|72|
  |12345121|Programming 1|2006|1|87|
  |12345678|Computing Mathematics|2005|2|43|
  |12345678|Computing Mathematics|2006|1|65|
  |12345121|Web Database Applications|2006|1|65|
  |12345876|Computing Mathematics|2005|1|75|
  |12345876|Programming 1|2005|2|55|
  |12345303|Computing Mathematics|2006|1|80|
  
    + Problem: other information?
    + Solution: keep adding more columns or tables
  
# The Database Design Process
+ three major stages in database design
  - Requirements analysis
    + what exactly the database is needed for
    + what data will be stored
    + how the data items relate to each other
  - Conceptual design
    + distill requirements into a formal description of the database design
  - Logical design
    + map the database design onto an actual database management system and database tables
# The Entity Relationship Model
+ A model which can help transform the requirements into a formal description of the entities and relationships that appear in the database.
+ Entities
  - distinct objects
+ Relationships
  - associations between these entities
+ Example:
  - Database: University
  - Entities: Student and Course
  - Relationship: Enrollment
## Representing Entities
## Representing Relationships
## Partial and Total Participation
## Entity or Attribute?
## Entity or Relationship?
## Intermediate Entities
## Weak and Strong Entities
# Entity Relationship Modeling Examples
# Using the Entity Relationship Model
## Using Tools for Database Design
+ MySQL Workbench
  - [Download MySQL Workbench](https://dev.mysql.com/downloads/workbench/)
    + If you need to use an older version, click on the **Archive** tab.
  - [How To Connect To MySQL Server After Install XAMPP On Mac OS](https://www.dev2qa.com/how-to-connect-to-mysql-server-after-install-xampp-on-mac-os/#:~:text=After%20download%20XAMPP%20mac%20os,and%20ftp%20server%20as%20service.)
  -[create a new user](https://stackoverflow.com/questions/1559955/host-xxx-xx-xxx-xxx-is-not-allowed-to-connect-to-this-mysql-server)

