---
title: NoSQL
enableToc: true
tags:
  - Database
---
# What is NoSQL
SQL databases store related data in tables and rows. Each row in the table represents a different record. The table columns are rigid and have defined types, e.g a name column would store Strings and you would not be able to insert a number. This is referred to as a table schema. 

NoSQL databases have an equivalent to tables called collections. Each collection is filled with documents. Documents are JSON documents which have a field-value store. The benefit for this is that the document is schema-less, fields do not have any specific type and there are no guarantees that a field exists which is more flexible.

For an SQL database it is impossible to add data until you define tables, field types and relations (schema). You will need to design and implement this schema before any business logic can be created. Changing the schema later on is possible but it can be complicated depending on the changes and the number of records that need to be changed. Since a NoSQL database is schema-less, data can be added anywhere at any time.
For example, a table of Users in SQL might be represented something like this

| id (number) | name (string) | lastName (string) | email (string)  |
| ----------- | ------------- | ----------------- | --------------- |
| 1           | Aaron         | A                 | Aaron@email.com |
The same information in NoSQL might look like this
```json
{
	id: 1,
	name: "Aaron",
	lastname: "A",
	email: "Aaron@email.com"
}
```

If we get new requirements that say we need to also collect a users date of birth and middle name we would need to change the entire table before we can work on features related to the new requirements.

| id (number) | name (string) | middleName (string) | lastName (string) | email (string)  | DOB (string) |
| ----------- | ------------- | ------------------- | ----------------- | --------------- | ------------ |
| 1           | Aaron         | *null*              | A                 | Aaron@email.com | *null*       |
| 2           | Bill          | Will                | Mill              | bill@email.com  | 01/02/1999   |

Meanwhile for NoSQL we can just start incorporating the new requirements straight away,
```json
{
	id: 1,
	name: "Aaron",
	lastname: "A",
	email: "Aaron@email.com"
},
{
	id: 2,
	name: "Bill",
	middleName: "Will",
	lastname: "Mill",
	email: "bill@email.com",
	DOB: "01/02/1999"
}
```

# Normalisation and Denormalisation
Database normalisation is the process of organising data in the database to reduce data redundancy and improve data integrity. For example if we have some User table and a Company table with denormalised data,

**User Table**

| id  | name  | company  | companyPhone |
| --- | ----- | -------- | ------------ |
| 1   | Aaron | Facebook | 0123456789   |
| 2   | Bill  | Facebook | 0123456789   |
| 3   | Carl  | Google   | 9876543210   |

If Facebook wanted to change their name to Meta and their phone number then they would need to scan every record with the company Facebook and change the name and phone number. This is what is meant by redundant data as the same information is just repeated for each record.

We can move this information to another table and just store a reference to the information in the new table to minimise data redundancy. We can just update company data without changing user data. 
**Company Table**

| company_id | company | companyPhone |
| ---------- | ------- | ------------ |
| F1         | Meta    | 0123123123   |
| G2         | Google  | 9876543210   |
**User Table**

| id  | name  | company_id (FK) |
| --- | ----- | --------------- |
| 1   | Aaron | F1              |
| 2   | Bill  | F1              |
| 3   | Carl  | G2              |
In SQL we can use a **JOIN** clause in order to obtain related data in multiple tables. NoSQL does not have an equivalent, if NoSQL data was normalised then we would need to fetch all Company documents and all User Documents and manually link the two in program logic. Therefore NoSQL data is usually denormalised.

# Data Integrity
SQL databases have schemas to enforce data integrity, you can think of data integrity as the assumptions we make to consider our data valid. For the previous tables we could have the rules 
- Ensure all users have a company_id
- Cannot remove companies if there are users assigned to them
An SQL database will not allow operations that could result in invalid data.

In NoSQL databases, the database does not enforce any rules.

# Transaction
In SQL databases we can execute two or more updates in a single operation referred to as a transaction. A transaction guarantees that either both updates succeed or fail. 

For example, an online store if a user buys an item we create an order id as proof of purchase and then we need to decrement the amount of stock we have. If the user was provided with a proof of purchase and the stock amount was not decremented then the amount of stock in the system is now inaccurate. SQL transactions prevent this from occurring.

In NoSQL databases, modification of a ***single document*** is atomic, if you are updating multiple fields in a document then all fields are updated or it is unchanged. However there are no transaction equivalents for ***multiple documents***.

# Performance
NoSQL is quoted as being faster than SQL, as NoSQL has denormalised data it is faster to retrieve all necessary information about a specific item in a single document request. However if data needed isn't contained in one document then SQL JOINS will be faster. This performance really depends on how the data is structured and how it is being queried.

Since all the data is also contained on a single document it is fast to insert as well. If we had a table called user which has a lot of relations we may need to insert data into all related tables which can make writes slower.

# When to use NoSQL
**Advantages**
- Fast insertion and reads as all data is contained in a blob* ([Depends on design/query](#performance))
- Schema-less
- NoSQL databases are convenient for scale, [[notes/Database Scaling#Database Sharding|Database Scaling]] is much easier as data is self contained on each document. 
- Built for metrics/aggregations. Common use in logging. 

**Disadvantages**
- ACID is not guaranteed (consistency). Not suitable for  transactions
- Not read optimised, read times are slower compared to SQL. If you want to read the 'date of birth' field for each user then you would need to read entirety of every user document and check if a date of birth field exists as NoSQL is schema-less. SQL can just read the specific column and ignore the other data fields.
- Joins are hard because no relations

**Projects where SQL is ideal**
- Logical related and discrete data requirements which can be identified up-front
	- Schema can be difficult to alter later on, especially at scale
- Data Integrity is essential
	- Anything where a transaction may occur.
-
**Projects where NoSQL is ideal**
- non-relational, indeterminate or constantly evolving data requirements
- Speed and scalability is imperative
- Simpler or looser objectives, flexibility. 
# References
- [SQL vs NoSQL differences](https://www.sitepoint.com/sql-vs-nosql-differences/)
- [Introduction to NoSQL](https://www.youtube.com/watch?v=xQnIN9bW0og)