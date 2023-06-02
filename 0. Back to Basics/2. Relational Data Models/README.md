## Importance of Relational Databases:
---
* Standardization of data model: Once your data is transformed into the rows and columns format, your data is standardized and you can query it with SQL
* Flexibility in adding and altering tables: Relational databases gives you flexibility to add tables, alter tables, add and remove data.
* Data Integrity: Data Integrity is the backbone of using a relational database.
* Structured Query Language (SQL): A standard language can be used to access the data with a predefined language.
* Simplicity : Data is systematically stored and modeled in tabular format.
* Intuitive Organization: The spreadsheet format is intuitive but intuitive to data modeling in relational databases.

## OLAP vs OLTP:
---
* Online Analytical Processing (OLAP):
Databases optimized for these workloads allow for complex analytical and ad hoc queries, including aggregations. These type of databases are optimized for reads.

* Online Transactional Processing (OLTP):
Databases optimized for these workloads allow for less complex queries in large volume. The types of queries for these databases are read, insert, update, and delete.

* The key to remember the difference between OLAP and OLTP is analytics (A) vs transactions (T). If you want to get the price of a shoe then you are using OLTP (this has very little or no aggregations). If you want to know the total stock of shoes a particular store sold, then this requires using OLAP (since this will require aggregations).

Read more: https://medium.com/t%C3%BCrk-telekom-bulut-teknolojileri/whats-the-difference-between-oltp-and-olap-bdcafdffb1c3

|Online-transactional processing (OLTP)   | Online Analytical Processing (OLAP)  |
| ------------ | ------------ |
|OLTP databases enable normalization in tables.   |OLAP databases do not allow normalization in tables.   |
|OLTP supports the traditional database management systems approach.  |OLAP supports the data warehouse approach.   |
|OLTP has a response time of milliseconds.   |OLAP has a response time of seconds to minutes.   |
| OLTP databases comprise several quick online transactions.  |OLAP databases comprise large data volumes.   |
|OLTP is a real-time transaction processing system.   | OLAP is a database that allows you to analyze business metrics by category and attribute.  |

## Normal Forms:

Database normalization entails organizing a database into several tables in order to reduce redundancy.
---
### Objectives:
1. To free the database from unwanted insertions, updates, & deletion dependencies
2. To reduce the need for refactoring the database as new types of data are introduced
3. To make the relational model more informative to users
4. To make the database neutral to the query statistics

Read more: https://www.freecodecamp.org/news/database-normalization-1nf-2nf-3nf-table-examples/

### Types of Normal Forms:
#### First Normal Form (1NF):
* Atomic values: each cell contains unique and single values
* Be able to add data without altering tables
* Separate different relations into different tables
* Keep relationships between tables together with foreign keys

#### Second Normal Form (2NF):
* Have reached 1NF
* All columns in the table must rely on the Primary Key

#### Third Normal Form (3NF):
* Must be in 2nd Normal Form
* No transitive dependencies
* Remember, transitive dependencies you are trying to maintain is that to get from A-> C, you want to avoid going through B.

When to use 3NF:
When you want to update data, we want to be able to do in just 1 place.

## Denormalization:
---
JOINS on the database allow for outstanding flexibility but are extremely slow. If you are dealing with heavy reads on your database, you may want to think about denormalizing your tables. You get your data into normalized form, and then you proceed with denormalization. So, denormalization comes after normalization.

## Normalize vs Denormalize:
---
Normalization is about trying to increase data integrity by reducing the number of copies of the data. Data that needs to be added or updated will be done in as few places as possible.

Denormalization is trying to increase performance by reducing the number of joins between tables (as joins can be slow). Data integrity will take a bit of a potential hit, as there will be more copies of the data (to reduce JOINS).

Read more: https://medium.com/analytics-vidhya/database-normalization-vs-denormalization-a42d211dd891#:~:text=Normalization%20is%20the%20technique%20of,to%20make%20data%20retrieval%20faster.

## Star Schema:
---
* Simplest style of data mart schema
* Consist of 1 or more fact tables referencing multiple dimension tables

### Benefits:
* Denormalize tables, simplify queries and provide fast aggregations

### Drawbacks:
* Issues that come with denormalization
* Data Integrity
* Decrease Query Flexibility
* Many to many relationship -- simplified

## Snowflake Schema:
---
* Logical arrangement of tables in a multidimensional database
* Represented by centralized fact tables that are connected to multiple dimensions
* Dimensions of snowflake schema are elaborated, having multiple levels of relationships, child tables having multiple parents
* Star schema is a special, simplified case of snowflake schema
* Star schema does not allow for one to many relationships while snowflake schema does

Read more: https://www.guru99.com/star-snowflake-data-warehousing.html

## Fact vs Dimension Table
---
|Fact Table   |Dimension Table   |
| ------------ | ------------ |
| A fact table stores the measurements together with the properties of dimension tables.  | The qualities along which the fact table calculates the metric are stored in the dimension tables.  |
|There are fewer attributes in a fact table, but there are more records.   |The dimension table has fewer records and more attributes.   |
|The primary key of a fact table is a concatenation of the primary keys of all dimension tables.   | Dimension tables have individual primary keys.  |
| You can create fact tables only when a dimension table is complete.  |You must create dimension tables first, i.e., before fact tables.   |
| There are fewer fact tables in a schema.  | There are more dimension tables in a schema.  |
| The data in a fact table can be numerical or textual.  | A dimension table always has textual attributes only.  |