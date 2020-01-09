# Maven

## 基础配置

```xml
<properties>
    <maven.compiler.target>1.8</maven.compiler.target>
    <maven.compiler.source>1.8</maven.compiler.source>
</properties>
```

## 插件

```xml
<build>
    <plugins>
        <!-- Tomcat -->
        <plugin>
            <groupId>org.apache.tomcat.maven</groupId>
            <artifactId>tomcat7-maven-plugin</artifactId>
            <version>2.2</version>
            <configuration>
                <path>/</path>
                <port>9090</port>
                <uriEncoding>UTF-8</uriEncoding>
            </configuration>
        </plugin>
    </plugins>
</build>
```

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

- [Maven 3 - 华为开源镜像站](https://mirrors.huaweicloud.com/apache/maven/maven-3/)

### setting.xml 配置

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

#### mirrorOf 配置

`mirrorOf` 用来指定该镜像针对的仓库。用法如下：

- `*` 匹配所有仓库
- `external:*` 匹配除了本机和基于文件的所有外部构建地址。
- `repo,repo1` 匹配仓库repo和repo1
- `*,!repo1` 除了仓库repo1匹配所有