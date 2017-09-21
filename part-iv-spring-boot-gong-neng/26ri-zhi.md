### 26. 日志

Spring Boot使用[Commons Logging](https://commons.apache.org/logging)进行所有内部日志记录，但使基础日志实现开放。 默认配置提供了[Java Util Logging](https://docs.oracle.com/javase/7/docs/api/java/util/logging/package-summary.html)，[Log4J2](https://logging.apache.org/log4j/2.x/)和[Logback](http://logback.qos.ch/)。 在每种情况下，记录器都预先配置为使用控制台输出和可选文件输出都可用。

默认情况下，如果使用’Starters’，将会使用Logback。 还包括适当的Logback路由，以确保使用Java Util Logging，Commons Logging，Log4J或SLF4J的依赖库都能正常工作。

    >有很多可用于Java的日志记录框架。 如果上面的列表看起来很混乱，别担心。 一般来说，您不需要更改日志依赖关系，并且Spring Boot默认值将正常工作。