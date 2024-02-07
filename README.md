# Postgresql Cheatsheet
## Introduction
- [X] Table Create / Drop
  * [X] Create Table
  * [X] Drop Table
  * [X] Truncate
- [X] CRUD
  * [X] Create
  * [X] Read
    * [X] Read All
    * [X] Read Spesific Column
    * [X] Where
    * [X] Where with Or/And operators
    * [X] Order by
    * [X] Like / Not Like
    * [X] Count
    * [X] Sum
    * [X] Avg
    * [X] Min / Max
    * [X] Group by
    * [X] Having
    * [X] SubQuery
    * [X] Inner Join
  * [X] Update
  * [X] Delete


## Table Create / Drop
**Create Table** <br /><br />
Without auto increment
```
Create Table customer
(
	id int Primary key not null,
	name Varchar(15),
	money int
)
```
With auto increment
```
Create Table customer
(
	id SERIAL Primary key not null,
	name Varchar(15),
	money int
)
```

**Drop Table**
```
Drop Table customer
```

**Reset Table**
```
Truncate table customer
```

## CRUD
**Create**
```
Insert into customer (name,money) values('test',123)
```

**Read**
* Read all
```
Select * from customer
```
* Read Spesific Column
```
Select name from customer
```
* Where
```
Select name from customer where id=2
```
* Where with Or/And operators
```
Select name from customer where name='test' and id=8 or name='ali' order by productID ASC
```
* Order by
```
Select name from customer where name='test' order by id ASC
```
* Like
```
Select name from customer where name like 'a%'
```
* Not Like
```
Select name from customer where name not like 'a%'
```
* Count
```
Select Count(*) from customer where name='test'
```
* Sum
```
Select sum(money) from customer
Select sum(money) from customer where money>=12345
```
* Avg
```
Select avg(money) from customer
Select avg(money) from customer where name='test'
```
* Min / Max
```
Select min(money), max(money) from customer
```
* Group by
```
select name,count(*) from customer group by name
select name,count(*) as amount from customer group by name
select name, sum(money) from customer group by name
select name, avg(money) from customer group by name
```
* Having
```
select name, count(*) as amount from customer group by name having count(*)>2
```
* SubQuery
```
select * from customer where money=(select max(money) from customer)
```
* Inner Join
```
select customer.name,job.name from customer inner join job on customer.job=job.id
```

**Update**
```
Update customer set name='newTestName' where id=1
```

**Delete**
```
Delete from customer where id=1
```

## Relational Tables
### Foreign Key
Basicly primary key is unique for tables but foreign keys connecting tables with other tables.
![example for foreign key]([https://myoctocat.com/assets/images/base-octocat.svg](https://www.programiz.com/sites/tutorial2program/files/foreign-key.png)https://www.programiz.com/sites/tutorial2program/files/foreign-key.png)
