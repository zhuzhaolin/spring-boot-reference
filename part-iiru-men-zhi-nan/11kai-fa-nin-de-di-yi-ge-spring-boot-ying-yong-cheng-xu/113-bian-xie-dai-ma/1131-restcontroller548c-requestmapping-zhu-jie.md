### 11.3.1 @RestController和@RequestMapping 注解

我们的Example类的第一个注解是@RestController。 这被称为 stereotype annotation。它为人们阅读代码提供了一些提示，对于Spring来说，这个类具有特定的作用。在这里，我们的类是一个web @Controller，所以Spring在处理传入的Web请求时会考虑这个类。

@RequestMapping注解提供“路由”信息。 告诉Spring，任何具有路径“/”的HTTP请求都应映射到home方法。 @RestController注解告诉Spring将生成的字符串直接返回给调用者。
>@RestController和@RequestMapping注解是Spring MVC 的注解（它们不是Spring Boot特有的）。 有关更多详细信息，请参阅Spring参考文档中的[MVC](http://docs.spring.io/spring/docs/4.3.7.RELEASE/spring-framework-reference/htmlsingle#mvc)部分。