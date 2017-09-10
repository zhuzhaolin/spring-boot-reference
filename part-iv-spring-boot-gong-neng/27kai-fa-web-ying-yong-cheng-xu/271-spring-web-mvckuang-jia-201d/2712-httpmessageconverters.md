### 27.1.2 HttpMessageConverters

Spring MVC使用HttpMessageConverter接口转换HTTP请求和响应。 包括一些开箱即用的合理配置，例如对象可以自动转换为JSON（使用Jackson库）或XML（使用Jackson XML扩展，如果可用，否则使用JAXB）。 字符串默认使用UTF-8进行编码。

如果需要添加或自定义转换器，可以使用Spring Boot HttpMessageConverter类：
```
import org.springframework.boot.autoconfigure.web.HttpMessageConverters;
import org.springframework.context.annotation.*;
import org.springframework.http.converter.*;
@Configuration
public class MyConfiguration {
    @Bean
    public HttpMessageConverters customConverters() {
        HttpMessageConverter<?> additional = ...
        HttpMessageConverter<?> another = ...
        return new HttpMessageConverters(additional, another);
    }
}
```

上下文中存在的任何HttpMessageConverter bean将被添加到转换器列表中。 您也可以以这种方式覆盖默认转换器。