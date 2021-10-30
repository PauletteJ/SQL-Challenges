Revising the Select Query I

Query all columns for all American cities in the CITY table with populations larger than 100000. The CountryCode for America is USA. 

SELECT * FROM city WHERE population > 100000 AND countrycode = "USA";


-------

Revising the Select Query II

Query the NAME field for all American cities in the CITY table with populations larger than 120000. The CountryCode for America is USA.

SELECT name FROM city WHERE population > 120000 AND countrycode = "USA";

-------

Select All

Query all columns (attributes) for every row in the CITY table.

SELECT * FROM city;

-------

Query all columns for a city in CITY with the ID 1661.

SELECT * FROM city WHERE ID = 1661;

--------

Query all attributes of every Japanese city in the CITY table. The COUNTRYCODE for Japan is JPN.

SELECT * FROM city WHERE countrycode = 'JPN';

--------

Query the names of all the Japanese cities in the CITY table. The COUNTRYCODE for Japan is JPN. 

SELECT name FROM city WHERE countrycode = 'JPN';

--------

Query a list of CITY and STATE from the STATION table.

SELECT city, state FROM station;

--------

Weather Observation Station 3

Query a list of CITY names from STATION for cities that have an even ID number. Print the results in any order, but exclude duplicates from the answer.

SELECT DISTINCT(city) FROM station WHERE ID % 2 = 0;

--------

Weather Observation Station 4

Find the difference between the total number of CITY entries in the table and the number of distinct CITY entries in the table.

SELECT COUNT(city) - COUNT(DISTINCT(city)) FROM station;

--------

Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically. 

SELECT TOP 1 city, LEN(city) FROM station ORDER BY LEN(city), city ASC;
SELECT TOP 1 city, LEN(city) FROM station ORDER BY LEN(city) DESC, city DESC;

--------

Weather Observation Station 6

Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.

SELECT DISTINCT(city) FROM STATION WHERE city LIKE "[AEIOU]%";

Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.

--------
Weather Observation Station 7

Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.

SELECT DISTINCT(city) FROM STATION WHERE city LIKE "%[AEIOU]";

--------

Weather Observation Station 8

Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.

SELECT DISTINCT(city) FROM station WHERE city LIKE "[AEIOU]%[AEIOU]";

--------

Weather Observation Station 9

Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.

SELECT DISTINCT(city) FROM station WHERE city NOT LIKE "[AEIOU]%";

--------

Weather Observation Station 10

Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.

SELECT DISTINCT(city) FROM station WHERE city NOT LIKE "%[AEIOU]";

--------

Weather Observation Station 11

Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.

SELECT DISTINCT(city) FROM station WHERE city NOT LIKE "[AEIOU]%" OR city NOT LIKE "%[AEIOU]";

--------

Weather Observation Station 12

Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.

SELECT DISTINCT(city) FROM station WHERE city NOT LIKE "%[AEIOU]" AND city NOT LIKE "[AEIOU]%";

--------

Higher Than 75 Marks

Query the Name of any student in STUDENTS who scored higher than Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.

SELECT name FROM students WHERE marks > 75 ORDER BY RIGHT(name, 3) ASC, ID ASC;

--------

Employee Names

Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.

SELECT name FROM employee ORDER BY name;

--------

Employee Salaries

Write a query that prints a list of employee names (i.e.: the name attribute) for employees in Employee having a salary greater than per month who have been employees for less than $2000 per month who have been employees for less than 10 months. Sort your result by ascending employee_id.

SELECT name FROM employee WHERE salary > 2000 AND months < 10 ORDER BY employee_id;

--------

Revising Aggregations - The Count Function

Query a count of the number of cities in CITY having a Population larger than 100000.

SELECT COUNT(name) FROM city WHERE population > 100000;

--------

Revising Aggregations - The Sum Function

Query the total population of all cities in CITY where District is California. 

SELECT SUM(population) FROM city WHERE district = "California";

--------

Revising Aggregations - Averages

Query the average population of all cities in CITY where District is California. 

SELECT AVG(population) FROM city WHERE district = "California";

--------

Average Population

Query the average population for all cities in CITY, rounded down to the nearest integer.

SELECT FLOOR(AVG(population)) FROM city;

--------

Japan Population

Query the sum of the populations for all Japanese cities in CITY. The COUNTRYCODE for Japan is JPN.

SELECT SUM(population) FROM city WHERE countrycode = "JPN";

--------

Population Density Difference

Query the difference between the maximum and minimum populations in CITY.

SELECT MAX(population) - MIN(population) FROM city;

--------

The Blunder

Samantha was tasked with calculating the average monthly salaries for all employees in the EMPLOYEES table, but did not realize her keyboard's 0 key was broken until after completing the calculation. She wants your help finding the difference between her miscalculation (using salaries with any zeros removed), and the actual average salary.

Write a query calculating the amount of error (i.e.: actual-miscalculated
average monthly salaries), and round it up to the next integer.

SELECT CAST (CEILING((AVG(CAST(salary AS FLOAT))  - AVG(CAST(REPLACE(salary, 0, '') AS FLOAT)))) AS INT) FROM employees;


--------

Top Earners

We define an employee's total earnings to be their monthly salary x months worked, and the maximum total earnings to be the maximum total earnings for any employee in the Employee table. Write a query to find the maximum total earnings for all employees as well as the total number of employees who have maximum total earnings. Then print these values as space-separated integers.

--------

Weather Observation Station 2

Query the following two values from the STATION table:

The sum of all values in LAT_N rounded to a scale of 2 decimal places.
The sum of all values in LONG_W rounded to a scale of 2 decimal places.

SELECT FORMAT(SUM(lat_n), 'F2'), FORMAT(SUM(long_w), 'F2') FROM station;

--------

