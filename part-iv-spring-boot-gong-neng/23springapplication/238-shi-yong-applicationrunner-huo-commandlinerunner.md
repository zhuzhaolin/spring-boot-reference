### 23.8 使用ApplicationRunner或CommandLineRunner

SpringApplication启动时如果您需要运行一些特定的代码，就可以实现ApplicationRunner或CommandLineRunner接口。 两个接口都以相同的方式工作，并提供一个单独的运行方法，这将在SpringApplication.run（…）完成之前调用。

CommandLineRunner接口提供对应用程序参数的访问（简单的字符串数组），而ApplicationRunner使用上述的ApplicationArguments接口。

```
@Component
public class MyBean implements CommandLineRunner {
    public void run(String... args) {
        // Do something...
    }
}
```

如果定义了若干CommandLineRunner或ApplicationRunner bean，这些bean必须按特定顺序调用，您可以实现org.springframework.core.Ordered接口，也可以使用org.springframework.core.annotation.Order注解。