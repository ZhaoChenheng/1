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
# 2.重写OverRide和重载Overload的区别
- 重写
	- 是子类跟父类的关系,子类继承父类时重写父类的方法
	- 返回值、方法名、参数列表 相同
	- 访问修饰符与父类相同或者比父类更宽泛
- 重载 
	- 常用的多个构造方法就是重载 
	- 方法名相同 参数列表不同（类型，个数，顺序）   
	- 与访问修饰符、返回值无关
# 3.Comparable接口和Comparator接口的区别
- 这两个接口的方法主要是对对象进行排序 
- Comparable多用于对象类的实现 重写compareTo方法
- Comparator多用于匿名内部类   重写compare方法
```
class Teacher implements Comparable<Teacher>{
	String name;
	Double salary;
	
	@Override
	public int compareTo(Teacher o) {
		if(this.salary>o.salary) {
			return -1;
		}else if(this.salary<o.salary) {
			return 1;
		}else {
				if(this.name.compareTo(o.name)>0) {
					return -1;
				}else if(this.name.compareTo(o.name)<0) {
					return 1;
				}else {
					return 0;
				}
		}
	}
}
```
```
Set<People> set = new TreeSet<People>(new Comparator<People>() {
	@Override
	public int compare(People p1, People p2) {
		if(p1.getSalary() - p2.getSalary()>0) {
			return 1;
		}else if (p1.getSalary() - p2.getSalary()<0){
			return -1;
		}else {
			if(p1.getName().compareTo(p2.getName()) >0) {
				return 1;
			}else if(p1.getName().compareTo(p2.getName()) <0) {
				return -1;
			}else {
				return 0;
			}
		}
	}
			
});
```
