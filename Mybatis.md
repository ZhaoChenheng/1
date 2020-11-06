# MyBatis



## MyBatis 是否支持延迟加载？如果支持，它的实现原理是什么？
- Mybatis仅支持<resultMap>标签里的association关联的对象和collection关联的集合对象的延迟加载,可以配置是否启用延迟加载 
```
<setting name="lazyLoadingEnabled" value="true"/> 
<setting name="aggressiveLazyLoading" value="false"></setting>
```


## 通常一个 Xml 映射文件，都会写一个 Mapper 接口与之对应，请问，这个 Mapper 接口的工作原理是什么？Mapper接口里的方法，参数不同时，方法能重载吗？
- Mapper 接口的工作原理是 JDK 动态代理，MyBatis 运行时会使用 JDK 动态代理为 Mapper 接口生成代理 proxy 对象，代理对象 proxy 会拦截接口方法，转而执行MappedStatement所代表的 sql，然后将sql语句执行结果返回
- 接口的全限名就是映射文件中的namespace的值，接口的方法名就是映射文件中 MappedStatement 的 id 值，
- namespace+id 是作为 Map<String, MappedStatement>的 key 使用的，可唯一定位一个MappedStatement


## 简述 MyBatis 的 Xml 映射文件和 MyBatis 内部数据结构之间的映射关系？
- MyBatis 将所有 Xml 配置信息通过dom4j技术封装到 All-In-One 重量级对象 Configuration 内部。
- 每个resultMap标签会被解析为 ResultMap 对象，其每个子元素会被解析为 ResultMapping 对象。
- 每个parameterMap标签会被解析为 ParameterMap 对象，其每个子元素会被解析为 ParameterMapping 对象。
- 每一个 select insert update delete标签均会被解析为 MappedStatement 对象，标签内的 sql 会被解析为 BoundSql 对象。
