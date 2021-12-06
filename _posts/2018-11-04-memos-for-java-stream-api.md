---
title: "Memos for Java Stream API"
layout: single
categories: 'blog'
tags: 'blog'
navigation: True
subclass: 'post tag-speeches'
comments: true
date: 2018-11-04 15:47:41 EST
---

## Stream.generate

```java
Random random = new Random();
List<Integer> numbers = Stream
    .generate(() -> random.nextInt(100))
    .limit(5)
    .collect(Collectors.toList());
```

## convert list of Integer to int array

```java
List<Integer> list = Arrays.asList(5, 2, 1);
int[] arr = list.stream()
  .mapToInt(Integer::intValue)
  .sorted()
  .toArray();
// int[3] { 1, 2, 5 }
```
