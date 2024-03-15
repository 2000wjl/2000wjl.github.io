---
title: Java多线程
date: 2024-03-15 09:49:24
tags: [Java,多线程]
---

# 多线程

> 为了提高CPU利用率，减少CPU的空闲时间，提高程序运行速度而引入的概念。一般来说，一个单核处理器只能同时运行一个线程，双核则两个线程，但超线程技术的引入改变了这一点。例：I9 13900HX 为24核心32线程处理器

## Java多线程的实现方式

### 继承Thread

```java
Thread thread01 = new Thread01();
thread01.start();

public static class Thread01 extends Thread{
    @Override
    public void run(){
        //业务代码
    }
} 
```

### 实现Runnable接口

```java
Runnable01 runnable01 = new Runnable01();
new Thread(runnable01).start();

public static class Runnable01 implements Runnable{
    @Override
    public void run(){
        //业务代码
    }
} 
```

### 实现Callable接口

```java
FutureTask<Integer> futureTask = new FutureTask<>(new Callable01());
new Thread(futureTask).start();
futureTask.get();//阻塞式等待线程结束并返回

public static class Callable01 implements Callable<Integer>{
    @Override
    public Integer call() throws Exception{
        //业务代码
        return 1;
    }
} 
```

### 线程池

```java
private static ExecutorService service = Executors.newFixedThreadPool(10);//指定大小core=max，不回收
private static ExecutorService service = Executors.newCacheThreadPool(10);//core是0，都可回收
private static ExecutorService service = Executors.newSingleThreadExecutor();//单线程的线程池，保证任务的顺序执行
private static ExecutorService service = Executors.newScheduledThreadPool();//定时任务的线程池

service.execute();//没有返回值
service.submit();//有返回值
```

#### 原生创建线程池

```java

/**
 * corePoolSize 核心线程数，一直存在除非(allowCoreThreadTimeOut)
 * maximumPoolSize 最大线程数
 * keepAliveTime 存活时间，如果当前线程数大于corePoolSize，空闲时间大于keepAliveTime则释放
 * unit 时间单位
 * BlockingQueue<Runnable> workQueue 阻塞队列 正在等待执行的任务
 * threadFactory 线程工厂
 * handler 如果队列满了 按照指定的拒绝策略拒绝执行任务
 */
ThreadPoolExecutor threadPoolExecutor = new ThreadPoolExecutor();

```

#### 线程池串行化

```java

//************单个任务***********
//上个任务完成就执行
thenRunAsync//无上一步结果，无返回值
thenAcceptAsync//有上一步结果，无返回值
thenApplyAsync//有上一步结果，有返回值
//************单个任务***********

//************两个任务的组合***********
//两个任务都完成才执行
runAfterBoth//无上一步返回结果，无返回值
thenAcceptBothAsync//有上一步结果，无返回值
thenCompletableFuture//有上一步结果，有返回值

//两个任务只要有一个完成就执行
runAfterEither//无上一步返回结果，无返回值
acceptEither//有上一步结果，无返回值，两个任务的返回类型应相同
applyToEither//有上一步结果，有返回值，两个任务的返回类型应相同
//************两个任务的组合***********
    
//************多个任务的组合***********
//所有任务都完成才执行
allOf
    
    //只要有一个完成就执行
    anyOf
//************多个任务的组合***********

```

