[P140](https://www.bilibili.com/video/BV18J411W7cE?p=141)

# 第一天：学生管理系统

### 一、实现思路

#### 1.定义学生类

Student

成员变量：

- 学号：id
- 姓名：name
- 年龄：age
- 居住地：address

构造方法：

1. 无参构造
2. 带四个参数的构造

成员方法：

- 每个变量成员对应给出get/set方法

```java
package com.itheima;

/*
* 学生类：
* ALT + insert
* */

public class Student {
    //学号
    private String sid;

    //姓名
    private String name;

    //年龄
    private String age;

    //居住地
    private String address;

    public Student() {
    }

    public Student(String sid, String name, String age, String address) {
        this.sid = sid;
        this.name = name;
        this.age = age;
        this.address = address;
    }

    public String getSid() {
        return sid;
    }

    public void setSid(String sid) {
        this.sid = sid;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getAge() {
        return age;
    }

    public void setAge(String age) {
        this.age = age;
    }

    public String getAddress() {
        return address;
    }

    public void setAddress(String address) {
        this.address = address;
    }
}

```



#### 2.主页面的代码编写

1. 用输出语句完成主页面的编写
2. 用scanner实现键盘录入数据
3. 用switch语句完成操作选择
4. 用循环完成回到主页面

```java
package com.itheima;

import java.util.Scanner;

public class StudentManager {


    public static void main(String[] args) {

        while (true) {
            System.out.println("--------欢迎来到学生管理系统--------");
            System.out.println("1 添加学生");
            System.out.println("2 删除学生");
            System.out.println("3 修改学生");
            System.out.println("4 查看所有学生");
            System.out.println("5 退出");
            System.out.println("请输入你的选择");


            Scanner sc = new Scanner(System.in);
            String line = sc.nextLine();

            //用switch来完成语句操作
            switch (line) {
                case "1":
                    System.out.println();
                    break;
                case "2":
                    System.out.println();
                    break;
                case "3":
                    System.out.println();
                    break;
                case "4":
                    System.out.println();
                    break;
                case "5":
                    System.out.println();
                    //break;
                    System.exit(0);  //JVM退出
            }
        }
    }


}

```



#### 3.添加学生的代码编写

1. 用键盘录入选择添加学生
2. 定义一个方法,用于添加学生
3. 调用方法

```java
package com.itheima;

import java.util.ArrayList;
import java.util.Scanner;

public class StudentManager {


    public static void main(String[] args) {

        //创建集合对象，用于存储学生数据
        ArrayList<Student> array = new ArrayList<Student>();

        while (true) {
            System.out.println("--------欢迎来到学生管理系统--------");
            System.out.println("1 添加学生");
            System.out.println("2 删除学生");
            System.out.println("3 修改学生");
            System.out.println("4 查看所有学生");
            System.out.println("5 退出");
            System.out.println("请输入你的选择");


            Scanner sc = new Scanner(System.in);
            String line = sc.nextLine();

            //用switch来完成语句操作
            switch (line) {
                case "1":
                    addStudent(array);
                    break;
                case "2":
                    System.out.println();
                    break;
                case "3":
                    System.out.println();
                    break;
                case "4":
                    System.out.println();
                    break;
                case "5":
                    System.out.println();
                    //break;
                    System.exit(0);  //JVM退出
            }
        }
    }

    public static void addStudent(ArrayList<Student> array){
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入学生学号：");
        String sid = sc.nextLine();
        System.out.println("请输入学生姓名：");
        String name = sc.nextLine();
        System.out.println("请输入学生年龄：");
        String age = sc.nextLine();
        System.out.println("请输入学生居住地：");
        String address = sc.nextLine();


        Student s = new Student();
        s.setAddress(address);
        s.setAge(age);
        s.setName(name);
        s.setSid(sid);

        array.add(s);

        System.out.println("添加学生成功");


    }


}

```

p143

#### 4.查看学生的代码编写

1. 定义一个方法，用于查看学生信息
2. 调用方法，用于查看学生的信息
3. 将集合中的数据提出出来

```java
package com.itheima;

import java.util.ArrayList;
import java.util.Scanner;

public class StudentManager {


    public static void main(String[] args) {

        //创建集合对象，用于存储学生数据
        ArrayList<Student> array = new ArrayList<Student>();

        while (true) {
            System.out.println("--------欢迎来到学生管理系统--------");
            System.out.println("1 添加学生");
            System.out.println("2 删除学生");
            System.out.println("3 修改学生");
            System.out.println("4 查看所有学生");
            System.out.println("5 退出");
            System.out.println("请输入你的选择");


            Scanner sc = new Scanner(System.in);
            String line = sc.nextLine();

            //用switch来完成语句操作
            switch (line) {
                case "1":
                    addStudent(array);
                    break;
                case "2":
                    findAllStudent(array);
                    break;
                case "3":
                    System.out.println();
                    break;
                case "4":
                    System.out.println();
                    break;
                case "5":
                    System.out.println();
                    //break;
                    System.exit(0);  //JVM退出
            }
        }
    }

    public static void addStudent(ArrayList<Student> array){
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入学生学号：");
        String sid = sc.nextLine();
        System.out.println("请输入学生姓名：");
        String name = sc.nextLine();
        System.out.println("请输入学生年龄：");
        String age = sc.nextLine();
        System.out.println("请输入学生居住地：");
        String address = sc.nextLine();


        Student s = new Student();
        s.setAddress(address);
        s.setAge(age);
        s.setName(name);
        s.setSid(sid);
        array.add(s);

        System.out.println("添加学生成功");


    }

    public static void findAllStudent(ArrayList<Student> array){
        

        System.out.println("学号\t\t\t姓名\t\t年龄\t\t居住地");
        for (int i = 0; i < array.size(); i++) {
            Student s = array.get(i);
            System.out.println(s.getSid()+"\t"+s.getName()+"\t"+s.getAge()+"\t"+s.getAddress());
        }

    }

}
```



#### 5.查看学生的代码编写升级版

1. 定义一个方法，用于查看学生的信息
2. 如果没有数据，则提示添加数据

在findallstudent方法中加入这个

```java
if (array.size()==0){
            System.out.println("无信息，请先添加信息再进行查询");
            //为了让程序不再往下执行
            return;
        }
```



#### 6.删除学生的代码编写

1. 显示提示信息，键盘录入要删除的学生学号。
2. 遍历找到，并删除。

```java
//删除x函数的方法
public static void deleteStudent(ArrayList<Student> array){
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入你要删除的学生学号");
        String sid = sc.nextLine();
        for (int i = 0; i < array.size(); i++) {
            Student s = array.get(i);
            if (s.getSid().equals(sid)){
                array.remove(i);
                break;
            }
        }



    }
```



#### 7.修改学生的代码编写

```java
public static void updateStudent(ArrayList<Student> array){

        Scanner sc = new Scanner(System.in);

        System.out.println("请输入你要修改学生的学号");

        String sid = sc.nextLine();

        System.out.println("请输入学生新姓名");
        String name = sc.nextLine();
        System.out.println("请输入学生新年龄");
        String age = sc.nextLine();
        System.out.println("请输入学生新地址");
        String address = sc.nextLine();

        Student s = new Student();
        s.setName(name);
        s.setAge(age);
        s.setAddress(address);
        for (int i = 0; i < array.size(); i++) {
            Student student = array.get(i);
            if (student.getSid().equals(sid)){
                array.set(i,s);
            }
        }
        
        System.out.println("学生修改成功");
    }
```

#### 8.学号不唯一或不存在的问题

- 在删除或修改学生前，对学号是否存在进行判断。
- 存在则执行，不存在则提示修改或删除信息。

删除方法：

```java
public static void deleteStudent(ArrayList<Student> array){
        int index = -1;
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入你要删除的学生学号");
        String sid = sc.nextLine();
        for (int i = 0; i < array.size(); i++) {
            Student s = array.get(i);
            if (s.getSid().equals(sid)){
                index = i;
                break;
            }
        }
        if (index==-1){
            System.out.println("该学生不存在，请重新输入");
        }
        else {
            array.remove(index);
            System.out.println("删除学生信息成功");
        }

    }
```

修改方法：

```java
public static void updateStudent(ArrayList<Student> array){

        int index = -1;
        Scanner sc = new Scanner(System.in);

        System.out.println("请输入你要修改学生的学号");

        String sid = sc.nextLine();

        for (int i = 0; i < array.size(); i++) {
            Student s = array.get(i);
            if (s.getSid().equals(sid)){
                index = i;
                break;
            }
        }
        if (index==-1){
            System.out.println("该学生不存咋，请重新输入信息");
        }
        else {
            System.out.println("请输入学生新姓名");
            String name = sc.nextLine();
            System.out.println("请输入学生新年龄");
            String age = sc.nextLine();
            System.out.println("请输入学生新地址");
            String address = sc.nextLine();

            Student s = new Student();
            s.setName(name);
            s.setAge(age);
            s.setAddress(address);
            array.set(index,s);
            System.out.println("学生修改成功");
        }
}   
```

#### 9.学生学号重复问题

判断是否重复的真假方法

```java
public static boolean isUsed(ArrayList<Student> array, String sid){
        boolean flag = false;
        for (int i = 0; i < array.size(); i++) {
            Student s = new Student();
            if (s.getSid().equals(sid)){
                flag  = true;
                break;
            }
        }
        return flag;

    }
```

# 二、第二天继承

### 一、继承概述

- 格式：public class 子类名 extends 父类名{}
- 子类可以有父类的内容，子类有自己特有的内容
- 提高了代码的复用性，提高了代码的维护用
- 削弱了子类的独立性，不能滥用继承

Fu函数：

```java
package com.itheima_01;

public class Fu {
    public int age = 40;

    public void show(){
        System.out.println("show方法被调用");
    }

}

```

Zi函数

```java
package com.itheima_01;

public class Zi extends Fu {
    public int height = 175;

    public void show(){

        System.out.println(age);
        System.out.println(height);
    }
    public void method(){
        System.out.println("method方法被调用");
    }
}

```

```java
//demo函数

package com.itheima_01;
/*
* 测试类
* */

public class Demo {

    public static void main(String[] args) {
        Fu f = new Fu();
        f.show();

        Zi z = new Zi();
        z.method();
        z.show();
    }
}

```



#### 1.继承特点

- 在类中使用成员变量，使用变量先在本方法中找，如果没有则去找类中，在之后找其父类
- 首先在子类范围中，然后是子类成员，再者就是父类的成员范围中找。

```java
package com.itheima_01;

public class Zi extends Fu {
    public int height = 175;
    public int age = 20;

    public void show(){
        int age = 30;

        System.out.println(age);
        System.out.println(height);

        //this指向的是成员变量
        System.out.println(this.age);
        //访问的是本类中的父类成员变量
        System.out.println(super.age);
    }
    public void method(){
        System.out.println("method方法被调用");
    }
}

```

- super()——访问父类的构造方法，this()——访问的是子类的构造方法，
- this.成员方法——访问本类中的成员方法，super同理

#### 2.构造方法的访问特点，成员访问特点，方法重写

- 子类中的所有构造方法都会访问父类中的无参构造方法。
- 父类无无参构造方法，可以指定父类的构造方法。显式调用构造方法，或者自己提供一个无参构造方法
- 通过子类对象访问一个方法，现在子类范围中找，在父类成员范围中找。
- 子类不可能去重写父类中的私有方法，子类中的访问权限不能比父类中低，（public>默认>private）
- 不能一下继承多个类，但是支持多层继承

#### 3.示例

person类

```java
package com.itheima_03;

public class Person {
    private String name;
    private int age;

    public Person() {
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}

```

student类

```Java
package com.itheima_03;

public class Teacher extends Person {

    public Teacher(){

    }

    public Teacher(String name, int age) {
        super(name, age);
    }

    public void teach(){
        System.out.println("成就每一位学员");
    }
}

```

测试类

```java
package com.itheima_03;

public class Demo {

    public static void main(String[] args) {
        Teacher t1 = new Teacher();
        t1.setName("林青霞");
        t1.setAge(30);
        System.out.println(t1.getName() + "," + t1.getAge());
        t1.teach();

        Teacher t2 = new Teacher("风清扬",33);
        System.out.println(t2.getName() + "," + t2.getAge());
        t2.teach();

    }
}

```

