### 24. 外部配置

Spring Boot允许您外部化您的配置，以便您可以在不同的环境中使用相同的应用程序代码。 您可以使用properties文件，YAML文件，环境变量和命令行参数来外部化配置。 可以使用@Value注释将属性值直接注入到您的bean中，该注释可通过Spring环境(Environment)抽象访问，或通过@ConfigurationProperties[绑定到结构化对象](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#boot-features-external-config-typesafe-configuration-properties)。

Spring Boot使用非常特别的PropertySource命令，旨在允许合理地覆盖值。属性按以下顺序选择：

    1. 在您的HOME目录设置的Devtools全局属性（~/.spring-boot-devtools.properties）。
    2. 单元测试中的 @TestPropertySource 注解。
    3. 单元测试中的 @SpringBootTest#properties 注解属性
    4. 命令行参数。
    5. SPRING_APPLICATION_JSON 中的属性值（内嵌JSON嵌入到环境变量或系统属性中）。
    6. ServletConfig 初始化参数。
    7. ServletContext 初始化参数。
    8. 来自 java:comp/env 的JNDI属性。
    9. Java系统属性（System.getProperties()）。
    10. 操作系统环境变量。
    11. RandomValuePropertySource，只有随机的属性     random.* 中。
    12. jar包外面的 Profile-specific application properties （application- {profile} .properties和YAML变体）
    13. jar包内的 Profile-specific application properties （application-{profile}.properties和YAML变体）
    14. jar包外的应用属性文件（application.properties和YAML变体）。
    15. jar包内的应用属性文件（application.properties和YAML变体）。
    16. 在@Configuration上的@PropertySource注解。
    17. 默认属性（使用SpringApplication.setDefaultProperties设置）。
    
一个具体的例子，假设你开发一个使用name属性的@Component：
```
import org.springframework.stereotype.*
import org.springframework.beans.factory.annotation.*
@Component
public class MyBean {
    @Value("${name}")
    private String name;
    // ...
}
```

在应用程序类路径（例如，您的jar中）中，您可以拥有一个application.properties，它为 name 属性提供了默认属性值。 在新环境中运行时，可以在您的jar外部提供一个application.properties来覆盖 name 属性; 对于一次性测试，您可以使用特定的命令行开关启动（例如，java -jar app.jar –name=”Spring”）。

SPRING_APPLICATION_JSON属性可以在命令行中提供一个环境变量。 例如在UN*X shell中：

```
$ SPRING_APPLICATION_JSON='{"foo":{"bar":"spam"}}' java -jar myapp.jar
```
在本例中，您将在Spring环境中使用foo.bar = spam。 您也可以在系统变量中将JSON作为spring.application.json提供：
```
$ java -Dspring.application.json='{"foo":"bar"}' -jar myapp.jar
``` 
或命令行参数： 
```
$ java -jar myapp.jar --spring.application.json='{"foo":"bar"}'
``` 

 或作为JNDI变量 java:comp/env/spring.application.json 。 
    