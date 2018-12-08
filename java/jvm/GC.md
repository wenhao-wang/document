# 垃圾收集器介绍
## JVM默认垃圾收集器
+ jdk7 默认垃圾收集器Parallel Scavenge(新生代) + Parallel Old(老年代)
+ jdk8 默认垃圾收集器Parallel Scavenge(新生代) + Parallel Old(老年代)
+ jdk9 默认垃圾收集器G1

垃圾回收器是垃圾回收算法（标记-清除，复制，标记-整理算法）的具体体现，不同商家、版本的jvm所提供的垃圾收集器可能有所差别
>下面描述七种不同分代的收集器：
- Serial
- ParNew
- Parallel Scavenge
- Serial Old
- Parallel Old
- CMS
- G1

垃圾收集器分类
- 新生代收集器：Serial, ParNew, Parallel Scavenge
- 老年代收集器：serial Old, Parallel Old, CMS;
- 整堆处理器：G1

## Parallel Scavenge 收集器
Parallel Scavenge收集器是一个新生代收集器，使用的是**复制算法**的收集器，而且也是多线程收集器。
Parallel Scavenge收集器，目标达到一个可控制的吞吐量，使用-XX:MaxGCPauseMillus参数控制垃圾停顿时间

## Parallel Old收集器
使用多线程与**标记-整理**算法，这个收集器在jdk1.6中才开始提供

## G1
G1是一款面向服务器端应用的垃圾收集器，使用G1收集器时，java堆的内存布局就与其他收集器有很大差别，它将整个java堆划分为多个大小小相等的独立区域(Region),虽然还保留新生代和老年代的概念，但新生代和老年代不再是物理隔离，他们都是一部分Region的集合，具体特点如下：
- 并行与并发
- 分代收集
- 空间整合
- 可预测的停顿
- 初试标记
- 并发标记
- 最终标记
- 筛选回收