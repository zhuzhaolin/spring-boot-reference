### 24.5 properties 文件中的占位符

application.properties中的值在使用时通过已有的环境进行过滤，以便您可以引用之前定义的值（例如，从系统属性）。

```
app.name=MyApp
app.description=${app.name} is a Spring Boot application
```
    >您也可以使用此技术创建现有Spring Boot属性的“简写“。 有关详细信息，请参见[第72.4节“使用”短命令行参数“how-to”](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#howto-use-short-command-line-arguments)。