
# C10K/C10M problem
http://www.kegel.com/c10k.html

|机器配置|客户端|客单价|总价|年份|
|--|--|--|--|--|
1GHz,2GB,Gbps $1200 | 20K client, 50Kb/s/c | $0.08/c | $100|2001
24c,3GHz,100GB | 2M client |10KB/socket? | |2012, [Whatapp](https://qunfei.wordpress.com/2016/09/20/from-c10k-to-c100k-problem-push-over-1000000-messages-to-web-clients-on-1-machine-simultaneously/)
12c,2.66GHz,96GB,10Gbps | 10M client, 512Kb/s/c |3.2KB/socket | |2015, [MigrateoryData](https://migratorydata.com//2015/05/20/how-migratorydata-solved-the-c10m-problem-10-million-concurrent-connections-on-a-single-commodity-server/)

I/O策略 1:1线程 VS M:N 线程

[SEDA: An Architecture for Well-Conditioned,Scalable Internet Services, welsh01, SOSP](http://www.sosp.org/2001/papers/welsh.pdf)

https://cs.uwaterloo.ca/~brecht/servers/readings.html
https://pages.cs.wisc.edu/~remzi/Classes/739/Fall2018/
https://github.com/smallnest/C1000K-Servers
http://highscalability.com/blog/2013/5/13/the-secret-to-10-million-concurrent-connections-the-kernel-i.html

# Nginx
http://www.aosabook.org/en/nginx.html

# Nodejs
[Node 之父 Ryan Dahl：我不想被定义, 2017](https://www.infoq.cn/article/2017%2F09%2FNode-Ryan-Dahl)  
[Design Mistakes in Node, 2018](https://tinyclouds.org/jsconf2018.pdf)  

http://www.gevent.org/

https://people.csail.mit.edu/rinard/teaching/osnotes/
https://pdos.csail.mit.edu/6.828/2018/schedule.html
https://www.cs.cmu.edu/~15712/syllabus.html
https://www.cc.gatech.edu/~rama/CS6210-External/

# Netty
[Netty in Action, maurer2015](https://book.douban.com/subject/24700704/)  


# UNIX network
![Figure 6.6. Comparison of the five I/O models.](https://www.masterraghu.com/subjects/np/introduction/unix_network_programming_v1.3/files/06fig06.gif)

https://github.com/JackJiang2011/MobileIMSDK

[Unix Network Programming, Volume 1](https://book.douban.com/subject/4859464/)

# RAW字节、编解码、序列化

## TCP网络数据编解码
原始字符流|  半包| 粘包| 粘包
|---|---|---|---|
AB CD|A BCD  |ABC D  |ABCD  

## 应用层数据编解码格式
![](http://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCE9a6a724d25fc64f2a2476428b09f9891/162)

[msgpack](https://msgpack.org/)  
[Protocol Buffers](https://developers.google.com/protocol-buffers)

[Serialization Performance comparison](https://maxondev.com/serialization-performance-comparison-c-net-formats-frameworks-xmldatacontractserializer-xmlserializer-binaryformatter-json-newtonsoft-servicestack-text/)
从编码空间、序列化和反序列化速度上面，比较了流行的编解码工具的性能。  

https://blog.mbedded.ninja/programming/serialization-formats/a-comparison-of-serialization-formats/