## hdfs优点
- 数据冗余、硬件容错
- 处理流式的数据访问（一次写入多次读取）
- 适合存储大文件
- 可构建在廉价机器上

## hdfs缺点
- 不适合小文件存储
> 在HDFS中，namenode将文件系统中的元数据存储在内存中，因此，HDFS所能存储的文件数量会受到namenode内存的限制。一般来说，每个文件、目录、数据块的存储信息大约占150个字节，根据当前namenode的内存空间的配置，就可以计算出大约能容纳多少个文件了。如果小文件过多，就会大量占用namenode的内存。

> HDFS小文件是独立的存在，不会占用一个默认block大小，而是占用实际的文件大小。
- 数据访问延迟

## hdfs架构图
![hdfs架构](https://hadoop.apache.org/docs/stable/hadoop-project-dist/hadoop-hdfs/images/hdfsarchitecture.png)

## 注意
- 我们已经在hdfs-site.xml中设置了副本系数为1，为什么此时查询文件看到的3呢？  
如果你是通过hdfs shell的方式put的上去的那么，才采用默认的副本系数1。如果我们是java api上传上去的，在本地我们并没有手工设置副本系数，所以否则采用的是hadoop自己的副本系数。
