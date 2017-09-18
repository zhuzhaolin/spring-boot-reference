24.7.2 宽松的绑定

Spring Boot使用一些宽松的规则将环境属性绑定到@ConfigurationProperties bean，因此不需要在Environment属性名称和bean属性名称之间进行完全匹配。 常用的例子是这样有用的：虚分离（例如上下文路径绑定到contextPath）和大写（例如PORT绑定到端口）环境属性。

例如，给定以下@ConfigurationProperties类：

```
@ConfigurationProperties(prefix="person")
public class OwnerProperties {
    private String firstName;
    public String getFirstName() {
        return this.firstName;
    }
    public void setFirstName(String firstName) {
        this.firstName = firstName;
    }
}
```

可以使用以下属性名称：

**表格 24.1. relaxed binding**

| Property | Note |
| :--- | :--- |
| person.firstName | 标准骆峰命名法。 |
| person.first-name | 虚线符号，推荐用于.properties和.yml文件。 |
| person.first_name |  	下划线符号，用于.properties和.yml文件的替代格式。
 |
| PERSON_FIRST_NAME | 	大写格式 推荐使用系统环境变量时。 |



