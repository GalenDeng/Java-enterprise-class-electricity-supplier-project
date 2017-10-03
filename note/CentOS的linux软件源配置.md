 ## CentOS的ssh操作 (2017.10.03)
 1. `ssh Galen@192.168.135.129` 
 ```
其中: Galen : ssh登入的用户名
    192.168.135.129 ： ssh登入的用户的IPv4的地址
 ```

 2. `把版本和软件源设置和阿里云的一样`并`生成缓存`
 ```
 地址为： 
 http://mirrors.aliyun.com/help/centos

 centos 6: 

1) sudo wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-6.repo

rusult:
--2017-10-03 12:28:50--  http://mirrors.aliyun.com/repo/Centos-6.repo
Resolving mirrors.aliyun.com... 113.107.235.238, 121.10.25.108, 121.10.25.110, ...
Connecting to mirrors.aliyun.com|113.107.235.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2572 (2.5K) [application/octet-stream]
Saving to: “/etc/yum.repos.d/CentOS-Base.repo”

100%[==============================================>] 2,572       --.-K/s   in 0s      

2017-10-03 12:28:50 (108 MB/s) - “/etc/yum.repos.d/CentOS-Base.repo” saved [2572/2572]


生成缓存：
2) yum makecache

rusult:
[Galen@Galen ~]$ yum makecache
Loaded plugins: fastestmirror, refresh-packagekit, security
Determining fastest mirrors
 * base: mirrors.aliyun.com
 * extras: mirrors.aliyun.com
 * updates: mirrors.aliyun.com
base                                                             | 3.7 kB     00:00     
base/group_gz                                                    | 226 kB     00:00     
base/filelists_db                                                | 6.4 MB     00:03     
base/primary_db                                                  | 4.7 MB     00:01     
base/other_db                                                    | 2.8 MB     00:01     
extras                                                           | 3.4 kB     00:00     
extras/filelists_db                                              |  25 kB     00:00     
extras/prestodelta                                               | 1.3 kB     00:00     
extras/primary_db                                                |  29 kB     00:00     
extras/other_db                                                  |  30 kB     00:00     
updates                                                          | 3.4 kB     00:00     
updates/filelists_db                                             | 2.3 MB     00:01     
updates/prestodelta                                              | 108 kB     00:00     
updates/primary_db                                               | 3.7 MB     00:01     
updates/other_db                                                 |  50 MB     00:25     
Metadata Cache Created

 ```

 3. `利用sudo命令来执行超级用户的权限的方法`
 ```
$whereis sudoers －－－－－－－找出文件所在的位置，默认都是/etc/sudoers    
 在ubuntu中由于禁用了root用户，默认情况下会把安装系统时建立的用户添加到sudoers中。但在redhat和centos中并没有把任何root用户之外的用户默认的添加到sudoers之中。这样我们在执行sudo 命令时就会出现xxx is not in the sudoers file. This incident will be reported.这样的错误输出。现在为了安全起见比较提倡使用普通用户做日常操作，而在需要超级用户的时候使用sudo 来做，这样，我们就有必要把一些用户添加到sudoers之中。

1).首先利用whereis 命令查找sudoers配置文件的目录（默认会在/etc/sudoers)
[root@localhost xiaofei]# whereis sudoers
sudoers: /etc/sudoers /etc/sudoers.bak /usr/share/man/man5/sudoers.5.gz

2)然后需要切换到root用户，更改/etc/sudoers的权限
[root@localhost xiaofei]# chmod u+w /etc/sudoers

3)然后就可以利用vi编辑器来把用户添加到sudoers之中
[root@localhost xiaofei]# vi /etc/sudoers
然后找到root    ALL=(ALL)       ALL所在的位置，把所要添加的用户添加到文件之中，

顺便提一下vi编辑器的用法。刚进入vi编辑器的时候牌命令行模式，这时可以通过方向键来移动光标，找到要编辑的位置之后按下“i”，然后就进入了插入模 式，这时候你可以输入或删除字符。编辑完成之后按“esc”键退出插入模式，进入命令行模式，这时候按“：”可以进入末行模式，输入“wq”保存并退出。

下面是添加完的结果。
## Allow root to run any commands anywhere
root    ALL=(ALL)       ALL
xiaofei ALL=(ALL)       ALL              （这一行是添加的内容，xiaofei是我的用户名）
然后需要把sudoers 的写权限去掉（否则系统不允许执行suoders文件）：
[root@localhost xiaofei]# chmod u-w /etc/sudoers
至此，在退出root用户之后就可以利用sudo命令来执行超级用户的权限了。
```

