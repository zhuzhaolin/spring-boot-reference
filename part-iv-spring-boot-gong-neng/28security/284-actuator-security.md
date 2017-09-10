### 28.4 Actuator Security

如果Actuator也在使用中，您会发现：

    + 即使应用程序端点不安全，管理端点也是安全的。
    + Security 事件将转换为AuditEvent实例，并发布到AuditEventRepository。
    + 默认用户将具有ACTUATOR角色以及USER角色。
Actuator的安全功能可以使用外部属性（management.security.*）进行修改。要覆盖应用程序访问规则，请添加一个类型为WebSecurityConfigurerAdapter的@Bean，如果您不想覆盖执行程序访问规则，则使用@Order（SecurityProperties.ACCESS_OVERRIDE_ORDER）或@Order（ManagementServerProperties.ACCESS_OVERRIDE_ORDER）覆盖执行器访问规则。