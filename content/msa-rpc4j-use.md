## msa-rpc4j-use
### Introduction
msa-rpc4j是一款轻量级rpc nio通讯框架，底层通讯采用了netty nio通讯框架，rpc调用速度更快，序列化采用protostuff，序列化速度性能更优，为了保持高可用，采用zookeeper作为
服务注册中心，所以msa-rpc4j是一款具有高性能、高可用的通讯框架。
### Quick Start
##### 服务端
##### step1:引入msa-rpc4j-server
maven:
```$xslt
<dependency>
  <groupId>com.github.microcmpt</groupId>
  <artifactId>msa-rpc-server</artifactId>
  <version>1.0-SNAPSHOT</version>
</dependency>
```
gradle:
```$xslt
compile group: 'com.github.microcmpt', name: 'msa-rpc-server', version: '1.0-SNAPSHOT'
```
#####  step2:定义一个服务端接口HelloRpc4jService
```
public interface HelloRpc4jService {
    /**
     * Hello string.
     *
     * @param str the str
     * @return the string
     */
    String hello(String str);
}
```
##### step3:实现服务端业务逻辑HelloRpc4jServiceImpl类
```
@RpcService(value = HelloRpc4jService.class)
public class HelloRpc4jServiceImpl implements HelloRpc4jService {
    /**
     * Hello string.
     *
     * @param str the str
     * @return the string
     */
    public String hello(String str) {
        return "Hello, " + str;
    }
}
```
##### 消费端
#####  step1:引入msa-rpc-client
maven:
```$xslt
<dependency>
  <groupId>com.github.microcmpt</groupId>
  <artifactId>msa-rpc-client</artifactId>
  <version>1.0-SNAPSHOT</version>
</dependency>
```
gradle:
```$xslt
compile group: 'com.github.microcmpt', name: 'msa-rpc-client', version: '1.0-SNAPSHOT'
```
##### step2:通过DefaultInvocationProxy创建代理客户端
```
HelloRpc4jService client = DefaultInvocationProxy.newInstance(HelloRpc4jService.class);
String resp = client.hello("rpc4j");
System.out.println("返回结果:" + resp);
```
### Annotation
#### @RpcService
@RpcService用于标记该服务为暴露出去的API服务，服务端启动时自动注册到注册中心