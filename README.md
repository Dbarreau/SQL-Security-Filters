# SQL Security Filters
<p align="center">
![SQLicon](SQL) 
</p>

## Project Description
My organization wants to make its systems more secure. I help check the system, look for any potential security problems, and make sure employee computers are updated. Below are examples of how I used SQL filters to look at security-related data.

---

## Retrieve After-Hours Failed Login Attempts
There was a security issue reported after business hours (after 18:00). I needed to check all failed login attempts during this time.

```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = False;
```
<p align="center">
  <img src="falseattempts" alt="After Hours Failed Logins">
</p>


---

## Retrieve Login Attempts on Specific Dates

A suspicious event happened on 2022-05-09. I wanted to see any logins on that date or before.

```sql
SELECT * 
FROM log_in_attempts 
WHERE login_date = '2022-05-09' OR login_date < '2022-05-09';
```
<p align="center">

![Login Attempts on Specific Dates](Dates)
</p>

This selects all login attempts on 2022-05-09 or earlier. The OR operator makes sure both dates are included.

---

## Retrieve login attempts outside of Mexico
I also wanted to check for login attempts that happened outside of Mexico.

```sql
SELECT * 
FROM log_in_attempts
WHERE NOT country LIKE 'Mex%';
```
This returns all logins not from Mexico. I used NOT with LIKE and % because the data has different forms of Mexico, like “MEX” or “MEXICO.”

<p align="center">
![Login Attempts Outside Mexico](Outside%20of%20Mexico)
</p>

---

## Retrieve employess in Marketing
The Marketing department in the East building needs computer updates. I had to find which employees to update.

```sql
SELECT * 
FROM employees
WHERE department = 'Marketing' AND Office LIKE 'East%';
```
This gets all employees in Marketing at the East building. The AND operator makes sure both conditions are true.

<p align="center">
![Employees in Marketing](Marketing)
</p>

---

## Retrieve employees in Finance and Sales
Finance and Sales employees also need updates, but they require a different update.
```sql
SELECT *
FROM employees
WHERE department = 'Finance' OR department = 'Sales';
```
<p align="center">
![Employees in Finance or Sales](Finance%20or%20Sales)
</p>

This query selects employees in either Finance or Sales. I used OR because I want employees from either department, not just both.

---

## Retrieve employees that are not in IT
Finally, I needed to get employees who are not in IT to apply one more security update.

```sql
SELECT *
FROM employees
WHERE NOT department = 'Information Technology';
```
<p align="center">
![Employees Not in IT](No%20IT)
</p>

This selects all employees who are not in IT.

---

## Summary

I used SQL filters to find specific information in the log_in_attempts and employees tables. I used AND, OR, and NOT to filter results and LIKE with % to find patterns. This helped me investigate failed logins, find employees in certain departments, and make sure updates were applied correctly.

