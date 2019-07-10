[CS vs SE, Hoare09](https://reinout.vanrees.org/weblog/2009/07/01/ep-keynote.html)  
[什么是工程](https://en.wikipedia.org/wiki/Engineering)  
[CS != SE](http://www.cnblogs.com/buaashine/archive/2012/12/12/2813931.html)  
[We Are All Confident Idiots](https://www.guokr.com/article/439517/)  

[MIT 16.355](http://sunnyday.mit.edu/16.355/)  
[CMU-SEI](https://sei.cmu.edu/)  
[MIT-SAL](http://systemarchitect.mit.edu/index.php)  

# 基本问题

> One of the biggest problems with software is that **it’s complex and abstract**. The result being that it’s hard to visualise the runtime characteristics of a piece of software from diagrams or even the code itself.

* 逻辑（问题怎么解）  
  问题域分解/服务功能划分  
  输出：类/对象图、需求分析 
  
* 场景（验证能否走通）
  突出系统间依赖  
  输出：用例
  
* 过程（数据怎么走）  
  接口/信息流/容错  
  输出：交互图、时序图  

* 开发
  流程：源码 -> 源码仓库 -> 发布系统
  测试：单元测试 -> 系统测试 -> QA -> 预发布 -> 线上
  组件：配置中心/链路追踪/统一日志/消息（基础架构怎么做）
  输出：产品展示/服务交互API

* 物理（SRE怎么做）  
  网络/计算/存储/容器  
  可扩展/高可用/高性能  
  输出：基础设施 

[Humphrey-SPA award](https://resources.sei.cmu.edu/news-events/events/watts/watts.cfm)  
[SE-history, 1996](https://www.dagstuhl.de/Reports/96/9635.pdf)  
https://en.wikipedia.org/wiki/Software_engineering  
https://en.wikipedia.org/wiki/Software_development  

[Engineering a Safer World, 2012](http://sunnyday.mit.edu/safer-world/index.html)  
[SE, 1968](http://homepages.cs.ncl.ac.uk/brian.randell/NATO/nato1968.PDF)  
[No Silver Bullet, 1986](http://sunnyday.mit.edu/16.355/BrooksNoSilverBullet2.html)  
[Software Engineering Economics, 1984](http://csse.usc.edu/TECHRPTS/1984/usccse84-500/usccse84-500.pdf)  
[SWEBOK, 2004](https://www.computer.org/web/swebok/index)  

[构建之法](https://book.douban.com/subject/27069503/)  
[A Multi-Decade Perspective, Scacchi, 2018](https://www.ics.uci.edu/~wscacchi/Papers/New/IEEE-Computer-Scacchi-2018.pdf)  
[自我评价](http://www.cnblogs.com/xinz/p/3852177.html)

> software craftsmanship

# 开发流程

[Process Models, 2001](https://www.ics.uci.edu/~wscacchi/Papers/SE-Encyc/Process-Models-SE-Encyc.pdf)  
[Waterfall, 1970](http://www-scf.usc.edu/~csci201/lectures/Lecture11/royce1970.pdf)  
[Spiral, 1988](http://www-scf.usc.edu/~csci201/lectures/Lecture11/boehm1988.pdf)  
[PSP, 1996](http://www.star.cc.gatech.edu/documents/SpencerRugabear/psp.pdf)  
[CMM, 1991](http://sunnyday.mit.edu/16.355/cmm.pdf)  
[The Agile Methods Fray](http://www-scf.usc.edu/~csci201/lectures/Lecture11/demarco2002.pdf)  
[Agile Software Development, 2003](https://book.douban.com/subject/1140457/)  
https://en.wikipedia.org/wiki/Agile_software_development  

# 需求和规格

> 解决/不解决什么问题？谁的问题？
creator driven (问题分治还是工作分治)  
Be Zara, not Foxconn (从效率模式->快速响应式)  

第一原理  
[Top risks, 2001](http://sunnyday.mit.edu/16.355/lawrence-requirements.pdf)  
[Requirements Engineering, 2000](http://mcs.open.ac.uk/ban25/papers/sotar.re.pdf)  
[Clean Coder, 2011](https://book.douban.com/subject/11614538/)  
[软技能](https://book.douban.com/subject/26835090/)  
https://firstround.com/review/Responsiveness-New-Efficiency/  

https://simplicable.com/new/coding-principles  
https://about.gitlab.com/handbook/  
https://en.wikipedia.org/wiki/List_of_software_development_philosophies
http://blog.vgod.tw/
https://blog.youxu.info/
http://blog.54chen.com/
http://www.yankay.com
http://www.valleytalk.org

http://people.scs.carleton.ca/~deugo/Patterns/ospdg/
https://www.cs.cmu.edu/~aldrich/courses/413/


# 软件实现与质量

> 写诗还是写文档
根据现有的时间/预算/知识/复杂度，利用最佳实践、技术、框架、工具、设备（工程/学习能力）

[Clean Code](https://book.douban.com/subject/5442024/)  
[Refactoring](https://book.douban.com/subject/4262627/)  
[Code complete](https://book.douban.com/subject/1477390/)  

测试工具和方法  
[xUnit, 2007](https://book.douban.com/subject/1859393/)  
[TDD, 2003](https://book.douban.com/subject/1229924/)  
[OO tests, 2009](https://book.douban.com/subject/4156589/)  

[Agile Developer](https://book.douban.com/subject/4164024/)

# 软件发布和运维

![](https://d1.awsstatic.com/product-marketing/DevOps/DevOps_feedback-diagram.ff668bfc299abada00b2dcbdc9ce2389bd3dce3f.png)

流量切换 sla  
服务依赖/状态/降级  
发布和灰度   

[Kubernetes In Action, 2017](https://book.douban.com/subject/26997846/)  
[Continuous Delivery](https://book.douban.com/subject/6862062/)  
[Site Reliability Engineering](https://book.douban.com/subject/26875239/)  
[Infrastructure as Code](https://d1.awsstatic.com/whitepapers/DevOps/infrastructure-as-code.pdf)  

https://lpd-ios.github.io/2017/05/08/Git-Work-Flow/  
https://docs.gitlab.com/ee/README.html  
https://ohshitgit.com/  
www.conventionalcommits.org  
https://www.atlassian.com/git/tutorials  
https://github.com/GetMyle/Guides/wiki/MYLE-GitHub-Flow  
https://about.gitlab.com/2016/03/08/gitlab-tutorial-its-all-connected/  