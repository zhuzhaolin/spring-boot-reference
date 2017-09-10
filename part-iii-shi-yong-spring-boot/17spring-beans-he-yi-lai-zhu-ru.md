### 17. Spring Beans 和 依赖注入

您可以自由使用任何标准的Spring Framework技术来定义您的bean及其依赖注入关系。 为了简单起见，我们发现使用@ComponentScan搜索bean，结合@Autowired构造函数(constructor)注入效果很好。

如果您按照上述建议（将应用程序类放在根包(root package)中）构建代码，则可以使用
@ComponentScan而不使用任何参数。 所有应用程序组件（@Component，@Service，@Repository，@Controller等）将自动注册为Spring Bean。

以下是一个@Service Bean的例子，我们可以使用构造函数注入获取RiskAssessor bean。

```
package com.example.service;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;
@Service
public class DatabaseAccountService implements AccountService {
    private final RiskAssessor riskAssessor;
    @Autowired
    public DatabaseAccountService(RiskAssessor riskAssessor) {
        this.riskAssessor = riskAssessor;
    }
    // ...
}
```
如果一个bean 只有一个构造函数，则可以省略@Autowired。
```
@Service
public class DatabaseAccountService implements AccountService {
    private final RiskAssessor riskAssessor;
    public DatabaseAccountService(RiskAssessor riskAssessor) {
        this.riskAssessor = riskAssessor;
    }
    // ...
}
```

    >注意，如何使用构造函数注入允许将RiskAssessor字段标记为final，表示不能更改。
