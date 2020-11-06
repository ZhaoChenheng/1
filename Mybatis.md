# MyBatis



## MyBatis 是否支持延迟加载？如果支持，它的实现原理是什么？
- Mybatis仅支持<resultMap>标签里的association关联的对象和collection关联的集合对象的延迟加载,可以配置是否启用延迟加载 
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
- 每一个<select>、<insert>、<update>、<delete>标签均会被解析为 MappedStatement 对象，标签内的 sql 会被解析为 BoundSql 对象。
