# Đề Bài alien-inclusion Defcamp 2022

```php
<?php

if (!isset($_GET['start'])){
    show_source(__FILE__);
    exit;
} 

include ($_POST['start']);
echo $secret;
```

Phân tích code : 
- Nếu đầu vào start trống thì sẽ in source code 
- Để qua đk thì method POST tham số start sẽ là flag.php => key
- Với url tham số sau start cũng không đc bỏ trống để tránh in source 

Url:  `http://35.242.212.223:30277/?start=a`

![start](https://github.com/tinasahara1/Vulnerable-CTF-/blob/f0b18abe67b6de463e82592478fb4308668eb05b/images/start2PNG.PNG)
