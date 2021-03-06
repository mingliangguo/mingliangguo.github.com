---
title: "spring boot development tips"
layout: single
categories: 'blog'
tags: 'blog'
navigation: True
subclass: 'posts'
comments: true
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

### Spring Boot Configuratin Binding

- [Spring Boot Configuration Binding](https://github.com/spring-projects/spring-booT/wiki/Spring-Boot-Configuration-Binding)

### Enable logging

The following can be used as the jvm parameter to enable a specific logging category for spring boot application. e.g. the following enables the debug level logging for spring security.

```bash
- name: JVM_ARGS
  value: "-Dlogging.level.org.springframework.security=DEBUG"
```

### Error handling

- [Error Handling for REST with Spring](https://www.baeldung.com/exception-handling-for-rest-with-spring)


### details of the dependencies

Go check the pom file of each starters to understand what are the exact dependencies pulled in.

- [maven repo url](https://repo1.maven.org/maven2/org/springframework/boot/spring-boot-dependencies)
- [spring.io repo url](https://repo.spring.io/milestone/org/springframework/boot/spring-boot-dependencies)
