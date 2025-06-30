---
title: MyBatis打印完整可执行的SQL语句
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
<img src='./img.png' alt="">

# 填写关键词，匹配到关键词的SQL将会被打印
<img src='./img_1.png' alt="">

# 指定拦截的函数，函数内执行的所有SQL都将会被打印
<img src='./img_2.png' alt="">