# Applying-filters-with-SQL
For this project the task is to ensure the system is safe, investigate all potential security issues, and update employee computers as needed.
The following steps provide examples of how I used SQL with filters to perform security-related tasks.

# Retrieve after hours failed login attempts:
![UnsuccessfulAfterHoursLogins](https://i.imgur.com/p530xUk.png)

First, the suspucious logins must be identified. This is accomplished by running the following query:
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = FALSE;
Within the log_in_attempts table the login_time and (login) success are filtered for so we get the correct time parameters returned.

# Retrieve login attempts on specific dates
![LoginsBetween5-8And5-9](https://i.imgur.com/cqkdbNY.png)

Next, we move on to checking logins on specific dates. Since a suspicious activity occurred on 5-9 we will check for any oddities between 5-8 and 5-9 using the following query:
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
Again, the log_in_attempts table is utilized but this time we filter for the login_date. The date is then filtered down to the specific dates of being between 5-8-22 and 5-9-22.

# Retrieve login attempts outside of Mexico
![OutsideMexico](https://i.imgur.com/Y48l1z5.png)
The suspicious login attempts appear to have occurred outside of Mexico. To filter for that information the following query was implemented:
SELECT *
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
For a third time the log_in_attempts table is required. We need to filter for all countries except Mexico. 'NOT' tells the database that we need everything except this. The '%' after 'MEX' detects both MEX, MEXICO, and all other abbreviations.

# Retrieve employees in Marketing
![MarketingEmpls](https://i.imgur.com/VGGEqyF.png)
Now we need to determine which computers need updated in the marketing department. The updates will begin with the marketing employees located in the east building. To filter for this this query is used:
SELECT *
FROM employees
WHERE department = 'Marketing' AND office LIKE 'EAST%';
We move onto selecting the employees table, but on those in the marketing department and located in the east building. 

# Retrieve employees in Finance or Sales
![FinanceOrSalesEmpls](https://i.imgur.com/JW6rxow.png)
Many of the computers for the finance and sales departments also need updated. So we move onto them next with the following filter:
SELECT *
FROM employees
WHERE department = 'Finance' OR department = 'Sales';
This query is similar to the previous, except now we are looking for two particular departments.

# Retrieve all employees not in IT
![NotInIT](https://i.imgur.com/ReTG4pC.png)
Finally we need to install a security patch on all company computers except those in IT. To filter for all computers, except IT devices, we utilze the following query:
SELECT *
FROM employees
WHERE NOT department = 'Information Technology';
All company computers will be listed, except for those under IT.


# Conclusion
In this lab we queried for times, dates, departments, and locations. Many tables and clauses were utilied to perfom these duties.
