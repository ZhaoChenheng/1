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
