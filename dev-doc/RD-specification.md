# 研发工程指南

[Java for small team](https://ncrcoe.gitbooks.io/java-for-small-teams/content/)

[serverside-checklist](https://github.com/mtdvio/going-to-production/blob/master/serverside-checklist.md)


## 代码规范

[阿里p3c的规约](https://github.com/alibaba/p3c)  

[阿里JAVA开发手册](https://github.com/alibaba/p3c/blob/master/Java%E5%BC%80%E5%8F%91%E6%89%8B%E5%86%8C%EF%BC%88%E5%B5%A9%E5%B1%B1%E7%89%88%EF%BC%89.pdf)

### 工具、静态分析
[PMD (bad smell)](https://pmd.github.io/) + [SpotBug (error)](https://spotbugs.github.io/)  
[阿里编码规约插件](https://github.com/alibaba/p3c/tree/master/idea-plugin)   
[Save Action](https://github.com/dubreuia/intellij-plugin-save-actions)  


### 服务返回错误码
业务编码[中心申请协调].错误类型[P参数，B业务，S系统].场景.自定义  
1000.P.GetCustomer.NameIsNull  
1001.S.Unknow.Exception

### 代码提交  

### 代码设计  
函数、设计模式

## 工程规范

[阿里云，JAVA工程脚手架](https://start.aliyun.com/)  
[COLA](https://github.com/alibaba/COLA)

![](https://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCEd5b7a03343330a8b391bfbe59f1b77e5/194)

项目命名  
项目结构  
项目管理工具   
包名：com.company.biz.component

## 二方库

[maven本地仓库设置](https://maven.apache.org/settings.html#Servers)  
[项目pom.xml设置](https://maven.apache.org/pom.html)  

部署：  
mvn deploy -pl app/rest-api,.   

prod版本修改:    
mvn versions:set -DremoveSnapshot=true  
[mvn versions:set](https://www.mojohaus.org/versions-maven-plugin/set-mojo.html)

## 接口规范

[yapi](https://github.com/ymfe/yapi)  
[apizza](https://www.apizza.net/) 

接口知识库与网关  
发布平台    

## 数据库设计规范

### 连接池
[hikaricp](https://github.com/brettwooldridge/HikariCP)  
druid社区更新滞后了许多，LocalDatetime社区反馈了很久

## 持续集成规范
### CI代码审查  
[Sonar-java](https://www.sonarsource.com/java/)  
[JaCoCo](https://www.eclemma.org/jacoco/)

代码评审  
单元测试  
集成测试  
系统测试  
构建  
部署环境  

### 容器
jvm的环境需要支持容器对内存和cpu的设置
传说8u191以上已经默认支持

-XX:+UseContainerSupport已经默认加入到jdk中  
https://medium.com/adorsys/jvm-memory-settings-in-a-container-environment-64b0840e1d9e  
[8u191](https://medium.com/adorsys/usecontainersupport-to-the-rescue-e77d6cfea712)    
[8u131](https://blog.softwaremill.com/docker-support-in-new-java-8-finally-fd595df0ca54)  

[kubernetes资源限制](https://kubernetes.io/docs/concepts/policy/limit-range/)  