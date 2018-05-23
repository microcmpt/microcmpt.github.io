## msa-api-regcovery
### Quick Start
开启注册中心web控制台，在启动类上@EnableRegcoveryDashboard
```$xslt
@SpringBootApplication
@EnableRpc4jServer
@EnableRegcoveryDashboard
public class Rpc4jServerSampleApplication {
	public static void main(String[] args) {
		SpringApplication.run(Rpc4jServerSampleApplication.class, args);
	}
}
```
### API Help
- 查询所有服务端服务信息
```$xslt
url: GET [ip:port]/api/v1/services
```
response:
```$xslt
{
    "result": "ok",
    "data": [
        {
            "rootNode": "/registry",
            "childNode": "com.msa.sample.api.HelloRpc4jService",
            "subChildNode": "address-0000000058",
            "serviceAddr": "192.168.4.80:8025"
        }
    ]
}
```
- 根据服务名查询服务信息
```$xslt
url: GET [ip:port]/api/v1/services/{name}
```
response:
```$xslt
{
    "result": "ok",
    "data": [
        {
            "rootNode": "/registry",
            "childNode": "com.msa.sample.api.HelloRpc4jService",
            "subChildNode": "address-0000000058",
            "serviceAddr": "192.168.4.80:8025"
        }
    ]
}
```
- 新增服务节点
```$xslt
url: POST [ip:port]/api/v1/service/{name}/addr/{serviceAddr}
```
response:
```$xslt
{
    "result": "ok"
}
```
- 删除服务节点
```$xslt
url: DELETE [ip:port]/api/v1/service/{name}/addr/{serviceAddr}
```
response:
```$xslt
{
    "result": "ok"
}
```
- 修改服务节点
```$xslt
url: UPDATE [ip:port]/api/v1/service/{name}/addr/{serviceAddr}/value/{val}
```
response:
```$xslt
{
    "result": "ok"
}
```