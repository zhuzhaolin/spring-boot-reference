### 14.2 查找主应用程序类

我们通常建议您将应用程序主类放到其他类之上的根包(root package)中。 @EnableAutoConfiguration注解通常放置在您的主类上，它隐式定义了某些项目的基本“搜索包”。 例如，如果您正在编写JPA应用程序，则@EnableAutoConfiguration注解类的包将用于搜索@Entity项。

使用根包(root package)还可以使用@ComponentScan注释，而不需要指定basePackage属性。 如果您的主类在根包中，也可以使用@SpringBootApplication注释。

这是一个典型的布局：
```
com
 +- example
     +- myproject
         +- Application.java
         |
         +- domain
         |   +- Customer.java
         |   +- CustomerRepository.java
         |
         +- service
         |   +- CustomerService.java
         |
         +- web
             +- CustomerController.java
```

Application.java文件将声明main方法以及基本的@Configuration。
```
package com.example.myproject;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.EnableAutoConfiguration;
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
@Configuration
@EnableAutoConfiguration
@ComponentScan
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```

