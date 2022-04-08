---
layout:     post
title:      Mac配置JDK环境变量
subtitle:   JDK配置详解
date:       2022-03-16
author:     skyunique
header-img: img/post-bg-os-metro.jpg
catalog: 	 true
tags:
    - MACOS
    - CENTOS7

---

# 前言

​				MAC配置多版本的jdk，用于多项目环境切换使用

# 正文


```
export JAVA_7_HOME=/Library/Java/JavaVirtualMachines/jdk1.7.0_80.jdk/Contents/Home

export PATH=$PATH:$JAVA_HOME/bin:$JAVA_HOME/jre/bin

export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
```

```
export JAVA_8_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_251.jdk/Contents/Home

export PATH=$PATH:$JAVA_HOME/bin:$JAVA_HOME/jre/bin

export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
```

```
export JAVA_8_ORCL_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_181.jdk/Contents/Home

export PATH=$PATH:$JAVA_HOME/bin:$JAVA_HOME/jre/bin

export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
```



```
# 默认JDK版本为1.7

export JAVA_HOME=$JAVA_7_HOME
```

```
# alias切换JDK版本

alias jdk7="export JAVA_HOME=$JAVA_7_HOME"

alias jdk8="export JAVA_HOME=$JAVA_8_HOME"

alias jdk8_orcl="export JAVA_HOME=$JAVA_8_ORCL_HOME"

```

```
注：
	1、切换环境变量时使用命令：jdk7或者是jdk8
	2、每次切换环境变量时需要执行命令：source ~/.bash_profile，然后执行1命令才能切换成功
```

```
注：
	1、当tomcat没有运行 .sh 命令的权限时，使用 chmod +x *.sh 命令给以后缀为.sh的运行命令赋权限
	2、当前命令在tomcat的bin目录下运行（不确定，还未测试是否在其他地方此命令也好用，我正好在bin目录下运行了）
```



```
1、下载后缀名称为.dmg的JDK安装呗
2、双击安装JDK
3、command+shift+G跳转JDK安装路径（/Library/Java/JavaVirtualMachines）
4、cat ~/.bash_profile命令查看当前配置
5、vi ~/.bash_profile修改该配置文件，配置安装的JDK路径
6、保存，使用alias配置查看当前环境所配置的JDK
```



