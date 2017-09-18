### 24.6 使用YAML替代 Properties

[YAML](http://yaml.org/)是JSON的超集，因此这是分层配置数据一种非常方便的格式，。 每当您的类路径中都有SnakeYAML库时，SpringApplication类将自动支持YAML作为 properties 的替代方法。
    >如果您使用“Starters”，SnakeYAML将通过spring-boot-starter自动提供。