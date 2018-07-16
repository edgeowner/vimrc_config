## 端口查询命令
### netstat命令
常见参数：
```
-a (all)显示所有选项，默认不显示LISTEN相关
-t (tcp)仅显示tcp相关选项
-u (udp)仅显示udp相关选项
-n 拒绝显示别名，能显示数字的全部转化成数字。
-l 仅列出有在 Listen (监听) 的服務状态

-p 显示建立相关链接的程序名
-r 显示路由信息，路由表
-e 显示扩展信息，例如uid等
-s 按各个协议进行统计
-c 每隔一个固定时间，执行该netstat命令。
注：LISTEN和LISTENING的状态只有用-a或者-l才能看到
```

### 命令实例
#### 1. 列出所有端口 (包括监听和未监听的)
```
列出所有端口 netstat -a
netstat -a | more
```
```
列出所有 tcp 端口 netstat -at
netstat -at
```
```
列出所有 udp 端口 netstat -au
netstat -au
```
#### 2. 列出所有处于监听状态的 Sockets
```
只显示监听端口 netstat -l
```
```
只列出所有监听 tcp 端口 netstat -lt
```
```
只列出所有监听 udp 端口 netstat -lu
```
```
只列出所有监听 UNIX 端口 netstat -lx
```

#### 3. 列出所有处于监听状态的 Sockets
```
显示所有端口的统计信息 netstat -s
```
```
显示 TCP 或 UDP 端口的统计信息 netstat -st 或 -su
```
#### 4. 在 netstat 输出中显示 PID 和进程名称 netstat -p

```
netstat -p 可以与其它开关一起使用，就可以添加 “PID/进程名称” 到 netstat 输出中，这样 debugging 的时候可以很方便的发现特定端口运行的程序。
```

#### 5. 在 netstat 输出中不显示主机，端口和用户名 (host, port or user)
```
当你不想让主机，端口和用户名显示，使用 netstat -n。将会使用数字代替那些名称。
同样可以加速输出，因为不用进行比对查询。
netstat -an  

如果只是不想让这三个名称中的一个被显示，使用以下命令
netsat -a --numeric-ports
netsat -a --numeric-hosts
netsat -a --numeric-users
```

#### 6. 持续输出 netstat 信息
netstat 将每隔一秒输出网络信息。
```
netstat -- c
```

#### 7. 显示系统不支持的地址族 (Address Families)
```
netstat --verbose
```

#### 8. 显示核心路由信息 netstat -r
```
netstat -r
```

#### 9. 找出程序运行的端口
并不是所有的进程都能找到，没有权限的会不显示，使用 root 权限查看所有的信息。
```
netstat -ap | grep ssh
```

找出运行在指定端口的进程
```
netstat -an | grep ':80'
```

#### 10. 显示网络接口列表
```
netstat -i
```
```
显示详细信息，像是 ifconfig 使用 netstat -ie
```

#### 11. IP和TCP分析
查看连接某服务端口最多的的IP地址
```
netstat -nat |awk '{print $6}'
```

#### 12. 查询网络端口占用情况
netstat命令
```
netstat -an | grep 3306
```
lsof命令
```
lsof -i:80
```
查看所有进程监听的端口
```
sudo lsof -i -P | grep -i "listen"
```


### 参考：
1.[Linux netstat命令详解](https://www.cnblogs.com/ggjucheng/archive/2012/01/08/2316661.html)
















