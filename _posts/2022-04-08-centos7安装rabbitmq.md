## centos7安装rabbitmq

### 1. 安装依赖文件

> ​	yum install gcc glibc-devel make ncurses-devel openssl-devel xmlto

### 2.下载erlang和rabbitmq安装包

> ​	传送门	https://www.erlang.org/downloads
>

​	本次示例版本采用是如下图

​		![image-20210823092538512](https://cdn.jsdelivr.net/gh/skyunique/uploadPic/img/20220408140115.png)

### 3.安装 erlang

> 将安装包上传到/usr/local/下

```shell
--解压
cd /usr/local
tar -zxvf otp_src_24.0.tar.gz
cd otp_src_24.0/
--编译安装
./configure --prefix=/usr/local/erlang
make && make install


参考：
--#配置 '--prefix'指定的安装目录
#./configure --prefix=/usr/local/erlang --with-ssl -enable-threads -enable-smmp-support -enable-kernel-poll --enable-hipe --without-javac
```

> ​	注意以下问题：![image-20210820155907653](https://cdn.jsdelivr.net/gh/skyunique/uploadPic/img/20220408140125.png)

```
sudo yum install ncurses-devel.x86_64
```

> --检查是否安装成功

```
cd /usr/local/erlang
./erl
--输入 halt(). 退出控制台
```

![image-20210820162116749](https://cdn.jsdelivr.net/gh/skyunique/uploadPic/img/20220408140135.png)

> ​     配置环境变量

```
vim /etc/profile
#在文件末尾添加下面代码 'ERLANG_HOME'等于上一步'--prefix'指定的目录
ERLANG_HOME=/usr/local/erlang
PATH=$ERLANG_HOME/bin:$PATH
export ERLANG_HOME
export PATH
末尾加上：export PATH=$PATH:/usr/local/erlang/bin
#使环境变量生效
source /etc/profiles
```

![image-20210820162444918](https://gitee.com/skyunique7/upload-pic/raw/master/img/20210820162444.png)		

### 4.安装RabbitMQ

> 传送门：https://github.com/rabbitmq/rabbitmq-server/releases/

```
#解压rabbitmq，官方给的包是xz压缩包，所以需要使用xz命令
xz -d rabbitmq-server-generic-unix-3.9.4.tar.xz

#xz解压后得到.tar包，再用tar命令解压
tar -xvf rabbitmq-server-generic-unix-3.6.1.tar


#移动目录 
cp -rf ./rabbitmq_server-3.6.1 /usr/local/
cd /usr/local/
mv rabbitmq_server-3.9.4 rabbitmq-3.9.4

#开启管理页面插件
cd ./rabbitmq-3.6.1/sbin/
./rabbitmq-plugins enable rabbitmq_management
```

![image-20210823092227787](https://cdn.jsdelivr.net/gh/skyunique/uploadPic/img/20220408140143.png)

> 启动

```
#启动命令
#启动命令，该命令ctrl+c后会关闭服务
./rabbitmq-server
 
#在后台启动Rabbit
./rabbitmq-server -detached

#查看服务状态
./rabbitmq-server status

#停止服务
./rabbitmq-server stop

#关闭服务
./rabbitmqctl stop
 
#关闭服务(kill) 找到rabbitmq服务的pid   [不推荐]
ps -ef|grep rabbitmq
kill -9 ****
```

> 添加管理员账号

```
#进入RabbitMQ安装目录
cd /usr/local/rabbitmq-3.9.4/sbin
 
#添加用户
#rabbitmqctl add_user Username Password
./rabbitmqctl add_user rabbitadmin 123456
 
#分配用户标签
#rabbitmqctl set_user_tags User Tag
#[administrator]:管理员标签
./rabbitmqctl set_user_tags rabbitadmin administrator

# 设置用户权限，用户YAGBIHO具有/vhost这个virtual host中所有资源的配置、写、读权限
# set_permissions [-p <vhostpath>] <user> <conf> <write> <read>
./rabbitmqctl set_permissions -p "/" rabbitadmin ".*" ".*" ".*"


```

![image-20210823104739042](https://cdn.jsdelivr.net/gh/skyunique/uploadPic/img/20220408141139.png)

> 登录  [http://服务器IP地址:15672/](http://xn--ip-fr5c86lw2a0cw16k:15672/)

![image-20210823104833326](https://cdn.jsdelivr.net/gh/skyunique/uploadPic/img/20220408141146.png)

