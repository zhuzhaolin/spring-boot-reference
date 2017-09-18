### 23.1 启动失败

如果您的应用程序无法启动，则注册的FailureAnalyzers会提供专门的错误消息和具体操作来解决问题。 例如，如果您在端口8080上启动Web应用程序，并且该端口已在使用中，则应该会看到类似于以下内容的内容：

```
***************************
APPLICATION FAILED TO START
***************************
Description:
Embedded servlet container failed to start. Port 8080 was already in use.
Action:
Identify and stop the process that's listening on port 8080 or configure this application to listen on another port.
```
    >Spring Boot提供了众多的FailureAnalyzer实现，您可以非常容易地[添加自己的实现](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#howto-failure-analyzer)。
    
如果没有故障分析器(analyzers)能够处理异常，您仍然可以显示完整的自动配置报告，以更好地了解出现的问题。 为此，您需要启用debug属性或启用org.springframework.boot.autoconfigure.logging.AutoConfigurationReportLoggingInitializer的DEBUG日志。

例如，如果使用java -jar运行应用程序，则可以按如下方式启用 debug：   
```
$ java -jar myproject-0.0.1-SNAPSHOT.jar --debug
``` 
    