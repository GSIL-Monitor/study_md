### ElasticSearch

---



#### 一: 安装和启动

#####  1. ElasticSearch下载

> 官方地址: https://www.elastic.co/cn/downloads/elasticsearch
>
> github: https://github.com/elastic/elasticsearch

下载或clone后解压



##### 2. 单实例节点启动

```
# cd elasticsearch目录下
bin/elasticsearch
bin/elasticsearch -d # 后台启动
```

默认端口9200, 启动完成后访问`http://ip:9200` 即可查看到集群信息

启动中我遇到两个错误: 

**错误一:** 

```
can not run elasticsearch as root  
-- 不能以root用户启动
```

```
[root@01 bin]# groupadd xiefy
[root@01 bin]# useradd xiefy -g xiefy -p 123123
[root@01 bin]# chown -R xiefy:xiefy elasticsearch
```



**错误二:**

```shell
ERROR: [2] bootstrap checks failed
[1]: max file descriptors [65535] for elasticsearch process is too low, increase to at least [65536]
[2]: max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]

-- 错误[1]: max file descriptors过小
-- 错误[2]: max_map_count过小, max_map_count文件包含限制一个进程可以拥有的VMA(虚拟内存区域)的数量，系			  统默认是65530，修改成262144
```

```
# 切换到root用户
vi /etc/security/limits.conf

# 添加如下
* soft nofile 65536
* hard nofile 65536
```

```
# 切换到root用户
vi /etc/sysctl.conf

# 添加如下
vm.max_map_count=655360
# 重新加载配置文件或重启
sysctl -p # 从配置文件“/etc/sysctl.conf”加载内核参数设置
```



##### 3. elasticsearch-head插件安装

>   一个用于浏览Elastic Search集群并与之进行交互(操作和管理)的web界面
>
>   GitHub: https://github.com/mobz/elasticsearch-head
>
>   要使用elasticsearch-head, 需要具备nodejs环境: 

**nodejs安装**

>  下载源码: https://nodejs.org/en/download/

安装方式有多种, 我用源码安装方式(包含npm)

1. 下载源码:

   ```
   https://nodejs.org/dist/v8.9.4/node-v8.9.4.tar.gz
   ```

2. 解压源码: 

   ```
   tar xzvf node-v* && cd node-v*
   ```

3. 安装必要的编译软件

   ```
   sudo yum install gcc gcc-c++
   ```

4. 编译

   ```
   ./configure
   make
   ```

5. 编译&安装

   ```
   sudo make install
   ```

6. 查看版本

   ```
   node --version
   npm -version
   ```

   ​

下载或克隆`elasticsearch-head`后, 进入`elasticsearch-head-master`目录:

- `npm install` 

  速度太慢可以使用淘宝镜像: `npm install -g cnpm --registry=https://registry.npm.taobao.org`

- `npm run start`

- open <http://localhost:9100/>

这时可以访问到页面, 并没有监听到集群.

解决head插件和elasticsearch之间的访问跨域问题. 

修改elasticsearch目录下的`elasticsearch.yml`

```
# 加入以下内容
http.cors.enabled: true
http.cors.allow-origin: "*"
```

然后: http://localhost:9100/ 即可访问到管理页面. 



##### 4. 分布式安装启动

elasticsearch的横向扩展很容易: 这里建立一个主节点(node-master), 两个随从节点(node-1, node-2)

我提前拷贝了三个es:

```shell
[xiefy@01 elk]$ ll
total 33620
-rw-r--r-- 1 root  root  33485703 Aug 17 22:42 elasticsearch-5.5.2.tar.gz
drwxr-xr-x 7 root  root      4096 Jan  8 11:17 elasticsearch-head-master
drwxr-xr-x 9 xiefy xiefy     4096 Jan  8 10:15 elasticsearch-master
drwxr-xr-x 9 xiefy xiefy     4096 Jan  8 14:13 elasticsearch-node1
drwxr-xr-x 9 xiefy xiefy     4096 Jan  8 14:16 elasticsearch-node2
-rw-r--r-- 1 root  root    921421 Jan  8 11:14 master.zip
```



分别在三个es目录中的`config/elasticsearch.yml`中加入

**node-master**:

```
cluster.name: xiefy_elastic 
node.name: node-master 
node.master: true 
network.host: 0.0.0.0 

# 除此之外, head插件需要连接到port: 9200的节点上, 还需要这个配置
http.cors.enabled: true
http.cors.allow-origin: "*"
```

**node-1**:

```
cluster.name: xiefy_elastic 
node.name: node-1
network.host: 0.0.0.0
http.port: 9201 
discovery.zen.ping.unicast.hosts: ["127.0.0.1"]
```

**node-2**:

参考node-1



相关配置解释: 

* cluster.name: 集群名称, 默认是elasticsearch

* node.name: 节点名称, 默认随机分配

* node.master: 是否是主节点, 默认情况下不写也可以, 第一个起来的就是Master

* network.host: 默认情况下只允许本机通过localhost或127.0.0.1访问, 为了测试方便, 

  我需要远程访问所以配成了`0.0.0.0`

* http.port: 默认为9200, 同一个服务器下启动多个es节点, 默认端口号会从9200默认递增1, 这里我手动指定了

* discovery.zen.ping.unicast.hosts: ["host1", "host2"]

  Elasticsearch默认使用服务发现(Zen discovery)作为集群节点间发现和通信的机制, 当启动新节点时，通过这个ip列表进行节点发现，组建集群.



分别启动三个es实例和head插件:

访问`http://ip:9100`:

![](http://thank-bucket-01.oss-cn-beijing.aliyuncs.com/md_pic/es%E4%B8%89%E4%B8%AA%E8%8A%82%E7%82%B9%E9%9B%86%E7%BE%A4.png)

#### 二: 基础概念

....



#### 三: 基础用法

##### 1. 索引

* 方式一: head插件可以直接新建/删除/查询索引(Index)

* 方式二: 通过rest api 

  ```shell
  # 新建
  curl -X PUT 'localhost:9200/book'
  # 成功返回 {"acknowledged":true,"shards_acknowledged":true}

  # 删除
  curl -X DELETE 'localhost:9200/book'

  # 查看当前节点下所有Index
  curl -X GET 'http://localhost:9200/_cat/indices?v'
  ```

这样创建的Index是没有结构的. 可以看到索引信息的mappings:{}

下面来定义一个有结构映射的Index

> PUT http://ip:9200/people

```json
{
	"settings": {
		"number_of_shards": 3,
		"number_of_replicas": 1
	},
	"mappings": {
		"man": {
			"properties": {
				"name": {"type": "text"},
				"country": {"type": "keyword"},
				"age": {"type": "integer"},
				"birthday": {
					"type": "date",
					"format": "yyyy-MM-dd HH:mm:ss||yyyy-MM-dd||epoch_millis"
				}
			}
		},
		"women": {
			
		}
	}
}
```

里面设置了分片数, 备份数, 和两个type的结构映射.



##### 插入数据

> PUT http://47.94.210.157:9200/people/man/1
>
> 指定ID为1 

```
{
	"name": "伊布",
	"country": "瑞典",
	"age": 30,
	"birthday": "1988-12-12"
}
```



如果不指定ID, 会生成为随机字符串, 此时需要改为POST方式



##### 查看数据

> ```
> http://ip:9200/people/man/1?pretty=true
> ```