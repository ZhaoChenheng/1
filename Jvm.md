# JVM
## 1.1什么是垃圾？ 
  没有任何引用指向一个对象或多个对象（循环引用）<br>
![Image text](https://github.com/ZhaoChenheng/1/blob/master/img/WX20201030-090926%402x.png)
![Image text](https://github.com/ZhaoChenheng/1/blob/master/img/%E6%B2%A1%E6%9C%89%E4%BB%BB%E4%BD%95%E5%BC%95%E7%94%A8%E6%8C%87%E5%90%91%E8%AF%A5%E5%AF%B9%E8%B1%A1.png)
## 1.2如何定位垃圾 ？
### 1.2.1引用计数（不能解决循环引用的垃圾）    当变为0时,这个对象变为垃圾<br>
![Image text](https://github.com/ZhaoChenheng/1/blob/master/img/1.png)
### 1.2.1根可达算法  <br>
![Image text](https://github.com/ZhaoChenheng/1/blob/master/img/12.png)
## 1.3常见的垃圾回收算法 
### 1.3.1 Mark-Sweep标记清除算法（位置不连续   产生碎片） <br>
![Image text](https://github.com/ZhaoChenheng/1/blob/master/img/123.png)
### 1.3.2 Copying拷贝算法（没有碎片，浪费空间）<br>
![Image text](https://github.com/ZhaoChenheng/1/blob/master/img/1234.png)
### 1.3.3 标记压缩算法（没有碎片 效率偏低）<br>
![Image text](https://github.com/ZhaoChenheng/1/blob/master/img/12345.png)
