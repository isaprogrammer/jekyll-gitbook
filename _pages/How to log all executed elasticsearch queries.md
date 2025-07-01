---
title: 打印Elasticsearch的查询请求
author: Yalong Lee
date: 2025-06-29
category: Jekyll
layout: post
---

# elasticsearch-7x

```java
package org.elasticsearch.client;

public class RestClient implements Closeable {
    
    private static HttpRequestBase createHttpRequest(String method, URI uri, HttpEntity entity, boolean compressionEnabled) {
        switch (method.toUpperCase(Locale.ROOT)) {
            case "DELETE":
                return addRequestBody(new HttpDeleteWithEntity(uri), entity, compressionEnabled);
            case "GET":
                return addRequestBody(new HttpGetWithEntity(uri), entity, compressionEnabled);
            case "HEAD":
                return addRequestBody(new HttpHead(uri), entity, compressionEnabled);
            case "OPTIONS":
                return addRequestBody(new HttpOptions(uri), entity, compressionEnabled);
            case "PATCH":
                return addRequestBody(new HttpPatch(uri), entity, compressionEnabled);
            case "POST":
                HttpPost httpPost = new HttpPost(uri);
                addRequestBody(httpPost, entity, compressionEnabled);
                return httpPost;
            case "PUT":
                return addRequestBody(new HttpPut(uri), entity, compressionEnabled);
            case "TRACE":
                return addRequestBody(new HttpTrace(uri), entity, compressionEnabled);
            default:
                throw new UnsupportedOperationException("http method not supported: " + method);
        }
    }
    
}
```

