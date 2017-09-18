### 24.6.5 合并YAML列表

[如上所述](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#boot-features-external-config-loading-yaml)，任何YAML内容最终都会转换为属性。 当通过配置文件覆盖“列表”属性时，该过程可能比较直观。

例如，假设名称和描述属性默认为空的MyPojo对象。 让我们从FooProperties中公开MyPojo的列表：
```
@ConfigurationProperties("foo")
public class FooProperties {
    private final List<MyPojo> list = new ArrayList<>();
    public List<MyPojo> getList() {
        return this.list;
    }
}
```
类比以下配置：
```
foo:
  list:
    - name: my name
      description: my description
---
spring:
  profiles: dev
foo:
  list:
    - name: my another name
```

如果dev配置没有激活，FooProperties.list将包含一个如上定义的MyPojo条目。 如果启用了配置文件，列表仍将包含一个条目（名称为“my another name”，description=null）。 此配置不会将第二个MyPojo实例添加到列表中，并且不会将项目合并。

当在多个配置文件中指定集合时，使用具有最高优先级的集合（并且仅使用该配置文件）：
```
foo:
  list:
    - name: my name
      description: my description
    - name: another name
      description: another description
---
spring:
  profiles: dev
foo:
  list:
     - name: my another name
 ```
 
 在上面的示例中，考虑到dev配置文件处于激活状态，FooProperties.list将包含一个MyPojo条目（名称为“my another name”和description=null）。