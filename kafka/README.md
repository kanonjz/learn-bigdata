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
