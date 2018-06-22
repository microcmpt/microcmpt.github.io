## - Introduction
Microcmpt是基于`Spring Boot`框架的微服务架构落地解决方案，它主要由msa-api-gateway(微服务网关)、msa-api-regcovery(服务注册中心)、msa-rpc4j(轻量级RPC通讯框架)、msa-scheduler(任务调度中心)等组件组成，
使得微服务架构落地更加容易。

---
## - Components
![](images/microcmpt.png)

 - [RPC框架]
   - ![avatar](images/msa-rpc4j.png)
   - [`msa-rpc4j`](content/msa-rpc4j-use.md)
   - [`spring-boot-msa-rpc4j`](content/spring-boot-msa-rpc4j-use.md)
 - [服务网关] 
   - [`msa-api-gateway`](content/msa-api-gateway-use.md)
   - [`msa-api-gateway-registry`](content/msa-api-gateway-registry-use.md)
 - [服务注册中心]
   - [`msa-api-regcovery`](content/msa-api-regcovery-use.md)
   - [`spring-boot-api-regcovery-dashboard`](content/spring-boot-api-regcovery-dashboard-use.md)
 - [定时任务调度中心] 
   - [`msa-scheduler`](content/msa-scheduler-use.md)
 - [分布式配置中心]
   - 待开发
 - [分布式追踪系统]
   - 待开发
   
---
## - Download
 - [Downloads]
   - [`SDK Download`](http://mvnrepository.com/search?q=microcmpt)    
   - [`NPM Download`](https://www.npmjs.com/package/msa-api-gateway)  

---
## - Contributors
![](images/contributor.png)沈夏平@<1378127237@qq.com>，![](images/contributor.png)刘颖@<woshibihu@qq.com>

---
## - Sample for Microcmpt
microcmpt的组件如何使用？具体代码见：[`Microcmpt Sample On GitHub`](https://github.com/microcmpt/msa-sample)

___
<center>Copyright © 2018 Microcmpt Group</center>