## 如何接入

### 1. 引入Maven依赖：

在`pom.xml`文件中新增如下依赖：

```xml
<dependency>
    <groupId>com.ctrip.framework.apollo</groupId>
    <artifactId>apollo-client</artifactId>
    <version>1.1.0</version>
</dependency>
```

### 2. 新增配置文件

在项目内新增配置文件：`META-INF/app.properties`，内容如下：

```properties
app.id=your-app-id
apollo.bootstrap.enabled=true
```

在硬盘上新增配置文件：`C:/opt/settings/server.properties`，内容如下：

```properties
# Windows配置文件位置：C:/opt/settings/server.properties
# Unix Like系统配置文件位置：/opt/settings/server.properties

# 当前配置方式下，env参数没什么作用
env=DEV

# 指定配置Server，需要那个环境，则启用那个环境
# LOCAL
apollo.meta=http://172.16.163.72:8080
# DEV
# apollo.meta=http://172.16.163.71:8080
# QASA
# apollo.meta=http://172.16.163.77:9080
# QASB
# apollo.meta=http://172.16.162.193:9080
```

> 更多配置方式，请参考【[官方文档](https://github.com/ctripcorp/apollo/wiki/Java客户端使用指南)】。

### 3. 与`Spring`集成：

#### 基于`XML`的配置：

> Spring 3.0 及之后的版本已不再推荐使用`XML`配置了。

修改`applicationContext.xml`文件，邢增`apollo`配置：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:apollo="http://www.ctrip.com/schema/apollo"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
                           http://www.springframework.org/schema/beans/spring-beans.xsd
                           http://www.ctrip.com/schema/apollo 
                           http://www.ctrip.com/schema/apollo.xsd">
    <!-- 这个是最简单的配置形式 -->
    <apollo:config/>
    <!-- 指示Apollo注入dev.plugin namespace的配置到Spring环境中  -->
    <apollo:config namespaces="dev.plugin"/>
    <!-- others -->
</beans>
```

> 注：需要把`Apollo`相关的`xml namespace`加到配置文件头上，不然会报xml语法错误。

#### 基于`Java`的配置（推荐）

相对于基于XML的配置，基于Java的配置是目前比较流行的方式。

注意`@EnableApolloConfig`要和`@Configuration`一起使用，不然不会生效。

```java
@Configuration
// 在配置类上新增`@EnableApolloConfig`注解既可。
@EnableApolloConfig
public class AppConfig {
    // do something...
}

@Configuration
// 指示Apollo注入dev.plugin namespace的配置到Spring环境中
@EnableApolloConfig({"dev.plugin"})
public class AnotherAppConfig {
    // do something...
}
```

#### Spring Boot集成方式（推荐）

使用方式很简单，只需要在application.properties/bootstrap.properties中按照如下样例配置即可。

##### 注入默认application namespace的配置示例

```properties
# will inject 'application' namespace in bootstrap phase
apollo.bootstrap.enabled = true
```

##### 注入非默认application namespace或多个namespace的配置示例

```properties
apollo.bootstrap.enabled = true
# will inject 'application', 'dev.plugin' namespace in bootstrap phase
apollo.bootstrap.namespaces = application, dev.plugin
```

### 4. 使用配置：

#### Spring Placeholder的使用

##### XML使用方式

```xml
<bean class="com.chtwm.datasupply.TestBean">
    <!-- timeout是参数名称，100是默认值 -->
    <property name="timeout" value="${timeout:100}"/>
    <property name="batch" value="${batch:200}"/>
</bean>
```

##### Java Config使用方式

```java
// timeout是参数名称，100是默认值
@Value("${timeout:100}")
private int timeout;
```

>  更多使用配置的方式，请参考【[官方文档](https://github.com/ctripcorp/apollo/wiki/Java客户端使用指南)】。

### 5. 其他问题：

> 注：部分项目使用了`filters`目录下的文件来加载相应环境的配置，若移除了`fliters`文件中的配置，也请相应的删掉`config.properties`文件中的配置。

#### 切换配置环境、集群：

在`/opt/settings/server.properties`文件中可以指定配置中心的`apollo.meta`和`apollo.cluster`来达到切换环境和集群的目的。

