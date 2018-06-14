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
```aidl
java -Dconfig.path.prefix=config目录 -jar msa-scheduler-1.0.0.jar
```
##### step3:添加一个定时任务<br/>
```aidl
curl -H "Content-Type:application/json" -X POST --data '{"jobName":"job","jobGroupName":"","cron":"0/10 * * * * ?","triggerName":"","triggerGroupName":"jobGroup","applicationId":"sampleConsumer","uri":"/api/hello/sxp","jobDescription":"job"}' http://localhost:8083/api/v1/add
```
### scheduler.properties属性说明

### API
