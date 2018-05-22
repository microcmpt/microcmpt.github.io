## msa-rpc4j
### Quick Start
#### _1.msa-rpc4j与Spring Boot结合使用_
##### 1.1.服务端
#####  step1:引入msa-rpc4j-server
maven:
```$xslt
<dependency>
  <groupId>com.github.microcmpt</groupId>
  <artifactId>msa-rpc-server</artifactId>
  <version>1.0-SNAPSHOT</version>
</dependency>
<dependency>
  <groupId>com.github.microcmpt</groupId>
  <artifactId>spring-boot-msa-rpc4j-starter</artifactId>
  <version>1.0-SNAPSHOT</version>
</dependency>
```
gradle:
```$xslt
compile group: 'com.github.microcmpt', name: 'msa-rpc-server', version: '1.0-SNAPSHOT'
compile group: 'com.github.microcmpt', name: 'spring-boot-msa-rpc4j-starter', version: '1.0-SNAPSHOT'
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
##### step4:在spring boot启动类加入注解@EnableRpc4jServer，实现rpc4j-server自动配置
```$xslt
@SpringBootApplication
@EnableRpc4jServer
public class Rpc4jServerSampleApplication {

	/**
	 * The entry point of application.
	 *
	 * @param args the input arguments
	 */
	public static void main(String[] args) {
		SpringApplication.run(Rpc4jServerSampleApplication.class, args);
	}
}
```

##### 1.2.消费端
#####  step1:引入msa-rpc-client和spring-boot-msa-rpc4j-starter
maven:
```$xslt
<dependency>
  <groupId>com.github.microcmpt</groupId>
  <artifactId>msa-rpc-client</artifactId>
  <version>1.0-SNAPSHOT</version>
</dependency>
<dependency>
  <groupId>com.github.microcmpt</groupId>
  <artifactId>spring-boot-msa-rpc4j-starter</artifactId>
  <version>1.0-SNAPSHOT</version>
</dependency>
```
gradle:
```$xslt
compile group: 'com.github.microcmpt', name: 'msa-rpc-client', version: '1.0-SNAPSHOT'
compile group: 'com.github.microcmpt', name: 'spring-boot-msa-rpc4j-starter', version: '1.0-SNAPSHOT'
```
##### step2:定义一个消费端接口HelloRpc4jServiceRpcClient并添加注解@Rpc4jClient
```
@Rpc4jClient
public interface HelloRpc4jServiceRpcClient extends HelloRpc4jService {
}
```
##### step3:在控制类中调用该服务接口
```
@RestController
@RequestMapping("/api")
public class HelloRpc4jController {
    /**
     * The Hello rpc 4 j service.
     */
    @Resource
	private HelloRpc4jServiceRpcClient helloServiceRpcClient;

    /**
     * Hello string.
     *
     * @param name the name
     * @return the string
     */
    @RequestMapping(method = RequestMethod.GET, value = "/hello/{name}")
    public String hello(@PathVariable("name")String name) {
        return helloServiceRpcClient.hello(name);
    }
}
```
##### step4:在spring boot启动类加入注解@EnableRpc4jClients，实现rpc4j-client自动配置
```$xslt
@SpringBootApplication
@EnableRpc4jClients
public class Rpc4jClientSampleApplication {
	/**
	 * The entry point of application.
	 *
	 * @param args the input arguments
	 */
	public static void main(String[] args) {
		SpringApplication.run(Rpc4jClientSampleApplication.class, args);
	}
}
```