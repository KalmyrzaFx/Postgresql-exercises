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
**Q5)For this challenge you need to create a simple SELECT statement that will return all columns from the people table WHERE their age is over 50**
people table schema<br>
id<br>
name<br>
age<br>
You should return all people fields where their age is over 50 and order by the age descending<br>
**Solution**
```
	SELECT * from people where age > 50 order by age DESC;
```
**Q6)You are working for a local school, and you are responsible for collecting tuition from students.** <br>
You have a list of all students, some of them have already paid tution and some haven't. <br>
Write a select statement to get a list of all students who haven't paid their tuition yet. The list should include all the data available about these students.<br>
**Solution**
```
	create table students (
	name varchar(50) not null,
	age integer not null,
	semester integer not null,
	mentor varchar(50) not null,
	tution_recieved boolean not null)
	
	select * from students where tution_recieved = false;
```
**Q7)Your task is to sort the information in the provided table 'companies' by number of employees (high to low).<br>
Returned table should be in the same format as provided:**<br>
**Solution**
```
	select * from companies order by employees desc;
```
**Q8)Given the following table 'decimals'**<br>
```
decimals table schema

id
number1
number2
Return a table with two columns (root, log) where the values in root are the square root of those provided in
number1 and the values in log are changed to a base 10 logarithm from those in number2.
```
**Solution**
```
	create table decimals (
	id bigserial not null,
	number1 int not null,
	number2 int not null)

	insert into decimals (number1, number2)
	values (9, 100)

	select sqrt(number1), log(number2) from decimals;
```
**Q9)Given a demographics table in the following format:**<br>
```
demographics table schema

id
name
birthday
race
you need to return the same table where all letters are lowercase in the race column.
```
**Solution**
```
	create table demographics (id bigserial,
		name varchar(50),
		birthday date,
		race varchar(20));


	insert into demographics (name, birthday, race)
	values ('Tom', '12-12-2008', 'Mongoloid')

	select id,name,birthday,lower(race) as race
	from demographics;
```
**Q10)to hexYou have access to a table of monsters as follows:**<br>
```
monsters table schema
id
name
legs
arms
characteristics
Your task is to turn the numeric columns (arms, legs) into equivalent hexadecimal values.

output table schema
legs
arms
```
**Solution**
```
	create table demographics (id bigserial,
		name varchar(50),
		birthday date,
		race varchar(20));


	insert into demographics (name, birthday, race)
	values ('Tom', '12-12-2008', 'Mongoloid')

	select id,name,birthday,lower(race) as race
	from demographics;
```	
