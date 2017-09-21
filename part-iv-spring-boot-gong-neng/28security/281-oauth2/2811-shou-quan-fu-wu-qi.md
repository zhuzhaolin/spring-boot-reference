### 28.1.1 授权服务器

要创建授权服务器并授予访问令牌，您需要使用@EnableAuthorizationServer并提供security.oauth2.client.client-id和security.oauth2.client.client-secret]属性。 客户端将为您注册在内存中。

```
$ curl client:secret@localhost:8080/oauth/token -d grant_type=password -d username=user -d password=pwd
```

/token 端点的基本身份验证凭证是client-id和client-secret。 用户凭据是普通的Spring Security用户details （在Spring引导中默认为“user”和随机密码）。


要关闭自动配置并自行配置授权服务器功能，只需添加一个类型为AuthorizationServerConfigurer的@Bean。