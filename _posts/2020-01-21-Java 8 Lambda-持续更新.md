---
layout:     post
title:      Java 8 Lambda 表达式
subtitle:   持续更新
date:       2020-01-21
author:     BY liningwonder
header-img: img/post-bg-re-vs-ng2.jpg
catalog: true
tags:
    - Java 8 Lambda 表达式
---

# Lambda 表达式总结


### 基本概概念

#### 1. 内部类（非静态内部类、静态内部类、匿名内部类）

内部类定义在一个类的内部，包含非静态内部类、静态内部类两种。

（1）内部类可以访问外部内的任何成员，包括private修饰的，反之不成立。  
（2）非静态内部类的实例需要寄生在外部内类的实例里面，即必须先初始化外部类。  
（3）成员变量名字相同时，可以通过OutClass.this.来引用。  
（4）外部类的静态方法不能访问非静态内部类。静态内部类的实例方法只能访问外部内的静态成员。  
（5）匿名内部类由于没有名字，只能用一次。  
（6）Java 8 中局部变量被匿名内部类访问时，该变量相当于使用final修饰。Java 8以下不支持，必须显示声明为final。  


#### 2. 函数式接口、lambda表达式、匿名内部类

（1）lambda表达式的目标类型必须时明确 函数式接口，即lambda表达式的结果时函数式接口的实例。  
（2）lambda表达式可以代替匿名内部类，简化代码。  
（3）方法引用和构造器引用。  


```java
public interface Flyable {
    void fly(String weather);
}
```

```java
public interface Eat {
    void eat();
}
```

```java
public abstract class AbstractCar {
    public abstract String getName();
}
```

```java
public class AnonymousInnerClass {

    private void test(Eat eat) {
        System.out.println("eat act");
        eat.eat();
    }

    private void test(AbstractCar car) {
        System.out.println("car name");
        System.out.println(car.getName());
    }

    private void test(Flyable flyable) {
        System.out.println("I'm flying");
    }

    public static void main(String[] args) {
        AnonymousInnerClass a = new AnonymousInnerClass();
        a.test(new Eat() {
            public void eat() {
                System.out.println("I'm eating");
            }
        });
        a.test(new AbstractCar() {
            @Override
            public String getName() {
                return "Audi";
            }
        });
        a.test(() -> {System.out.println("I'm eating");});
        a.test(() -> System.out.println("I'm eating"));
        a.test(new Flyable() {
            @Override
            public void fly(String weather) {
                System.out.println("the weather is " + weather);
            }
        });
        a.test(weather -> {System.out.println("the weather is " + weather);});
        a.test(weather -> System.out.println("the weather is " + weather));
    }

}
```
