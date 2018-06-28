### Linux中如何开启8080端口供外界访问

Centos7默认安装了firewalld，如果没有安装的话，则需要YUM命令安装；firewalld真的用不习惯，与之前的iptable防火墙区别太大，但毕竟是未来主流讲究慢慢磨合它的设置规则；

#### Firewall端口配置
安装Firewall命令：
```
yum install firewalld firewalld-config
```

**Firewall开启常见端口命令**：
```
firewall-cmd --zone=public --add-port=80/tcp --permanent
firewall-cmd --zone=public --add-port=443/tcp --permanent
firewall-cmd --zone=public --add-port=22/tcp --permanent
firewall-cmd --zone=public --add-port=21/tcp --permanent
firewall-cmd --zone=public --add-port=53/udp --permanent
```

**Firewall关闭常见端口命令**：
```
firewall-cmd --zone=public --remove-port=80/tcp --permanent
firewall-cmd --zone=public --remove-port=443/tcp --permanent
firewall-cmd --zone=public --remove-port=22/tcp --permanent
firewall-cmd --zone=public --remove-port=21/tcp --permanent
firewall-cmd --zone=public --remove-port=53/udp --permanent
```
**批量添加区间端口**
```
firewall-cmd --zone=public --add-port=4400-4600/udp --permanent
firewall-cmd --zone=public --add-port=4400-4600/tcp --permanent
```

**开启防火墙命令**：
```
systemctl start firewalld.service
```

**重启防火墙命令**：
```
firewall-cmd --reload  或者   service firewalld restart
```
**查看端口列表**：
```
firewall-cmd --permanent --list-port
```

**禁用防火墙**：
```
systemctl stop firewalld
```

**设置开机启动**
```
systemctl enable firewalld
```

**停止并禁用开机启动**
```
sytemctl disable firewalld
```

**查看状态**
```
systemctl status firewalld或者 firewall-cmd --state
```


#### 参考
1. [Centos7（Firewall）防火墙开启常见端口命令](https://www.5yun.org/10074.html)
2. [linux系统分析工具之netstat（六）](http://blog.51cto.com/xuclv/1166393)
3. [每天一个linux命令（56）：netstat命令](http://www.cnblogs.com/peida/archive/2013/03/08/2949194.html)
4. [Linux查看端口占用情况和开启端口命令](https://blog.csdn.net/ljbmxsm/article/details/50650008)
5. [linux如何查看正在使用的端口](https://blog.csdn.net/q361239731/article/details/53180126)


