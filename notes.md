Queries are some request to database to get some information
DBMS => Database Management Systems (make it easy to create ans secure a database and allow to perform the C.R.U.D operations)
***
primary key must be always Unique
foreign key stores the primary key of a row in another database table and defines a relationsheep between two tables
***
Data types
INT
DECIMAL(M,N)
VARCHAR(1) => store a text with 1 charecter
BLOB => binary large object
DATE => 'YYYY-MM-DD'
TIMESTAMP => 'YYYY-MM-DD HH:MM:SS'
***
CREATE TABLE database_name ();

```SQL
CREATE TABLE student (
	student_id INT PRIMARY KEY,
	name VARCHAR(20),
	major VARCHAR(30),
	-- PRIMARY KEY(student_id) also we can do this 
);

DESCRIBE student -- This will discribe our Database to show

ALTER TABLE student ADD gpa DECIMAL(3,2); -- All a column

INSERT INTO student VALUES(1, 'Tyrell', 'Mathemathics'); -- Add a value to table

SELECT * From student; -- Show all of the table

-- If we dont have a part of a column , we do this
Insert INTO student(student_id, name) VALUES(2,'elliot'); -- We dont insert the major



```

```SQL
CREATE TABLE student (
	student_id INT AUTO_INCREMENT, -- Will all Automaticly id number
	name VARCHAR(20) NOT NULL,  -- Will not allow null
	major VARCHAR(30) UNIQUE, -- just unique
	-- PRIMARY KEY(student_id) also we can do this 
);

-- for changing a thing in our table 
UPDATE student
SET major = 'Math'
WHERE major = 'Mathemathics'; -- or ( WHERE student_id = 1; )
-- We can use OR to check the multiple things , for example we can change the things that major is Mathematics and physics
-- if we wanna to change all of the majors , we delete the WHERE line

DELETE FROM student
WHERE student_id = 5; -- This will delete the row that student_id is 1

DELETE FROM student -- delete everything

SELECT *
FROM student
LIMIT 3; -- show the table until the row 2


SELECT *
FROM student
WHERE major IN ('Mathematics' , 'physics' ); -- display just that rows


-- count something

SELECT COUNT(student_id)
FROM student;

-- give average

SELECT AVG(student_id)
FROM student;

-- With GROUP BY we can make groups our selected information

SELECT SUM(sales) , client
FROM works
GROUP BY client;

-- Find a specific thing in our tables with something like regex in SQL
-- In here we wanna to find a name that have in the end of the name 'ddl'
--  __ = one charecter     % = any

SELECT *
FROM client
WHERE client_name LIKE '%ddl'

-- find the clients that born after October

SELECT *
FROM employee
WHERE birth_date LIKE '____-10%';  (4 underline for year)


```

= means equal but <> means not equals v

When we wanna to use foreign key we must add at the end line =>  ON DELETE SET NULL , and this is for when a row is deleted or something deleted in the table , NULL will be showing instead of that
ON DELETE CASCADE will delete all of the things that requires to that deleted thing entirely

when we have primary key we used ON DELETE CASCADE bit when we have foreign key we use ON DELETE SET NULL

tablename.row_name => we can select  a row like this too

# Nested Queries
```SQL

-- find the persons who have sold over 30000 from company

SELECT person.name , person.lastname
FROM person
WHERE person.id IN (
	SELECT works_with_id
	FROM works_tab
	WHERE works_tab.totalsales > 30000
);

```

we can show a message after adding somthing in the table or row with TRIGGER in SQL