### 27.1.4 MessageCodesResolver

Spring MVC有一个生成错误代码的策略，用于从绑定错误中提取错误消息：MessageCodesResolver。 Spring Boot将为您创建一个错误代码，如果您设置spring.mvc.message-codes-resolver.format属性PREFIX_ERROR_CODE或POSTFIX_ERROR_CODE（请参阅DefaultMessageCodesResolver.Format中的枚举）。