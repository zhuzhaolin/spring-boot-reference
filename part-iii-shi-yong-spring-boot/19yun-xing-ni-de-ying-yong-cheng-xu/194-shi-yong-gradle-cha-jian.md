### 19.4 使用Gradle插件
Spring Boot Gradlet插件还包括一个bootRun任务，可用于以exploded 形式运行应用程序。 每当导入spring-boot-gradle-plugin时，都会添加bootRun任务：

```
$ gradle bootRun
```

您可能还需要使用一些有用的操作系统环境变量：
```
$ export JAVA_OPTS=-Xmx1024m -XX:MaxPermSize=128M
```