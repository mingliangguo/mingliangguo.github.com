---
title: "spring boot development tips"
layout: post
cover: false
categories: 'blog'
tags: 'blog'
navigation: True
subclass: 'post tag-speeches'
comments: true
logo: 'assets/images/ghost.png'
cover: 'assets/images/cover4.jpg'
date: 2019-09-06 09:28:27 EDT
---


## Common application properties

- [Common application properties](https://docs.spring.io/spring-boot/docs/current/reference/html/common-application-properties.html)

## configuration to disable hystrix

There is no centralized configuration to disable hystrix. Separate configurations have to be made to disable the configuration for individual commands.

```groovy
spring.cloud.circuit.breaker.enabled=false
hystrix.command.default.circuitBreaker.enabled=false
```

## Actuator endpoints

By default, the actuator endpoints are not exposed. To expose specific ones, use `maangement.endpoints.web.exposure.include` to expose specific endpoints. For more details, refer to: https://docs.spring.io/spring-boot/docs/current/reference/html/production-ready-monitoring.html

```yaml
management:
  health:
    redis:
      enabled: false
  endpoint:
    health:
      show-details: always
  endpoints:
    web:
      base-path: '/'
      exposure:
        include: 'info,health,metrics'
    security:
      enabled: false
```
