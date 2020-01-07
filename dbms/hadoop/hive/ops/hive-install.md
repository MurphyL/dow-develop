# Hadoop集群搭建

> 假设集群共三个节点，三个节点的IP分别为192.168.10.1，192.168.10.2，192.168.10.3。

### 基础环境准备

#### 1. Hosts配置

> 三个机器都要配置

```shell
192.168.10.1 hadoop1 # Hadoop NameNode，Hadoop DataNode，Hive子节点，Yarn NodeManager
192.168.10.2 hadoop2 # Hive主节点，Hadoop DataNode，Yarn ResourceManager
192.168.10.3 hadoop3 # Yarn主节点，Hadoop DataNode，Hive子节点，Yarn NodeManager
```

#### 2. 各节点创建用户`hive`

> 三个机器都要配置

```shell
groupadd supergroup
useradd -g supergroup hive
passwd hive		# 设置用户密码

```

#### 3. 各节点间免密登录

> 需要`hadoop1`访问所有节点（包括自己）无障碍。验证方式如下：

```shell
ssh hadoop1
ssh hadoop2
ssh hadoop3
```

> 需要`hadoop2`访问所有节点（包括自己）无障碍。验证方式如下：

```shell
ssh hadoop1
ssh hadoop2
ssh hadoop3
```

#### 4. 确认`Java`环境

```shell
which java    # /opt/jdk1.8.0_131/bin/java
java -version # 1.8.0_131
```

### 安装`Hadoop`

#### Hadoop环境准备

> 三个节点相同的操作。

```shell
# 创建工作目录
mkdir -p /data/hadoop/tmp /data/hadoop/hdfs/namenode /data/hadoop/hdfs/datanode
chown -R hive:supergroup /data/hadoop/tmp
chown -R hive:supergroup /data/hadoop/hdfs

su hive     # 以下操作尽量需要在hive用户下完成，Hadoop的权限管理一定程度上依赖了系统用户的权限

# 安装Hadoop
rz hadoop.tar.gz
tar -zxvf hadoop.tar.gz
cd hadoop-2.9.2
pwd         # /home/hive/backup/hadoop-2.9.2

# 配置环境变量
vi ~/.bashrc	# 按照下文设置环境变量
source ~/.bashrc
```

> 环境变量如下：

```shell
export HADOOP_HOME=/home/hive/backup/hadoop-2.9.2
export HADOOP_PREFIX=$HADOOP_HOME
export HADOOP_MAPRED_HOME=$HADOOP_HOME 
export HADOOP_COMMON_HOME=$HADOOP_HOME 
export HADOOP_HDFS_HOME=$HADOOP_HOME 
export YARN_HOME=$HADOOP_HOME
export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native 
export PATH=$PATH:$HADOOP_HOME/sbin:$HADOOP_HOME
```

#### 修改Hadoop配置

```shell
vi $HADOOP_HOME/etc/hadoop/slaves
```

> 配置内容如下：

```text
hadoop1
hadoop2
hadoop3
```

```shell
vi $HADOOP_HOME/etc/hadoop/core-site.xml
```

> 修改`hadoop.proxyuser`开头的配置为：

```xml
    <!-- 若系统创建的缓存目录为/data/hadoop/tmp -->
    <property>
        <name>hadoop.tmp.dir</name>
        <value>/data/hadoop/tmp</value>
    </property>
    <!-- 若系统创建的用户为hive -->
    <property>
       <name>hadoop.proxyuser.hive.groups</name>
       <value>*</value>
    </property>
    <property>
       <name>hadoop.proxyuser.hive.hosts</name>
       <value>*</value>
    </property>
```

```shell
vi $HADOOP_HOME/etc/hadoop/hdfs-site.xml
```

```xml
   <!-- 设置block副本数为3 -->
   <property>
      <name>dfs.replication</name>
      <value>3</value>
   </property>
   <!-- 若系统创建的用户组为supergroup -->
   <property>
      <name>dfs.permissions.superusergroup</name>
      <value>supergroup</value>
   </property>
   <!-- 若系统创建的HDFS namenode数据存储目录为/data/hadoop/hdfs/namenode -->
   <property>
      <name>dfs.namenode.name.dir</name>
      <value>file:///data/hadoop/hdfs/namenode</value>
   </property>
   <!-- 若系统创建的HDFS datanode数据存储目录为/data/hadoop/hdfs/datanode -->
   <property>
      <name>dfs.datanode.data.dir</name>
      <value>file:///data/hadoop/hdfs/datanode</value>
   </property>
```

#### 启动`Hadoop`

> 以下配置仅在hadoop1节点操作即可。

```shell
# 验证Hadoop的安装
$HADOOP_HOME/bin/hadoop version
# 如无异常则格式化NameNode
$HADOOP_HOME/bin/hadoop namenode -format
# 无报错则启动HDFS服务
$HADOOP_HOME/sbin/start-dfs.sh
# 通过Web UI确认HDFS
curl http://192.168.10.54:50070
# 启动Yarn
$HADOOP_HOME/sbin/start-yarn.sh
curl http://192.168.10.1:8088
```

### 安装Hive

#### 准备工作目录

```shell
# HDFS - Hive相关目录权限设置
$HADOOP_HOME/bin/hadoop fs -mkdir -p /tmp
$HADOOP_HOME/bin/hadoop fs -chown -R hive:supergroup /tmp
$HADOOP_HOME/bin/hadoop fs -mkdir -p /user/hive/warehouse
$HADOOP_HOME/bin/hadoop fs -chown -R hive:supergroup /user/hive/warehouse
```
#### 配置、安装

> `hadoop2`作为Hive主节点

```shell
mkdir ~/logs
rz hive.tar.gz
tar -zxvf hive.tar.gz
cd apache-hive-3.1.1-bin
pwd         # /home/hive/backup/apache-hive-3.1.1-bin
# 配置环境变量
vi ~/.bashrc        # 按照下文设置环境变量
source ~/.bashrc
```

> 设置环境变量

```shell
export HIVE_HOME=/home/hive/backup/apache-hive-3.1.1-bin
export PATH=$PATH:$HIVE_HOME/bin

```
#### Hive主节点（`hadoop2`）配置

注释`$HIVE_HOME/conf/hive-site.xml`下的`hive.metastore.uris`节点配置；
配置zookeeper等信息（`hive.zookeeper`）开头（值需知会开发）以及`hive.server2.zookeeper.namespace`（值可以随意定，如`data_supply_hive`，但是需知会开发）；

```shell
vi $HIVE_HOME/conf/hive-site.xml
```

```xml
    <!-- Zookeeper HiveServer2的namespace -->
    <property>
        <name>hive.server2.zookeeper.namespace</name>
        <value>data_supply_hive</value>
    </property>
    <!-- Zookeeper协调服务连接串，多个以英文逗号分割 -->
    <property>
        <name>hive.zookeeper.quorum</name>
        <value>zk_node1:2181,zk_node2:2181</value>
    </property>
    <!-- Zookeeper协调服务连接串，多个以英文逗号分割 -->
    <property>
        <name>hive.zookeeper.client.port</name>
        <value>2181</value>
    </property>
    <!-- meta store 配置 -->
    <!-- meta store配置，主节点要注释该配置，子节点要启用该配置 -->
    <!--
    <property>  
        <name>hive.metastore.uris</name>  
        <value>thrift://hadoop2:9083</value>  
    </property>
    -->
    <property>
        <name>hive.server2.thrift.port</name>
        <value>10001</value>
    </property>
    <!-- 元数据存储数据库配置 -->
    <!-- MySQL JDBC连接串 -->
    <property>
        <name>javax.jdo.option.ConnectionURL</name>
        <value>jdbc:mysql://192.168.10.40:3306/hive_dev?createDatabaseIfNotExist=true&amp;useSSL=true</value>
    </property>
    <!-- MySQL JDBC Driver -->
    <property>
        <name>javax.jdo.option.ConnectionDriverName</name>
        <value>com.mysql.jdbc.Driver</value>
    </property>
    <!-- MySQL User -->
    <property>
        <name>javax.jdo.option.ConnectionUserName</name>
        <value>hive</value>
    </property>
    <!-- MySQL Password -->
    <property>
        <name>javax.jdo.option.ConnectionPassword</name>
        <value>hive</value>
    </property>
```

##### 子节点配置

```xml
    <!-- 除如下配置，其他配置均与主节点保持一致 -->
    <!-- meta store配置，主节点要注释该配置，子节点要启用该配置 -->
    <property>  
        <name>hive.metastore.uris</name>  
        <value>thrift://hadoop2:9083</value>  
    </property>
```

#### 配置MySQL为元数据管理库

```shell
vi $HIVE_HOME/conf/hive-site.xml 	# 配置MySQL的三个选项（javax.jdo.option开头）
$HIVE_HOME/bin/schematool -initSchema -dbType mysql
```

>  创建一个MySQL数据库，用于存储Hive的元数据；

```sql
ALTER TABLE `columns_v2`
    CHANGE COLUMN `COMMENT` `COMMENT` VARCHAR(256) NULL DEFAULT NULL COLLATE 'ucs2_general_ci';

ALTER TABLE `table_params`
    CHANGE COLUMN `PARAM_VALUE` `PARAM_VALUE` MEDIUMTEXT NULL COLLATE 'utf8_general_ci';

ALTER TABLE `partition_keys`
    CHANGE COLUMN `PKEY_COMMENT` `PKEY_COMMENT` VARCHAR(4000) NULL DEFAULT NULL COLLATE 'utf8_general_ci';
```

#### 验证、启动


```sql
# 验证Hive安装
$HIVE_HOME/bin/beeline
!connect jdbc:hive2://zk_node1:2181,zk_node2:2181/;serviceDiscoveryMode=zooKeeper;zooKeeperNamespace=data_supply_hive hive hive
```

> #### 验证Hive

```sql
show functions;
desc function uuid;
select 1;
```

> Ctrl+C推出Hive，启动Hive Server

```shell
$HIVE_HOME/bin/hiveserver2
# 验证安装
curl http://192.168.10.2:10002
```