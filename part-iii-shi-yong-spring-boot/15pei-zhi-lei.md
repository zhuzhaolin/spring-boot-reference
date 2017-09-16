### 15. 配置类

Spring Boot支持基于Java的配置。虽然可以使用XML配置用SpringApplication.run()，但我们通常建议您的主source是@Configuration类。 通常，定义main方法的类也是作为主要的@Configuration一个很好的选择。

    >许多使用XML配置的Spring示例已经在网上发布。 如果可能的话我们建议始终尝试使用等效的基于Java的配置。 搜索 enable* 注解可以是一个很好的起点。