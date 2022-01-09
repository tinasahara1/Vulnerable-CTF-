# [Lab:  Blind SQL injection with conditional responses](https://portswigger.net/web-security/sql-injection/blind/lab-conditional-responses)

>This lab contains a blind SQL injection vulnerability. The application uses a tracking cookie for analytics, and performs an SQL query containing the value of the submitted cookie.The database contains a different table called users, with columns called username and password. You need to exploit the blind SQL injection vulnerability to find out the password of the administrator user.To solve the lab, log in as the administrator user.
>

## Step 1 : Check vul sql blind
![check1]()


## Step 2 : Check length password 
![check1]()

=> Length of administrator password : 20 
## Step3 : Use the substring to find the first letter of password 
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
![check]()

=> The first letter is '6'

## Step 4 : Code py 


