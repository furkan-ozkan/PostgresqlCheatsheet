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
  * [X] Update
  * [X] Delete
- [X] Relational Table
  * [X] Foreign Key
  * [X] Joins
  	* [X] Inner Join
  	* [X] Left Join
  	* [X] Right Join
  	* [X] Full Join
  	* [X] Cross Join
  * [X] Intersect and Except
  	* [X] Intersect
  	* [X] Except
  * [X] Union and Union All 
  	* [X] Union
  	* [X] Union All
- [X] String Functions 
  	* [X] ASCII
  	* [X] Concat
   	* [X] Left / Right
    * [X] Lenght
     * [x] Replace
	* [X] Reverse
      * [X] Substring
- [X] Math. Functions 
  	* [X] Abs
  	* [X] Ceil
  	* [X] Floor
  	* [X] Pi
  	* [X] Random
  	* [X] Round
  	* [X] Power
  	* [X] Log
  	* [X] Sign
  	* [X] Sqrt
- [X] Time Functions 
  	* [X] Current Date
  	* [X] Current Time
  	* [X] Now

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
![example for foreign key](https://www.programiz.com/sites/tutorial2program/files/foreign-key.png)

### Joins
* Inner Join
```
select customer.name,job.name from customer inner join job on customer.job=job.id
```
* Left Join
```
select customer.id,customer.name,job.name from customer left join job on job=job.id
```
* Right Join
```
select customer.id,customer.name,job.name from customer right join job on job=job.id
```
* Full Join
```
select customer.id,customer.name,job.name from customer full join job on job=job.id order by customer.id ASC
```
* Cross Join
```
select * from customer cross join job
```
### Intersect and Except
* Intersect
```
select id from customer intersect select id from job order by id ASC
```
* Except
```
select id from customer except select id from job order by id ASC
```
### Union and Union All
* Union
```
select id from customer union select id from job order by id ASC
```
* Union all
```
select id from customer union all select id from job order by id ASC
```
## String Functions
* ASCII
```
select ASCII ('A')
```
* Concat
```
select CONCAT(id,'_',name) from customer
```
* Left & Right
```
select left(name,2) from customer
select right(name,2) from customer
```
* Lenght
```
select lenght(name) from customer
```
* Replace
```
select replace(name,'i','k') from customer
```
* Reverse
```
select reverse(name) from customer
```
* Substring
```
select substring(name,2,2) from customer
```
## Math. Functions
* Abs
```
select abs(-5)
```
* Ceil
```
select ceiling(4.85)
```
* Floor
```
select floor(4.85)
```
* Pi
```
select pi()
```
* Random
```
select random()
```
* Round
```
select Round(18.1234,2)
```
* Power
```
select power(2,4)
```
* Log
```
select log(3,2)
```
* Sign
```
select sign(25)
select sign(-25)
select sign(0)
```
* Sqrt
```
select sqrt(625)
```

## Time Functions
* Current Date
```
select Current_Date
```
* Current Time
```
select Current_Time(0)
```
* Now
```
select now()
```
