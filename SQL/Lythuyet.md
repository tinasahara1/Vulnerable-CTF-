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
- **WHERE** <condition>;
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
