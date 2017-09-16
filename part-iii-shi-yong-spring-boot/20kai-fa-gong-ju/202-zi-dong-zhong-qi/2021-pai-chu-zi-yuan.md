### 20.2.1 排除资源

在类路径下，某些资源在更改时不一定需要触发重新启动。 例如，Thymeleaf模板可以直接编辑不需重启。
默认情况下，有一些排除项，更改 /META-INF/maven，/META-INF/resources，/resources，/static，/public或/templates中的资源不会触发重新启动，但会[触发实时重新加载](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#using-boot-devtools-livereload)。
如果要自定义这些排除项，可以使用spring.devtools.restart.exclude属性。 例如，要仅排除 /static和 /public，您可以设置：

```
spring.devtools.restart.exclude=static/**,public/**
```
    >如果要保留这些默认值并添加其他排除项，请改用spring.devtools.restart.additional-exclude属性。