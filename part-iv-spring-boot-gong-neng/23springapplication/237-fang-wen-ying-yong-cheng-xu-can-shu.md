### 23.7 访问应用程序参数

如果您需要访问传递给SpringApplication.run()的应用程序参数，则可以注入org.springframework.boot.ApplicationArguments bean。 ApplicationArguments接口提供对原始String []参数以及解析选项和非选项参数的访问：

```
import org.springframework.boot.*
import org.springframework.beans.factory.annotation.*
import org.springframework.stereotype.*
@Component
public class MyBean {
    @Autowired
    public MyBean(ApplicationArguments args) {
        boolean debug = args.containsOption("debug");
        List<String> files = args.getNonOptionArgs();
        // if run with "--debug logfile.txt" debug=true, files=["logfile.txt"]
    }
}
```

    >Spring Boot还将向Spring Environment 注册一个CommandLinePropertySource。 这允许您也使用@Value注解注入应用程序参数。