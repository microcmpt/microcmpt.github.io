## msa-scheduler-use
### Introduction
msa-scheduler是为调度众多定时任务而生的调度中心，msa-scheduler单机最大可承受几万个定时任务的执行，可采用集群模式，可将定时任务平均
分配到各个集群节点，减轻单机执行任务的负担，有如下特点：
- 可伸缩
- 错失触发
- 任务优先级
### Quick Start
##### step1:将config目录置于你认为适合的路径下
##### step2:启动msa-scheduler
```
java -Dconfig.path.prefix=config目录 -jar msa-scheduler-1.0.0.jar
```
##### step3:添加一个定时任务
```
curl -H "Content-Type:application/json" -X POST --data '{"jobName":"job","jobGroupName":"","cron":"0/10 * * * * ?","triggerName":"","triggerGroupName":"jobGroup","applicationId":"sampleConsumer","uri":"/api/hello/sxp","jobDescription":"job"}' http://localhost:8083/api/v1/add
```
### scheduler.properties
```
# zookeeper
scheduler.zk.addresses=localhost:2181

# email
# 开启邮件通知功能
scheduler.mail.enable=true
# 邮箱服务器域名
scheduler.mail.host=smtp.qq.com
# 发送邮件邮箱地址
scheduler.mail.username=1378127237@qq.com
# 发送邮箱授权码
scheduler.mail.password=mestuwkkygoigaje
scheduler.mail.protocol=smtp
# 接收邮件人邮箱，可填写多个，多个以英文逗号分隔
scheduler.mail.to=1378127237@qq.com
scheduler.mail.properties.mail.smtp.auth=true 
scheduler.mail.properties.mail.smtp.starttls.enable=true
scheduler.mail.properties.mail.smtp.stattls.required=true

# quartz
scheduler.quartz.threadPool.threadCount=13
# 持久库配置
scheduler.quartz.dataSource.quartzDS.driver=com.mysql.jdbc.Driver
scheduler.quartz.dataSource.quartzDS.URL=jdbc:mysql://localhost:3306/quartz?characterEncoding=utf-8&useSSL=false
scheduler.quartz.dataSource.quartzDS.user=root
scheduler.quartz.dataSource.quartzDS.password=123456
scheduler.quartz.dataSource.quartzDS.maxConnections=5
# 是否开启集群配置
scheduler.quartz.jobStore.isClustered=true
scheduler.quartz.jobStore.clusterCheckinInterval=15000

# okhttp(单位：s)
#默认为10s
#scheduler.okhttp.connect-timeout=20
#scheduler.okhttp.read-timeout=30
#scheduler.okhttp.write-timeout=30
```