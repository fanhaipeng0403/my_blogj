
---
title: SSH config使用教程
date: 2018-01-17 15:14:50
tags: Nginx
---

SSH config是Linux系统下针对SSH客户端的一个参数配置方案，可以将一些关于SSH命令的参数放到配置文件中去，执行ssh命令的时候从文件中读取，简化命令行的操作。


# 配置ssh的config

```


# configuration 1
Host cluster
	HostName 192.168.11.11
	User tom


# configuration 2
Host  aliyun
	HostName=202.44.2.2
	User tom




# configuration 3


Host elk
  HostName 10.10.1.74
  User ubuntu
  
  #跳板机
  ProxyCommand ssh -W %h:%p fhp@54.157.70.250
  ForwardAgent yes

```

# 修改ssh会话的连接时间

1. 进入ssh目录：cd etc/ssh
2. 编辑sshd_config文件：vi sshd_config
3. 找到属性ClientAliveInterval和ClientAliveCountMax修改连接状态规则为：

```
　　　　ClientAliveInterval  3000
　　　　ClientAliveCountMax  10
```


4. `sudo /etc/init.d/ssh restart`


--------------------- 
