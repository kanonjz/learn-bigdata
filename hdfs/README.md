![hdfs架构](https://hadoop.apache.org/docs/stable/hadoop-project-dist/hadoop-hdfs/images/hdfsarchitecture.png)

问题：我们已经在hdfs-site.xml中设置了副本系数为1，为什么此时查询文件看到的3呢？
 如果你是通过hdfs shell的方式put的上去的那么，才采用默认的副本系数1
 如果我们是java api上传上去的，在本地我们并没有手工设置副本系数，所以否则采用的是hadoop自己的副本系数
