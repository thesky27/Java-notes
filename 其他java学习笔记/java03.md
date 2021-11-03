# 第七天

### 1.类与对象

- 对象还是通过引用来操作的，就跟c++一样

- 对象的创建与使用：
  - 必须用new来创建对象，构造器，类包括属性和方法。

### 2.封装

- 该漏的漏，该处得出。——高内聚，低耦合。
- 属性私有——get/set，快捷键——alt+insert:快速生成get/set

```java
package oop.demo04;


//类
public class Student {

    //属性私有
    private String name; //名字
    private int id; //学号
    private char sex; //性别


    //提供一些public的get与set的方法

    //get——获取这个数据
    public String getName(){
        return this.name;
    }
    //set——得到数据
    public void setName(String name){
        this.name = name;
    }

    public int getId() {
        return id;
    }

    //快捷键——alt+insert
    public void setId(int id) {
        this.id = id;
    }

    public char getSex() {
        return sex;
    }

    public void setSex(char sex) {
        this.sex = sex;
    }
//学习（）
    //睡觉（）


}




package oop;
import oop.demo03.pet;
import oop.demo04.Student;

public class Aplication {

    public static void main(String[] args) {
        Student s1 = new Student();
        s1.setName("三个");

    }
}
```



### 3.继承

- 是对类的一种抽象，子类是对父类的扩展。
- CTRL+H——是打开关系树
- 任何类都默认继承object类。
- java中只能有一个父类，只有单继承没有多继承。
- 调用父类的构造器及其规则都与c++相同，构造器先执行父类无参构造器

super调用父类的构造方法，必须在构造方法的第一个

super和this不能同时调用构造方法

父类的引用可以指向子类。方法的调用只和左边——定义的数据类型有关

非静态方法可以重写，子类的方法必须相同，但是方法体不一定相同。

- 子类重写父类的方法，参数列表与方法名相同
- 范围可以扩大，但不能缩小。
- 抛出异常——可以被缩小，但不能扩大。
- Alt+insert: override——重写快捷键

### 4.多态

- 子类能调用的方法可以使自己或者父类的
- 父类类型只能调用自身的方法。属性没有多态。
- 父类引用指向子类对象。
- final，private，static方法不能重写。
- instanceof——判断一个对象的类型。
- 类型之间的转化由高到低直接转换，否则就会强制转换。
- 子类转化为父类，可能会丢失自己的一些方法

### 5.static方法

- 静态变量可以直接用类名访问，非静态则不能。
- 非静态方法可以调用静态方法中的东西，静态方法不能调用普通的方法、
- 代码块——分为匿名代码块和静态代码块。静态代码块只执行一次。

静态导入包，加入final之后就不能被继承了。

### 6.抽象类

- 抽象方法——只有抽象类的方法，没有方法的实现。抽象类的所有方法，继承了它的子类，都必须实现他的方法
- public abstract class action，——接口可以多继承
- 不能new这个抽象类，只能靠子类去实现他。
- 抽象类可以写普通方法，抽象方法必须写在抽象类中。

### 7.接口

- 接口的本质就是契约，约束
- 接口不能被实例化，必须重写接口中的方法

### 8.内部类

- 在一个类中再写一个类，就是内部类。通过外部泪来实例化内部类
- 一个Java类中可以有多个class类，但是只能有一个public class

### 9.异常

主要是分为两大类

- ERROR
  - 由Java虚拟机生成并抛出，大多数错误域代码执行操作无关——比如栈溢出
- EXCEPTION
  - 百分之九十是程序员的错误

```java
package exception;

public class demo01 {

    public static void main(String[] args) {

        int a = 1;
        int b = 0;
        try {
            System.out.println(a/b);
        }catch (ArithmeticException e){
            System.out.println("程序出现异常，除数不能为零");
        }finally {
            System.out.println("Finally");
        }

    }

}
```

- 逻辑思维跟c++是一样的。
- 快捷键——CTRL+Alt+t，可以主动抛出异常

```Java
try {
            System.out.println(a/b);
        } catch (Exception e) {
            e.printStackTrace();//打印错误的栈信息
        }

if (b==0){
            throw new ArithmeticException();//主动抛出异常
        }
```

假设方法中，处理不了这个异常，方法要向上抛出异常。

```Java
int a = 1;
        int b = 0;
        try {
            new demo01().test(1,0);
        } catch (ArithmeticException e) {
            e.printStackTrace();
        }
public void test(int a,int b) throws ArithmeticException{
        if (b==0){
            throw new ArithmeticException();//主动抛出异常
        }
    }
```

### 10.自定义异常



- 了解就好

```Java
package exception;

public class MyException extends Exception{

    private int detail;
    public MyException(int a){
        this.detail = a;
    }

    @Override
    public String toString() {
        return "MyException{" +
                "detail=" + detail +
                '}';
    }
}


package exception;

public class Test {

    static void test(int a) throws MyException{
        if(a>10){
            throw new MyException(a); //抛出
        }
        System.out.println("OK");
    }

    public static void main(String[] args) {
        try {
            test(1);
        } catch (MyException e) {
            System.out.println(e);
        }
    }

}

```

