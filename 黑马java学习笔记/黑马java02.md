# 第三天

### 一、_package

- 本质是文件夹，可以对类进行分类管理

![image-20211015200337514](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20211015200337514.png)

### 二、导包，权限修饰符

- 四种修饰符——private，默认，protected，public
- 在同一类中都可以访问四种修饰符，同一个包中不管是子类还是无关类都可以访问后三种
- 不同包的类中可以访问后两种，无关类只能访问public类。

#### 2.1final修饰符

final修饰：被final修饰的方法不能被重写，被final修饰的成员变量不能再被改写，被final修视则不能再次作为父类被继承。

final修饰基本变量，那该变量就成为了常量，不能被修改。

final修饰引用变量时，地址值不能改变，但是地址里面的内容是可以改变的

#### 2.2static修饰符

```java
public static String university;//类的所有对象共享这个

Student.university = "清华大学";
```

判断是否被所有对象共享，可以通过类名调用，也可以通过对象名调用，推荐类名。

访问特点：

- 静态成员方法只能访问静态成员方法，静态成员变量
- 非静态成员方法，既能访问静态又能访问非静态的方法和变量。

### 三、多态

#### 1.简介：

同一个对象在不同时刻表现出来的多种形态。

多态的继承和体现：有继承和实现关系，有方法重写，有父类的引用指向子类的对象。

多态的实现

```java
package com.itheima_04;
public class Animal {
    public void eat(){
        System.out.println("动物吃东西");
    }
}

package com.itheima_04;

public class cat extends Animal{

    @Override
    public void eat() {
        System.out.println("小猫吃东西");
    }
}

package com.itheima_04;

public class demo {

    public static void main(String[] args) {
        Animal a = new cat();
    }
}
```

- 多态中的成员方法，编译看左边，运行看右边。成员变量：编译看左边，执行看右边
- 成员方法有重写，成员变量没有

#### 2.好处与笔端

多态的使用

```Java
package com.itheima_04;

import com.itheima_04.cat;

public class Animaloperator {

    /* public void useanimal(cat c){
        c.eat();
    }
    public void useanimal(dog d){
        d.eat();
    }*/
    public void useanimal(Animal a){
        //Animal a = new cat();
        //Animal a = new dog();
        
        a.eat();
    }

}

package com.itheima_04;

public class demo {

    public static void main(String[] args) {
        cat c = new cat();
        dog d = new dog();
        Animaloperator ao = new Animaloperator();

        ao.useanimal(c); //小猫吃东西
        ao.useanimal(d); //小狗吃骨头

    }
}
```

- 多态性是不能访问子类特有的功能，好处：定义方法的时候，使用父类作为参数，将来在使用的时候，使用具体的子类型参与操作。

#### 3.多态中的转型

##### 3.1向上转型

- 将子类对象赋值给父类引用

##### 3.2向上转型

```java
Animal a =new Cat();
a.eat();
Cat c = (Cat) a;
```

#### 4.抽象类

- 一个没有方法体的方法应该定义为抽象方法，而类中如果有抽象方法，该类必须定义为抽象类。
- 抽象类和抽象方法必须使用abstract，抽象类中不一定有抽象方法，由抽象方法的类一定是抽象类
- 通过子类的对象实例化，抽象的子类要摸重写抽象类中的所有方法，要么是抽象类。
- 抽象类可以像正常的类一样

### 四、接口

##### 1.接口的定义

- 接口是一种公共的标准规范，只要符合标准，就可以通用，Java中的接口更多体现在对行为的抽象
- 关键字是interfece，继承接口类事implement

```java
package com.itheima_05;

/*
* 定义了一个接口
* */

public interface Jumping {
    public abstract void jump();

}

package com.itheima_05;

public class Cat implements Jumping {

    @Override
    public void jump() {
        System.out.println("猫科一条好");
    }
}

```

- 通过实现类对象实例化，叫做接口多态。抽象类多态，接口多态
- 多态的前提：有继承关系或实现关系，有方法重写，有父指向类对象

##### 2.接口的成员特点

在抽象类中如下：

```java
int num3 = 30;
//等价于
public static final int num3 = 30
```

- 成员变量默认修饰符：public static final
- 接口中没有构造方法，因为接口是对行为进行的抽象，是没有具体的存在。一个类如果没有父类，默认继承object类
- 成员方法：只能是抽象方法，默认修饰符：public abstract

##### 3.类与接口的关系

- 继承只能单继承，类与接口的关系实现可以是单实现也可以多实现，还可以在继承一个类的同时实现多个接口
- 接口的关系：可以单继承也可以多继承。
- 抽象类是对类的抽象，接口是对行为进行抽象

