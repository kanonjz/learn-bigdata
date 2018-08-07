## YARN诞生背景
MapReduce1.x存在的问题：
- 单点故障。JobTracker挂掉了，整个集群就挂掉了。
- 中心节点压力大不易扩展。
- 仅能够支持MapReduce作业，不支持除了MapReduce之外的计算框架。

YARN是一个操作系统级别的资源调度框架，可以让更多的计算框架如MapReduce、Spark、Storm、Flink都运行在同一个集群里面，且不同的计算框架可以共享同一个HDFS集群上的数据，享受整体的资源调度，进而提高集群资源的利用率。

## YARN架构
![yarn架构](http://oyrpkn4bk.bkt.clouddn.com/yarn%E6%9E%B6%E6%9E%84.png)

ResourceManager：
- ResourceManager负责整个集群的资源管理和分配，是一个全局的资源管理系统。

NodeManager：
- NodeManager是每个节点上的资源和任务管理器，它是管理这台机器的代理，负责该节点程序的运行，以及该节点资源的管理和监控。
- 以心跳的方式向ResourceManager汇报资源使用情况（CPU和内存）。
- 接收并处理来自AppMaster的Container启动、停止等各种请求。

AppMaster：
- 用户提交的每个应用程序均包含一个AppMaster，它可以运行在ResourceManager以外的机器上。
- 负责与RM调度器协商以获取资源（用Container表示）
- 与NM通信以启动/停止任务。
- 监控所有任务运行状态，并在任务运行失败时重新为任务申请资源以重启任务

Container：资源的一种抽象



## 运行过程
1、client向RM提交应用程序，其中包括启动该应用的ApplicationMaster的必须信息，例如ApplicationMaster程序、启动ApplicationMaster的命令、用户程序等。

2、ResourceManager启动一个container用于运行ApplicationMaster。

3、启动中的ApplicationMaster向ResourceManager注册自己，启动成功后与RM保持心跳。

4、ApplicationMaster向ResourceManager发送请求，申请相应数目的container。

5、ResourceManager返回ApplicationMaster的申请的containers信息。申请成功的container，由ApplicationMaster进行初始化。container的启动信息初始化后，AM与对应的NodeManager通信，要求NM启动container。AM与NM保持心跳，从而对NM上运行的任务进行监控和管理。

6、container运行期间，ApplicationMaster对container进行监控。container通过RPC协议向对应的AM汇报自己的进度和状态等信息。

7、应用运行期间，client直接与AM通信获取应用的状态、进度更新等信息。

8、应用运行结束后，ApplicationMaster向ResourceManager注销自己，并允许属于它的container被收回。
