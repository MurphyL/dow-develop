## Kettle

kettle是一个ETL（Extract, Transform and Load）工具，ETL工具在数据仓库项目使用非常频繁。

### 主要应用场景

- 在不同应用或数据库之间整合数据
- 把数据库中的数据导出到文本文件
- 大批量数据装载入数据库
- 数据清洗
- 集成应用相关项目是个使用


### HTTP API

API主页：http://121.40.155.130:8101/
任务状态：http://121.40.155.130:8101/kettle/status/
任务执行结果查询：http://121.40.155.130:8101/kettle/jobStatus/?name=x&id=981a196a-643f-42c6-8888-97da0b7924bb&xml=y
执行文件中的任务：http://121.40.155.130:8101/kettle/executeJob/?job=../task/murph/test&dt=2019-11-12
执行子服务器上的任务：http://121.40.155.130:8101/kettle/runJob/?job=fxjb&dt=2019-11-12


### 链接

- [Sourceforge - Pentaho kettle](https://sourceforge.net/projects/pentaho/)