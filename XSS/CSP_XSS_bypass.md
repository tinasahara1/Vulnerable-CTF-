# XSS + Content security policy(CSP) bypass techniques 
[Tham khảo thêm các cách bypass CSP](https://bhavesh-thakur.medium.com/content-security-policy-csp-bypass-techniques-e3fa475bfe5d)

- CSP là một cơ chế bảo mật của trình duyệt nhằm mục đích xác định các resources có thể fetch data hoặc thi hành trên web page đó . Nó có thể hiểu là 1 policy quyết định `scripts, images, iframes` nào có thể được gọi hoặc thi hành trên 1 trang cụ thể từ các locations khác nhau 
- Content-Security-Policy được thực thi qua response headers hoặc trên các meta elements của HTML. Từ đó trình duyệt có thể làm theo các policy đã thiết lập 
- Nhiều người vẫn nghĩ CSP có thể giảm thiểu XSS nhưng không => CSP chỉ là 1 lớp bảo mật bổ sung nhằm ngăn chặn các cuộc tấn công chèn nội dung 

+ `script-src` : Chỉ thị nguồn được phép thi hành cũng như fetch dữ liệu trên web page (ví dụ : thi hành trực tiếp trong thuộc tính <script> , các thuộc tính onclick , xslt đều có thể được thi hành )
+ `selt` : Xác định rằng việc tải các tài nguyên trên web page được phép từ cùng một miền
+ `data` : cho phép tải tài nguyên từ resources thông qua data schema (eg Base64 encoded images)
+ `none` : Không có bất kì nguồn nào được load bất kì thứ gì
+ `unsafe-eval` : Nó cho phép sử dụng hàm eval và các hàm tương tự để tạo chuỗi 
+ `unsafe-inline` : Nó cho phép các dữ liệu không an toàn được thêm vào và thực thi 
+ `nonce` : thuộc tính cho phép bạn “danh sách trắng” inline nhất định `script và style` elements, trong khi tránh sử dụng các CSP unsafe-inline
  
![image](https://user-images.githubusercontent.com/57553555/162897903-dab04872-2205-4723-b228-334005db5db4.png)


## Content-Security-Policy -- `report-uri`
- Ta phát hiện Response có chứa report-uri => Nó là 1 trong những CSP 

[Tài liệu tham khảo](https://portswigger.net/web-security/cross-site-scripting/content-security-policy)
![image](https://user-images.githubusercontent.com/57553555/162882701-ffac233e-51e2-4ed0-9938-c258ed9efbd1.png)

- `report-uri` => Nó thường lấy cái policy cuối cùng trong list => Vì vậy ta có thể ghi thêm 1 CSP của ta nhằm bypass => Bằng cách kết hợp xss để chèn csp không an toàn vào `;script-src-elem 'unsafe-inline'`

Payload : 
```js
message=<script>alert(1)</script>&token=;script-src-elem 'unsafe-inline' 
```

## Content-Security-Policy --nonce

![image](https://user-images.githubusercontent.com/57553555/162885986-ac84a18c-bd86-4e21-b437-15cc6a0ad1bf.png)
  
- Theo như response trả về ta có 2 thứ cần quan tâm là : Content-Security-Policy: script-src 'nonce-Y8Ret8N5CPXrSG';style-src 'unsafe-inline'; và Content-Type: text/xsl => [Payload xss content_type](https://github.com/tinasahara1/XSS_content_type-/blob/master/XSS.md)
- Để bypass nó ta cần 1 payload xss với content-type kiểu text/xsl và đính kèm nonce-mahoa

Payload :   
```xsl
?src=<x:script xmlns:x="http://www.w3.org/1999/xhtml" nonce="Y8Ret8N5CPXrSG">alert(1)</x:script>  
```
  
  
