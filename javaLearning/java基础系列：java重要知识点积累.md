# JAVA重要知识总结 #
## 基本类型和不变类型 ##
**8种基本类型** 
第一类：整型 byte short int long
第二类：浮点型 float double
第三类：逻辑型 boolean
第四类：字符型 char

**不变类型** 
与基本类型对应的封装类型：Byte,Short,Integer,Long,Float,Double,Boolean,Character
另外还有字符串类型：String

## StringBuffer和StringBuild ##
StringBuffer是线程安全的，效率低；
StringBuild 是线程不安全的，效率高。
## 集合 ##
![java集合架构图](https://github.com/hangliebe/MyBlog/tree/master/javaLearning/picture/collection_architecture_diagram.gif)
>List(集)元素有序，可重复.

ArrayList：初始化大小10，扩容原容量0.5倍+1（10->16），线程不安全

Vertor：初始化大小为10，扩容原容量1倍（10->20），线程安全

>Set(集) 元素无序的、不可重复。

Hashset:初始化大小16，扩容原容量1倍，线程不安全，底层实现是一个HashMap（保存数据），实现Set接口。

>Map是一个双列集合

HashMap：初始化大小16，加载因子为0.75，扩容原容量1倍，线程不安全。允许null作为key或者value。

HashTable:初始大小11，加载因子为0.75，扩容原容量1倍+1，线程安全。不允许null作为key或者value。
## 如何捕获子线程异常 ##
1 在子线程中try-catch 直接捕获

2 为子线程设置UncaughtExceptionHandler

3 Future的get方法
[Future的使用](https://cloud.tencent.com/developer/article/1487126 "Future的使用")

    package com.timedimension.lib;
    
    public class MultiThreading {
    public static void main(String[] args) {
        firstMethod();
        secondMethod();
        thirdMethod();
    }

    // sub thread try-catch
    private static void firstMethod() {
        Thread subThread = new Thread(new Runnable() {
            @Override
            public void run() {
                try {
                    throw new Exception("first sub thread");
                } catch (Exception ex) {
                    System.out.println(ex.getMessage());
                }
            }
        });
        subThread.start();
    }

    // UncaughtExceptionHandler method
    private static void secondMethod() {
        Thread subThread = new Thread("second sub thread"){
            @Override
            public void run() {
                int num1 = 10;
                int num2 = 0;
                int num3 = num1 / num2;
            }
        };

        subThread.setUncaughtExceptionHandler(new Thread.UncaughtExceptionHandler() {
            @Override
            public void uncaughtException(Thread thread, Throwable throwable) {
                System.out.println("thread:"+thread.getName()+" throwable:"+throwable.getMessage());
            }
        });
        subThread.start();
    }

    // Future get
    private static void thirdMethod(){

    }
    }
## NIO ##
NIO三大组件：Channel,Buffer，Selector

[真正理解NIO](https://www.jianshu.com/p/362b365e1bcc "真正理解NIO")