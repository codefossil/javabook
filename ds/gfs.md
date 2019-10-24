# 工作负载
`n 100TB` = n k磁盘 = n K台节点/集群  
QPS = `n 100个客户端`  
文件总大小=n TB，文件总数=`n 十亿个 KB小文件`，单文件大多n+ GB  

# 动机
数据仓库/应用数据流/归档数据/计算中间数据

- 文件大大小小，数量多，莫法管
- 节点必须是廉价的PC
- 并发追加数据必须保证原子性

`设计优先级`：组件容错>大文件追加写>顺序读>接口  

# 解决方案
![](https://ofirm.files.wordpress.com/2013/01/gfs_architecture.png)
造一个类似posix api库，借鉴单机Linux文件系统原理   
文件 = 元数据 + `N 定长数据块`  
M 客户端 -> 全局中心化1 master + N chunk服务器  
`数据流和控制流分开`

# 局限

- 适合连续的大读/写/追加写
- 适合数据容错
- 不适合master HA
- 不适合小文件(固定长度chunk)
- 追加写可能会重复

# 细节
## 简单读

![read](image/read.svg?sanitize=true)

## 单master
- 文件名称 + 块映射 -> 操作日志
- master控制和监控chunk服务器

## master的容错恢复
重放操作日志  
- 根据文中提示，操作日志应该是类似LSM机制
- master + shadow master (`通过外部监控系统容错重启`)

## 更新数据

![update](image/update.svg?sanitize=true)

### lease = 单primay + 多备
- primary维护数据修改顺序性
- 客户端 + primary实现自动跨数据块拆分
- 副本有个chunk版本号（容忍副本重启丢失数据更新）

## 不一致性模型
> 作者说了弱一致性并不是大问题，因为app都是追加写/数据部分都做了幂等  
> 一切为了简单性 (先实现出来，之后再来优化)  

### 更新失败，没有回滚
副本更新失败，会导致当前数据块的数据不一致

### 更新写和追加写
- 跨块更新写会被改为2次写入不同的块，并发可能会交叉覆盖
- 追加写不会跨块，一次操作。

# 性能

- ~1M文件，~1M分块
- 元数据chunk服务器有10GB，master只有10MB+
- 读得有500MB/s，写得有100MB/s
- master ops ~500/s
- 单个chunk服务器有~15KB个chunk，需要~20min恢复所有数据（优先级低，带宽被限制到50Mbps）

[gfs-sosp03](https://pdos.csail.mit.edu/6.824/papers/gfs.pdf)  
[lecture3](https://pdos.csail.mit.edu/6.824/notes/l-gfs-short.txt)