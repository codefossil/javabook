> OODA loop

- Part of the process of architecting a software system is about understanding **what is significant and why**
- Understanding **the speed at which your organisation or business changes** is important

# 架构

业务规则=约束+原则  
结构=边界+接口  

> 架构=重要的系统设计=结构+愿景=构建成本最小化+效率最大化

[康威定律, 1967](http://www.melconway.com/Home/Conways_Law.html)  
[架构漫谈, 2016](https://www.infoq.cn/article/an-informal-discussion-on-architecture-part01)  

[Clean Architecture](https://book.douban.com/subject/30333919/)  
提出以企业业务规则和应用业务规则为核心，满足外部系统为目的涉及的“插件系统”。底层离中心业务越远越易变，高层中心业务规则是赚钱的法宝比较不易变。 

[Building Evolutionary Architectures, 2017](https://book.douban.com/subject/27148120/)  
[Just Enough Software Architecture](https://book.douban.com/subject/24872314/)    
[Architectural and philosophical points](https://www.w3.org/DesignIssues/)  

# 化繁为简

[Engeering: An endless frontier, Auyang2004](https://book.douban.com/subject/3287111/)

[Complexity, Mitchell2011](https://book.douban.com/subject/6749832/)

[控制论与科学方法论, 2005](https://book.douban.com/subject/1322336/)

[GEB, 97](https://book.douban.com/subject/1291204/)

[系统论，95](https://book.douban.com/subject/1008370/)

[System Architecture: Strategy and Product Development for Complex Systems](https://book.douban.com/subject/26938710/)  
分析了一种系统化的思考方式和识别方法，结合大量实例自顶向下剖析了架构复杂系统的过程，总结出系统分为形式和功能，通过分解和分层等方法破解复杂系统。


# 边界

> the discipline of **systems thinking** proves to be an invaluable tool in assessing exposure, opportunities, parametric sensitivities. 
> instrument–process–operand model

DDD/TDD/BDD/CQRS/DCI/  
[DDD](https://book.douban.com/subject/1418618/)  

[the magic number seven, 1956](https://academic.microsoft.com/paper/1984314602/reference)

# 伸缩
  
[Architecting for scale, 2016](https://book.douban.com/subject/27071892/)  
[Software design for large system, 1988](https://web.njit.edu/~kirova/BC-SDP.pdf)  
[排队论及其应用浅析](https://www.slideshare.net/frogd/ss-27959518)  
[构建高性能Web站点, 2009](https://book.douban.com/subject/3924175/)  
# 性能优化
> Performance is all about code path

* 优化问题，把所有访问路径列出来
* 各种cache/各种延迟影响很大

[我对后端优化的一点想法](https://www.slideshare.net/jamestong/2012-12552732)  
[5-minute rule](http://www.hpl.hp.com/techreports/tandem/TR-86.1.pdf)  
[Think Clearly About Performance](https://method-r.com/wp-content/uploads/2018/07/TCAP-from-MOTD2.pdf)
https://carymillsap.blogspot.com/2010/09/my-otn-interview-at-oow2010-which-hasnt.html

# 模式/原则

沉默成本（可用性）  
机会成本（兼容性）  
边际成本（扩展性）  
You Aren't Gonna Need It.  
If it ain't broke, don't fix it.  
飞轮效应  
dependency inversion
SOLID

[Big Design Up Front](https://en.wikipedia.org/wiki/Big_Design_Up_Front)  
  

[Stop Learning Frameworks, 2018](https://sizovs.net/2018/12/17/stop-learning-frameworks/)  
[TAOUP, 2003](https://book.douban.com/subject/5387401/)   

https://java-design-patterns.com/principles/  
[dp](https://sourcemaking.com/design_patterns)  

[worse is better](http://dreamsongs.com/WorseIsBetter.html)  
[The Rule of Least Power, 2001](https://www.w3.org/2001/tag/doc/leastPower.html)  

[Laws of Software Development](http://www.globalnerdy.com/2007/07/18/laws-of-software-development/)  
[方法论、方法论——程序员的阿喀琉斯之踵](http://mindhacks.cn/2008/10/29/methodology-for-programmers/)  
[PEP 20](https://www.python.org/dev/peps/pep-0020/)  
[system-desgin](https://github.com/donnemartin/system-design-primer)  


# 可视化和文档化设计

[Software Architecture for Developers, 2014](https://book.douban.com/subject/26248182/)  
权衡BDUF和演变式设计，软件架构中的争论，怎样产出图/文档

todo  
https://web.njit.edu/~kirova/is663-s11.html  
https://handbookofsoftwarearchitecture.com/