# 工作负载
数据量 10TB+分布在`1K+节点`  
每天有100+程序 ->` 1K jobs`

# 动机

crawled document/web request log -> inverted indices/graph data/data aggregation  
* 输入都是item的集合
* 计算都是输出中间k/v集合，再把相同k进行合并
* 程序自动在集群并行处理/执行
* 普通程序员都能跑大数据，无需关心输入数据分割、程序调度、机器故障、内部通讯

# 解决方案

![](https://i1.wp.com/mikepluta.com/wp-content/uploads/word-count-as-mapreduce.png?resize=940%2C665)
造一个map->reduce程序库，利用GFS/调度系统/资源管理系统/部署系统等基础设施  
map(k1, v1) -> list(k2, v2)  
reduce(k2, list(v2) -> list(k2, v3)]

# 缺陷
* 不是所有应用都是map/shuffle/reduce这种模式

# 细节
![](http://www.broadgateconsultants.com/blog/wp-content/uploads/2012/08/mapreduce.png)
## 过程
数据集 -> GFS -> `分成M份`
用户程序调用开始 -> scheduling system -> 配置中间结果分成R组，由W个worker处理。(`通常M=200_000, R=5_000, W=2_000`)  
用户程序自动分发 -> `master copy` + `M-1 worker copy`  
`master负责分任务给worker，保存任务的完成状态M*R，保存R份中间k/v文件位置`  
map worker -> 中间k/v结果 -> master-> reduce worker -> append to输出文件  

* 不需要等待所有map完成，再调用reduce。从结果看，master是不会干涉计算的，因此只要有map完成任务，这个批次中间k/v结果就会进入R个本地文件，master会通知reduce worker RPC获取÷自己负责的那块R的部分数据，再排序，计算结果就追加到临时文件后面，直到所有map完成
* 所有任务完成，master -> wake up 用户程序 
* worker保持为纯函数，简单实现，不需要维护任何状态信息
* M/R任务是怎样分配的？应该是一开始就分配好的，但是不清楚多少给map，多少给reduce。

## 容错

### master和所有worker PING/PONG
### worker容错
* 没有完成的map和reduce需要re-executed
* 完成但挂掉的map worker需要re-executed
  * reduce worker已经读取了这个mapper的中间k/v结果，master通知其取消工作
  * reduce worker没有读取完中间k/v结果，master通知其取消读取
* 完成的reduce任务不需要re-executed
### master容错
认为没必要
### 语义容错
map/reduce可能会被重复执行

## 数据局部性

存储与计算在一起  
master就近分配woker（怎么分）

## 性能
* 10亿条100byte数据 ≈ 1TB
* 100~200 Gbps root Ethernet network
* W=1800, R=4000, M=15000
* 排序大概花了891秒≈15分钟

代码量从3800行C++代码 -> 700行

[mapreduce-osdi04](https://research.google.com/archive/mapreduce-osdi04.pdf)  
[MapReduce: A major step backwards](http://databasecolumn.vertica.com/2008/01/mapreduce_a_major_step_back.html)  
[lecture1](https://pdos.csail.mit.edu/6.824/notes/l01.txt)
https://www.mikepluta.com/hadoop-v1-architecture-overview/  
https://stackoverflow.com/questions/21509272/must-hadoop-finish-maps-before-reduce  