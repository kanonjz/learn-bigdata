## YARN诞生背景
MapReduce1.x存在的问题：
- 单点故障。JobTracker挂掉了，整个集群就挂掉了。
- 中心节点压力大不易扩展。
- 仅能够支持MapReduce作业，不支持除了MapReduce之外的计算框架。

![](http://oyrpkn4bk.bkt.clouddn.com/mapreduce1.png)

YARN是一个操作系统级别的资源调度框架，可以让更多的计算框架如MapReduce、Spark、Storm、Flink都运行在同一个集群里面，且不同的计算框架可以共享同一个HDFS集群上的数据，享受整体的资源调度，进而提高集群资源的利用率。

![](http://oyrpkn4bk.bkt.clouddn.com/yarn.png)
