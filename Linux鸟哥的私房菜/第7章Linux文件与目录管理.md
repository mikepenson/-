# 第7章 Linux文件与目录管理
## 7.1 目录与路径
### 7.1.1 相对路径与绝对路径
* **绝对路径：**绝对路径的写法一定是由根目录`/`写起， 例如`/usr/share/doc`这个目录
* **相对路径：**路径的写法不是有`/`写起，例如由`/usr/share/doc`这个目录到`/usr/share/man`下面时，可以写成`cd ../man`，这就是相对路径的写法。

### 7.1.2 目录的相关操作
```
特殊目录
.	代表此层目录
..	代表上层目录
-	代表前一个工作目录
~ 	代表当前用户所在的主文件夹
~account	代表account这个用户的主文件夹（account是账号的名称）
```

* cd（切换目录）
* pwd（显示目前所在目录）
	- pwd -P（显示正确的完整路径）
* mkdir（新建新目录）
* rmdir（删除“空”目录）

### 7.1.3 关于执行文件路径的变量： $PATH
```
# 查看当前用户执行文件的路径
➜  ~ echo $PATH 
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/root/bin
# 将/root加入PATH中
➜  ~ PATH="$PATH":/root
```

## 7.2 文件与目录管理
* 查看文件与目录： `ls`
* 复制、删除与移动： `cp, rm, mv`

取得路径的文件名与目录名称

```
# 取得路径的文件名
➜  ~ basename /etc/sysconfig/network
network
➜  ~ dirname /etc/sysconfig/network
# 取得路径的目录名称
/etc/sysconfig
```

## 7.3 文件内容查阅

* cat： 由第一行开始显示文件内容（重要）
* tac： 从最后一行开始显示， tac是cat的倒写形式
* nl： 显示的时候顺便输出行号
* more： 一页一页地显示文件的内容
* less： 与more类似，但比more相比，支持往前翻页（重要）
* head： 只看头几行
* tail： 只看尾几行
* od： 以二进制的形式读取文件内容(不懂，第一次接触)
* touch： 修改文件时间或者创建新文件

```
# 显示最后的20行
➜  ~ tail -n 20 /etc/man_db.conf
# 显示100行以后的数据
➜  ~ tail -n +100 /etc/man_db.conf
# 持续监测man_db.conf内容
➜  ~ tail -f /etc/man_db.conf

# 新建空文件
➜  ~ touch testtouch
# 将testtouch文件的mtime调整至2天前
➜  ~ touch -d "2 days ago" testtouch
➜  ~ ls -l testtouch
-rw-r--r-- 1 root root 0 10月  7 23:39 testtouch
```

**Linux系统下文件的主要变动时间参数：**

* modification time（mtime）： 当该文件的“内容数据”更改时，就会更新这个时间；
* status time（ctime）： 当这个文件的“状态”改变时， 就会更新这个时间，如权限与属性被更改了， 都会更新这个时间
* access time（atime）： 当文件被读取时就会更新这个时间，如cat去读文件就会更新该文件的atime


## 7.4 文件与目录的默认权限与隐藏权限
### 7.4.1 文件默认权限： umask
umask就是指定“目前用户在新建文件或目录时候的权限默认值”，该默认值是需要被减掉的权限

在默认权限的属性上，目录与文件是不一样的：

* 用户新建“文件”默认权限： -rw-rw-rw-
* 用户新建“目录”默认权限： drwxrwxrwx
* 新建文件时： （-rw-rw-rw-）-（-----w-w-）==> -rw-r--r--
* 新建目录时：（drwxrwxrwx）-（d----w--w-）==> drwxr-xr-x

```
➜  ~ umask
022
➜  ~ umask -S
u=rwx,g=rx,o=rx
➜  ~ umask 002 # 默认权限减去其他身份的写权限
```

### 7.4.2 文件隐藏属性chattr， lsattr
chattr命令只能在Ext2/Ext3的文件系统上使用

```
➜  ~ chattr +i test # test不能被删除、改名，设置连接也无法写入或者添加数据
➜  ~ chattr -i test
➜  ~ chattr +a test # 被添加数据，不能被删除或者修改，设置连接也无法写入或者添加数据
➜  ~ chattr -a test

➜  ~ lsattr nohup.out   # 显示文件隐藏属性
```

### 7.4.3 文件特殊权限SUID， SGID， SBIT



