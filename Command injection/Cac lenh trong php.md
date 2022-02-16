# LỆNH THỰC THI

- exec()                : cho phép gọi và thực thi lệnh của hệ thống => tự xử lí và ko hiện đầu ra 
- passthru()            : cho phép gọi và thực thi lệnh của hệ thống => mà bạn muốn nó trả về raw(có thể là binary)
- system()              : cho phép gọi và thực thi lệnh của hệ thống => hiển thị output ngay lập tức dạng vban
- proc_open /popen()    : đọc ghi các luồng tương tác với 1 lệnh thực thi 
 

# LỆNH TƯƠNG TÁC MẢNG
- next()                : hàm trả về giá trị tiếp theo của mảng 
- end()                 : hàm trả về giá trị cuối của mảng
- array_reverse($array) : hàm đảo ngược all gtri của mảng
- prev()                : hàm trả về giá trị trước đó của mảng

# LỆNH THƯ MỤC
- chdir("images")      : chuyển thư mục hiện tại đến thư mục images     #/home/php   ==> /home/php/images
- getcwd()             : lấy thư mục hiện tại                           #/home/php
- opendir()            : mở thư mục 
- scandir()            : trả về 1 mảng tên file trong thư mục    



# LỆNH ĐỌC FILE
- readfile()                        : có tác dụng mở một file và đọc nội dung của file đó
- file()                            : trả về ndung 1 file vào 1 mảng
- show_source('flag.php')           : trả về một tệp có cú pháp PHP được tô sáng
- highlight_file('test.txt')        : trả về một tệp có cú pháp PHP được highlight
- var_dump(file('flag.php'))        : đọc ndung file 
- file_get_contents("test.txt")     : đọc nội dung của một file thành chuỗi.
- print_r(file('flag.php'))         : đọc ndung file 
- get_defined_functions()

## Dạng 


# CÁC HÀM 
```php
__FILE__      : Tên tập tin hiện tại
__DIR__       : Đường dẫn thư mục hiện tại
__FUNCTIONS__ : Hàm hiện tại
__CLASS__     : Lớp hiện tại
__METHOD__    : Phương thức hiện tại
__NAMESPACE__ : Nameѕpace hiện tại
```





