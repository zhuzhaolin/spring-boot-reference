### 16.2 禁用指定的自动配置

如果您发现正在使用一些不需要的自动配置类，可以使用@EnableAutoConfiguration的exclude属性来禁用它们。
```
import org.springframework.boot.autoconfigure.*;
import org.springframework.boot.autoconfigure.jdbc.*;
import org.springframework.context.annotation.*;
@Configuration
@EnableAutoConfiguration(exclude={DataSourceAutoConfiguration.class})
public class MyConfiguration {
}
```
如果类不在classpath路径上，则可以使用注释的excludeName属性，并指定全限定名(fully qualified name)。 最后，您还可以通过spring.autoconfigure.exclude属性控制要排除的自动配置类列表.

    >注解和使用属性(property)定义都可以指定要排除的自动配置类。