# 集合

## 1.迭代器 Iterator 是什么？
- 迭代器(设计模式的一种)要是用来遍历集合用的，它的特点是更加安全，因为它可以确保，在当前遍历的集合元素被更改的时候，就会抛出 ConcurrentModificationException 异常。
- 每一个集合的内部数据结构是可能不尽相同的，所以对每一个集合存和取都可能不一样，虽然我们可以人为的在每一个类中定义next()和hasnext()方法，但这个会使整个集合体系过于臃肿，于是就有了迭代器。
- 迭代器是将这个方法抽取出接口，然后在每个类的内部，定义了自己的迭代方式，这样做就规定了整个集合体系的next()和hasnext()方法，使用者不管怎么实现，会用即可。 
- 迭代器的定义为：提供了一种方法访问一个容器对象中的各个元素，则又不需要暴露该对象内部的细节
## 2.Arraylist 与 LinkedList 区别?
- Arraylist 底层使用的是 数组           LinkedList底层使用的是 双向- 链表 (1.6 之前为循环链表，JDK1.7 取消了循环)
- ArrayList 采用数组存储，执行add(E e)方法的时候， ArrayList 会默认在将指定的元素追加到此列表的末尾，这种情况时间复杂度就是 O(1)。但是如果要在指定位置 i 插入和删除元素的话,时间复杂度就为 O(n-i)。
- LinkedList 采用链表存储，所以对于add(E e)方法的插入，删除元素时间复杂度不受元素位置的影响，近似 O(1)，如果是要在指定位置i插入和删除元素的话,时间复杂度近似为o(n))因为需要先移动到指定位置再插入。
- ArrayList 的空 间浪费主要体现在在 list 列表的结尾会预留一定的容量空间，而 LinkedList 的空间花费则体现在它的每一个元素都需要消耗比 ArrayList 更多的空间
## 3.Arraylist 和 Vector 的区别?
- ArrayList 是 List 的主要实现类，底层使用 Object[ ]存储，适用于频繁的查找工作，线程不安全 ；
- Vector 是 List 的古老实现类，底层使用 Object[ ]存储，线程安全的。
## 4.HashMap 和 Hashtable 的区别
- HashMap 是非线程安全的， 效率高一点。HashTable 是线程安全的,HashTable 内部的方法基本都经过synchronized 修饰。
- HashMap 可以存储 null 的 K 和 V，但 null 作为K只能有一个，null 作为V可以有多个；HashTable 不允许有 null 键和 null 值，否则会抛出 NullPointerException。
- Hashtable 默认的初始大小为 11，之后每次扩充，容量变为原来的 2n+1。HashMap 默认的初始化大小为 16。之后每次扩充，容量变为原来的 2 倍。创建时如果给定了容量初始值，那么 Hashtable 会直接使用你给定的大小，而 HashMap 会将其扩充为 2 的幂次方大小。	
- JDK1.8 以后的 HashMap 在解决哈希冲突时有了较大的变化，当链表长度大于阈值时，将链表转化为红黑树，以减少搜索时间。Hashtable 没有这样的机制。
## 5.HashSet 如何检查重复
- 当你把对象加入HashSet时，HashSet 会先计算对象的hashcode值来判断对象加入的位置，同时也会与其他加入的对象的 hashcode 值作比较，如果没有相符的 hashcode，HashSet 会假设对象没有重复出现。但是如果发现有相同 hashcode 值的对象，这时会调用equals()方法来检查 hashcode 相等的对象是否真的相同。如果两者相同，HashSet 就不会让加入操作成功。
