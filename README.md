## 安装hadoop
1. 使用wget命令安装，地址到官网上找
2. 修改环境变量，用source命令生效
```
export HADOOP_HOME=/home/xiaoju/hadoop-2.6.5
export PATH=$PATH:$HADOOP_HOME/bin
```

## MapReduce
![理解MapReduce](http://oyrpkn4bk.bkt.clouddn.com/MapReduce.jpg)

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

## 参考资料
[知乎：关于MapReduce的理解](https://www.zhihu.com/question/23345991)
