# databasetask
# Introduction
## SCHEMAS
### Majors(Major,Advisor)
## SQLQUERY:
~~~
CREATE TABLE Majors (
Major VARCHAR(50) PRIMARY KEY,
Advisor VARCHAR(100) NOT NULL
);
~~~
## Table Description
~~~
describe Majors;
~~~
## Result
~~~
+---------+--------------+------+-----+---------+-------+
| Field   | Type         | Null | Key | Default | Extra |
+---------+--------------+------+-----+---------+-------+
| Major   | varchar(50)  | NO   | PRI | NULL    |       |
| Advisor | varchar(100) | NO   |     | NULL    |       |
+---------+--------------+------+-----+---------+-------+
~~~
