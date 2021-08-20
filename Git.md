# Git

## 版本控制

Git是分布式版本控制系统，没有中央服务器，每个人的电脑就是一个完整的版本库。多人协作方式：自己在电脑上改了文件A，其他人也在电脑上改了文件A，把各自的修改数据推送给对方。

PPT：

为何使用git？例子引入

分布式  引入svn进行比较

三个区域 

分支管理

远程仓库 github

what why 

git branch 查看当前分支和所有分支



## 1.创建版本库

<img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210811161922106.png" alt="image-20210811161922106" style="zoom:50%;" />

这几个命令表示：在E盘的gitbank文件夹下新建一个gitnum01版本库，然后通过命令git init 把这个目录变成git可以管理的仓库。  pwd命令是用于显示当前的目录；

## 2.提交文件的操作

1.在创建的版本库gitnum01文件夹下新建一个test01.txt文本，通过以下代码将该文本从工作区提交到暂存区：

```
$ git add readme.txt       //文件名
```

2.把该文本从暂存区提交到本地仓库：

```
$ git commit -m '提交注释'
```

3.查看是否还有文件未提交：

```
$ git status
```

​	若修改了文件但是未提交则会出现以下结果：

<img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210811165059683.png" alt="image-20210811165059683" style="zoom:67%;" />

4.可以查看该文件修改了什么内容：

```
$ git diff test01.txt
```

<img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210811165305500.png" alt="image-20210811165305500" style="zoom:67%;" />

如图所示：改文本添加了“2222”

注意：首次提交文件时需要完善个人邮箱和名字，如图所示：

<img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210811171629898.png" alt="image-20210811171629898" style="zoom:67%;" />

5.查看所有的历史提交版本

```
$ git log
```

<img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210811172948105.png" alt="image-20210811172948105" style="zoom:67%;" />

## 3.git 撤销与回滚

#### a.git commit 之前

​	未添加到暂存区（撤销在文件里修改的内容）：

    ```
    $ git checkout -- 文件名
    ```



​	已经添加到暂存区（将添加到暂存区的文件撤销出来）：

~~~
$ git reset HEAD 文件名
~~~



#### b.git commit 之后

###### 删除提交的某个版本：

rebase命令删除的是输入的commit id 的**前一个版本**

~~~
$ git rebase -i 'commit id'
~~~

<img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210816140602265.png" alt="image-20210816140602265" style="zoom:50%;" />

按i后，将删除的版本前的pick改为d；

![image-20210816143051200](C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210816143051200.png)

~~~
pick：保留该commit（缩写:p）
reword：保留该commit，但我需要修改该commit的注释（缩写:r）edit：保留该commit, 但我要停下来修改该提交(不仅仅修改注释)（缩写:e）
squash：将该commit和前一个commit合并（缩写:s）
fixup：将该commit和前一个commit合并，但我不要保留该提交的注释信息（缩写:f）
exec：执行shell命令（缩写:x）
drop：我要丢弃该commit（缩写:d）
~~~



最后:按Esc 输入:wq保存退出

<img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210816143403945.png" alt="image-20210816143403945" style="zoom:67%;" />



###### 回到之前提交的某个版本：



```
$ git reset 'commit id' //commit 的后面的一串数字
```

<img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210816102016028.png" alt="image-20210816102016028" style="zoom:67%;" />



## 4.Git 冲突

Git冲突是在多用户协同工作下出现，在一些情况下Git可以智能自动合并，但有时需要用户手动合并。

具体情况：

(1)两个分支中修改了同一个文件

(2)两个分支中修改了同一个文件的名称

解决方法：

(1)在当前分支上，直接修改冲突代码  add——commit

(2)在本地当前分支上，修改冲突代码  add——commit——push



冲突的产生：刚开始我从远程仓库拉下了一个分支，并进行了修改，但是我的同事也拉下了同一个分支进行了修改并提交了。那么这个时候我推送分支到远程仓库时就会出错。于是我重新从远程仓库拉下同事新推送的分支，也会产生冲突。

解决冲突：权衡留下哪个版本。
