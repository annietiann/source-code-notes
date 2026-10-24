- Java source-code reading notes based on JDK 8/16, Spring 5, Spring Boot 2, RocketMQ 4.x and Redis.
- Each topic is documented as call chains traced from the entry method (exhaustive branches), overall flow summaries (text or diagrams), class hierarchy charts, and cross-comparison tables.
- 38 notes plus 11 execution-flow diagrams in total.
- Maintained by a senior backend developer (IBM / Ping An Puhui, microservices & messaging).

**Java 源码学习笔记（基于JDK 8/16、Spring 5、Spring Boot 2、RocketMQ 4.x、Redis 源码）**

笔记类型：

- 调用链（入口方法出发，穷尽分支）
- 整体流程（文字概括 or 流程图）
- 类继承图
- 横向对比表

共 38 篇笔记 + 11 张流程图

**0. JVM**
- [Hotspot启动流程Jdk16](0.%20jvm/1.%20Hotspot_Launch_Process_JDK16.pdf) jvm的初始化,main方法的执行,类加载过程
- [Hotspot启动流程Jdk8](0.%20jvm/2.%20Hotspot_Launch_Process_JDK8.pdf)
- [Heap初始化Jdk8](0.%20jvm/3.%20Heap_Init_JDK8.pdf) 新生代/老年代的初始化,GC线程的创建,并发标记过程,Major GC和Full GC
- [Heap分配内存与GC](0.%20jvm/4.%20Heap分配内存与GC_JDK8.pdf)
- [CMS GC流程Jdk8](0.%20jvm/7.%20GC_CMS_JDK8.svg)
- [G1 GC流程Jdk8](0.%20jvm/7.%20GC_G1_JDK8.svg)
- [CMS vs G1](0.%20jvm/5.%20CMS_vs_G1.pdf)
- [类加载](0.%20jvm/6.%20Class_Loading.pdf) 从.class文件到InstanceKlass实例

**1. 并发编程**
- [Synchronized的一切](1.%20concurrency/1.%20Synchronized.pdf) 锁膨胀过程
- [volatile与内存屏障](1.%20concurrency/1.%20volatile_jdk8.pdf)
- [ThreadPoolExecutor](1.%20concurrency/2.%20executors_1_ThreadPoolExecutor.pdf) thread worker的一生
- [ScheduledThreadPoolExecutor](1.%20concurrency/2.%20executors_2_ScheduledThreadPoolExecutor.pdf) 周期任务的实现
- [FutureTask](1.%20concurrency/2.%20executors_3_FutureTask.pdf)
- [CompletableFuture](1.%20concurrency/2.%20executors_4_CompletableFuture.pdf)
- [ForkJoinPool](1.%20concurrency/2.%20executors_5_ForkJoinPool.pdf) 分治算法&工作窃取算法
- [AQS](1.%20concurrency/3.%20locks_1_AQS.pdf) 模版方法模式的典型示例
- [ReentrantLock](1.%20concurrency/3.%20locks_2_ReentrantLock.pdf)
- [ReentrantReadWriteLock](1.%20concurrency/3.%20locks_3_ReentrantReadWriteLock.pdf)
- [ConcurrentHashMap](1.%20concurrency/4.%20collections_ConcurrentHashMap.pdf) 数据结构,bucket坐标规律,扩容过程
- [HashMap](1.%20concurrency/4.%20collections_HashMap.pdf) hashCode的计算,扩容过程
- [并发容器全景对比表](1.%20concurrency/4.%20collections_summary.pdf) 各种Queues和Maps
- [五大同步器速查表](1.%20concurrency/5.%20synchronizers.pdf) 使用场景及用法
- [ThreadLocal](1.%20concurrency/6.%20ThreadLocal.pdf)
- [ReentrantLock流程图](1.%20concurrency/7.%20ReentrantLock_流程图.svg)
- [读写锁流程图](1.%20concurrency/7.%20ReentrantReadWriteLock_流程图.svg)
- [ScheduledThreadPoolExecutor](1.%20concurrency/7.%20ScheduledThreadPoolExecutor_流程图.svg) thread worker和DelayedWorkQueue的工作流程
- [Synchronized锁膨胀流程图](1.%20concurrency/7.%20Synchronized_流程图.svg)
- [九种并发队列对比图](1.%20concurrency/7.%20collections_queues_流程图.svg) 入队出队

**3. JDK 类库**
- [压缩流装饰器链路](3.%20jdk/compress.svg)
- [函数式编程](3.%20jdk/jdk8_features_functional_programming.pdf) lambda实现原理
- [Stream 实战笔记](3.%20jdk/jdk8_features_streams.pdf) 流水线的装配和启动
- [Stream 执行模型](3.%20jdk/stream.svg) 并行vs串行

**4. Spring 全家桶**
- [IoC](4.%20spring/1.%20IoC.pdf) IoC详细过程,依赖注入方式,循环依赖解决方案
- [AOP](4.%20spring/2.%20AOP.pdf) XMLvs注解式, 切面类的加载,proxy的创建,拦截器执行顺序
- [MVC](4.%20spring/3.%20MVC.pdf) HTTP请求处理流程,视图的解析和渲染
- [RESTful × MyBatis](4.%20spring/4.%20RESTful_MyBatis.pdf) 请求解析,返回内容的协商
- [MultipartResolver 文件上传](4.%20spring/5.%20MultipartResolver.pdf)
- [全局异常处理](4.%20spring/6.%20GlobalExceptionHandler.pdf)
- [Spring Boot 启动流程](4.%20spring/7.%20spring_boot_1_startup.pdf) 自动装配底层实现,内嵌服务器的创建启动
- [Spring Boot 属性绑定](4.%20spring/7.%20spring_boot_2_propertiesBinding.pdf)
- [Spring Boot 事务](4.%20spring/7.%20spring_boot_3_transaction.pdf)
- [Spring Boot 定时任务](4.%20spring/7.%20spring_boot_4_job.pdf)
- [Spring Cloud 微服务](4.%20spring/7.%20spring_cloud_%E5%BE%AE%E6%9C%8D%E5%8A%A1.pdf) 服务治理,负载均衡,跨服务通信,熔断限流,分布式事务
- [Spring MVC × Tomcat 启动部署总结](4.%20spring/8.%20spring_startup_summary.pdf)

**5. 消息中间件**
- [SpringBoot × RocketMQ](5.%20middleware/RocketMQ.pdf) 启动,负载均衡,异步拉取,消费,同步重试,底层通信
- [RocketMQ 消费端流程](5.%20middleware/RocketMQ.svg)

**6. Redis**
- [Redis 分布式锁实战](6.%20redis/使用场景.pdf)
- [Redis 高可用全家桶](6.%20redis/复制_哨兵_集群_内存优化_事务_缓存.pdf)

**7. 操作系统与 I/O**
- [零拷贝四种方案](7.%20os/zero_copy_流程图.svg)

**书单（源码研读时的参照）**

Java Concurrency in Practice · Effective Java · 深入理解Java虚拟机 · G1GC 算法与实现 · Concurrency in Java (Brian Goetz) · Modern Java in Action · Programming Concurrency on the JVM · Java并发编程之美 · Design Patterns (GoF) · Head First Design Patterns

---

*作者：Annie Tian —— 7年+后端开发（IBM / 平安普惠），微服务与消息系统方向。笔记均产自源码研读过程，欢迎拍砖。*
