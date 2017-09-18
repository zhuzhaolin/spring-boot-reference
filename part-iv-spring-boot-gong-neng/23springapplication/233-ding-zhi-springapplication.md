### 23.3 定制SpringApplication

如果SpringApplication默认值不符合您的想法，您可以创建本地实例并进行自定义。 例如，关闭banner：
```
public static void main(String[] args) {
    SpringApplication app = new SpringApplication(MySpringConfiguration.class);
    app.setBannerMode(Banner.Mode.OFF);
    app.run(args);
}
```

    >传递给SpringApplication的构造函数参数是spring bean的配置源。 在大多数情况下，这些将引用@Configuration类，但它们也可以引用XML配置或应扫描的包。
    
也可以使用application.properties文件配置SpringApplication。 有关详细信息，请参见[第24章“外部配置”](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#boot-features-external-config)。

有关配置选项的完整列表，请参阅[SpringApplication Javado](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/api/org/springframework/boot/SpringApplication.html)c。    