# 第五天

### 1.数组的使用

```java
package com.kuang.array;

public class demo01 {

    public static void main(String[] args) {
        int[] arrays = {1,2,3,4,5};
//        int sum= 0;
//
//        for (int i = 0; i < arrays.length; i++) {
//            System.out.println(arrays[i]);
//        }
//        for (int i = 0; i < arrays.length; i++) {
//            sum += arrays[i];
//        }
//        for (int array : arrays) {
//            System.out.println(array);
//        }
        printarry(arrays);

    }
    //打印数组
    public static void printarry(int [] arry){
        for (int i = 0; i < arry.length; i++) {
           System.out.println(arry[i]);
        }
    }
    //数组反转

    public static int [] reverse(int[] args) {
        int[] result = new int[args.length];

        //反转操作
        for (int i = 0,j=result.length-1; i < args.length; i++,j--) {
            result[j]=args[i];
        }
        return result;

    }
}
```

### 2.二维数组的使用

```java
package com.kuang.array;

public class demo02 {
    public static void main(String[] args) {
        int[][] arry = {{1,2},{2,3},{3,5},{4,5}};
        System.out.println(arry[0]); //返回的是对象

        for (int i = 0; i < arry.length; i++) {
            for (int i1 = 0; i1 < arry[0].length; i1++) {
                System.out.println(arry[i][i1]);
            }
        }
        
    }
}

//Array的使用
package com.kuang.array;
import java.util.Arrays;
public class demo03 {
    public static void main(String[] args) {
        int[] a = {1,326,4,231,43,43,40};
       System.out.println(a);  //输出的是一个哈希 [I@7c30a502
        //用Array来实现排序
        Arrays.sort(a);
        System.out.println(Arrays.toString(a));
    }
}
```

### 3.冒泡排序

```Java
package com.kuang.array;
import java.util.Arrays;
public class demo03 {
    public static void main(String[] args) {
        int[] a = {12,4,23,53,24,16,57,34};
        int[] b = sort(a);
        System.out.println(Arrays.toString(b));
    }

    //冒泡排序
    public static int [] sort(int[] arry){
        int temp = 0;

        for (int i = 0; i < arry.length ; i++) {
            //内层循环，比较判断两个数，如果是第一个数比第二个数大，则交换位置。
            for (int j = i+1; j <arry.length; j++) {
                if (arry[i]>arry[j]){
                    temp = arry[i];
                    arry[i]=arry[j];
                    arry[j]=temp;
                }
            }
        }

        return arry;

    }
}
```

### 4.稀疏数组

稀疏矩阵的存储与还原

```Java
package com.kuang.array;

public class demo04 {

    public static void main(String[] args) {
        int[][] array1 = new int[11][11];
        array1[1][2] = 1;
        array1[2][3] = 1;
        System.out.println("输出原始的数组");

        for (int[] ints : array1) {
            for (int anInt : ints) {
                System.out.print(anInt+"\t");
            }
            System.out.println();
        }
        //转化为稀疏矩阵
        int sum = 0;
        for (int i = 0; i < 11; i++) {
            for (int i1 = 0; i1 < 11; i1++) {
                if (array1[i][i1]!=0){
                    sum++;
                }
            }
        }

        System.out.println("有效的个数为"+sum);
        int [][] array2 = new int[sum+1][3];
        array2[0][0] = 11;
        array2[0][1] = 11;
        array2[0][2] = sum;

        int count = 0;
        for (int i = 0; i < array1.length; i++) {
            for (int i1 = 0; i1 < array1[i].length ; i1++) {
                if (array1[i][i1]!=0){
                    count++;
                    array2[count][0] = i;
                    array2[count][1] = i1;
                    array2[count][2] =array1[i][i1] ;
                }
            }
        }
        for (int i = 0; i < array2.length; i++) {
            System.out.println(array2[i][0]+"\t"+array2[i][1]+"\t"+array2[i][2]);
        }

        int[][] array3 = new int[array2[0][0]][array2[0][1]];
        for (int i = 1; i < array2.length; i++) {
            array3[array2[i][0]][array2[i][1]] = array2[i][2];
        }


        for (int[] ints : array3) {
            for (int anInt : ints) {
                System.out.print(anInt+"\t");
            }
            System.out.println();
        }
    }
}

```

# 第六天

### 1.面向对象

- 三大特性：封装、继承、多态
- 方法定义：与c++基本一样

静态与非静态方法的调用

```java
package oop.demo01;

public class demo02 {

    public static void main(String[] args) {
        //静态方法调用
        student.say2();

        //非静态方法调用
        student stu = new student();
        stu.say1();

    }
}



package oop.demo01;
//学生类
public class student {
    //非静态方法
    public  void say1(){
        System.out.println("学生说话");
    }
    //静态方法
    public static void say2(){
        System.out.println("学生说话");
    }
}
```

static方法是与类一起加载的。 

非静态方法只有在类实例化之后才存在。



### 2.形参与实参的区别——引用

```java
package oop.demo01;

public class demo03 {

    public static void main(String[] args) {

        Person person = new Person();
        System.out.println(person.name);  //null

        demo03.change(person);
        System.out.println(person.name); // 秦将

    }
    public static void change (Person person){
        person.name = "秦将";
    }
}
class Person{
    String name;
}

```

### 3.类与对象的创建

- 一个项目中最好只有一个main方法，
- 在主程序中，实例化其他类，并可以进行操作

### 4.构造器

- 一个类即使什么也不写，也会存在一个方法，与类名相同，没有返回值。
- 相当于c++中的构造函数。
- alt+insert——快速构造。