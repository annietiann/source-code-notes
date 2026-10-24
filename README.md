• Java source-code reading notes based on JDK 8/16, Spring 5, Spring Boot 2, RocketMQ 4.x and Redis.  
• Each topic is documented as call chains traced from the entry method (exhaustive branches), overall flow summaries (text or diagrams), class hierarchy charts, and cross-comparison tables.  
• 38 notes plus 11 execution-flow diagrams in total.  
• Maintained by a senior backend developer (IBM / Ping An Puhui, microservices & messaging).

**Java 源码学习笔记（基于JDK 8/16、Spring 5、Spring Boot 2、RocketMQ 4.x、Redis 源码）**

笔记类型：

- 调用链（入口方法出发，穷尽分支）
- 整体流程（文字概括 or 流程图）
- 类继承图
- 横向对比表

共 38 篇笔记 + 11 张流程图

**0. JVM**
- [Hotspot 启动流程（JDK16）](0.%20jvm/1.%20Hotspot_Launch_Process_JDK16.pdf) —— main.c → JLI_Launch → JVMInit → 新线程继续执行主干链
- [Hotspot 启动流程（JDK8）](0.%20jvm/2.%20Hotspot_Launch_Process_JDK8.pdf) —— 与 JDK16 版对照阅读，**双版本文件路径与结构差异**
- [Heap 初始化（JDK8）](0.%20jvm/3.%20Heap_Init_JDK8.pdf) —— 启动主干到 universe 初始化、两代堆空间成型
- [对象分配与 GC 触发策略](0.%20jvm/4.%20GC_JDK8.pdf) —— CollectedHeap::obj_allocate → GenCollectorPolicy::mem_allocate_work 分配重试链
- [CMS vs G1 vs ZGC 对比表](0.%20jvm/5.%20CMS_vs_G1.pdf) —— 原理/优点/缺点/适用场景逐项对照
- [类加载触发点](0.%20jvm/6.%20Class_Loading.pdf) —— 解释器执行 _invokestatic/_new 等指令时经 ConstantPool::klass_at 解析符号
- [CMS GC 全流程（JDK8）](0.%20jvm/7.%20GC_CMS_JDK8.svg)
- [G1 GC 全流程（JDK8）](0.%20jvm/7.%20GC_G1_JDK8.svg)

**1. 并发编程**
- [monitorenter 字节码视角](1.%20concurrency/1.%20basics_Synchronized.pdf) —— 解释器 switch(opcode) 里的锁
- [volatile 与内存屏障](1.%20concurrency/1.%20basics_volatile_jdk8.pdf) —— 解释器 switch(opcode) 里的屏障
- [ThreadPoolExecutor](1.%20concurrency/2.%20executors_1_ThreadPoolExecutor.pdf) —— 含 Executors 三大工厂池容量陷阱
- [ScheduledThreadPoolExecutor](1.%20concurrency/2.%20executors_2_ScheduledThreadPoolExecutor.pdf)
- [FutureTask](1.%20concurrency/2.%20executors_3_FutureTask.pdf)
- [CompletableFuture](1.%20concurrency/2.%20executors_4_CompletableFuture.pdf)
- [ForkJoinPool](1.%20concurrency/2.%20executors_5_ForkJoinPool.pdf) —— work-stealing 与并行度选择
- [AQS 总纲](1.%20concurrency/3.%20locks_1_AQS.pdf) —— ReentrantLock/CountDownLatch/Semaphore 共用骨架：acquire → addWaiter → acquireQueued → park
- [ReentrantLock](1.%20concurrency/3.%20locks_2_ReentrantLock.pdf)
- [ReentrantReadWriteLock](1.%20concurrency/3.%20locks_3_ReentrantReadWriteLock.pdf) —— state 高低 16 位拆分与写降级
- [ConcurrentHashMap](1.%20concurrency/4.%20collections_ConcurrentHashMap.pdf) —— 锁桶粒度与 size 的 CounterCell
- [HashMap](1.%20concurrency/4.%20collections_HashMap.pdf)
- [并发容器全景对比表](1.%20concurrency/4.%20collections_summary.pdf) —— 阻塞/非阻塞 × 数据结构 × 同步方式 × 使用场景
- [五大同步器速查表](1.%20concurrency/5.%20synchronizers.pdf) —— Semaphore/CountDownLatch/CyclicBarrier/Phaser/Exchanger 作用与选型
- [ThreadLocal](1.%20concurrency/6.%20ThreadLocal.pdf) —— ThreadLocalMap 开放寻址、过期项探测与内存泄漏链
- [ReentrantLock 流程图](1.%20concurrency/7.%20ReentrantLock_流程图.svg)
- [读写锁流程图](1.%20concurrency/7.%20ReentrantReadWriteLock_流程图.svg)
- [Synchronized 锁升级流程图](1.%20concurrency/7.%20Synchronized_流程图.svg)
- [线程池执行流程图](1.%20concurrency/7.%20ThreadPool_流程图.svg)
- [九种并发队列对比图](1.%20concurrency/7.%20collections_queues_流程图.svg)

**3. JDK 类库**
- [压缩流装饰器链路](3.%20jdk/compress.svg) —— Java IO 流体系（java.io / java.util.zip）
- [函数式编程](3.%20jdk/jdk8_features_functional_programming.pdf)
- [Stream 实战笔记](3.%20jdk/jdk8_features_streams.pdf)
- [Stream 执行模型](3.%20jdk/stream.svg) —— sink 链与并行拆分

**4. Spring 全家桶**
- [IoC 容器](4.%20spring/1.%20IoC.pdf)
- [AOP 代理创建](4.%20spring/2.%20AOP.pdf) —— doCreateBean → 代理链
- [MVC 容器初始化](4.%20spring/3.%20MVC.pdf)
- [RESTful × MyBatis 全链路](4.%20spring/4.%20RESTful_MyBatis.pdf)
- [MultipartResolver 文件上传](4.%20spring/5.%20MultipartResolver.pdf)
- [全局异常处理](4.%20spring/6.%20GlobalExceptionHandler.pdf)
- [Spring Boot 启动流程](4.%20spring/7.%20spring_boot_1_startup.pdf)
- [Spring Boot 属性绑定](4.%20spring/7.%20spring_boot_2_propertiesBinding.pdf)
- [Spring Boot 事务](4.%20spring/7.%20spring_boot_3_transaction.pdf) —— 回滚规则与传播行为
- [Spring Boot 定时任务](4.%20spring/7.%20spring_boot_4_job.pdf)
- [Spring Cloud 微服务](4.%20spring/7.%20spring_cloud_%E5%BE%AE%E6%9C%8D%E5%8A%A1.pdf)
- [Spring MVC × Tomcat 启动部署总结](4.%20spring/8.%20spring_startup_summary.pdf) —— Engine→Host→Context→Wrapper 容器树与 war 部署全程

**5. 消息中间件**
- [SpringBoot × RocketMQ 集成启动流程](5.%20middleware/RocketMQ.pdf) —— starter 自动装配 → ListenerContainerConfiguration 注册 → 消费者拉取启动全程
- [RocketMQ 消费端源码链路](5.%20middleware/RocketMQ.svg) —— 双线程循环、长轮询、ProcessQueue 流控、位点异步上报全链路

**6. Redis**
- [Redis 分布式锁实战](6.%20redis/使用场景.pdf) —— SET NX PX + lua 解锁缺陷分析 → Redlock 争议，附生产实践
- [Redis 高可用全家桶](6.%20redis/复制_哨兵_集群_内存优化_事务_缓存.pdf) —— 复制握手→首次全量→命令传播→哨兵故障转移→集群分区与迁移

**7. 操作系统与 I/O**
- [零拷贝四种方案](7.%20os/zero_copy_流程图.svg) —— read/write → mmap → sendfile → sendfile+DMA → splice；RocketMQ 用 mmap、Kafka 用 sendfile 的选型逻辑

**书单（源码研读时的参照）**

Java Concurrency in Practice · Effective Java · 深入理解Java虚拟机 · G1GC 算法与实现 · Concurrency in Java (Brian Goetz) · Modern Java in Action · Programming Concurrency on the JVM · Java并发编程之美 · Design Patterns (GoF) · Head First Design Patterns

---

*作者：Annie Tian —— 7年+后端开发（IBM / 平安普惠），微服务与消息系统方向。笔记均产自源码研读过程，欢迎拍砖。*
