---
title: Spring事务
date: 2024-03-28 18:04:11
tags: [Java,Spring,事务]
---

# Spring事务

## 事务

### ACID原则

**事务的原子性(Atomicity)：**是指一个事务要么全部执行，要么不执行，也就是说一个事务不可能只执行了一半就停止了。比如你从[取款机](https://baike.baidu.com/item/取款机/1812936?fromModule=lemma_inlink)取钱，这个事务可以分成两个步骤：1划卡，2出钱。不可能划了卡，而钱却没出来。这两步必须同时完成，要么就不完成。

**事务的**[一致性](https://baike.baidu.com/item/一致性/0?fromModule=lemma_inlink)(Consistency)：是指事务的运行并不改变数据库中数据的一致性。例如，完整性约束了a+b=10，一个事务改变了a，那么b也应该随之改变。

**独立性（Isolation）：**事务的独立性也称作隔离性，是指两个以上的事务不会出现交错执行的状态。因为这样可能会导致数据不一致，更加具体的来讲，就是事务之间的操作是独立的。

**持久性（Durability）：**[事务](https://baike.baidu.com/item/事务/0?fromModule=lemma_inlink)的[持久性](https://baike.baidu.com/item/持久性/0?fromModule=lemma_inlink)是指事务执行成功以后，该事务对数据库所作的更改便是持久的保存在数据库之中，不会无缘无故的[回滚](https://baike.baidu.com/item/回滚/0?fromModule=lemma_inlink)。

## 编程式事务

> 通过 `TransactionTemplate`或者`TransactionManager`手动管理事务，实际应用中很少使用，但是对于你理解 Spring 事务管理原理有帮助。

使用`TransactionTemplate` 进行编程式事务管理的示例代码如下：

```java
@Autowired
private TransactionTemplate transactionTemplate;
public void testTransaction() {

        transactionTemplate.execute(new TransactionCallbackWithoutResult() {
            @Override
            protected void doInTransactionWithoutResult(TransactionStatus transactionStatus) {

                try {

                    // ....  业务代码
                } catch (Exception e){
                    //回滚
                    transactionStatus.setRollbackOnly();
                }

            }
        });
}

```

使用 `TransactionManager` 进行编程式事务管理的示例代码如下：

```java
@Autowired
private PlatformTransactionManager transactionManager;

public void testTransaction() {

  TransactionStatus status = transactionManager.getTransaction(new DefaultTransactionDefinition());
          try {
               // ....  业务代码
              transactionManager.commit(status);
          } catch (Exception e) {
              transactionManager.rollback(status);
          }
}
```

## 声明式事务

> 推荐使用（代码侵入性最小），实际是通过 AOP 实现（基于`@Transactional` 的全注解方式使用最多）。使用 `@Transactional`注解进行事务管理的示例代码如下：

```java
@Transactional(propagation = Propagation.REQUIRED)
public void aMethod {
  //do something
  B b = new B();
  C c = new C();
  b.bMethod();
  c.cMethod();
}
```

### 问题

由于Spring声明式事务是通过`AOP`实现，通过代理对象来管理事务，对于同一个类的方法间的调用，事务注解不能起效。在上个例子中，`bMethod`与`cMethod`均受到事务管理，但若存在`dMethod`在此类中，该方法的事务注解不会生效。

## 解决

我们可以将`dMethod`抽取到另一个类中，以实现`AOP`的代理对象事务自治。当然更优雅的解决方案为通过`AopContext`获取当前代理对象并调用目标方法，如图所示。

![image-20240328181238579](https://upyun.zyhwjl.cn/img//2024/03/28/18-12-38-4bda3e49a44bdcca415a5920d6c68879-image-20240328181238579-06e289.png)
