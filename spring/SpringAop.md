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
>>主要由java.lang.reflect.Proxy和java.lang.reflect.InvocationHandler接口实现
#### 缺点
>>动态代理只能对实现了相应interface的类使用，如果某个类没有实现任何的Interface，就无法shiy动态代理对其产生相应的代理对象
### CGLIB动态字节码
#### 实现
>>CGLIB扩展对象行为的原理是：对目标对象进行继承扩展，为其生成相应的子类，而子类可以通过复写来扩展父类的行为，只要将横切逻辑放入到子类中，然后让系统使用扩展后的目标对象的子类，就可以达到与代理模式相同的效果了
#### 优点
>>相比动态代理，CHLIB的优势就是可以为没有实现任何接口的类进行扩展，要对该类进行扩展，我们就要使用CGLIB类库，实现一个net.sf.cglib.proxy.Callback，或者使用net.sf.cglib.proxy.MethodInterceptor(继承自Callback)
#### 缺点
>>使用CGLIB对类进行扩展对唯一限制就是无法对final方法进行复写
