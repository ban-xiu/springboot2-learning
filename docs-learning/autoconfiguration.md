# 自动装配

@EnableAutoConfiguration 注解是自动装配的入口，实际上是走了@AutoConfigurationImportSelector 注解的流程

主要流程：
1. 读取了 spring.factories 的 EnableConfiguration 的值，里面包含了需要自动装配的类，启动时实例化为 bean
2. EnableConfiguration 的值通过解析注解映射

