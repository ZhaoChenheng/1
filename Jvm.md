# JVM
## 1.1什么是垃圾？ 
  没有任何引用指向一个对象或多个对象（循环引用）<br>
![Image text]（https://github.com/ZhaoChenheng/1/blob/master/img/WX20201030-090926%402x.png）![Image text](https://github.com/ZhaoChenheng/1/blob/master/img/WX20201030-090926%402x.png)
## 1.2如何定位垃圾 ？
### 1.2.1引用计数（不能解决循环引用的垃圾）    当变为0时,这个对象变为垃圾</br>
  
### 1.2.1根可达算法  
