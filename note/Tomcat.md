## Tomcat
1. `简介`
```
Tomcat是一个web容器,JavaEE程序可以在此运行
```
2. `安装注意`
```
安装tomcat之前需要安装好jdk
```

### *linux系统*
3. `从给出的网址中下载`
```
wget http://download.happymmall.com/tomcat/apache-tomcat-7.0.73.tar.gz

```
4. `解压缩`
```
tar -zxvf apache-tomcat-7.0.73.tar.gz
```
5. `配置环境变量`
```
1)sudo vim  /etc/profile
2)export CATALINA_HOME=/developer/apache-tomcat-7.0.73.tar.gz
注：CATALINA_HOME为您安装tomcat的路径
3)通过vim的:wq命令进行保存退出
4)使配置生效 source /etc/profile
```
6. `配置UTF-8字符集`--`解决乱码问题`
```
1)进入tomcat安装的conf文件夹，编辑server.xml
  如：${CATALINA_HOME}/conf/server.xml
2)找到配置8080默认端口的位置,在xml节点末尾增加URIEncoding="UTF-8"
如：
    <Connector port="8080" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" URIEncoding="UTF-8" />
```
7. `Tomcat验证(linux)`
```
1)进入系统解压缩后的tomcat目录
2)进入bin的目录
3)执行./startup.sh
看到如图表示启动成功：
[Galen@Galen bin]$ sudo ./startup.sh 
Using CATALINA_BASE:   /usr/local/src/apache-tomcat-7.0.73
Using CATALINA_HOME:   /usr/local/src/apache-tomcat-7.0.73
Using CATALINA_TMPDIR: /usr/local/src/apache-tomcat-7.0.73/temp
Using JRE_HOME:        /usr
Using CLASSPATH:       /usr/local/src/apache-tomcat-7.0.73/bin/bootstrap.jar:/usr/local/src/apache-tomcat-7.0.73/bin/tomcat-juli.jar
Tomcat started.

4)打开启动tomcat机器的IP地址和默认的8080端口,本机请访问http://localhost:8080

5)如果用其他机器访问(如虚拟机安装的CentOS),请执行ifconfig,找到此
机器的IP地址，进行访问
如：
http://192.168.135.129:8080/

6)如果没有见到Apache Tomcat/7.0.73的页面，可能是linux的防火墙导致的，可以尝试 iptables -F 关闭防火墙
```
### *windows系统*
3. `安装系统环境`
```
Windows7 64位
```
4. `Tomcat版本`
```
Tomcat7
```
5. `安装步骤`
```
1) 下载
  [登录](http://learning.happymmall.com/tomcat/)进行下载
2)解压缩
3)Tomcat环境变量配置
   * 计算机属性->高级系统配置->高级->环境变量->系统变量中新建
   * 增加环境变量
     CATALINA_HOME 如：D:\Program Files\windows_apache-tomcat-7.0.75\apache-tomcat-7.0.75
4)配置UTF-8字符集
   * 进入到Tomcat安装的conf文件夹，编辑server.xml
   * 找到配置8080默认端口的位置,在xml节点末尾增加URIEncoding="UTF-8"
```
6. `Tomcat验证(windows)`
```
1)进入系统解压缩后的tomcat目录
2)进入bin的目录
3)执行./startup.bat
看到Tomcat的窗口，并且有Server startup in 1343 ms 的英文提示,表示启动成功：
4)浏览器中输入： http://localhost:8080/  or  http://127.0.0.1:8080/  来进入Tomcat的页面
```
### *Tomcat的常用命令*
1. `Tomcat启动`
* linux：  ${CATALINA_HOME}/bin/startup.sh
* windows: ${CATALINA_HOME}/bin/startup.bat

2.  `Tomcat关闭`
* linux：  ${CATALINA_HOME}/bin/shutdown.sh
* windows: ${CATALINA_HOME}/bin/shutdown.bat