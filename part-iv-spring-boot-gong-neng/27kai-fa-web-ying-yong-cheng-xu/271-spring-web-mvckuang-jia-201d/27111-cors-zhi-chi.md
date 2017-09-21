### 27.1.11 CORS 支持

[跨原始资源共享](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing/)（CORS）是[大多数浏览器](http://note.youdao.com/)实现的[W3C规范](http://caniuse.com/#feat=cors)，允许您以灵活的方式指定什么样的跨域请求被授权，而不是使用一些不太安全和不太强大的方法，如IFRAME或JSONP。

从版本4.2起，Spring MVC支持CORS开箱即用。 在Spring Boot应用程序中的controller方法使用@CrossOrigin注解的CORS配置不需要任何特定的配置。 可以通过使用自定义的addCorsMappings(CorsRegistry)方法注册WebMvcConfigurer bean来定义全局CORS配置：

```
@Configuration
public class MyConfiguration {
    @Bean
    public WebMvcConfigurer corsConfigurer() {
        return new WebMvcConfigurerAdapter() {
            @Override
            public void addCorsMappings(CorsRegistry registry) {
                registry.addMapping("/api/**");
            }
        };
    }
}
```