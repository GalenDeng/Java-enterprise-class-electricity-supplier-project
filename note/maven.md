## *maven* (2017.10.11)
 1. `简介`
 
* Maven是Java项目的构建和管理工具
* 作用
```
1)用Maven可以方便的创建项目基于archetype可以创建多种类型的java项目
2)Maven仓库对jar包(artifact)进行统一管理，避免jar文件的重复拷贝和版本冲突
3)团队开发，Maven管理项目的RELEASE(正式发布版本)和SNAPSHOT(快照版本)版本，方便多模块(Modeule)项目的
  各个模块之间的快速集成
```
2. `Maven安装(linux)`
```
1) 安装系统环境
   CentOS 6.8 64位
2) 安装版本
   3.0.5
3) 安装步骤
* 首先要确保电脑上已经安装了JDK
* 登录这里下载3.0.5版本
  https://mirrors.tuna.tsinghua.edu.cn/apache/maven/maven-3/3.0.5/binaries/
* 通过tar 或 unzip进行解压缩
  tar -zxvf package_name
* 配置环境变量
* 1) sudo /etc/profile 在最下面增加Maven的环境变量
* 2) export MAVEN_HOME=_DIR__MAVEN_unpackage_PATH
     注： "="后边是安装在系统中Maven解压缩后的位置
* 3) export PATH=$PATH:$JAVA_HOME/bin:$MAVEN_HOME/bin
* 4) 执行source /etc/profile,使之生效，如下图所示：
```
 