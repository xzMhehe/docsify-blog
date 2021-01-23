## RabbitMQ引言
RabbitMQ是实现了高级消息队列协议（`AMQP`）的开源消息代理软件（亦称面向消息的中间件）。RabbitMQ服务器是用Erlang语言编写的，而集群和故障转移是构建在开放电信平台框架上的。所有主要的编程语言均有与代理接口通讯的客户端库。


- rabbitmq 官网：https://www.rabbitmq.com/
- erlang 环境 https://www.erlang.org/downloads           https://github.com/erlang/otp/releases

|RabbitMQ version|Minimum required Erlang/OTP|Maximum supported Erlang/OTP|
| - | - | - |
|3.8.10、3.8.9| 22.3 | 23.x |

- AMQP协议
AMQP（advanced message queuing protocol）`在2003年时被提出，最早用于解决金融领不同平台之间的消息传递交互问题。顾名思义，AMQP是一种协议，更准确的说是一种binary wire-level protocol（链接协议）。这是其和JMS的本质差别，AMQP不从API层进行限定，而是直接定义网络交换的数据格式。这使得实现了AMQP的provider天然性就是跨平台的。以下是AMQP协议模型:
![](https://image.codingce.com.cn/20210122111115.png)

## 安装
### Windows 安装
- 安装 erlang环境
- 配置 erlang环境变量
- 安装 rabbitmq

#### 使用
sbin 目录下
- RabbitMQ Service-install 安装服务
- RabbitMQ Service-remove 删除服务
- RabbitMQ Service-start 启动
- RabbitMQ Service-stop 启动


#### 访问 RabbitMQ 主页
在`sbin`目录启动控制台, 输入以下命令
```bash
rabbitmq-plugins.bat enable rabbitmq_management
```

通过 http://localhost:15672 访问

>默认账号密码: guest|guest


注意一点：当卸载重新安装的时候会出现 RabbitMQ 服务注册失败, 此时需要进入注册表 清理erlang 搜索 RabbitMQ ErlSrv, 对应的项全部删除


### Linux 安装
- 1.将rabbitmq安装包上传到linux系统中
	erlang-22.0.7-1.el7.x86_64.rpm
	rabbitmq-server-3.7.18-1.el7.noarch.rpm

- 2.安装Erlang依赖包
	rpm -ivh erlang-22.0.7-1.el7.x86_64.rpm

- 3.安装RabbitMQ安装包(需要联网)
	yum install -y rabbitmq-server-3.7.18-1.el7.noarch.rpm
		注意:默认安装完成后配置文件模板在:/usr/share/doc/rabbitmq-server-3.7.18/rabbitmq.config.example目录中,需要	
				将配置文件复制到/etc/rabbitmq/目录中,并修改名称为rabbitmq.config
- 4.复制配置文件
	cp /usr/share/doc/rabbitmq-server-3.7.18/rabbitmq.config.example /etc/rabbitmq/rabbitmq.config

- 5.查看配置文件位置
	ls /etc/rabbitmq/rabbitmq.config

- 6.修改配置文件(参见下图:)
	vim /etc/rabbitmq/rabbitmq.config

![](https://image.codingce.com.cn/20210122111442.png)


将上图中配置文件中红色部分去掉`%%`,以及最后的`,`逗号 修改为下图:
![](https://image.codingce.com.cn/20210122111518.png)

- 7.执行如下命令,启动rabbitmq中的插件管理
	rabbitmq-plugins enable rabbitmq_management
	
	出现如下说明:
		Enabling plugins on node rabbit@localhost:
    rabbitmq_management
    The following plugins have been configured:
      rabbitmq_management
      rabbitmq_management_agent
      rabbitmq_web_dispatch
    Applying plugin configuration to rabbit@localhost...
    The following plugins have been enabled:
      rabbitmq_management
      rabbitmq_management_agent
      rabbitmq_web_dispatch

    set 3 plugins.
    Offline change; changes will take effect at broker restart.

- 8.启动RabbitMQ的服务
	systemctl start rabbitmq-server
	systemctl restart rabbitmq-server
	systemctl stop rabbitmq-server
	

- 9.查看服务状态(见下图:)
	systemctl status rabbitmq-server
  ● rabbitmq-server.service - RabbitMQ broker
     Loaded: loaded (/usr/lib/systemd/system/rabbitmq-server.service; disabled; vendor preset: disabled)
     Active: active (running) since 三 2019-09-25 22:26:35 CST; 7s ago
   Main PID: 2904 (beam.smp)
     Status: "Initialized"
     CGroup: /system.slice/rabbitmq-server.service
             ├─2904 /usr/lib64/erlang/erts-10.4.4/bin/beam.smp -W w -A 64 -MBas ageffcbf -MHas ageffcbf -
             MBlmbcs...
             ├─3220 erl_child_setup 32768
             ├─3243 inet_gethost 4
             └─3244 inet_gethost 4
      .........

![](https://image.codingce.com.cn/20210122111606.png)

- 10.关闭防火墙服务
	systemctl disable firewalld
    Removed symlink /etc/systemd/system/multi-user.target.wants/firewalld.service.
    Removed symlink /etc/systemd/system/dbus-org.fedoraproject.FirewallD1.service.
	systemctl stop firewalld   

也可以放开15672端口

- 11.访问web管理界面
	http://服务器ip:15672/



![](https://image.codingce.com.cn/20210122111701.png)


>文章已上传gitee https://gitee.com/codingce/hexo-blog   
>项目地址: https://github.com/xzMhehe/codingce-java