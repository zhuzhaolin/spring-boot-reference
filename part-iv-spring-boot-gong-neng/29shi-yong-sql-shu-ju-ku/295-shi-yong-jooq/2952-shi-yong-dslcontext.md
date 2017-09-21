### 29.5.2 使用 DSLContext

jOOQ提供的流畅的API是通过org.jooq.DSLContext接口启动的。 Spring Boot将自动配置DSLContext作为Spring Bean并将其连接到应用程序DataSource。 要使用DSLContext，您只需@Autowire它：
```
@Component
public class JooqExample implements CommandLineRunner {
    private final DSLContext create;
    @Autowired
    public JooqExample(DSLContext dslContext) {
        this.create = dslContext;
    }
}
```

    >jOOQ手册倾向于使用名为create的变量来保存DSLContext，我们在此示例中也是这样。
    
然后，您可以使用DSLContext构建查询：

```
public List<GregorianCalendar> authorsBornAfter1980() {
    return this.create.selectFrom(AUTHOR)
        .where(AUTHOR.DATE_OF_BIRTH.greaterThan(new GregorianCalendar(1980, 0, 1)))
        .fetch(AUTHOR.DATE_OF_BIRTH);
}
```