# JVM
## 1.1什么是垃圾？ 
  没有任何引用指向一个对象或多个对象（循环引用）
  ![Image text](https://github.com/ZhaoChenheng/1/blob/master/img/%E6%B2%A1%E6%9C%89%E4%BB%BB%E4%BD%95%E5%BC%95%E7%94%A8%E6%8C%87%E5%90%91%E8%AF%A5%E5%AF%B9%E8%B1%A1.png)
## 1.2如何定位垃圾 ？
### 1.2.1引用计数（不能解决循环引用的垃圾）    当变为0时,这个对象变为垃圾
 ![Image text](https://github.com/ZhaoChenheng/1/blob/master/img/%E6%B2%A1%E6%9C%89%E4%BB%BB%E4%BD%95%E5%BC%95%E7%94%A8%E6%8C%87%E5%90%91%E8%AF%A5%E5%AF%B9%E8%B1%A1.png)
### 1.2.1根可达算法  
