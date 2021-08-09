## Redis安装

- 步骤1：在[Redis官网](https://redis.io/)下载Redis，Windows直接下载或者Linux下使用wget都可以

```bash
$ wget https://download.redis.io/releases/redis-6.2.6.tar.gz
```

- 步骤2：解压Redis压缩包

```bash
$ tar -zxvf redis-6.2.6.tar.gz -C /opt
```

- 步骤3：编译Redis源码
```bash
$ cd redis-6.2.6/
$ make
```
- 步骤4：安装Redis（将Redis程序拷贝到/usr/local/bin/目录下，使得Redis命令可以在任意位置调用）
```bash
$ make install
```

## Redis简单测试
```
[root@server redis-6.2.6]# redis-server &
[1] 22868
[root@server redis-6.2.6]# 22868:C 26 Oct 2021 22:39:39.084 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
22868:C 26 Oct 2021 22:39:39.084 # Redis version=6.2.6, bits=64, commit=00000000, modified=0, pid=22868, just started
22868:C 26 Oct 2021 22:39:39.084 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
22868:M 26 Oct 2021 22:39:39.084 * monotonic clock: POSIX clock_gettime
                _._                                                  
           _.-``__ ''-._                                             
      _.-``    `.  `_.  ''-._           Redis 6.2.6 (00000000/0) 64 bit
  .-`` .-```.  ```\/    _.,_ ''-._                                  
 (    '      ,       .-`  | `,    )     Running in standalone mode
 |`-._`-...-` __...-.``-._|'` _.-'|     Port: 6379
 |    `-._   `._    /     _.-'    |     PID: 22868
  `-._    `-._  `-./  _.-'    _.-'                                   
 |`-._`-._    `-.__.-'    _.-'_.-'|                                  
 |    `-._`-._        _.-'_.-'    |           https://redis.io       
  `-._    `-._`-.__.-'_.-'    _.-'                                   
 |`-._`-._    `-.__.-'    _.-'_.-'|                                  
 |    `-._`-._        _.-'_.-'    |                                  
  `-._    `-._`-.__.-'_.-'    _.-'                                   
      `-._    `-.__.-'    _.-'                                       
          `-._        _.-'                                           
              `-.__.-'                                               

22868:M 26 Oct 2021 22:39:39.085 # WARNING: The TCP backlog setting of 511 cannot be enforced because /proc/sys/net/core/somaxconn is set to the lower value of 128.
22868:M 26 Oct 2021 22:39:39.085 # Server initialized
22868:M 26 Oct 2021 22:39:39.085 # WARNING overcommit_memory is set to 0! Background save may fail under low memory condition. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
22868:M 26 Oct 2021 22:39:39.085 * Loading RDB produced by version 6.2.6
22868:M 26 Oct 2021 22:39:39.085 * RDB age 1065 seconds
22868:M 26 Oct 2021 22:39:39.085 * RDB memory usage when created 0.77 Mb
22868:M 26 Oct 2021 22:39:39.085 # Done loading RDB, keys loaded: 0, keys expired: 0.
22868:M 26 Oct 2021 22:39:39.085 * DB loaded from disk: 0.000 seconds
22868:M 26 Oct 2021 22:39:39.085 * Ready to accept connections

[root@server redis-6.2.6]# redis-cli
127.0.0.1:6379> set name ZhangSan
OK
127.0.0.1:6379> get name
"ZhangSan"
```

## Redis命令

### 控制台命令

|             命令             |                             作用                             |
| :--------------------------: | :----------------------------------------------------------: |
|         redis-server         |                   前台启动（默认6379端口）                   |
|        redis-server &        |                   后台启动（默认6379端口）                   |
|     ps-ef \| grep redis      |                      查看redis后台进程                       |
|      redis-cli shutdown      |            关闭redis服务（先完成数据操作再关闭）             |
|   kill -9 pid 或 kill pid    |              关闭redis服务（直接关闭redis服务）              |
|  redis-server redis.conf &   |               后台启动redis，同时指定配置文件                |
|          redis-cli           |               默认连接本机6379端口的redis服务                |
|      redis-cli -p port       |                 连接本机指定端口的redis服务                  |
|   redis-cli -h ip -p port    |             连接指定ip主机上指定端口的redis服务              |
|       redis-benchmark        |                        redis性能测试                         |
|      redis-cli 接 ping       |                     测试redis服务连通性                      |
|      redis-cli 接 info       |                   查看redis服务器统计信息                    |
| redis-cli 接 info [指定内容] | 查看指定的redis服务器统计信息，如info Replication查看集群信息 |
|                              |                                                              |

### 客户端命令
|      命令       |                             作用                             |
| :-------------: | :----------------------------------------------------------: |
|      ping       |                     测试redis服务连通性                      |
|      info       |                   查看redis服务器统计信息                    |
| info [指定内容] | 查看指定的redis服务器统计信息，如info Replication查看集群信息 |
|  select index   |                        切换数据库实例                        |
|  set key value  |                           保存数据                           |
|     get key     |                           查询数据                           |
|                 |                                                              |
|                 |                                                              |
|                 |                                                              |

## Redis基础知识
### Redis的数据库实例
- Redis数据库作用实例类似mysql
- 实例只能由Redis维护，开发者不能创建和维护
- 默认创建16个实例，编号0至15，通过编号使用
- 可以通过配置文件redis.conf指定创建的实例个数
- Redis的数据库实例占用空间很少
- 默认情况下，Redis客户端会连接0号数据库实例
## 参考链接

- [Redis官网](https://redis.io/)
- [Redis文档中心](http://www.redis.cn/documentation.html)
- [Redis命令参考](http://redisdoc.com/)

