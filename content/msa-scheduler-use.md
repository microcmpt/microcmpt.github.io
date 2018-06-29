## msa-scheduler-use
### Introduction
msa-scheduler是为调度众多定时任务而生的调度中心，msa-scheduler单机最大可承受几万个定时任务的执行，可采用集群模式，可将定时任务平均
分配到各个集群节点，减轻单机执行任务的负担，有如下特点：
- 可伸缩
- 错失触发
- 任务优先级

### Quick Start
##### step1:下载zip并解压
[scheduler-1.0.0.zip download](/microcmpt/msa-scheduler/raw/master/downloads/1.0.0/msa-scheduler-1.0.0.zip)

##### step2:启动scheduler
- [windows]
  执行start-scheduler.cmd脚本
- [linux]
  执行start-scheduler.sh脚本
  
##### step3:添加一个定时任务
访问http://localhost:8080/scheduler-ui.html，新增任务