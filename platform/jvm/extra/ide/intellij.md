# Intellij IDEA

## 有用的设置

### 代码自动编译

首先，设置自动编译：

> File | Settings | Build, Execution, Deployment | Compiler | Build project automatically

其次，设置运行时编译：

> 双击Shift搜索进入Registry ，找到compiler.automake.allow.when.app.running ，然后勾选上。

## Live Template

### 生成`serialVersionUID`

```java
// Edit variables: groovyScript("new Random().nextLong().abs()")
private static final long serialVersionUID = $serialVersionUID$L;
```

## 常用插件

- [Alibaba Java Coding Guidelines](https://plugins.jetbrains.com/plugin/10046-alibaba-java-coding-guidelines/)
- [Free MyBatis plugin](https://plugins.jetbrains.com/plugin/8321-free-mybatis-plugin/)
- [jclasslib Bytecode viewer Ingo Kegel](https://plugins.jetbrains.com/plugin/9248-jclasslib-bytecode-viewer/)
- [Lombok](https://plugins.jetbrains.com/plugin/6317-lombok/)
- [Maven Helper](https://plugins.jetbrains.com/plugin/7179-maven-helper/)
- [Rainbow Brackets](https://plugins.jetbrains.com/plugin/10080-rainbow-brackets/)
- [SequenceDiagram](https://plugins.jetbrains.com/plugin/8286-sequencediagram/)



