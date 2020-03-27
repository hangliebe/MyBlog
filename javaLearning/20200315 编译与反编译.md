# 1 编译 #
## 1.1 编译器 ##
&emsp;&emsp;计算机只能识别01,无法读懂程序员用java等高级语言写出的if else代码,所以这些代码在使用之前一定要转换成可以执行的二进制文件。

&emsp;&emsp;这也是编译器存在的原因。编译器是将高级语言编写的程序解析成计算机需要的详细机器语言指令集的程序。
编译器是一个程序,其工作是转换源码为可执行代码。

&emsp;&emsp;可执行代码是用计算机的本机语言或机器语言表示的代码。这种语言由数字代码(01)表示的详细指令组成。不同的计算机具有不同的机器语言。
## 1.2 java编译器 ##
&emsp;&emsp;JDK安装后,在bin文件夹下有一个javac.exe的应用程序,这个程序可以简单看作是java编译器。

&emsp;&emsp;javac.exe将java源码(java文件)编译成二进制字节码文件(.class文件),这是一种特殊的二进制文件,它是JVM的"机器语言"。
 
&emsp;&emsp;所以说javac.exe并没有将java源码直接翻译成计算机可以识别的机器语言,而是翻译成了java虚拟机识别的语言,而jvm将其再进一步翻译成对应的机器语言,这是java程序实现跨平台的原因,因为java程序可以跑在任何安装了jvm的计算机上。

&emsp;&emsp;扩展学习《[深入浅出JIT编译器](https://www.ibm.com/developerworks/cn/java/j-lo-just-in-time/index.html "深入浅出JIT编译器")》 
## 1.3 Android 编译器 ##
&emsp;&emsp;我们了解到JVM是java程序的运行环境,用来运行java的字节码程序。google为android平台专门设计了运行环境,以前是Dalvik,现在是ART(Android Runtime)
![android 架构图](https://github.com/hangliebe/MyBlog/tree/master/javaLearning/picture/android_architecture_diagram.jpg)
# 2 反编译 #
## 2.1反编译工具 ##
（1）dex2jar

&emsp;&emsp;从下面链接可以下载最新的[dex2jar工具](https://github.com/pxb1988/dex2jar/releases "dex2jar工具")：


（2）jadx

&emsp;&emsp;下载[jadx工具](https://github.com/skylot/jadx "jadx工具"),下载并解压,执行jadx-0.7.1\binjadx-gui.bat, 将反编译出的jar包拖进来就可以看到源码文件。
## 2.2反编译步骤 ##
1 解压出apk包中的classes.dex

2 使用的dex2jar工具中的d2j-dex2jar.bat 操作apk解压出来的classes.dex，得到classes-dex2jar.jar

3 使用jd-gui打开反编译出来的classes-dex2jar.jar,就可以看到所有的源码。
