# sql_practice

##Examples
#####Give me a list of all invoices
`SELECT * FROM invoices`

#####Give me the name of every artist
`SELECT name FROM artists`

#####Give me the first and last names of every employee
`SELECT first_name, last_name FROM employees`

#####Give me a list of every employee by hire date in descending order
`SELECT * FROM employees ORDER BY hire_date DESC`

#####Give me a list of employees' first_name, last_name, hire_date hired before FEB 15 2011
`SELECT first_name, last_name, hire_date FROM employees WHERE hire_date < '2011-02-15'`

#####Give me a list of all employees whose name begin with "A"
`SELECT * FROM employees WHERE first_name LIKE 'A%'`

#####Give me a list of names of artists whose name ends with "smith"
`SELECT name FROM artists WHERE name LIKE '%smith'`

#####Give me a list of all names of artists whose name contains "smith"
SELECT name FROM artists WHERE name LIKE '%smith%'

#####Give me a list of all invoices from Redmond, WA
SELECT * FROM invoices WHERE billing_city = 'Redmond' AND billing_state = 'WA'

##Syntax for Inner JOIN
The INNER JOIN keyword selects all rows from both tables as long as there is a match between the columns in both tables

SELECT
