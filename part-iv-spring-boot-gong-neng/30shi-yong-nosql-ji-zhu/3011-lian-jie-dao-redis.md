### 30.1.1 连接到Redis

您可以像任何其他Spring Bean一样注入自动配置的RedisConnectionFactory，StringRedisTemplate或vanilla RedisTemplate实例。 默认情况下，实例将尝试使用localhost:6379连接到Redis服务器：
```
@Component
public class MyBean {
    private StringRedisTemplate template;
    @Autowired
    public MyBean(StringRedisTemplate template) {
        this.template = template;
    }
    // ...
}
```
如果您添加了您自己的任何自动配置类型的@Bean，它将替换默认值（除了在RedisTemplate的情况下，排除是基于bean名称“redisTemplate”而不是其类型）。 如果commons-pool2在类路径上，则默认情况下将获得一个pooled连接工厂。