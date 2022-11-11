---
title: Java学习-疑惑之什么是对象
date: 2021-04-05 15:24:33
tags: 学习
categories: [学习,Java,疑惑]
---

```java
/*
*如何新建调用point数据类型
*/
package zuoye3;

public class Wjl03 {
 public static void main(String[]args) {
     point p1=new point(3,8);
     point p2=new point(5,9);
     System.out.println(p2.distance(p1,p2));
 }
}

class point{
    int x=5,y=2;
    point(int px,int py){
        x=px;
        y=py;
    }
    point(){
         

    }
    double distance(point p1,point p2) {
        System.out.println(p1.x+" "+p2.x+" "+p1.y+" "+p2.y);
        return Math.sqrt((p1.x-p2.x)*(p1.x-p2.x)+(p1.y-p2.y)*(p1.y-p2.y));
    }

}


```

