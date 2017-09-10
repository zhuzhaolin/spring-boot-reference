### 29.5.3 定制jOOQ

您可以通过在application.properties中设置spring.jooq.sql-dialect来自定义jOOQ使用的SQL方言。 例如，要指定Postgres，您可以添加：

```
spring.jooq.sql-dialect=Postgres
```

通过定义自己的@Bean定义可以实现更高级的定制，这些定义将在创建jOOQ配置时使用。您可以为以下jOOQ类型定义bean：

    + ConnectionProvider
    + TransactionProvider
    + RecordMapperProvider
    + RecordListenerProvider
    + ExecuteListenerProvider
    + VisitListenerProvider
    
如果要完全控制jOOQ配置，您还可以创建自己的org.jooq.Configuration @Bean。