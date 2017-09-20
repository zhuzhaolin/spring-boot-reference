### 29.3.3 创建和删除JPA数据库

默认情况下，仅当您使用嵌入式数据库（H2，HSQL或Derby）时才会自动创建JPA数据库。 您可以使用spring.jpa。*属性显式配置JPA设置。 例如，要创建和删除表，您可以将以下内容添加到application.properties中。

```
spring.jpa.hibernate.ddl-auto=create-drop
```

Hibernate自己的内部属性名称（如果你记得更好）是hibernate.hbm2ddl.auto。您可以使用spring.jpa.properties *（将其添加到实体管理器时这个前缀会被删除）与其他Hibernate属性一起设置。 例：

```
spring.jpa.properties.hibernate.globally_quoted_identifiers=true
```
将hibernate.globally_quoted_identifiers 传递给Hibernate实体管理器。

默认情况下，DDL执行（或验证）将延迟到ApplicationContext启动。 还有一个spring.jpa.generate-ddl标志，但是如果Hibernate 自动配置是激活的，那么它将不会被使用，因为ddl-auto配置更好。