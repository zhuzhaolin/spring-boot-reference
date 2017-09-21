### 28.2 User Info中的令牌类型

Google和某些其他第三方身份认证提供商对在header中发送到用户信息端点的令牌类型名称更为严格。 默认值为“Bearer”，适合大多数提供程序并匹配规范，但如果需要更改，可以设置security.oauth2.resource.token-type。