# Serialization và Deserialization là gì 
- Serialization là quá trình chuyển đổi trạng thái thông tin của một đối tượng => một hình thức có thể được lưu trữ hoặc truyền. Nó thường có dạng byte,  XML,  JSON, ... => khi truyền qua mạng (network)
- Deserialization là quá trình ngược lại của quá trình serialization

## Serialize() 
- Hàm hỗ trợ đối tượng Serialization trong php là serialize( ) 
- Input của hàm là một object (Đối tượng)
- Output của hàm sẽ là một chuỗi lưu object đó => cụ thể sẽ lưu class của object và các thuộc tính của object.

## Unserialize()
- Hàm hỗ trợ đối tượng Deserialization là unserialize( ). 
- Input là một chuỗi đại diện cho object. 
- Output là object được xây dựng lại từ chuỗi truyền vào hàm unserialize( ).


### Cách khai thác 

Để khai thác được lỗ hổng PHP deserialization cần có 2 điều kiện :
  + Class phải sử dụng 1 trong 3 hàm **__wakeup(), __destruct(), __toString,__construct()**  để xử lý dữ liệu người dùng
  + Người dùng có thể chèn dữ liệu độc hại vào hàm unserialize() => **$_GET , $_POST , $_COOKIE , $_SESSION** 

Trong đó :

**__wakeup ( )**     : được thực thi khi một object được gọi dậy

**__destruct ( )**   : một trình hủy được gọi khi đối tượng bị hủy hoặc tập lệnh bị dừng hoặc thoát, PHP tự động gọi hàm này ở cuối tập lệnh (nếu được thiết lập)

**__construct ( )**  : cho phép người dùng khởi tạo các thuộc tính của một đối tượng khi tạo đối tượng, PHP sẽ tự động gọi hàm này khi tạo một đối tượng từ một lớp(class) 

