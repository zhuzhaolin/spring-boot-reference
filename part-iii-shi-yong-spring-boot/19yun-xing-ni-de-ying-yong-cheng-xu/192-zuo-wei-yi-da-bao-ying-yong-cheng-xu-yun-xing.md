### 19.2 作为已打包应用程序运行

如果您使用Spring Boot 的 Maven或Gradle插件创建可执行jar，则可以使用java -jar运行应用程序。 例如：

```1
$ java -jar target/myproject-0.0.1-SNAPSHOT.jar
```
也可以启用远程调试支持运行打包的应用程序。 这允许您将调试器添加到打包的应用程序中：
```
$ java -Xdebug -Xrunjdwp:server=y,transport=dt_socket,address=8000,suspend=n \
       -jar target/myproject-0.0.1-SNAPSHOT.jar
```