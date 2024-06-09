# run

SpringApplication.run() 是 SpringBoot 启动的入口

new SpringApplication 的主要流程：
1. 添加源，将配置类添加到源列表
2. 设置 web 环境
3. 设置初始化器，从 spring.factories 中加载
4. 设置监听器，从 spring.factories 中加载
5. 确定应用主类，是 SpringBoot 的入口点

其中设置初始化器是 SpringBoot 实现自动装配的核心，这一步会从 spring.factories 中加载并实例化指定的类

具体流程在 getSpringFactoriesInstances() 方法中：
1. 读取 spring.factories
2. 通过反射创建 SpringFactory 实例
3. 排序并返回

run() 方法的主要流程：
1. 获取监听器并启动
2. 装配环境参数
3. 创建应用上下文
4. 准备上下文，装配 bean
5. 上下文刷新
6. 上下文刷新的后置处理
7. 触发监听器事件
8. 返回上下文