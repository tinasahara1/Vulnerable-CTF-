# JWT KHÓA

## Thuật toán RS256 
- Sử dụng secret key để sign và verify nội dung signature trong JWT (mã hoá đối xứng)

## Thuật toán HS256 
- Sử dụng private key để sign vào nội dung signature và sử dụng public key để verify nội dung này (mã hoá bất đối xứng). 

>Nếu chuyển từ RS256 sang HS256 thì signature sẽ được verify bằng public key của HS256. khi đã thay đổi thuật toán mã hoá sang HS256, vì lúc này secret key tương đương với public key mà mình có được, chỉ cần sign signature bằng key mà mình có được, ứng dụng hệ thống sẽ verify trên public key nên sẽ có thể dễ dàng bypass được JWT verification. 
