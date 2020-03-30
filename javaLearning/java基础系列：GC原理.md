# GC知识点 #
## GC原理 ##
JAVA GC采用了分代思想,将java堆分成新生代，年老代，永久代。GC算法主要有标记-清除，标记-压缩，复制算法。

[java Garbage Colleciton Basics](https://www.oracle.com/webfolder/technetwork/tutorials/obe/java/gc01/index.html)
## 注意点 ##
### 执行System.gc() ###
执行System.gc()函数知识提醒虚拟机，希望进行一次垃圾回收。并不能立即生效，具体什么时候回收取决于虚拟机。而且不能保证一定会进行垃圾回收。当DisableExplicitGC设置为true，则不会进行回收。
