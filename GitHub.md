# GitHub

## 注册账号

登录https://github.com/网站，按照流程注册一个GitHub账号。

## 创建一个远程仓库

<img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210811143422869.png" alt="image-20210811143422869" style="zoom: 50%;" />

①：填写仓库的名称

②：填写远程仓库的相关注释

③：选择创建的远程仓库是公有仓库还是私有仓库

④：如果勾选，会在创建远程仓库时，自动在仓库中创建一个README文件。



代码托管平台会为我们提供两种格式的仓库地址：1.HTTPS格式的仓库地址；2.SSH格式的仓库地址。

- HTTPS格式：如果创建的仓库是私有仓库，当你通过https地址克隆远程仓库时，会提示你输入github的用户名和密码，以此来验证你是否有权限克隆当前的仓库。

- SSH格式：当你通过ssh地址操作远程仓库时，代码托管平台会通过ssh密钥验证你的身份，验证你是否有权利克隆当前的仓库。

## 环境搭建

### 1.创建SSH Key

在用户主目录下查看是否有.ssh目录，再看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果没有，则需要创建SSH Key。

如何创建？输入代码：

```
$ ssh-keygen -t rsa -C"249171721@qq.com"
```



输入后按回车，出现以下画面：

<img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210811144653730.png" alt="image-20210811144653730" style="zoom: 67%;" />

完成操作后，回到主目录查看是否有id_rsa和id_rsa.pub这两个文件，其中id_rsa是私钥，不能泄露出去；id_rsa.pub是公钥，可以公开。

### 2.在GitHub上导入SSH Key

登录Git点击个人头像，弹出选择框，选择“settings”，然后选择“SSH and GPG keys”。

点“**New SSH Key**”，填上任意Title，在Key文本框里粘贴**id_rsa.pub**文件的内容:

*如何测试密钥是否匹配成功呢？*

[相关文件](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/testing-your-ssh-connection)

1.打开Git Bash

2.输入：

```
$ssh -T git@github.com
```

可能会看到以下警告：

```
> The authenticity of host 'github.com (IP ADDRESS)' can't be established.
> RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
> Are you sure you want to continue connecting (yes/no)?
```

3.验证看到的消息中的指纹是否与rsa的公钥指纹匹配，如果是输入“yes”，

<img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210811153054887.png" alt="image-20210811153054887" style="zoom: 67%;" />



## 本地仓库和远程仓库

### 1.将本地代码上传到远程仓库



1.关联本地仓库和远程仓库

```
$ git remote add origin git@github.com:Bressole/snum01.git     //ssh地址         
```

<img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210812101006819.png" alt="image-20210812101006819" style="zoom: 50%;" />

2.将代码上传到远程仓库

```
git push -u origin master     //分支名
```

### 2.克隆远程和拉取分支

1.git clone 是从远程服务器克隆一个一模一样的版本库到本地；

克隆命令如下：

```
$ git clone git@github.com:Bressole/snum01.git     //ssh地址 
```

2.git pull是取回远程主机某个分支的更新，再与本地的指定分支合并。

```
git pull origin master         //master是一个分支名
```



区别：克隆是将一整个远程仓库克隆下来，会在对应文件位置里生成一个文件夹；

拉取是拉取远程仓库里的某一个分支；





- 可能会遇到的问题：

1.关联远程a仓库时出现以下错误，

![image-20210817094553321](C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210817094553321.png)

说明该本地仓库**已经关联了远程仓库了**，

解决方法：只要输入以下代码，把关联的仓库删掉，再重新关联即可。

~~~
git remote rm origin
~~~



2.push的时候报错冲突：

![image-20210817095730444](C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210817095730444.png)

这是因为在我将远程仓库拉取过来修改的这段时间里，**已经有人将我所拉取的文件修改了**。

解决方法：再pull一次

```
$ git pull origin master //分支名
```

这时候你所修改的文件会和拉取下来的新文件合并，需要你手动留下需要的部分再push。

通过以下代码：

```
$ git add e1.txt    //文件名
$ git push -u origin master   //分支名
```



3.拉取分支时报错：

![image-20210817105022269](C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210817105022269.png)

说明这时**拒绝合并不相关的历史**，通过以下代码可以解决：

~~~
$ git pull origin 分支名 --allow--unrelated-histories
~~~

![image-20210817105226419](C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210817105226419.png)



### 3.README.md文件

md是Markdown的缩写。

该文件是项目介绍，一般会包含简介，安装方式，主要功能介绍以及开源许可协议。



