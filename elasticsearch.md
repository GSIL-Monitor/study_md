



```
can not run elasticsearch as root  
```

不能以root用户启动

```
[root@01 bin]# groupadd xiefy
[root@01 bin]# useradd xiefy -g xiefy -p 123123
[root@01 bin]# chown -R xiefy:xiefy elasticsearch
```



**错误二:**

```
ERROR: [2] bootstrap checks failed
[1]: max file descriptors [65535] for elasticsearch process is too low, increase to at least [65536]
[2]: max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]
```

> 错误[1]: max file descriptors过小

```
# 切换到root用户
vi /etc/security/limits.conf

# 添加如下
* soft nofile 65536
* hard nofile 65536
```

> 错误[2]: max_map_count过小
>
> max_map_count文件包含限制一个进程可以拥有的VMA(虚拟内存区域)的数量，系统默认是65530，修改成262144

```
# 切换到root用户
vi /etc/sysctl.conf

# 添加如下
vm.max_map_count=655360
# 重新加载配置文件或重启
sysctl -p # 从配置文件“/etc/sysctl.conf”加载内核参数设置
```

