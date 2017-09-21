### 29.4.2 保护H2控制台

当Spring Security位于类路径上且启用了基本身份验证时，H2控制台将自动使用基本身份验证进行保护。 以下属性可用于自定义安全配置：

    + security.user.role
    + security.basic.authorize-mode
    + security.basic.enabled