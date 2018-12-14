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

### Aggregate Functions

Kewyords:
- AVG(): Take the average of a column
- MAX(): Get the max of a column
- SUM(): Sum the entries in a column
- MIN(): Get the minimum of a column
- AS: Use aliasing when generating multiple aggregated results to differentiate

### Sort and Group Results

Keywords:
- ORDER BY: sorts column in ascending order, use DESC to indicate descending order
- GROUP BY: group similar entries and aggregate
- HAVING: filter groups using this keyword

## Notes on SQL and Relational Databases

* Relational data bases are collections of tables
* SQL stands for Structured Query Language
	* SQL is a language used for interacting with relational databases
	* It can be used to query, modify, and create databases
* A query is a request for information from a database
	* A query uses the keywords SELECT and FROM to get information from a database
	* It is good practice to end queries with semicolons (;)
	* Single or multiple columns can be selected at one time
		* Example: multiple query of name and age columns of people table
		```
		SELECT name, age
		FROM people;
		```	
	* You can combine keywords in a query to count unique values in a column
		* Example
		```
		SELECT COUNT (DISTINCT country)
		FROM films;
		```
* Queries can be filtered based on information from other rows
	* Use the WHERE keyword to filter a query
		* Example: filter film titles based on release date
		```
		SELECT title
		FROM films
		WHERE release_year > 2009;
		```
		* For text in PostgreSQL use single quotes with WHERE
	* Filter based on multiple conditions with an AND statement
		* Example:
		```
		SELECT title
		FROM films
		WHERE release_year < 2000
		AND release_year > 1980;
		```
	* When combining conditional filter AND and OR, use parentheses to clarify the order 
	of operations
		* Example
		```
		SELECT title 
		FROM films
		WHERE (release_year = 1994 OR release_year = 1995)
		AND (certification = 'PG' OR certification = 'R');
		```
	* The BETWEEN keyword provides a useful way to generate ranges
		* Example:
		```
		SELECT title
		FROM films
		Where release_year
		BETWEEN 2000 AND 2010;
		```
* Aggregate functions are useful for operating on the data in a SQL database
	* To use an aggregate function, place the column in parantheses
		* Example:
		```
		SELECT AVG(budget)
		FROM films;
		```
* Example of joining info from two tables
	```
	SELECT title, imdb_score
	FROM films
	JOIN reviews
	ON films.id = reviews.film_id
	WHERE title = 'To Kill a Mockingbird';
	```