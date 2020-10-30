# JVM
## 1.1什么是垃圾？ 
  没有任何引用指向一个对象或多个对象（循环引用）<br>
  <img src="https://github.com/ZhaoChenheng/1/blob/master/img/%E6%B2%A1%E6%9C%89%E4%BB%BB%E4%BD%95%E5%BC%95%E7%94%A8%E6%8C%87%E5%90%91%E8%AF%A5%E5%AF%B9%E8%B1%A1.png" width="600" height="400">    
  <img src="https://github.com/ZhaoChenheng/1/blob/master/img/WX20201030-090926%402x.png" width="600" height="400">
  
## 1.2如何定位垃圾 
### 1.2.1引用计数（不能解决循环引用的垃圾）    当变为0时,这个对象变为垃圾<br>
 <img src="https://github.com/ZhaoChenheng/1/blob/master/img/1.png" width="600" height="400">
### 1.2.1根可达算法  <br>
 <img src="https://github.com/ZhaoChenheng/1/blob/master/img/12.png" width="600" height="400">
 
## 1.3常见的垃圾回收算法 
### 1.3.1 Mark-Sweep标记清除算法（位置不连续   产生碎片） <br>
 <img src="https://github.com/ZhaoChenheng/1/blob/master/img/123.png" width="600" height="400">
### 1.3.2 Copying拷贝算法（没有碎片，浪费空间）<br>
 <img src="https://github.com/ZhaoChenheng/1/blob/master/img/1234.png" width="600" height="400">
### 1.3.3 标记压缩算法（没有碎片 效率偏低）<br>
  <img src="https://github.com/ZhaoChenheng/1/blob/master/img/123456.png" width="600" height="400">
## 1.4JVM内存分代模型(用于分代垃圾回收算法)
### 1.4.1部分垃圾回收器的的使用模型
### 1.4.2新生代+老年代+永久代(1.7)/元数据区(1.8 Metaspace)
永久代/元数据区 -->.class      
永久代必须指定大小限制   元数据可以设置，也可以不设置(受限于物理内存)
符串常量1.7--永久代  1.8--堆
### 1.4.3 堆内存逻辑分区
新生代=Eden + 2个suvivor区      老年代(顽固分子)
1.YGC回收之后,大多数对象都会被回收,剩下的活着的对象全部放入s0
2.再次YGC,活着的对象eden+s0-->s1
3.再次YGC,活着的对象eden+s1-->s0
4.年龄足够-->老年代(15 CMS 6)
5.s区装不下-->老年代
6.老年代满了会触发FGC (Full GC)
 <img src="https://github.com/ZhaoChenheng/1/blob/master/img/12345.png" width="600" height="400">
 
## 1.5常见的垃圾回收器
1.5.1 serial 年轻代 串行回收
1.5.2 PS     年轻代 并行回收
1.5.3 ParNew 年轻代 配合CMS的并行回收
1.5.4 SerialOld
1.5.5 ParallelOld
1.5.6 ConcurrentMarkSweep 老年代 并发的，垃圾回收和应用程序同时执行，降低STM的时间（200ms）
1.5.7 G1(10ms)
1.5.8 ZGC(1ms)    PK   C++
1.5.9 Shenandoah
1.5.10 Eplisn
JDK1.8  默认的垃圾回收：PS+ParallelOld
 <img src="https://github.com/ZhaoChenheng/1/blob/master/img/222.png" width="600" height="400">

  

