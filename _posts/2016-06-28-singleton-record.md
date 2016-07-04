---
layout: post_layout
title: 单例模式-记录
time: 2016年06月30日 星期四
location: 上海
pulished: true
excerpt_separator: "使用synchronized"
---

##### 单例模式
“一个类有且仅有一个实例，并且自行实例化向整个系统提供。”

##### 实现方式

 - 使用内部静态类的方式保存INSTANCE

```java
public class Singleton implements Serializable {

    // 使用静态内部类保存INSTANCE
    private static class SingletonHolder {
        private static final Singleton _INSTANCE = new Singleton();
    }

    // 私有化构造函数  private or protected?
    private Singleton() {}

    // 对外接口，获取唯一实例句柄
    public static Singleton Instance() {
        return SingletonHolder._INSTANCE;
    }

    // readResolve方法应对单例对象被序列化时候
    private Object readResolve() {
        return Instance();
    }
}
```

 - 使用synchronized来保证线程同步。

```java
public class Singleton implements Serializable {

    private volatile static Singleton _INSTANCE;

    private Singleton() {}

    public static Singleton Instance() {
        if (_INSTANCE == null) {
            synchronized (Singleton.class) {
                if (_INSTANCE == null) {
                    _INSTANCE = new Singleton();
                }
            }
        }
        return _INSTANCE;
    }
}
```