## Introduction to SQL with Data Camp

This page contains my notes from the introduction to SQL course provided by Data Camp. 

## Useful Code

### Selecting Columns

Keywords:
- SELECT: select a column
- FROM: which table are we selecting something from
- LIMIT: limit the number of entries returned to a specified number
- DISTINCT: get only unique values from a column
- COUNT(): returns the number of rows in a column

### Filtering Results

Keywords:
- WHERE: filter based on numeric or text values
	- equal (=)
	- not equal (<>)
	- less than, greater than (<, >)
	- less than or equal to, greater than or equal to (<=, >=)
- AND: use with WHERE to filter based on multiple conditions
- OR: use to filter when two conditions must be met but not necessarily at the same time
- BETWEEN: Use to find ranges and remember that it is inclusive of the ends
- IN: allows you to specify a list where information is coming from
- NULL: represents a missing value
- IS NULL: checks for a missing value
- IS NOT NULL: checks for non-missing values
- LIKE: use for pattern matching
	- the % operator specifies 0, 1, or many characters (any character)
	- the _ operator specifies any single character
- NOT LIKE: select anything that does not match the pattern


## Notes on SQL and Relational Databases

I. Relational data bases are collections of tables
II. SQL stands for Structured Query Language
	A. SQL is a language used for interacting with relational databases
	B. It can be used to query, modify, and create databases
III. A query is a request for information from a database
	A. A query uses the keywords SELECT and FROM to get information from a database
	B. It is good practice to end queries with semicolons (;)
	C. Single or multiple columns can be selected at one time
		i. Example multiple query of name and age columns of people table
		```
		SELECT name, age
		FROM people;
		```
	D. You can combine keywords in a query to count unique values in a column
		i. Example
		```
		SELECT COUNT (DISTINCT country)
		FROM films;
		```
IV. Queries can be filtered based on information from other rows
	A. Use the WHERE keyword to filter a query
		i. Example: filter film titles based on release date
		```
		SELECT title
		FROM films
		WHERE release_year > 2009;
		```
		ii. For text in PostgreSQL use single quotes with WHERE
	B. Filter based on multiple conditions with an AND statement
		i. Example:
		```
		SELECT title
		FROM films
		WHERE release_year < 2000
		AND release_year > 1980;
		```
	C. When combining conditional filter AND and OR, use parentheses to clarify the order 
	of operations
		i. Example
		```
		SELECT title 
		FROM films
		WHERE (release_year = 1994 OR release_year = 1995)
		AND (certification = 'PG' OR certification = 'R');
		```
	D. The BETWEEN keyword provides a useful way to generate ranges
		i. Example:
		```
		SELECT title
		FROM films
		Where release_year
		BETWEEN 2000 AND 2010;
		```
	
