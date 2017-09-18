### 23.4 流式构建 API

如果您需要构建一个ApplicationContext层次结构（具有父/子关系的多个上下文），或者如果您只想使用“流式（fluent）”构建器API，则可以使用SpringApplicationBuilder。

SpringApplicationBuilder允许您链式调用多个方法，并包括允许您创建层次结构的父和子方法。

例如：
```
new SpringApplicationBuilder()
        .sources(Parent.class)
        .child(Application.class)
        .bannerMode(Banner.Mode.OFF)
        .run(args);
```

        >创建ApplicationContext层次结构时有一些限制，例如 Web组件必须包含在子上下文中，并且相同的环境将用于父和子上下文。 有关详细信息，请参阅[SpringApplicationBuilder Javadoc](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/api/org/springframework/boot/builder/SpringApplicationBuilder.html)。