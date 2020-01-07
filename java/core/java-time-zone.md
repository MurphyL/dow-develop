## 时区设置

### 全局设置

> 为应用程序设置全局时区。现在的应用程序中，通常设置时区的粒度更细。

- 设置环境变量

```sh
export TZ="America/Sao_Paulo"
```

- 设置JVM参数

```sh
java -Duser.timezone="Asia/Kolkata" com.company.Main
```

- 在Java程序中设置时区

```java
// 设置环境变量
System.setProperty("user.timezone", "Asia/Kolkata");

// 设置默认时区
TimeZone.setDefault(TimeZone.getTimeZone("Portugal"));
```

### 参考资料

- [Core Date Operations](https://github.com/eugenp/tutorials/tree/master/core-java-modules/core-java-date-operations)