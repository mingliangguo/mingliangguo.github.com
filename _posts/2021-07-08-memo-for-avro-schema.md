---
title: "Memo for Avro Schema"
layout: single
cover: false
categories: 'blog'
tags: 'blog'
navigation: True
subclass: 'posts'
comments: true
category: blog
date: 2021-07-08 14:55:42 EDT
---

- [Avro 1.4.0 Specification](https://avro.apache.org/docs/1.4.0/spec.html)

## Avro schema constraints

### Nullable and default values

```java
{
  "name": "AvroMapEntity",
  "fields": [
    {
      "name": "mapField",
      "type": [ "null",
        {
          "type": "map",
          "values": "int"
        }
      ],
      "default": null
    }
  ]
}
```
