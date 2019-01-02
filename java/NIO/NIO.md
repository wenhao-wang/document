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

