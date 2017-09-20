### 29.2 使用JdbcTemplate

Spring的JdbcTemplate和NamedParameterJdbcTemplate类是自动配置的，您可以将它们直接连接到您自己的bean中：

```
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.stereotype.Component;
@Component
public class MyBean {
    private final JdbcTemplate jdbcTemplate;
    @Autowired
    public MyBean(JdbcTemplate jdbcTemplate) {
        this.jdbcTemplate = jdbcTemplate;
    }
    // ...
}
```