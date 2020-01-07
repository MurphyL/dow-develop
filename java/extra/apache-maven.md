
## 国内Maven镜像站点

- Aliyun

```xml
<mirror>  
      <id>alimaven</id>  
      <name>aliyun maven</name>  
      <url>http://maven.aliyun.com/nexus/content/groups/public/</url>  
      <mirrorOf>central</mirrorOf>    
</mirror>
```

#### setting.xml 配置

```xml
<mirrors>
    <!-- 作为中央仓库的镜像 -->
    <mirror>
      <id>nexus-aliyun</id>
      <name>Nexus aliyun</name>
      <mirrorOf>central</mirrorOf>
      <url>http://maven.aliyun.com/nexus/content/groups/public</url>
    </mirror>
    <!-- 私有， 公司内部使用 -->
    <mirror>
      <id>nexus-mine</id>
      <name>Nexus mine</name>
      <mirrorOf>*</mirrorOf>
      <url>http://xx.xx.xx.xx/nexus/content/groups/public</url>
    </mirror>
  </mirrors>
```

##### mirrorOf 配置

`mirrorOf` 用来指定该镜像针对的仓库。用法如下：

- `*` 匹配所有仓库
- `external:*` 匹配除了本机和基于文件的所有外部构建地址。
- `repo,repo1` 匹配仓库repo和repo1
- `*,!repo1` 除了仓库repo1匹配所有