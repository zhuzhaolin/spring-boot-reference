### 28.3.1 Client

要使您的 web-app 进入OAuth2客户端，您可以简单地添加@ EnableOAuth2Client，Spring Boot将创建一个OAuth2ClientContext和OAuth2ProtectedResourceDetails，这些是创建OAuth2RestOperations所必需的。 Spring Boot不会自动创建这样的bean，但是您可以轻松创建自己的bean：

```
@Bean
public OAuth2RestTemplate oauth2RestTemplate(OAuth2ClientContext oauth2ClientContext,
        OAuth2ProtectedResourceDetails details) {
    return new OAuth2RestTemplate(details, oauth2ClientContext);
}
```

        >您可能需要添加限定符并查看您的配置，因为您的应用程序可能会定义多个RestTemplate。
        
此配置使用security.oauth2.client.*作为凭据（可能与授权服务器中使用的相同），但另外还需要知道授权服务器中的授权和令牌URI。 例如：

application.yml.
```
security:
    oauth2:
        client:
            clientId: bd1c0a783ccdd1c9b9e4
            clientSecret: 1a9030fbca47a5b2c28e92f19050bb77824b5ad1
            accessTokenUri: https://github.com/login/oauth/access_token
            userAuthorizationUri: https://github.com/login/oauth/authorize
            clientAuthenticationScheme: form
```
当您尝试使用OAuth2RestTemplate时，具有此配置的应用程序将重定向到Github进行授权。 如果您已经登录Github，您甚至不会注意到它已经被认证。 如果您的应用程序在端口8080上运行（在Github或其他提供商注册自己的客户端应用程序以获得更大的灵活性），这些特定的凭据才会起作用。

要限制客户端在获取访问令牌时要求的范围，您可以设置security.oauth2.client.scope（逗号分隔或YAML中的数组）。 默认情况下，scope是空的，由授权服务器决定其默认值，通常取决于客户端注册中的设置。
还有一个security.oauth2.client.client-authentication-scheme的设置，默认为“header”（但是如果像Github那样，您可能需要将其设置为“form”，例如，您的OAuth2提供程序不喜欢header 认证）。 事实上，security.oauth2.client.*属性绑定到AuthorizationCodeResourceDetails的一个实例，因此可以指定其所有的属性。

    >还有一个security.oauth2.client.client-authentication-scheme的设置，默认为“header”（但是如果像Github那样，您可能需要将其设置为“form”，例如，您的OAuth2提供程序不喜欢header 认证）。 事实上，security.oauth2.client.*属性绑定到AuthorizationCodeResourceDetails的一个实例，因此可以指定其所有的属性。
    
    >在非Web应用程序中，您仍然可以创建一个OAuth2RestOperations，它仍然连接到security.oauth2.client.*配置中。 在这种情况下，它是一个“客户端凭据令牌授予”，您如果使用它就请求它（并且不需要使用@EnableOAuth2Client或@EnableOAuth2Sso）。为了防止定义基础设施，只需从配置中删除security.oauth2.client.client-id（或使其成为空字符串）。