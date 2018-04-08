## 安装hadoop（伪分布式）
1. 使用wget命令安装，地址到官网上找
2. 修改环境变量，用source命令生效
```
export HADOOP_HOME=/home/xiaoju/hadoop-2.6.5
export PATH=$PATH:$HADOOP_HOME/bin
```
3. Java
4. 修改配置文件(hadoop_home/etc/hadoop)
```
hadoop-env.sh
	export JAVA_HOME=/home/hadoop/app/jdk1.7.0_79

core-site.xml
    <property>
	<name>fs.defaultFS</name>
	<value>hdfs://hadoop000:8020</value>
    </property>

    <property>
	<name>hadoop.tmp.dir</name>
	<value>/home/hadoop/app/tmp</value>
    </property>

hdfs-site.xml
    <property>
	<name>dfs.replication</name>
	<value>1</value>
    </property>

slaves
```
slaves文件在单机时直接写上自己的ip地址，多机时参考教程。
```
YARN环境搭建
1）mapred-site.xml
<property>
    <name>mapreduce.framework.name</name>
    <value>yarn</value>
</property>

2）yarn-site.xml
<property>
    <name>yarn.nodemanager.aux-services</name>
    <value>mapreduce_shuffle</value>
</property>

<property>
    <name>yarn.resourcemanager.hostname</name>
    <value>hadoop000</value>
</property>

```

5. 格式化文件系统（仅第一次执行即可，不要重复执行）
```
hdfs/hadoop namenode -format
```

6. 启动hdfs: sbin/start-dfs.sh
验证是否启动成功：jps
- DataNode
- SecondaryNameNode
- NameNode

浏览器访问方式： http://hadoop000:50070

## 安装hadoop集群
1. 在单台机器上按伪分布式搭好

2. 修改slaves配置文件，并用scp将hadoop文件夹发送到其他主机上

3. 设置免密登录，利用ssh-copy-id将master机器的公钥放到其他机器上

## hdfs基本操作
1. 端口[hadoop常用端口及其配置](http://www.aboutyun.com/thread-7513-1-1.html)

yarn界面：8088  

hdfs界面：50070  

JobHistory界面：19888

hdfs接收客户端连接的rpc端口：8020

2. 启动hdfs
```
sbin/start-dfs.sh
```

3. 停止hdfs
```
sbin/stop-dfs.sh
```

## 启动Jobhistory  
[参考文章](http://www.cnblogs.com/luogankun/p/4019303.html)

## MapReduce基本操作
运行jar包。com.didi.hadoop.mapreduce.WordCountApp是main函数所在的地方，所有要输入的文件都放在input目录下。
```
hadoop jar hadoop-train-1.0.jar com.didi.hadoop.mapreduce.WordCountApp hdfs://10.96.112.172:8020/input hdfs://10.96.112.172:8020/output/wc
```

## Combiner和Partition
**Combiner**是MapReduce的一个优化技巧，会在Mapper输出的基础上运行Combiner，Combiner的输出格式与Reducer的输入格式是一样的。由于MapReduce作业受到集群可用带宽的限制，Combiner可以最大限度地减少map和reduce任务之间传输的数据。

**Partitioner**就是将Mapper的结果按某种条件进行分区，每一个分区都由一个Reducer来进行处理，最终每一个Reducer都会生成一个结果集。

## hadoop中的进程
master：NameNode、SecondaryNameNode、ResourceManager、JobTracker

slave：DataNode、NodeManager、TaskTracker

## 参考资料
[知乎：关于MapReduce的理解](https://www.zhihu.com/question/23345991)
