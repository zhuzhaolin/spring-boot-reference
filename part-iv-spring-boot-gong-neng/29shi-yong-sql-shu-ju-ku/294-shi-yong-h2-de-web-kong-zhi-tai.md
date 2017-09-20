### 29.4 使用H2的Web控制台

[H2数据库](http://www.h2database.com/)提供了一个[基于浏览器的控制台](http://www.h2database.com/html/quickstart.html#h2_console)，Spring Boot可以为您自动配置。 满足以下条件时，控制台将自动配置：

    + 您正在开发一个Web应用程序
    + com.h2database：h2在类路径上
    + 您正在使用[Spring Boot的开发者工具](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#using-boot-devtools)