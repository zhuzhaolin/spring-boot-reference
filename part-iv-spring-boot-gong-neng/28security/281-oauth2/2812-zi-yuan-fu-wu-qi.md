### 28.1.2 资源服务器

要使用访问令牌(token)，您需要一个资源服务器（可以与授权服务器相同）。 创建资源服务器很简单，只需添加@EnableResourceServer并提供一些配置，以允许服务器解码访问令牌。 如果您的应用程序也是授权服务器，则它已经知道如何解码令牌，无需做其他事情。 如果你的应用程序是一个独立的服务，那么你需要给它一些更多的配置，以下选项之一：

+ security.oauth2.resource.user-info-uri使用/me资源（例如PWS上的https://uaa.run.pivotal.io/userinfo）
+ security.oauth2.resource.token-info-uri使用令牌解码端点（例如，PWS上的https://uaa.run.pivotal.io/check_token）。

如果您同时指定user-info-uri和token-info-uri，那么您可以设置一个标志，表示优先于另一个（prefer-token-inf=true是默认值）。


或者（不是user-info-uri或token-info-uri的情况）如果令牌是JWT，您可以配置security.oauth2.resource.jwt.key-value来本地解码（key是验证密钥verification key）。 验证密钥值是对称秘密或PEM编码的RSA公钥。 如果您没有密钥，并且它是公开的，您可以提供一个可以使用security.oauth2.resource.jwt.key-uri下载的URI（具有“value”字段的JSON对象）。 例如在PWS上：

```
$ curl https://uaa.run.pivotal.io/token_key
{"alg":"SHA256withRSA","value":"-----BEGIN PUBLIC KEY-----\nMIIBI...\n-----END PUBLIC KEY-----\n"}
```
如果您使用security.oauth2.resource.jwt.key-uri，则应用程序启动时需要运行授权服务器。 如果找不到密钥，它将记录一个警告，并告诉您如何解决该问题。
    >如果您使用                               security.oauth2.resource.jwt.key-uri，则应用程序启动时需要运行授权服务器。 如果找不到密钥，它将会在日志记录一个警告，并告诉您如何解决该问题。
    
OAuth2资源由order security.oauth2.resource.filter-order的过滤器链保护，默认情况下保护执行器(actuator)端点的过滤器（所以执行器(actuator)端点将保留在HTTP Basic上，除非更改顺序）。