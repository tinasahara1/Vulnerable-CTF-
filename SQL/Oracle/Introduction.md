# Query Basic 

## Version
```sql
SELECT banner FROM v$version
SELECT version FROM v$instance
SELECT user FROM dual UNION SELECT * FROM v$version
```

## Database
```sql
SELECT * FROM all_tables
SELECT * FROM all_tab_columns WHERE table_name = 'TABLE-NAME-HERE'

SELECT global_name FROM global_name;
SELECT name FROM V$DATABASE;
SELECT instance_name FROM V$INSTANCE;
SELECT SYS.DATABASE_NAME FROM DUAL;

```

## Conditional
```sql
SELECT CASE WHEN (YOUR-CONDITION-HERE) THEN to_char(1/0) ELSE NULL END FROM dual
```
