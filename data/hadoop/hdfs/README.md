## Hadoop Distributed File System

`HDFS`是`Hadoop`下的分布式文件系统，具有高容错、高吞吐量等特性，可以部署在低成本的硬件上。

### HDFS 架构

`HDFS` 遵循主/从架构，由单个 `NameNode` 和多个 `DataNode` 组成：

- `NameNode`: 负责执行有关 文件系统命名空间 的操作，例如打开，关闭、重命名文件和目录等。它同时还负责集群元数据的存储，记录着文件中各个数据块的位置信息。
- `DataNode`：负责提供来自文件系统客户端的读写请求，执行块的创建，删除等操作。

### 文件系统命名空间

`HDFS`的文件系统命名空间的层次结构与大多数文件系统类似，支持目录和文件的创建、移动、删除和重命名等操作，支持配置用户和访问权限，但不支持硬链接和软连接。`NameNode` 负责维护文件系统名称空间，记录对名称空间或其属性的任何更改。

### 文件系统操作

```sh
# 格式化文件系统
$HADOOP_HOME/bin/hadoop namenode -format

# 报告HDFS健康状况
$HADOOP_HOME/bin/hadoop dfsadmin -report
```

### 常用运维命令

```sh
# 启动
$HADOOP_HOME/bin/start-dfs.sh

# 停止
$HADOOP_HOME/bin/stop-dfs.sh
```

### 参考资料

- [Hadoop分布式文件系统——HDFS](https://github.com/heibaiying/BigData-Notes/blob/master/notes/Hadoop-HDFS.md)