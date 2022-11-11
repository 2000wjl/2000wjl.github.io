---
title: IDEA的模板注释
date: 2021-12-23 19:14:59
tags: 实用
categories: [折腾,实用,IDEA]
---

# 类注释

> 可参照说明自行修改

```java
/**
 * Created with IntelliJ IDEA.
 * @Author: 你的名字
 * @Date: ${YEAR}/${MONTH}/${DAY}/${TIME}
 * @Description: 
 */
```

`File--->Settings---->Editor---->File and Code Templates --->Includes--->File Header`

`applay`

 ![img](https://gitee.com/zyhwjl/images/raw/master/PicGo/https/img-blog.csdnimg.cn/da57d29c808246d3a1a072b6fef7da0d.png?x-oss-process=image/2021/12/23/19-10-03-821e15d2bfd8cd9b2db0d0813022e796-da57d29c808246d3a1a072b6fef7da0d-cf3b75.png)

> 效果![img](https://gitee.com/zyhwjl/images/raw/master/PicGo/https/img-blog.csdnimg.cn/ca09165df90d413fb1880a758bbc0658.png?x-oss-process=image/2021/12/23/19-10-13-8fd72aef1aa43a9ffbc8f74b494b70ad-ca09165df90d413fb1880a758bbc0658-323c08.png)

# 方法注释

> 自己改，前面没'/**'，不要自作聪明

```
**
* @Description: $description$
* @Param: $params$
* @return: $returns$
* @Author: 你的名字
* @Date: $date$
*/
```

![img](https://gitee.com/zyhwjl/images/raw/master/PicGo/https/img-blog.csdnimg.cn/20190919101418507.png?x-oss-process=image/2021/12/23/19-13-29-d57a9600c2ece2f2a07eb95008e2263d-20190919101418507-abe9c1.png)

![img](https://gitee.com/zyhwjl/images/raw/master/PicGo/https/img-blog.csdnimg.cn/20190919101554492.png?x-oss-process=image/2021/12/23/19-13-35-feec4991acace3937be182e2e43f65fb-20190919101554492-bb131f.png)

![img](https://gitee.com/zyhwjl/images/raw/master/PicGo/https/img-blog.csdnimg.cn/20200917115631555.png?x-oss-process=image/2021/12/23/19-13-45-cad90e004adfcd9473fd915fd7c90c2a-20200917115631555-7c7c12.png)

![img](https://gitee.com/zyhwjl/images/raw/master/PicGo/https/img-blog.csdnimg.cn/89fc8772694d49ea9bd889b7d168f464.png?x-oss-process=image/2021/12/23/19-14-11-ce8554d81f3d0349b9650379cee94bb9-89fc8772694d49ea9bd889b7d168f464-037a40.png)

## 为你的模板设置默认值：点击那个Edit variables

![img](https://gitee.com/zyhwjl/images/raw/master/PicGo/https/img-blog.csdnimg.cn/20190920113021835.png?x-oss-process=image/2021/12/23/19-14-19-92d42e1cd5bbb74c9f907c5dc03589fa-20190920113021835-6e94db.png)

**保存后，先按一个/ * ，紧跟着按Tab键 ，注释就出来了。当然，这个* 你可以随便写，最后注释快捷键就是 （/  你自定义按键 + Tab）**

> 效果![img](https://gitee.com/zyhwjl/images/raw/master/PicGo/https/img-blog.csdnimg.cn/3b9b9c2839ed44198828b19bff799eae.png?x-oss-process=image/2021/12/23/19-14-27-54cbf950a3d531440ecbd272b3d87ff4-3b9b9c2839ed44198828b19bff799eae-28fa47.png)

------

有小伙伴说注释按下后没出来。没出来的话是不是你操作到方法注释保存时这里有个警示呢？

![img](https://gitee.com/zyhwjl/images/raw/master/PicGo/https/img-blog.csdnimg.cn/20200917120528517.png?x-oss-process=image/2021/12/23/19-14-33-f16b8391f6880cd58e198cd50783e608-20200917120528517-a6b6d2.png)
