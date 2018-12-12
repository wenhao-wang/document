# Spring AOP
## Spring AOP的使用场景
- Authentication 权限
- Caching 缓存
- Transaction 事务
- Synchronization 同步
- persistence 持久化
## AOP技术的实现
### 动态代理
#### 实现
>主要由java.lang.reflect.Proxy和java.lang.reflect.InvocationHandler接口实现
#### 缺点
>动态代理只能对实现了相应interface的类使用，如果某个类没有实现任何的Interface，就无法shiy动态代理对其产生相应的代理对象
### CGLIB动态字节码
#### 实现
>CGLIB扩展对象行为的原理是：对目标对象进行继承扩展，为其生成相应的子类，而子类可以通过复写来扩展父类的行为，只要将横切逻辑放入到子类中，然后让系统使用扩展后的目标对象的子类，就可以达到与代理模式相同的效果了
#### 优点
>相比动态代理，CHLIB的优势就是可以为没有实现任何接口的类进行扩展，要对该类进行扩展，我们就要使用CGLIB类库，实现一个net.sf.cglib.proxy.Callback，或者使用net.sf.cglib.proxy.MethodInterceptor(继承自Callback)
#### 缺点
>使用CGLIB对类进行扩展对唯一限制就是无法对final方法进行复写

---
## Spring事务的实现
### Spring 事务特性
>事务有四个特性：AICD
- 原子性
- 一致性
- 隔离性
- 持久性
### 核心接口
#### 事务管理器
>Spring并不直接管理事务，而是提供了多种事务管理器，他们将事务管理的职责委托给Hibernate或者JTA等持久化机制所提供的相关平台框架的事务来实现。

> Spring事务管理器的接口是org.springframework.transaction.PlatformTransactionManager，通过这个接口，Spring为各个平台如JDBC、Hibernate等都提供了对应等事务管理器，但是具体的实现就是各个平台自己的事情了。

>```
>Public interface PlatformTransactionManager()...{
>    // 由TransactionDefinition得到TransactionStatus对象
>    TransactionStatus getTransaction(TransactionDefinition definition) throws TransactionException;
>  // 提交
>   Void commit(TransactionStatus status) throws TransactionException;
>   // 回滚
>   Void rollback(TransactionStatus status) throws TransactionException;
>}
>```

>从这里可知，具体的事务管理机制对Spring来说是透明的，它并不关心那些，那些是对应各个平台需要关心的，所以Spring事务管理等一个优点就是为不同等事务API提供一致的编程模型，如JTA、JDBC、Hibernate、JPA。下面分别对各个平台框架实现事务管理的机制进行介绍。

##### JDBC事务

##### Hibernate事物

##### Java持久化API事务(JPA)

##### Java原生API事务

#### 事物等基本属性定义

