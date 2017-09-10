### 25. 配置文件(Profiles)

Spring 配置文件提供了将应用程序配置隔离的方法，使其仅在某些环境中可用。 任何@Component或@Configuration都可以使用@Profile进行标记，以限制其在什么时候加载：
```
@Configuration
@Profile("production")
public class ProductionConfiguration {
    // ...
}
```

一般，您可以使用spring.profiles.active Environment属性来指定哪些配置文件处于激活状态。 您可以以任何方式指定属性，例如，您可以将其包含在您的application.properties中：

```
spring.profiles.active=dev,hsqldb
```

或者使用命令行--spring.profiles.active=dev,hsqldb在命令行中指定。