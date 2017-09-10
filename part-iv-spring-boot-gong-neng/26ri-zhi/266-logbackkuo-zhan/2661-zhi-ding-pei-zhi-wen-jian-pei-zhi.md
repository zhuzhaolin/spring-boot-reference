### 26.6.1 指定配置文件配置

<springProfile>标签允许您根据活动的Spring配置文件可选地包含或排除配置部分。 配置文件部分支持<configuration>元素在任何位置。 使用name属性指定哪个配置文件接受配置。 可以使用逗号分隔列表指定多个配置文件。
```
<springProfile name="staging">
    <!-- configuration to be enabled when the "staging" profile is active -->
</springProfile>
<springProfile name="dev, staging">
    <!-- configuration to be enabled when the "dev" or "staging" profiles are active -->
</springProfile>
<springProfile name="!production">
    <!-- configuration to be enabled when the "production" profile is not active -->
</springProfile>
```