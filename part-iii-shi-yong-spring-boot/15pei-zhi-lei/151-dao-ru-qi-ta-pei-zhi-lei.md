### 15.1 导入其他配置类

您不需要将所有的@Configuration放在一个类中。 @Import注解可用于导入其他配置类。 或者，您可以使用@ComponentScan自动扫描所有Spring组件，包括@Configuration类。