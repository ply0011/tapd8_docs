# 管理

## 中间库 MongoDB

### 性能

- 开启慢日志信息收集：[https://docs.mongodb.com/manual/administration/analyzing-mongodb-performance/#database-profiling](https://docs.mongodb.com/manual/administration/analyzing-mongodb-performance/#database-profiling)

- 系统 ulimit 设置：[https://docs.mongodb.com/manual/reference/ulimit/](https://docs.mongodb.com/manual/reference/ulimit/)

### 配置文件

- 运行中的配置文件：

### 运维

- 升级 mongodb：[https://docs.mongodb.com/manual/tutorial/upgrade-revision/](https://docs.mongodb.com/manual/tutorial/upgrade-revision/)
- 启动、关闭 mongod：[https://docs.mongodb.com/manual/tutorial/manage-mongodb-processes/](https://docs.mongodb.com/manual/tutorial/manage-mongodb-processes/)
- 切割日志文件：[https://docs.mongodb.com/manual/tutorial/rotate-log-files/](https://docs.mongodb.com/manual/tutorial/rotate-log-files/)

### 备份

- 使用 Atlas 备份：[https://docs.mongodb.com/manual/core/backups/#back-up-with-atlas](https://docs.mongodb.com/manual/core/backups/#back-up-with-atlas)
- 使用 Ops Manager 备份：[https://docs.mongodb.com/manual/core/backups/#back-up-with-mms-or-ops-manager](https://docs.mongodb.com/manual/core/backups/#back-up-with-mms-or-ops-manager)
- 备份物理文件：[https://docs.mongodb.com/manual/core/backups/#back-up-by-copying-underlying-data-files](https://docs.mongodb.com/manual/core/backups/#back-up-by-copying-underlying-data-files)
- 使用 mongodump 备份：[https://docs.mongodb.com/manual/core/backups/#back-up-with-mongodump](https://docs.mongodb.com/manual/core/backups/#back-up-with-mongodump)

### 监控

- Linux 服务器，通过 SNMP 监控：[https://docs.mongodb.com/manual/tutorial/monitor-with-snmp/](https://docs.mongodb.com/manual/tutorial/monitor-with-snmp/)

## Tapdata 

### 监控

#### 任务

1. 编辑任务，进入任务设置

2. 勾选发送邮件，各选项说明如下：
    - 当任务停止：只有当任务被人工停止时，会发送告警邮件
    - 当任务出错：只有当任务发生错误，被迫终止时，会发送告警邮件
    - 当任务被编辑：只有当任务被编辑时，会发送告警邮件
    - 当任务开启：只有当任务被开启时，会发送告警邮件

!(告警邮件设置)[../images/admin-cn-1.png]

#### 管理模块

1. 探测管理模块端口（默认是3030）是否存活，若可以访问则服务存活，反之则不存活。

2. 进入 tapdata 软件目录，执行指令： `./tapdata status`，查看 frontend PID 是否有值，有值则为存活，反之则不存活

3. 在管理模块所在的服务器上，执行 `ps -ef | grep node | grep management | grep -v grep`，查看是否有进程存活，有结果返回则为存活，反之则不存活

#### 数据发布

1. 探测数据发布服务端口（默认是3080）是否存活，若可以访问则服务存活，反之则不存活。

2. 进入 tapdata 软件目录，执行指令： `./tapdata status`，查看 api server manage PID 是否有值，有值则为存活，反之则不存活

3. 在数据发布服务所在的服务器上，执行 `ps -ef | grep node | grep apiserver | grep -v grep`，查看是否有进程存活，有结果返回则为存活，反之则不存活

#### 数据采集

1. 进入 tapdata 软件目录，执行指令： `./tapdata status`，查看 backend PID 是否有值，有值则为存活，反之则不存活

2. 在数据发布服务所在的服务器上，执行 `ps -ef | grep java | grep -v grep`，查看是否有进程存活，有结果返回则为存活，反之则不存活
