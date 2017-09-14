### 19.3 使用 Maven 插件

Spring Boot Maven 插件包含一个运行目标(goal )，可用于快速编译和运行应用程序。 应用程序以exploded的形式运行，就像在IDE中一样。

```
$ mvn spring-boot:run
```

您可能还需要使用一些有用的操作系统环境变量：
```
$ export MAVEN_OPTS=-Xmx1024m -XX:MaxPermSize=128M
```

