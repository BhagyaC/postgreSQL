# postgreSQL

## This is to familiarise how to deal with a read only replica of database - I am using a database of the Django web app

### Day 1 - Basics
- \l - list database
- \d - list all tables and sequences
- \dt - list all the tables
- The sequence is the incremented number of a specific queue
There is a website called mockaroo where we can create any number junk data to our database for practicing
It will give a sql file we can open it on the vs code and edit it. For those who are not confortable with the terminal code this is a best way.
-
- \? : will give all the options related to the postgresql 
- there is a way to run the sql code \i FILE where the file is the code to the sql or a python script
- If we add the attribute to the table/ relation as a BIGSERIAL  then the value will get auto incremented overtime.
## The SELECT FORM
- SELECT * FROM tablename : will give the entire values in the table
- SELECT FROM tablename : will give the number of rows in the table
## ORDER FORM
- SELECT * from table name ORDER BY column name
- SELECT DISTINCT attribute from table name ORDER BY column name : will give the distinct values of the total result
## WHERE CLUASE 
- It allows to filter the database on condition
-  SELECT * from table name WHERE attribute = "condition"
- In the where clause we can add the AND and the OR to add one or more attributes in the comparison
## COMPARISON
- SELECT 1=1; will give a true value we can perform the comparison opertation
- SELECT 1<>1; Is the not equal to comparison 
## LIMIT 
- It will limit the select operation to a perticular range
- SELECT * from tablename LIMIT 10
- SELECT * from tablename OFFSET 5 LIMIT 10 ; it will give you the data from the 6 to 26
- Actually LIMIT is not a sql key word but it can be used the original one is
- SELECT * from tablename OFFSET 5 FETCH FIRST 10 ROW ONLY;
- There are multiple column and in the where clause then we can write them in a braces and use by in 
- SELECT * from tablename WHERE attribute IN (option1, option2 ...)
- we can limit the BETWEEN after the WHERE clause and it will retrieve the data within that limit
- With the where clause we can use LIKE to match with a string % in a string will substitute any type of character
- if the string matches the '--' means two positions
## GROUP BY
- It will group the details according to a perticular column values.
- SELECT attribute, COUNT(*) from tablename GROUP BY attribute
- the group by can be followed by the order by which will give the above relation with sorted values
## GROUP BY HAVING
- This will help us to perform another operation after a aggrigation operation by the having term.

- To check what all are the arithmetic operation that we can use with postgresql then just use the select operation and test them
## ALIAS 
- We can find another variable name for each of the  them we can use AS parameter to use another attribure name

## COALESCE
- It will give the first value in a list
- It can be used to replace the null value to replace with another value
- SELECT COALESCE(attribute,"not given") from tablename
## NULLIF
- This is to tackle the division by zero
- it will take two arguments if both are same the result will be null otherwise the result is the first parameter
- SELECT 10/NULLIF(0,0)
## TIMESTAMP
- The date or the time normally get stored as the timestamp
- To get the date from the timestamp SELECT NOW():: DATE;
- SELECT NOW()::TIME;
- They have a documentation about the date and time types
## ADDING AND SUBTRACTING THE TIME
-  SELECT NOW() - INTERVAL '1 YEAR' 
- If you want to get only the date from the final time stamp element then 
- SELECT (NOW() + INTERVAL '10 MONTHS')::DATE;
 
## EXTRACT SPECIFIC VALUES FROM THE TIME STAMP
- SELECT EXTRACT(YEAR FROM NOW());
## AGE FUNCTION
- SELECT AGE(NOW(),atttribute of date of birth) AS DOB from table name
## PRIMARY KEY 
- The way to identify the unique values
## UNIQUE CONSTRAINTS
- To set up a column with unique values only
## CHECK CONSTARINTS
- Allow us to add the constrain based on a boolean value
- like it will check the some condition for the boolean expression and then it will allow the only true values for the conditions
## FOREIGN KEYS, JOINS AND RELATIONSHIPS
- Postgres is a relational database where we can connect multiple table using foriegn key 
- When we create a table we can make sure that the primary key of one table will be a foriegn key of another. Why we trying to access something that is not a value as the primary key we will get a error
- UPDATE tablename SET attribute_in_the_table (foriegn key )= value1 where the primary key  = value 2. If the value1 is not in the primary key values of the other table then we will get an error
## INNER JOIN
- We have to join two table it will return the common values
- SELECT * from tablename1 person JOIN tablename2 ON tablename.foriegnkey = tablenamee.primarykey 
- \x will give an record wise visualisation of data
## LEFT JOIN
- It will include all the values from the left tables as well as the additional values from the another table for only those who has a foriegn key values
- SELECT * FROM person LEFT JOIN car ON car.id = person.car_id
- SELECT * FROM person LEFT JOIN car ON car.id = person.car_id WHERE car.* is NULL for those who doesnot have a foriegn key constrain
- 
## How to export the query result to CSV
- How to generate the csv with postgres
- \copy (SELECT * FROM person LEFT JOIN car ON car.id = person.car_id) TO '/Users/amigos/result.csv' DELIMITER ',' CSV HEADER
## Serial and Sequence
- There are some id called BIGSERIAL which auto increment a number the type is indicated as bigint
- SELECT * from sequence_name: will give the id of the last value and then it is called or not along with the data for long count or not
- we can also the restart the sequence
## The Extension
- They are simply extention which is like function that helps in another more function
- uuid-ossp will generate universally unique identifiers
- It will give the guarenty that it is universally unique
- universally unique ids are described in wikipedia and how they created the combinations 
