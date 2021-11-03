# 第一天

### 1.跨平台原理

在需要运行的java应用程序的操作系统上，安装一个与操作系统对应的Java虚拟机（JVM）即可

### 2. JRE与JDK

- JRE是Java运行时的环境，包含JVM和运行时所必需的类
- JDK是程序开发工具，包含JRE与开发工具

### 3. JDK下载与安装

- 自己去官网上找

### 4.常用的DOS命令

- E:——切换到e盘
- calc——打开计算器
- mspaint——打开画图工具
- notepad——打开记事本
- dir——查看当前目录

### 5.配置环境变量

- 为了方便的使用java与javac命令

### 6.HelloWord案例

- 新建文档文件，修改为HelloWorld.java
- 写程序，保存
- 进入命令窗口，进入其所在目录，先编译在执行
- javac HelloWorld.java        java HelloWorld

---

---



# 第二天

### 1.卸载JDK

- 删除Java的安装目录，删除环境变量，查看是否删除成功

### 2.简单设置

- sout——输出，psvm——打开主程序。

### 3.数据类型及变量

- 大小写十分敏感，float类型要加F，long类型要加L

- 八进制——0，十六进制——0x

- ```ava
  //浮点数扩展         有限 离散  舍入误差 大约 接近但不等于
  //最好避免完全使用浮点数比较，有较大的误差
  //数字之间可以用下划线来隔开。
  
  public class demo03 {
  
      //类变量
      static double salary = 2500;
      
      //常量——不能被改变的值,修饰符不计较先后顺序
      static final double PI=3.1415;
  
      // 实例变量 ：从属于对象，如果不初始化，就默认这个类型的默认值 0 0.0    u0000  false，除了基本类型，其余默认值都是none
      
      String name;
      int age;
  
      
      public static void main(String[] args) {
  
          int i=10;
          System.out.println(i);
  
          //定义变量
          demo03 demo03=new demo03();
          System.out.println(demo03.age);
  
          
  
      }
  
  
  }
  
  ```

### 4.运算符

```java
//逻辑运算符 && || !——与或非
        
        /*
        * A = 0011 1100
        * B = 0000 1101
        * A&B=0000 1100
        * A|B=0011 1101
        * A^B=0011 0001
        * ~B=1111 0010
        *
        * */

        /*
        底层位移运算是十分快的
        * 0000 0000 0
        * 0000 0001 1
        * 0000 0010 2
        * 0000 0100 4
        * 0000 1000 8
        * 0001 0000 16
        * */
        
        System.out.println(2<<3); //结果是16

// 	三元运算符		x ? y :z
        //如果 x==true ,则结果为y，否则为z。
        int score = 70;
        String type = score<60 ? "不及格":"及格";
        System.out.println(type);
```

# 第三天

### 1.包机制

- 导入的包必须在这主包之下
- 导入的包尽量不能与之前的重名。

```java
package operator;
import java.util.Date;
import com.base.*;//d

//生成Doc解释文档,首先进入相对应的文件目录
//javadoc -encoding UTF-8 -charset UTF-8 w
```

### 2.用户交互Scanner

hasnext与next（）

```java
package com.kuang.scanner;

import java.util.Scanner;

public class demo01 {

    public static void main(String[] args) {
        //创建一个扫描器对象，用于接收键盘数据
        Scanner scanner = new Scanner(System.in);
        System.out.println("使用next方法接收：");

        //判断用户是否输入字符串
        if(scanner.hasNext()){
            //使用next接收
            String str = scanner.next(); //程序会等待用户输入完毕
            System.out.println("输入的内容为："+str);
        }
        //凡是属于IO流，要及时关闭
        scanner.close();

    }
    
}
//不能得到带有空格的字符串
```

hasline与nextline

```java
package com.kuang.scanner;

import java.util.Scanner;

public class demo02 {

    public static void main(String[] args) {

        //从键盘接收数据
        Scanner scanner = new Scanner(System.in);
        System.out.println("等待用户输入");
        /*if (scanner.hasNextLine()){
            String str = scanner.nextLine();
            System.out.println("输出内容："+str);
        }*/
        String str = scanner.nextLine();
        System.out.println("输出内容："+str);
        scanner.close();

    }
}
```



![image-20210927204751733](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210927204751733.png)

- 还可以判断输入的是否小数，字符，字节，浮点数等，但是必须要关闭scanner

```java
package com.kuang.scanner;

import java.util.Scanner;

public class demo03 {
    public static void main(String[] args) {
        //输入多个数字，求其总和与平均数，每输入一个数字用回车确认，通过输入非数字来结束
         Scanner scanner =new Scanner(System.in);
         double sum = 0;int m=0;
         while (scanner.hasNextDouble()){
             double x = scanner.nextDouble();
             m = m+1;
             sum = sum+x;
         }

         scanner.close();
        System.out.println("这"+m+"个数的和为"+sum+"平均值为"+(sum/m));
    }

}
```

### 3.结构

- 顺序结构，选择结构（if，else if ,else）
- switch结构与c++是一样的。字符的本质还是数字——反编译：java-class(字节码文件)——反编译（IDEA）
- while循环，do—while循环，for循环——100.for：快速生成循环
- 增强for循环——主要用于数组和集合

```java
int[] numbers={10,20,30,40,50};
        //遍历数组的元素
        for (int x:numbers){
            System.out.println(x);
        }

```

# 第四天

### 1.方法的定义

- println ——输出换行，print——不输出空格
- 调用跟c++是一样的。

```java
//必须先加入成类变量才能进行调用，加上static
    public static int add(int a,int b){
        return a+b;
    }
```

- 方法的定义和调用以及重载跟c++都是差不多的

### 2.命令行传参

- 运行之前一定要找到他的包的路径，再进行编译
- 之后在进行运行，有参数的要先传参数

### 3.可变参数

- 方法声明中在指定参数类型后加一个省略·号，
- 一个方法只能指定一个·可变参数·，且必须是方法的最后一个参数，任何普通参数在这之前都要先声明·

递归跟c++一样

### 4.数组的创建

```java
//变量类型  变量名字 = 变量的值
        //数组类型
        int sum=0;
        int[] nums; //1.声明一个数组
        nums = new int[10];//2.创建一个数组
        //3.对数组进行赋值。num.length——获取数组的长度
        for (int i = 0; i < nums.length; i++) {
            nums[i]=i;
            sum += nums[i];
        }
```

### 5.内存分析

在Java中将所有的操作压入栈中

```java
//静态初始化
        int[] a={1,2,3,5,6,6};

        //动态初始化
        int[] b = new int[10];
```

- 数组一旦被创建，大小不可改变，其元素必须是相同类型
- 数组对象本身是在堆中的

55
