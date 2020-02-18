# 监控指标

高并发情况下，可查看如下内容：

- CPU当前的利用率和系统的load
- 查看网卡的流量
- 查看磁盘I/O的密集程度
- 查看内存的使用等

## 磁盘IO

iostat –d –k （-d表示查看磁盘使用情况 –k表示以KB为单位显示）tps表示每秒处理的IO请求数（即每秒事务数）。

## 多功能诊断器pidstat（可监视进程和线程的性能情况）

pidstat –r –p PID m n（监控进 程内存使用）

pidstat –p PID –u m n（观察进程信息）

pidstat –p PID m n –u -t（观察监控线程）

pidstat –p PID m n –d -t（监控程序I/O情况）

### 导出指定Java应用程序的所有线程 

jstack –l PID > /tmp/t.txt

### 查看系统load值

用top / uptime。命令查看系统的load值。值越大越繁忙，只要每个CPU当前的活动线程数不大于3，负载正常。

### CPU利用率

top / grep CPU。多个/多核CPU时，查看每个CPU利用情况，按1，看每核的CPU利用率。

top默认按PID显示CPU消耗情况，按shift+H可按线程查看

top –p PID指定查看的进程

### 磁盘剩余空间

df –h 查看磁盘的剩余空间

du –d | -h /home/longlong 查看具体目录所占用的空间(-h按单位格式化输出，-d指定地柜深度)

### 网络traffic

sar –n DEV 1 1 看系统的网络状况（-n表汇报网络状况，DEV表查看的是各个网卡的网络流量）

### 内存使用

free –m (-d表示以MB为单位)查看系统内存使用情况

vmstat 查看swap I/O的情况（对应用应更关注虚拟内存swap的）

### 其他

QPS：每秒查询数

rt：请求的响应时间

select/ps：记录了数据库每秒处理的select语句的数量

update/ps、delete/ps

GC：GC发生时，JVM上的应用程序的工作线程将会暂时停止运行。











