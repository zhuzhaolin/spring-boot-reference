### 26.6.2 环境属性

标签允许您从Spring环境中显示属性，以便在Logback中使用。 如果您在logback中访问application.properties文件中的值，这将非常有用。 标签的工作方式与Logback标准的标签类似，但不是指定直接值，而是指定属性的来源（来自Environment）。 如果需要将属性存储在本地范围以外的位置，则可以使用scope属性。 如果在环境中未设置属性的情况下需要备用值，则可以使用defaultValue属性。

```
<springProperty scope="context" name="fluentHost" source="myapp.fluentd.host"
        defaultValue="localhost"/>
<appender name="FLUENT" class="ch.qos.logback.more.appenders.DataFluentAppender">
    <remoteHost>${fluentHost}</remoteHost>
    ...
</appender>
```

RelaxedPropertyResolver用于访问Environment属性。 如果以虚线表示法（my-property-name）指定源，则将尝试所有宽松的变体（myPropertyName，MY_PROPERTY_NAME等）。