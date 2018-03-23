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

## hdfs基本操作
1. 端口[hadoop常用端口及其配置](http://www.aboutyun.com/thread-7513-1-1.html)

yarn界面：8088  

hdfs界面：50070  

hdfs接收客户端连接的rpc端口：8020

2. 启动hdfs
```
sbin/start-dfs.sh
```

3. 停止hdfs
```
sbin/stop-dfs.sh
```

## MapReduce基本操作
运行jar包。com.didi.hadoop.mapreduce.WordCountApp是main函数所在的地方，所有要输入的文件都放在input目录下。
```
hadoop jar hadoop-train-1.0.jar com.didi.hadoop.mapreduce.WordCountApp hdfs://10.96.112.172:8020/input hdfs://10.96.112.172:8020/output/wc
```

## hadoop中的进程
master：NameNode、SecondaryNameNode、ResourceManager、JobTracker

slave：DataNode、NodeManager、TaskTracker

## 参考资料
[知乎：关于MapReduce的理解](https://www.zhihu.com/question/23345991)
