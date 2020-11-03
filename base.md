# 1.静态方法和实例方法不不同
-  静态方法可使用 “类命.方法名”直接调用
-  静态方法不能直接访问非静态成员
```
class c{
	int c = 1;
	public static void method(){
		System.out.print(c);//错误
	}
}
```
- 内部类有静态成员，那么该类一定是静态内部类
- 静态内部类的静态代码块 在类加载时不执行，什么时候调用静态内部类  什么时候执行
```
public class Static {
	public static void method1(){}
	
	public static  class A {
		static {}
		public static void method2(){}
	}
}
```
- 静态成员 在全类中只有一份，任何对象修改，都会影响其他对象
- 静态方法可继承、不能重写、没有多态
- 静态方法中不能使用this或super
