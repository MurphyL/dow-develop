## Kettle运维

```sh
# 指定端口运行远程服务
nohup /opt/kettle/data-integration/carte.sh 0.0.0.0 8101 > kettle.out 2>&1 &
# 通过配置文件运行服务端
nohup /opt/kettle/data-integration/carte.sh /root/.kettle/config-master.xml
```
- [使用HTTP执行远程服务](https://help.pentaho.com/Documentation/7.1/0R0/070/020/020/030)
- [Kettle实战](https://www.xiaominfo.com/categories/#Kettle实战)