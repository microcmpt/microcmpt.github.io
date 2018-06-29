## msa-scheduler-use
### Introduction
msa-scheduler是为调度众多定时任务而生的调度中心，msa-scheduler单机最大可承受几万个定时任务的执行，可采用集群模式，可将定时任务平均
分配到各个集群节点，减轻单机执行任务的负担，有如下特点：
- 可伸缩
- 错失触发
- 任务优先级

### Quick Start
##### step1:下载zip并解压
[scheduler-1.0.0.zip](https://github.com/microcmpt/msa-scheduler/blob/master/downloads/1.0.0/msa-scheduler-1.0.0.zip)

##### step2:启动scheduler
- [windows]
  执行start-scheduler.cmd脚本
- [linux]
  执行start-scheduler.sh脚本
  
##### step3:添加一个定时任务
访问http://localhost:8080/scheduler-ui.html，新增任务

### Properties Introduction
<table>
   <th>属性</th>
   <th>值</th>
   <th>说明</th>
   <tr>
      <td>scheduler.zk.enable</td>
      <td>true/false</td>
      <td>开启zk服务注册中心，默认为false</td>
   </tr>
   <tr>
      <td>scheduler.zk.addresses</td>
      <td>localhost:2181</td>
      <td>zk访问地址，根据自己的zk地址而定，多个以英文逗号分隔</td>
   </tr>
   <tr>
      <td>scheduler.mail.enable</td>
      <td>true/false</td>
      <td>是否开启发送邮件通知</td>
   </tr>
   <tr>
      <td>scheduler.mail.host</td>
      <td>示例格式：smtp.qq.com</td>
      <td>邮箱主机服务器地址</td>
   </tr>
   <tr>
      <td>scheduler.mail.username</td>
      <td>示例格式：1378127237@qq.com</td>
      <td>发送人邮件地址</td>
   </tr>
   <tr>
      <td>scheduler.mail.password</td>
      <td>示例格式：brVzdHV3a2t5Z29pZ2FqZTFxMnczZTRyIUAjJA==</td>
      <td>发送人邮箱授权码，加密后的</td>
   </tr>
</table>