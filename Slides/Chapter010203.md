# CSCI 360 Spring 2021
# Dr. Ning Zhang
# Chapters 1,2,3 MySQL Introduction

# Objectives:
+ Learn the basics of MySQL
+ Learn the installation of MySQL(XAMPP)
+ Learn how to use XAMPP and MySQL monitor

# 1. Basics of MySQL
## What is MySQL
+ pronounced “My Ess Cue Ell”
+ **“the world’s most popular open source database,”** as the developers at the [MySQL AB corporation](http://www.mysql.com) claim
+ modest-sized database
+ MySQL is a relatively recent entrant into the well-established area of **relational database management systems (RDBMs)**
+ Structured Query Language (SQL)
  - insert, retrieve, and manipulate data.
+ We can interact with the database using the PHP and Perl programming languages, and allows interaction with your data over the medium most people prefer these days: the Web.
  
## Why Is MySQL so Popular?
+ The MySQL development process focuses on offering a very efficient implementation of the features most people need. 
  - This means that MySQL still has fewer features than its chief open source competitor, PostgreSQL, or the commercial database engines.
  - The skills you get from this book will serve you well on any platform.
  - MySQL HAS been the choice for so many beginners and small sites, and now for some heavyweight database users in government and industry.
+ Factors
  - Size and speed
  - Ease of installation
  - Attention to standards
  - Responsiveness to community
  - Easy interface to other software


## Elements of MySQL and Its Environment
+ A MySQL installation has two components: 
  - a server that manages the data
  - clients that ask the server to do things with the data
    + MySQL monitor program that allows you to connect to a MySQL server and run SQL queries.
    + mysqladmin program that allows you to perform various server administration tasks.
    + any program that knows how to talk to the MySQL server is a client (a program for a web-based shopping site or an application to generate sales graphs for a marketing team can both be clients).
      - web server vs. database server
        ![web server vs. database server](https://docs.oracle.com/cd/E24150_01/pt851h2/eng/psbooks/tsvt/img/gv_DistinctTiersOfArchitectureStartingWithDatabaseMovingToApplicati_tsvt7fff.png)
  
+ Four aspects of using MySQL
  - MySQL server
  - SQL
    + core of MySQL use
  - Programming languages
    + a general-purpose programming language such as PHP or Perl to automatically create and execute SQL queries on the MySQL server.
  - Web database applications
    + you can use PHP or Perl to create dynamic, database-driven web applications that can publish information from the database to the Web, and capture information provided by users.

## The LAMP Platform
+ Linux operating system
+ Apache web server
+ MySQL database management system
+ Perl or PHP scripting language.

## Structured Query Language


# 2. Installation of MySQL
+ On textbook "Learning MySQL", Chapter 2 introduces the installation of the LAMP platform in details.
+ In our class, we use the XAMPP application.
  - [XAMPP Tutorial](XAMPP%20Tutorial.md)

# 3. Using the MySQL Monitor
+  client-server architecture
  - clients connect to the server to perform database operations
  
  ![client-server architecture](https://www.oreilly.com/library/view/access-database-design/1565926269/tagoreillycom20070221oreillyimages86579.png)
  
+ The standard MySQL command-line client or “monitor” program provided by MySQL AB is the client you’ll probably use the most often.
  - The monitor allows you to control almost all aspects of database creation and maintenance using SQL and the custom MySQL extensions to SQL.

## Starting the Monitor
+ The monitor program is called simply mysql and is found in a directory with the other MySQL programs. 
  - The exact location depends on your operating system and how you chose to install MySQL
    + you can locate the promgram from XAMPP directly
  
  ![](../Resources/xamppwin.png)
  
  ![](../Resources/xamppmac.png)
  
  ![](../Resources/1.startterminal.png)
  
  - from the command line, you type
    ~~~~
    mysql --user=root
    ~~~~
    
    ![](../Resources/1.startmysql.png)
    
    + Note: I am using MAC, the mysql program may look different on Windows, but all the commands we use in this class will be the same.
    + Note: The default password is NULL, if you have set up a password, you need to use the following command
    ~~~~
    mysql --user=root --password=the_mysql_root_password
    ~~~~
## Stoping the Monitor

~~~~
exit;
~~~~

![](../Resources/1.stopmonitor.png)

## Commands
+ version of MySQL
~~~~
SELECT VERSION();
~~~~

+ Note: Do NOT miss the ;

![](../Resources/1.selectversion.png)


+ list all the databases 

~~~~
SHOW DATABASES;
~~~~
  
![](../Resources/1.showdatabases.png)

## Style, Case, and Semicolons
+ A command-line command is a combination of 
  - SQL keywords
  - MySQL proprietary commands
  - names of databases and database components
+ A command-line command is Not case-sensitive
  - e.g.: **show databases** is equivalent to **SHOW DATABASE**
+ A command-line command follows conventions for better readibility.
  - SQL keywords and MySQL proprietary commands are **UPPPERCASE**.
  - names of databases and database components are **lowercase**.
+ A command-line command ends with the semicolon character (;).

~~~~
SELECT User, Host
FROM user;
~~~~

## The Monitor HELP 
+ **HELP** lists commands the monitor understands.

![](../Resources/1.help.png)

+ **HELP Contents** gets help on how to interact with the MySQL server. 

![](../Resources/1.helpcontents.png)

+ **HELP Data Manipulation**  gets information on data manipulation

![](../Resources/1.helpdatamanipulation.png)

+ **HELP SHOW DATABASES** gets information on SHOW DATABASES command

![](../Resources/1.helpshowdatabases.png)

## Running the Monitor in Batch Mode
+ run the following commands in interactive mode
~~~~
use mysql;
SELECT COUNT(*) FROM user;
~~~~

![](../Resources/1.batch1.png)

+ run the commands in batch mode
  - save the commands in a file with extension sql, e.g., count_users.sql
  - run the file using the followng command
  ~~~~
  SOURCE count_users.sql
  ~~~~
    + Note: 
      - If you do NOT use XAMPP, you need to specify the full path of the sql file if it is not in the current directory. The current directory is the directory when you open the terminal(MAC) or shell(windows). On my Mac, I created the file on the desktop, so the full path is "~/Desktop/count_users.sql". If you use Windows, the full path may look like "C:\folder_name\count_users.sql".
      - In our class, we use XAMPP, so if you want to execute the file, create/put it in the following folder.
    
      ![](../Resources/1.htdocs.png)
    
      - To find the folder, click **Explore**
    
      ![](../Resources/1.explore.png)
    
  - run the file using its full path
  
  ![](../Resources/1.batch2.png)
  
