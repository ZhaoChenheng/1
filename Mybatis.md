# MyBatis



## MyBatis 是否支持延迟加载？如果支持，它的实现原理是什么？
- Mybatis仅支持<resultMap>标签里的association关联的对象和collection关联的集合对象的延迟加载,可以配置是否启用延迟加载 
- 它的原理是，使用 CGLIB 创建目标对象的代理对象，当调用目标方法时，进入拦截器方法，比如调用 a.getB().getName()，拦截器 invoke()方法发现 a.getB()是 null 值，那么就会单独发送事先
- 保存好的查询关联 B 对象的 sql，把 B 查询上来，然后调用 a.setB(b)，于是 a 的对象 b 属性就有值了，接着完成 a.getB().getName()方法的调用。这就是延迟加载的基本原理。-每一个
- <select>、<insert>、<update>、<delete>标签均会被解析为 MappedStatement 对象，标签内的 sql 会被解析为 BoundSql 对象。
```
<setting name="lazyLoadingEnabled" value="true"/> 
<setting name="aggressiveLazyLoading" value="false"></setting>
```


## Mapper接口里的方法，参数不同时，方法能重载吗？
- 接口的全限名就是映射文件中的namespace的值，接口的方法名就是映射文件中 MappedStatement 的 id 值，
- namespace+id 是作为 Map<String, MappedStatement>的 key 使用的，可唯一定位一个MappedStatement
- 映射文件中，每一个select、insert、update、delete标签，都会被解析为一个MappedStatement对象。

## 简述 MyBatis 的 Xml 映射文件和 MyBatis 内部数据结构之间的映射关系？
- MyBatis 将所有 Xml 配置信息都封装到 All-In-One 重量级对象 Configuration 内部。
- 在 Xml 映射文件中，<parameterMap>标签会被解析为 ParameterMap 对象，其每个子元素会被解析为 ParameterMapping 对象。
- <resultMap>标签会被解析为 ResultMap 对象，其每个子元素会被解析为 ResultMapping 对象。
- 每一个select、insert、update、delete标签均会被解析为 MappedStatement 对象，标签内的 sql 会被解析为 BoundSql 对象。
