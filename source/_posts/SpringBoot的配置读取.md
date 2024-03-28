---
title: SpringBoot的配置读取
date: 2024-03-18 16:39:54
tags: [Java,SpringBoot]
---

# 配置类

```java
@ConfigurationProperties(prefix = "gulimall.thread")
@Component
@Data
public class ThreadPoolProperties {

    private Integer coreSize = 50;
    private Integer maxSize = 200;
    private Integer keepAlive = 10;

}
```

# 依赖

> 导入后重启项目可在properties文件中提示，也可不导入

```pom
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-configuration-processor</artifactId>
</dependency>
```

# 使用

```java
//@EnableConfigurationProperties(ThreadPoolProperties.class)
@Configuration
public class MyThreadConfig {

    public ThreadPoolExecutor threadPoolExecutor(ThreadPoolProperties pool){
        return new ThreadPoolExecutor(
                pool.getCoreSize(),
                pool.getMaxSize(), 
                pool.getKeepAlive(), 
                TimeUnit.SECONDS,
                new LinkedBlockingDeque<>(100000), 
                Executors.defaultThreadFactory(),
                new ThreadPoolExecutor.AbortPolicy());
    }

}
```
