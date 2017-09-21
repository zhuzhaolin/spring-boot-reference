### 28.3.2 单点登录

OAuth2客户端可用于从提供商获取用户详细信息（如果此类功能可用），然后将其转换为Spring Security的身份验证令牌。 以上资源服务器通过user-info-uri属性支持此功能这是基于OAuth2的单点登录（SSO）协议的基础，Spring Boot可以通过提供@ EnableOAuth2Sso注解来轻松加入。 上面的Github客户端可以通过添加该注释并声明在何处查找端点（除了上面列出的security.oauth2.client.*配置）外，还可以保护所有资源并使用Github/user/endpoint进行身份验证：

application.yml.
```
security:
    oauth2:
...
    resource:
        userInfoUri: https://api.github.com/user
        preferTokenInfo: false
```

由于默认情况下所有路径都是安全的，所以没有可以向未经身份验证的用户显示“家”页面，并邀请他们登录（通过访问/登录路径或由security.oauth2.sso.login-path指定的路径） 。

由于默认情况下所有路径都是要求安全的，所以没有可以向未经身份验证的用户显示“home”页面，并邀请他们登录（通过访问/login 路径或由security.oauth2.sso.login-path指定的路径） 。

要自定义保护的访问规则或路径，因此您可以添加“home”页面，例如，@EnableOAuth2Sso可以添加到WebSecurityConfigurerAdapter，并且注解将使其被修饰和增强，以使所需的/login路径可以工作。 例如，这里我们简单地允许未经身份验证的访问“/“下的主页面，并保留其他所有内容的默认值：
```
@Configuration
public class WebSecurityConfiguration extends WebSecurityConfigurerAdapter {
    @Override
    public void init(WebSecurity web) {
        web.ignore("/");
    }
    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http.antMatcher("/**").authorizeRequests().anyRequest().authenticated();
    }
}
```