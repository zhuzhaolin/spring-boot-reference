### 29.3.1 实体类

传统上，JPA’Entity’类在persistence.xml文件中指定。 使用Spring Boot此文件不是必需的，而是使用“实体扫描”。 默认情况下，将搜索主配置类下面的所有包（用@EnableAutoConfiguration或@SpringBootApplication注解的类）。

任何用@Entity，@Embeddable或@MappedSuperclass注解的类将被考虑。 典型的实体类将如下所示：

```
package com.example.myapp.domain;
import java.io.Serializable;
import javax.persistence.*;
@Entity
public class City implements Serializable {
    @Id
    @GeneratedValue
    private Long id;
    @Column(nullable = false)
    private String name;
    @Column(nullable = false)
    private String state;
    // ... additional members, often include @OneToMany mappings
    protected City() {
        // no-args constructor required by JPA spec
        // this one is protected since it shouldn't be used directly
    }
    public City(String name, String state) {
        this.name = name;
        this.country = country;
    }
    public String getName() {
        return this.name;
    }
    public String getState() {
        return this.state;
    }
    // ... etc
}
```

    >您可以使用@EntityScan注解自定义实体扫描位置。 请参见第[77.4节“从Spring配置中分离@Entity定义”](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#howto-separate-entity-definitions-from-spring-configuration)操作方法