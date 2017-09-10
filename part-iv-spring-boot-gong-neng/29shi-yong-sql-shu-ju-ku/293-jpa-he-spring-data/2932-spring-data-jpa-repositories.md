### 29.3.2 Spring Data JPA Repositories

Spring Data JPA库是可以定义用于访问数据的接口。 JPA查询是从您的方法名称自动创建的。 例如，CityRepository接口可以声明findAllByState(String state)方法来查找给定状态下的所有城市。

对于更复杂的查询，您可以使用Spring数据查询注解来注解您的方法。

Spring数据存储库通常从Repository或CrudRepository接口扩展。 如果您正在使用自动配置，将从包含主配置类（通过@EnableAutoConfiguration或@SpringBootApplication注解的包）的包中搜索存储库(repositories)。

这是一个典型的Spring数据库：

```
package com.example.myapp.domain;
import org.springframework.data.domain.*;
import org.springframework.data.repository.*;
public interface CityRepository extends Repository<City, Long> {
    Page<City> findAll(Pageable pageable);
    City findByNameAndCountryAllIgnoringCase(String name, String country);
}
```
我们只是触及了Spring Data JPA的表面。 有关完整的详细信息，请查阅其[参考文档](http://projects.spring.io/spring-data-jpa/)。
