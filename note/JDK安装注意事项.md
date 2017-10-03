## JDK安装注意事项(linux) {2017.10.3}
1. `清理系统默认自带的JDK`
```
rpm -qa | grep jdk 来查看已经自带的jdk,然后卸载。

卸载命令：
sudo yum remove XXX (XXX为上一个命令查到的结果)

如： sudo yum remove java-1.6.0-openjdk-1.6.0.38-1.13.10.4.el6.x86_64
```
2. `赋予权限`
```
sudo chmod 777 jdk-7u80-linux-x64.rpm
这里的jdk-7u80-linux-x64.rpm为下载的JDK的安装包
```
3. `安装`
```
sudo rpm -ivh jdk-7u80-linux-64.rpm
```
4. `默认安装路径/usr/java`
```
例如： /usr/java/jdk1.7.0_80
```
5. `JDK配置环境变量`
```
配置环境变量的步骤：
1) sudo vim /etc/profile
2) 在最下方增加
   export JAVA_HOME=/usr/java/jdk1.7.0_80
   export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
   注：JAVA_HOME为您安装JDK的路径
3)在export PATH中添加$JAVA_HOME/bin   //使到我们在不同的目录下都可以拿到JAVA_HOME/bin的各种命令
4)保存退出，通过vim的 :wq 命令进行保存退出
5)使配置生效 source /etc/profile
```
6. `JDK验证(linux)
```
1) 执行java -version命令，看到如下所示代表安装成功

result:
[Galen@Galen java]$ java -version
java version "1.7.0_80"
Java(TM) SE Runtime Environment (build 1.7.0_80-b15)
Java HotSpot(TM) 64-Bit Server VM (build 24.80-b11, mixed mode)
[Galen@Galen java]$ 

```

## JDK安装(windows)
1. `JDK安装`
1) 安装环境 ：`windows7 64位`
2) jdk版本： `7u80 64位`
3) 安装步骤： 安装jdk,下一步下一步...提示安装jre,继续下一步，安装成功。
2. `JDK环境变量配置`
1) 计算机属性->高级系统配置->高级->环境变量->系统变量中新建

2) 增加环境变量
JAVA_HOME
如： C:\Program Files\java\jdk1.7.0_80
CLASS_PATH
如：.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;
PATH中添加到jdk安装目录下的bin目录：
如：%JAVA_HOME%\bin;

3)jdk验证
执行`java -version`

result:
C:\Users\Administrator>java -version
java version "1.7.0_80"
Java(TM) SE Runtime Environment (build 1.7.0_80-b15)
Java HotSpot(TM) 64-Bit Server VM (build 24.80-b11, mixed mode)

