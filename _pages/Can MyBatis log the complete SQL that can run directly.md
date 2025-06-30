---
title: Can MyBatis log the complete SQL that can run directly
author: Yalong Lee
date: 2025-06-29
category: Jekyll
layout: post
---

# 字节码增强点

```java
@Override
public <E> List<E> query(MappedStatement ms, Object parameter, RowBounds rowBounds, ResultHandler resultHandler, CacheKey key, BoundSql boundSql) throws SQLException {
    // ...
    return list;
}
```

```java
@Override
public int update(MappedStatement ms, Object parameter) throws SQLException {
    // ...
    return doUpdate(ms, parameter);
}
```

# 加载探针，启动时会主动增强@RestController增强的类
![img.png](img.png)

# 填写关键词，匹配到关键词的SQL将会被打印
![img_1.png](img_1.png)

# 指定拦截的函数，函数内执行的所有SQL都将会被打印
![img_2.png](img_2.png)