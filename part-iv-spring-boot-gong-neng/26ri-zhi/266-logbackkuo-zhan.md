### 26.6 Logback扩展

Spring Boot包括大量的Logback扩展，可以帮助您进行高级配置。 您可以在logback-spring.xml配置文件中使用这些扩展。

    >您不能在标准logback.xml配置文件中使用扩展名，因为其加载时间太早。 您需要使用logback-spring.xml或定义logging.config属性。

    >扩展名不能与Logback的配置扫描一起使用。 如果您尝试这样做，对配置文件进行更改将导致类似于以下记录之一的错误：

```
ERROR in ch.qos.logback.core.joran.spi.Interpreter@4:71 - no applicable action for [springProperty], current ElementPath is [[configuration][springProperty]]
ERROR in ch.qos.logback.core.joran.spi.Interpreter@4:71 - no applicable action for [springProfile], current ElementPath is [[configuration][springProfile]]
```