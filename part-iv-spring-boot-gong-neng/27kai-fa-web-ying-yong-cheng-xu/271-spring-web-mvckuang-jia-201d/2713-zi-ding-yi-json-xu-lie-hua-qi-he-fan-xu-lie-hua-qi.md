### 27.1.3 自定义JSON序列化器和反序列化器

如果您使用Jackson序列化和反序列化JSON数据，则可能需要编写自己的JsonSerializer和JsonDeserializer类。 自定义序列化程序通常[通过一个模块注册到Jackson](http://wiki.fasterxml.com/JacksonHowToCustomDeserializers)，但是Spring Boot提供了一个备用的@JsonComponent注释，可以更容易地直接注册Spring Bean。

您可以直接在JsonSerializer或JsonDeserializer实现中使用@JsonComponent。 您也可以将它用于包含序列化器/解串器的类作为内部类。 例如：

```
import java.io.*;
import com.fasterxml.jackson.core.*;
import com.fasterxml.jackson.databind.*;
import org.springframework.boot.jackson.*;
@JsonComponent
public class Example {
    public static class Serializer extends JsonSerializer<SomeObject> {
        // ...
    }
    public static class Deserializer extends JsonDeserializer<SomeObject> {
        // ...
    }
}
```

```
ApplicationContext中的所有@JsonComponent bean将自动注册到Jackson，并且由于@JsonComponent是使用@Component进行元注解的，所以常规的组件扫描规则适用。

Spring Boot还提供了[JsonObjectSerializer](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot/src/main/java/org/springframework/boot/jackson/JsonObjectSerializer.java)和[JsonObjectDeserializer](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot/src/main/java/org/springframework/boot/jackson/JsonObjectDeserializer.java)基类，它们在序列化对象时为标准的Jackson版本提供了有用的替代方法。 有关详细信息，请参阅Javadoc。