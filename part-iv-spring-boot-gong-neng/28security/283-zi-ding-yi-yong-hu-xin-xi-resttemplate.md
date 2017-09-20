### 28.3 自定义用户信息RestTemplate

如果您有user-info-uri，则资源服务器功能在内部使用OAuth2RestTemplate来获取用户身份验证信息。 这是以UserInfoRestTemplateFactory类型的@Bean提供的。 大多数提供程序的默认值应该是能满足正常使用，但有时您可能需要添加其他拦截器，或者更改请求验证器（例如：令牌如何附加到传出请求）。 进行自定义，只需创建一个类型为UserInfoRestTemplateCustomizer的bean - 它具有一个方法，在bean创建之后但在初始化之前将被调用。 这里定制的rest模板只能在内部进行验证。 或者，您可以定义自己的UserInfoRestTemplateFactory @Bean来完全控制。

要在YAML中设置RSA密钥值，请使用“pipe”继续标记将其分割成多行（“|”），并记住缩进键值（它是标准的 YAML 语言功能）。 例：

```
security:
    oauth2:
        resource:
            jwt:
                keyValue: |
                    -----BEGIN PUBLIC KEY-----
                    MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKC...
                    -----END PUBLIC KEY-----
```