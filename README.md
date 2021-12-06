# Postgresql-exercises

**Q1)You will be given a table, numbers, with one column number.**
Return a table with a column is_even containing "Even" or "Odd" depending on number column values.
```
numbers table schema
number INT
output table schema
is_even STRING
```
**Q2)Write a select statement that takes name from person table and return "Hello,** 
<name> how are you doing today?" results in a column named greeting
```
SOLUTION
create table person 
(id bigserial not null primary key,
name varchar(50));
  
Insert into person (name)
values ('Mike')

SELECT 'Hello, ' || name || ' how are you doing today?'
AS greeting
FROM person;
```


**Q3) Messi goals function
Messi is a soccer player with goals in three leagues:**
```
LaLiga
Copa del Rey
Champions
Complete the function to return his total number of goals in all three leagues.
Note: the input will always be valid.

For example:

5, 10, 2  -->  17
```
**Solution**
```
CREATE FUNCTION total_messi_goals(laliga int, copa int, champions int)
RETURNS integer AS $$
begin 
	return laliga + copa + champions;
end
$$
LANGUAGE plpgsql;
  
select total_messi_goals(15, 8, 46);
```
**Q4)For this challenge you need to create a simple MIN / MAX statement that will return the Minimum and Maximum ages out of all the people.**
```
people table schema
id
name
age
select table schema
age_min (minimum of ages)
age_max (maximum of ages)  
```
**Solution**
```
CREATE TABLE people (id bigserial PRIMARY KEY, 
					 name varchar(50) NOT NULL, 
					 age bigint NOT NULL);
INSERT INTO people (name, age)
VALUES ('Aibek', 21 );
INSERT INTO people (name, age)
VALUES ('Sarah', 18 );
INSERT INTO people (name, age)
VALUES ('Don', 60 );
INSERT INTO people (name, age)
VALUES ('Tom', 42 );
INSERT INTO people (name, age)
VALUES ('Rose', 28 );


SELECT * from people;

SELECT min(age)
AS age_min,
max(age)
as age_max
from people;
```
