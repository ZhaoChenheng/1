# MyBatis



## MyBatis 是否支持延迟加载？如果支持，它的实现原理是什么？
- Mybatis仅支持<resultMap>标签里的association关联的对象和collection关联的集合对象的延迟加载,可以配置是否启用延迟加载 
```
<setting name="lazyLoadingEnabled" value="true"/> 
<setting name="aggressiveLazyLoading" value="false"></setting>
```
- 它的原理是，使用 CGLIB 创建目标对象的代理对象，当调用目标方法时，进入拦截器方法，比如调用 a.getB().getName()，拦截器 invoke()方法发现 a.getB()是 null 值，那么就会单独发送事先保存好的查询关联 B 对象的 sql，把 B 查询上来，然后调用 a.setB(b)，于是 a 的对象 b 属性就有值了，接着完成 a.getB().getName()方法的调用。这就是延迟加载的基本原理。

