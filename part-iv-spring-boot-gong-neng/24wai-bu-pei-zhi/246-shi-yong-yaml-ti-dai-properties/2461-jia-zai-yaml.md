### 24.6.1 加载 YAML

Spring Framework提供了两个方便的类，可用于加载YAML文档。 YamlPropertiesFactoryBean将YAML作为Properties加载，YamlMapFactoryBean将YAML作为Map加载。

例如，下面YAML文档：
```
environments:
    dev:
        url: http://dev.bar.com
        name: Developer Setup
    prod:
        url: http://foo.bar.com
        name: My Cool App
```

将转化为属性：

```
environments.dev.url=http://dev.bar.com
environments.dev.name=Developer Setup
environments.prod.url=http://foo.bar.com
environments.prod.name=My Cool App
```

YAML列表表示为具有[index] dereferencers的属性键，例如YAML：
```
my:
   servers:
       - dev.bar.com
       - foo.bar.com
```
将转化为属性：
```
my.servers[0]=dev.bar.com
my.servers[1]=foo.bar.com
```

要使用Spring DataBinder工具（@ConfigurationProperties做的）绑定到这样的属性，您需要有一个属性类型为java.util.List（或Set）的目标bean，并且您需要提供一个setter，或者 用可变值初始化它，例如 这将绑定到上面的属性
```
@ConfigurationProperties(prefix="my")
public class Config {
    private List<String> servers = new ArrayList<String>();
    public List<String> getServers() {
        return this.servers;
    }
}
```