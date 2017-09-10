### 25.2 以编程方式设置配置文件

您可以通过在应用程序运行之前调用SpringApplication.setAdditionalProfiles(…)以编程方式设置激活配置文件。 也可以使用Spring的ConfigurableEnvironment接口激活配置文件。