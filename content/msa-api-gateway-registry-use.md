## msa-api-gateway-registry-use
### Introduction
msa-api-gateway-registry用于将应用名（唯一）注册到服务注册中心，方便在服务网关通过应用名路由负载均衡到一台应用服务节点
### Quick Start
step1:在应用配置文件中，比如application.properties文件中加入如下配置信息：
```$xslt
spring.application.name=sampleConsumer
```
step2:在spring boot类加上@EnableApiGatewayRegistryClient启动应用名注册到注册中心自动配置，如下代码：
```
@SpringBootApplication
@EnableApiGatewayRegistryClient
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