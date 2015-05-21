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
`SELECT name FROM artists WHERE name LIKE '%smith%'`

#####Give me a list of all invoices from Redmond, WA
`SELECT * FROM invoices WHERE billing_city = 'Redmond' AND billing_state = 'WA'`

#####Find all the employees who were hired between 01/01/2000 and 12/31/2005 with the output
alphabetically order by last name & then first name.  (Output columns: employee #, last name, first name)
`SELECT lastname, firstname FROM employee WHERE hiredate BETWEEN 2000-01-01 AND 2005-12-31 ORDER BY lastname, firstname

#####Find all the employees who worked in the department named OPERATIONS or PLANNING in
ascending order of the department name (Output columns: employee #, last name, first name, job name, 
department #, department name)
`SELECT empno, lastname, firstname, job, workdept deptname FROM employee INNER JOIN department ON employee.workdept = department.deptname`

#####Show all the employees and their total compensation (salary+ bonus+ comm) in descending order based on their compensation (output columns: employee #, last name, first name, compensation)

`SELECT empno, lastname, firstname, salary+bonus+comm AS total_compensation FROM employee ORDER BY total_compensation`

#####Find the 10 lowest paid employees based on their total compensation (salary + bonus + comm) in lowest order first (output columns: employee #, last name, first name, compensation)

`SELECT empno, lastname, firstname, salary+bonus+comm AS total_compensation ORDER BY total_compentation LIMIT 10`


#####There are many job roles amoung the 42 employees. Find the number of poeple in each job role (at least 1) order by highest to lowest

`SELECT job, count(job) AS total_working_job FROM employeees GROUP BY job ORDER BY total_working_job`

#####There are many departments in the company. Find the number of employees in each department (at least 1) order from lowest to highest.

`SELECT deptno, deptname, COUNT(workdept), as TOTAL FROM (SELECT * FROM employee INNER JOIN department ON employee.workdept = department.deptno) GROUP BY deptno, deptname order by TOTAL;`






##Types of SQL Joins
1. **Inner Joins**
	
	- an inner join produces a result set that is limited to the rows wehre there is a match in both tables for what we're looking for. If you don't know which kind of join you need, this will usually be the safe bet

	*Example*:
	`SELECT gid, first_name, last_name, pid, gardener_id, plant_name 
	FROM Gardners
	INNER JOIN Plantings
	ON gid= gardener_id`

2. **Left Outer Join**
	
	- a left outer join, or left join, results in a set where all of the rows for the first, or left hand side, tables are preserved. The rows from the second or right hand side only show up if they have a match with the rows from the first table. Where there are values from teh left table but not from teh right, the table will read null, which means taht the value has not been set.

	*Example*:
	`'SELECT gid, first_name, last_name, pid, gardener_id, plant_name 
	FROM Gardners
	LEFT OUTER JOIN Plantings
	ON gid = gardener_id'`

3. **Right Outer Join**
	
	- a right outer join, or right join, is the same as a left join, except the roles are reversed. All teh rows from the right hand side table show up in the result, but teh rows from the table on the left are only there if they match the table on the right. Empty spaces are null, just like with the left join.

	*Example*: `SELECT gid, first_name, last_name, pid, gardener_id, plant_name 
	FROM Gardners
	RIGHT OUTER JOIN Plantings
	On gid = gardner_id`

4. **Full Outer Join**
	
	- a full outer join, or just outer join, produces a result set with all the rows of both tables, regardless of whether there are any matches. Similarly to the left and right joins, we call the empty spaces null.

