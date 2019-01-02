# NIO
### NIO介绍
>nio是non-blocking的简称，在jdk1.4里提供的新api。

>Sun官方标榜的特性如下：
+ 为所有的原始类型提供(Buffer)缓存支持
+ 字符集编码解码解决方案
+ Channel:一个新的原始I/O抽象
+ 支持锁和内存映射文件的文件访问接口。
+ 提供多路(non-blocking)非阻塞的高可伸缩性网络I/O。

> NIO实现高性能处理的原理：使用较少的线程处理更多的任务。通过Selector选择器来执行不同Channel通道中的任务，执行任务再结合AIO就能发挥服务器的最大性能，大大提升软件运行效率。

###NIO技术核心要点
+ 缓冲区（Buffer）
+ 通道（Channel）
+ 选择器（Selector)

### 缓冲区
#### 缓冲区介绍
>Buffer类是个抽象类，它具有7个直接子类，分别是ByteBuffer, CharBuffer,DoubleBuffer, FloatBuffer, IntBuffer, LongBuffer, ShortBuffer,也就是缓冲区中存储的数据类型并不像普通I/O流只能存储byte或char数据类型，Buffer类能存储的数据类型的多样的。
### Buffer类的使用
>Buffer类及其7个对应基本数据类型的子类都是抽象类，无法直接通过new进行实例化。因此，创建这些类的对象方式是将上述7种数据类型的数组包装（wrap）进缓冲区，需要借助静态方法wrap()完成。

### 缓冲区的四个核心技术点
+ capacity(容量)
+ limit(限制)
+ position(位置)
+ mark(标记)
> capacity:缓冲区的大小，

> limit：缓冲区的限制代表第一个不能读取或写入元素的index,缓冲区的限制不能为负，并且limit不能大于其capacity

>position:代表“下一个”要读取或写入元素的index，缓冲区的position不能为负，并且position不能大于其limit。

> mark: 缓冲区的标记是一个索引，在调用reset()方法时，会将缓冲区的position位置重置为该索引。标记(mark)并不是必须的。
###ByteBuffer类的使用
> 直接缓冲区与非直接缓冲区：在Buffer和硬盘之间会在JVM中创建中间缓冲区，通过ByteBuffer向硬盘存取数据时，需要将数据暂存在JVM的中间缓冲区，再交给ByteBuffer处理。如果使用直接缓冲区实现两端数据交互，则直接在内核空间进行处理，无需JVM创建新的缓冲区。

>直接缓冲区比非直接缓冲区在运行效率上高一些，原因在于，直接缓冲区使用DirectByteBuffer类进行实现的，而非直接缓冲区是使用HeapByteBuffer类实现的。直接缓冲区（DirectByteBuffer)在内部使用sun.misc.Unsafe类进行值的处理，Unsafe类的作用是JVM与操作系统进行直接通信，提高程序运行效率。

### char和byte的区别
>char是字符型数据类型，无符号的，占两个字节，大小范围为0～65535；

>byte是字节型数据类型，有符号的，占一个字节，大小范围为-128～127；



