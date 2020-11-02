# List
## ArrayList核心源码
```
public class ArrayList<E> extends AbstractList<E> implements List<E>, RandomAccess, Cloneable, java.io.Serializable{

    //默认初始容量大小
    private static final int DEFAULT_CAPACITY = 10;  
    //空数组（用于空实例）
    private static final Object[] EMPTY_ELEMENTDATA = {};   
    
    //用于默认大小空实例的共享空数组实例。
    //我们把它从EMPTY_ELEMENTDATA数组中区分出来，以知道在添加第一个元素时容量需要增加多少。
    private static final Object[] DEFAULTCAPACITY_EMPTY_ELEMENTDATA = {};
    
    //保存ArrayList数据的数组
    transient Object[] elementData; 
    //ArrayList 所包含的元素个数
    private int size;  
    
    /**
     * 带初始容量参数的构造函数（用户可以在创建ArrayList对象时自己指定集合的初始大小）
     */
    public ArrayList(int initialCapacity) {
        if (initialCapacity > 0) {
            this.elementData = new Object[initialCapacity];//如果传入的参数大于0，创建initialCapacity大小的数组
        } else if (initialCapacity == 0) {
            this.elementData = EMPTY_ELEMENTDATA;//如果传入的参数等于0，创建空数组
        } else {
            throw new IllegalArgumentException("Illegal Capacity: "+ initialCapacity);
        }
    }
     /**
     *默认无参构造函数
     *DEFAULTCAPACITY_EMPTY_ELEMENTDATA 为0.初始化为10，也就是说初始其实是空数组 当添加第一个元素的时候数组容量才变成10
     */
    public ArrayList() {
        this.elementData = DEFAULTCAPACITY_EMPTY_ELEMENTDATA;
    }

```
