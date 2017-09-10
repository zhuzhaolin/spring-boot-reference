### 28. Security

如果Spring Security位于类路径上，则默认情况下，Web应用程序将在所有HTTP端点上使用“basic”身份验证。 要向Web应用程序添加方法级安全性，您还可以使用所需的设置添加@EnableGlobalMethodSecurity。 有关更多信息，请参见“[Spring Security Reference](http://docs.spring.io/spring-security/site/docs/4.2.2.RELEASE/reference/htmlsingle#jc-method)”。

默认的AuthenticationManager有一个用户（用户名’user’和随机密码，在应用程序启动时以INFO级别打印）
```
Using default security password: 78fa095d-3f4c-48b1-ad50-e24c31d5cf35

```

    >如果您调整日志记录配置，请确保将org.springframework.boot.autoconfigure.security类别设置为记录INFO消息，否则将不会打印默认密码。

您可以通过提供security.user.password来更改密码。 这个和其他有用的属性通过 [SecurityProperties](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-autoconfigure/src/main/java/org/springframework/boot/autoconfigure/security/SecurityProperties.java)（属性前缀“security”）进行外部化。

默认的安全配置在SecurityAutoConfiguration和从那里导入的类中实现（用于Web安全的SpringBootWebSecurityConfiguration和用于认证配置的AuthenticationManagerConfiguration，这在非Web应用程序中也是相关的）。 要完全关闭默认的Web应用程序安全配置，您可以使用@EnableWebSecurity添加一个bean（这不会禁用身份验证管理器配置或Actuator的安全性）。 要定制它，您通常使用WebSecurityConfigurerAdapter类型的外部属性和bean（例如添加基于表单的登录）。 要关闭身份验证管理器配置，您可以添加AuthenticationManager类型的bean，或者通过将AuthenticationManagerBuilder自动连接到您的一个@Configuration类中的方法来配置全局AuthenticationManager。 Spring Boot示例中有几个安全应用程序可以让您开始使用常见的[用例](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-samples/)。

您在Web应用程序中获得的基本功能包括：

    + 具有内存存储和单个用户的AuthenticationManager Bean（请参阅用于用户属性的SecurityProperties.User）。
    + 对于常见的静态资源位置，忽略（不安全）路径(/css/**, /js/**, /images/**, /webjars/** and **/favicon.ico)。
HTTP所有其他端点的baseic security 。
    + 安全事件发布到Spring的ApplicationEventPublisher（成功、不成功的身份验证、拒绝访问）。
    + 默认情况下，Spring Security提供的常见的底层功能（HSTS，XSS，CSRF，缓存）都是打开的。
    
所有上述可以使用外部属性（security.*）打开、关闭或修改。 要覆盖访问规则而不更改任何其他自动配置的功能，请添加一个带有@Order(SecurityProperties.ACCESS_OVERRIDE_ORDER)的WebSecurityConfigurerAdapter类型的Bean，并配置它以满足您的需要。

    >默认情况下，WebSecurityConfigurerAdapter将匹配任何路径。 如果您不想完全覆盖Spring Boot自动配置的访问规则，您的适配器必须显式配置您要覆盖的路径。