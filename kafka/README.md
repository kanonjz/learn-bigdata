## 简介
kafka是分布式的流数据平台，进行流数据集成，以Pub/Sub形式的消息总线形式提供。

#### 特点
- 提供Pub/Sub方式的海量消息处理
- 以高容错的方式存储海量数据流
- 保证数据流的顺序

## 安装kafka
linux下安装kafka：

1. 使用wget命令安装

2. tar -zxvf 压缩文件 -C 指定目录

3. 启动自带的zookeeper.如果端口被占用，则需要修改zookeeper配置文件默认的端口，kafka配置文件也需要修改。
```
config/zookeeper.properties
config/server.properties
```

## 功能
在quickstart教程里，有这么4个功能
- 在控制台里实现发布订阅模式
- 建立多broker的集群
- 使用Kafka Connect实时从文件读取，以及实时输出到文件
- 使用Kafka Streams处理数据

4. 跟着官网教程来[Quickstart](http://kafka.apache.org/quickstart)

## 连接kafka
python：pykafka
