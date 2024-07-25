# A note for book: Java程序设计---基础、编程抽象与算法策略
写一些有意思的代码、章后作业，不会摘录书的内容

[code](../../Programming_Abstractions_in_Java/src/main/java/edu/stanford/cs/javacs2/)

Chep5:Array并到cs61b



比较重要的Chep：
chep3:基本数据结构的抽象方法；String
chep4:从抽象的数据单元 $\rightarrow$ 基本数据单元 $\rightarrow$ 由动态的数据到静态的文件



## Chep4 File

在计算机上长期存储：常用方式就是将逻辑上内聚的数据搜集在一起，在持久性存储介质上存储为文件

* 存储在文件中的信息是持久性的
* 文件通常是按顺序读取的

### 4.2 读取文本文件
1. 打开文件
   ```java
   FileReader rd = new FileReader("Hamlet.txt");
   ```
   FileReader仅能一次读取一次字符，不允许更大单位来读取数据
   ```java
   BufferedReader rd = new BufferedReader(new FileReader("Hamlet.txt"))
   ```
   利用BufferedReader，不仅可以用read读取单个字符，还可以readLine将整行文本当作一个字符串读取


### 4.3 编写文本文件
### 4.4 格式化输出
利用``System.out.printf("%d + %d = %d%n",n1,n2,sum)``以各种各样的格式显示数值
### 4.5 格式化输入
[code](../../Programming_Abstractions_in_Java/src/main/java/edu/stanford/cs/javacs2/ch4_File/CollegeGraduationRates.java)

利用``Scanner``类解决读取其他种类数据种类的问题,其实就是文本有顺序，类型全知道，scanner就是将下一个知道的类型，用该类型读取的方式进行读取。

