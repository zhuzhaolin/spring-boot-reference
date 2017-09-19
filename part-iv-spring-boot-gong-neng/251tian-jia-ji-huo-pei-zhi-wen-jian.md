### 25.1添加激活配置文件

spring.profiles.active属性遵循与其他属性相同的优先级规则，PropertySource最高。这意味着您可以在application.properties中指定活动配置文件，然后使用命令行开关替换它们。

有时，将特定于配置文件的属性添加到激活的配置文件而不是替换它们是有用的。 spring.profiles.include属性可用于无条件添加激活配置文件。 SpringApplication入口点还具有用于设置其他配置文件的Java API（即，在由spring.profiles.active属性激活的那些配置文件之上）：请参阅setAdditionalProfiles()方法。

例如，当使用开关 -spring.profiles.active=prod 运行具有以下属性的应用程序时，proddb和prodmq配置文件也将被激活：

```
---
my.property: fromyamlfile
---
spring.profiles: prod
spring.profiles.include:
  - proddb
  - prodmq
```
请记住，可以在YAML文档中定义spring.profiles属性，以确定此特定文档何时包含在配置中。 有关详细信息，请参见第72.7节“根据环境更改配置”。[](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#howto-change-configuration-depending-on-the-environment)