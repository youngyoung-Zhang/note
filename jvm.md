# jvm

## jvm参数

**-XX:survivor ratio**

> The SurvivorRatio parameter controls the size of the two survivor spaces. For example, -XX:SurvivorRatio=6 sets the ratio between each survivor space and eden to be 1:6, each survivor space will be one eighth of the young generation. The default for Solaris is 32. If survivor spaces are too small, copying collection overflows directly into the old generation. If survivor spaces are too large, they will be empty. At each GC, the JVM determines the number of times an object can be copied before it is tenured, called the tenure threshold. This threshold is chosen to keep the survivor space half full.
>
> Use the option -XX:+PrintTenuringDistribution to show the threshold and ages of the objects in the new generation. It is useful for observing the lifetime distribution of an application.

翻译：

> SurvivorRatio参数控制两个幸存者空间的大小。例如，-XX:survivor ratio=6将每个幸存者空间与伊甸园的比率设置为1:6，每个幸存者空间将是年轻一代的八分之一。Solaris的默认值是32。如果survivor空间太小，复制集合将直接溢出到老年代中。如果survivor空间太大，它们将是空的。在每个GC中，JVM在对象被保留（称为保留阈值）之前确定它可以被复制的次数。选择此阈值可使survivor空间**保持半满**。使用选项-XX:+PrintTenuringDistribution显示新一代对象的阈值和年龄。它有助于观察应用程序的生存期分布。

```bash
例：-XX:survivor ratio=6
在jvm种新生代和老年代的比例为：1：2
新生代又分为 eden和survivor区 将survivor ratio的值设置为6的意思是eden和每个survivor区的比值为6：1所以整个新生代的比值为6:1:1
```

**-XX:+PrintGCDetails -Xloggc:gc.log**

 **-XX:+HeapDumpOnOutOfMemoryError** 

 **-XX:HeapDumpPath=/usr/local/app/oom**

**-XX:HandlePromotionFailure**

**-XX:+PrintTenuringDistribution**

## jvm调优

- 如果survivor空间太小，复制集合将直接溢出到老年代中。如果survivor空间太大，它们将是空的。在每个GC中，JVM在对象被保留（称为保留阈值）之前确定它可以被复制的次数。选择此阈值可使survivor空间**保持半满**。
- 