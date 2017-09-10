### 24.7.5 @ConfigurationProperties 对比 @Value

@Value是核心容器功能，它不提供与类型安全配置属性相同的功能。 下表总结了@ConfigurationProperties和@Value支持的功能：

| 功能 | @ConfigurationProperties | 	@Value |
| :---: | :---: | :---: |
| Relaxed binding | Yes | No |
| Meta-data support | Yes | No |
| SpEL evaluation | No | Yes |

如果您为自己的组件定义了一组配置密钥，我们建议您将其分组到使用@ConfigurationProperties注释的POJO中。 还请注意，由于@Value不支持宽松的绑定，如果您需要使用环境变量提供值，那么它不是一个很好的选择。

最后，当您可以在@Value中编写一个Spel表达式时，这些表达式不会从[应用程序属性文件](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#boot-features-external-config-application-property-files)中处理。


