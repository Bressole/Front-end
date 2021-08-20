# 域名系统

## 1.概述

把互联网上的**主机名字**转换为**IP地址**。名字到IP地址的解析是由若干个域名服务器程序完成的。

## 2.互联网的域名结构

- 域名只是一个**逻辑概念**，并不代表计算机所在的物理地点。

- 域名的结构  ....三级域名.二级域名.顶级域名

  （级别**最低**的域名写在**最左边**，级别**最高**的域名写在**最右边**）

- 互联网采用了层次树状结构的命名方法。

<img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210813101957462.png" alt="image-20210813101957462" style="zoom:50%;" />

## 3.域名服务器

#### 1.区和域

- 一个服务器所负责管辖的（或有权限的）范围叫做**区**。

- 区是域的子集。

  <img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210813103341101.png" alt="image-20210813103341101" style="zoom:50%;" />



#### 2.域名服务器类型

##### a.根域名服务器

根域名服务器是最高层次的域名服务器，也是最重要的域名服务器。所有的根域名服务器都知道所有的顶级域名服务器的域名和IP地址。

目前共有13 个不同IP 地址的根域名服务器，它们的名字是用一个英文字母命名，从 a 一直到 m。

##### b.顶级域名服务器

负责管理在该顶级域名服务器注册的所有二级域名服务器。

##### c.权限域名服务器

负责一个区的域名服务器

##### d.本地域名服务器

对域名系统非常重要。当一个主机发出DNS查询请求时，这个查询请求报文就发送给本地域名服务器。



## 4.域名的解析过程

#### 1.递归查询

<img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210813110132611.png" alt="image-20210813110132611" style="zoom:67%;" />

#### 2.迭代查询

<img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210813110203862.png" alt="image-20210813110203862" style="zoom:67%;" />