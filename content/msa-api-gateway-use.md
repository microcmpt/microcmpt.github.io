## msa-api-gateway-use
### Introduction
msa-api-gateway是服务网关，使用服务网关统一拦截外部请求，由于服务网关是整个架构的入口，承担的责任重大，需要保持其单点故障导致整个服务不可用
并且还要具有良好的性能，所以服务网关采用nodejs开发，nodejs是单线程，基于事件模型，非阻塞IO，故采用其开发，并使用nodejs单机多核集群的特性，
加速请求处理能力，服务网关特点：
- 高并发
- 高吞吐量
- 高性能
- 高可用

### Quick Start
step1:启动服务网关
```$xslt
pm2 start zk_app.js
```
step2:发送http请求
```$xslt
curl -H 'Application-Name:sampleConsumer' http://localhost:1025/api/hello/123
```
> Application-Name：注册到注册中心时的应用名