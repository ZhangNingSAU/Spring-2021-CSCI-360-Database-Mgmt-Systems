# CSCI360 Spring 2021
# Chapter 6 Working with Database Structures
+ Objectives: dealing with **METADATA**
  - create database
  - create tables, including columns
  - alter structures
  - delete structures
# Creating and Using Databases
+ Syntax
~~~~
CREATE DATABASE database_name;
~~~~

+ Example(Assume the music database has not been created)

![cd1](../Resources/6-cd1.png)

+ If the dabases has already existed, the statement above yields an error.

![cd2](../Resources/6-cd2.png)

+ So we revise the syntax to avoid such error.

~~~~
CREATE DATABASE IF NOT EXISTS database_name;
~~~~


![cd3](../Resources/6-cd3.png)

+ Conventions and Restrictions
  - use lowercase names for databases to make your SQL machine-independent
    + case-sensitive in Mac OS and Linux
    + case-insensitive in Windows
  - max lenght: 64 characters
  - don't use reserved words (SELECT, FROM, USE...)
  - don't use special characters(slash, back slash, semicolon, period)
  - don't use whitespace as the last character for a database name
  
  ~~~~
  CREATE DATABASE IF NOT EXISTS mus;ic
  -- CREATE DATABASE IF NOT EXISTS mus; is a vailid statement, database mus will be created
  -- ic is not a valid statement, it yields one error.
  ~~~~
# Creating Tables
## Basics
## Collation and Character Sets
## Other Features

## Column Types
### Common column types
### Other integer types
### Other rational number types
### Other date and time types
### Other string types

## Keys and Indexes
## The AUTO_INCREMENT Feature
## The Sample Music Database

# Altering Structures
## Adding, Removing, and Changing Columns
## Adding, Removing, and Changing Indexes
## Renaming Tables and Altering Other Structures

# Deleting Structures
## Dropping Databases
## Removing Tables
