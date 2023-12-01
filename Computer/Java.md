 # 1_Java概述
***Java的特点***
1) OOP，面向对象编程。
2) 健壮性，拥有强类型机制、异常处理、垃圾自动收集等。
3) 跨平台性（针对字节码），一个编译后的class文件可以在多系统下运行。
4) 解释型语言，指被编译后的代码（即.class）不能直接被机器执行，需要解释器（JVM）来执行。跟它相反的是编译型语言，指编译后的代码可以直接被机器执行，例C/C++。

***运行原理***
![[Pasted image 20230321212811.png]]

**核心机制-JVM虚拟机：**.class文件会在JVM(Java virtual machine)虚拟机中执行生成结果，里面包含了指令集，负责执行指令、管理数据、内存、寄存器，在JDK中。
注：不同平台有各自专门的JVM，这也是为什么class文件可以跨平台执行，即屏蔽了运行平台的差异

***JDK和JRE***
1）JDK(Java Development Kit) Java开发工具包
包含JAVA开发工具和JRE
2）JRE(Java Runtime Environment) Java运行环境
包含JVM和JAVA核心类库，若只用运行JAVA.class，只用安装JRE

***配置环境变量***
Q：为什么要配置环境变量？
A：当想在Windows的DOS窗口中输入javac编译时，PC在当前目录和环境变量中没有发现javac.exe就不会执行、报错。
配置环境变量：
我的电脑->属性->高级系统设置->环境变量
![[Pasted image 20230321214112.png]]
1. 在系统变量或用户变量新建JAVA_HOME变量，值指向JDK文件夹
2. 在path中新建一个环境变量%JAVA_HOME%\\bin，即指向JDK中的bin(里面存放javac等编译器)，电脑就可以找到编译
![[Pasted image 20230321214120.png]]

***Java最简单的程序***
```java
public class Test{
  public static void main(String[ ] args){
     System.out.println("Hello,world!");
}
}
```
**注意**：**文件名需要与public class 的类名一致，即Test.java**
代码写好后，在DOS编译运行
转到存放.java的文件夹下
然后javac编译，代码无误就产生一个.class的文件
![[Pasted image 20230321214236.png]]
![[Pasted image 20230321214241.png]]
编译：java  类名    不用加 .class

**注意**：
1）程序中有中文时，文件编码应换成GBK，因为DOS窗口按GBK输出，否则会乱码
2）public class**公共类只能有一个**，且**文件名必须与公共类名相同**
3）Java语言**严格区分大小写**，不能混用
4）一个文件只有一个.java源文件，javac编译后所有类产生.class文件

 ***注释***
1）单行注释`//`
2）多行注释`/*  */`
3）文档注释`/**  */` 放在代码最前面，说明该文件的信息
![[Pasted image 20230322233214.png]]

注释内容可以被JDK提供的javadoc解析，生成一套以文档形式的说明文档
DOS中输入： javadoc   -d  文件夹名(绝对路径)  -author -xxx  Test.java

# 2_标识符、变量、数据类型、编码、进制
## 1.标识符
***定义合法标识符规则【重点】***
-   由 英文字母，0-9，_ 或$ 组成
-   **数字不可以开头**  (如果数字开头，编译器无法辨别这是数字还是标识符)
-   标识符不能包含空格。
-   不可以使用关键字和保留字，但能包含关键字和保留字。
-   Java 中严格区分大小写，长度无限制。

 ***Java 中的名称命名规范***
 Java 中的名称命名规范：除了包名和常量, 其他起名要遵循驼峰法
-   包名：多单词组成时所有字母都小写：xxxyyyzzz
-   类名、接口名：多单词组成时，所有单词的首字母大写： XxxYyyZzz
-   变量名、方法名：多单词组成时，第一个单词首字母小写，第二个单词开始每个单词首字母大写：xxxYyyZzz
-   常量名：所有字母都大写。多单词时每个单词用下划线连接：XXX_YYY_ZZZ

## 2.变量
***使用变量注意***
-   Java 中每个变量必须先声明，后使用；
-   使用变量名来访问这块区域的数据；
-   变量的作用域：其定义所在的一对{ }内；
-   变量只有在其作用域内才有效；
-   同一个作用域内，不能定义重名的变量；

***变量的分类-按声明的位置的不同***
- 在方法体外，类体内声明的变量称为成员变量。
- 在方法体内部声明的变量称为局部变量。
- 局部变量必须要赋初始值,否则输出会报错（**局部变量不会赋默认值**）
![[Pasted image 20230321214637.png]]
## 3.+号的使用
1）当左右两遍都是数值时，加法运算
System.out.println(100+98);  //198
2）当左右两边有一边为字符串，拼接运算
System.out.println("100"+98);  //10098
3）运算顺序：从左到右
System.out.println(100+3+"9");  //1039
System.out.println(100+"9"+3);  //10093

## 4.数据类型

![[Pasted image 20230322233225.png]]


1. ***整型***
![[Pasted image 20230321214724.png]]

**注意**：
1）各类型有**固定的的范围和字节长度**，不受OS的影响，保证了Java的可移植性
2）**整数默认为int型**，若要定义long，则要在后面加l或L(不用必须加)`long a = 1L`

2. ***浮点型***
![[Pasted image 20230321214752.png]]
**注意**：
1）浮点数在PC中存放形式：浮点数=符号位+指数位+尾数位
2）**尾数可能丢失**，造成精度损失（无限近似这个小数）
3）**浮点数默认为double型，在定义float时，必须要在浮点数后加f或F**
4）两种形式：
-   十进制：5.12     .521(其实是0.512,0可以省略)
-   科学计数法：5.12e2(5.12* 10的2次方)     5.12e-2(5.12/10的2次方)
5）通常使用double，因为比float精度更大，而且不用加f
6）浮点数在运算后得出的数值不精确
System.out.println(8.1/3);  //2.69999999990 结果不是整数2.7，因为PC不知道8.1后有没有小数
所以浮点数运算只用判断相差是否足够小即可

![[Pasted image 20230321214835.png]]
![[Pasted image 20230321214838.png]]

3. ***字符型char***
char占**2字节**，可以存放汉字
![[Pasted image 20230321214855.png]]
**注意**：
1）字符包括：用**单引号'  '括起**的单个字符或转义字符
2）char本质是一个整数，在Unicode中输出对应的字符
3）char赋个整数，会输出对应字符
4）char类型可以进行运算，相当于一个整数
5）Unicode值来表示字符型常量：‘\uXXXX’。XXXX代表一个十六进制整数。如：\u000a 表示\n。

4. ***布尔型boolean***
1）boolean占**1个字节**
2）boolean**只能赋true或false，不能赋常数值**
3）java不能自动将常数转换成布尔值，要不就用运算符 == 来得出是不是

## 5.基本数据类型转换

1. ***自动类型转换***
![[Pasted image 20230321215003.png]]
**注意**：
1）多种类型数据混合运算时，PC先把所有数据转**换成字节最大**的类型，然后计算
2）当把字节大的数据类型赋给字节小的时会报错
3）**byte、short和char不能转换**
4）byte、short、char能直接计算，**在计算前转换成int类型**
5）**boolean不参加转换**

2. ***强制类型转换***
- 自动类型转换的逆过程，将容量大的数据类型转换为容量小的数据类型。 使用时要加上强制转换符：()，但可能造成精度降低或溢出,格外要注意。
-  通常，字符串不能直接转换为基本类型，但通过基本类型对应的包装类则可以实现把字符串转换成基本类型。
- 如：String a = “43”; inti= Integer.parseInt(a);
- boolean类型不可以转换为其它的数据类型。

## 6.编码
1.  ***ASCII 码***
-   在计算机内部，所有数据都使用二进制表示。每一个二进制位（bit）有0 和1 两种状态，因此8个二进制位就可以组合出256 种状态，这被称为一个字节（byte）。一个字节一共可以用来表示256 种不同的状态，每一个状态对应一个符号，就是256 个符号，从0000000 到11111111。
-    ASCII码：上个世纪60年代，美国制定了一套字符编码，对英语字符与二进制位之间的关系，做了统一规定。这被称为ASCII码。ASCII码一共规定了128个字符的编码，比如空格“SPACE”是32（二进制00100000），大写的字母A是65（二进制01000001）。这128个符号（包括32个不能打印出来的控制符号），只占用了一个字节的后面7位，最前面的1位统一规定为0。
-    缺点：
	-   不能表示所有字符。
	-   相同的编码表示的字符不一样：比如，130在法语编码中代表了é，在希伯来语编码中却代表了字母Gimel(ג)。

 2. ***Unicode 编码***
    乱码：世界上存在着多种编码方式，同一个二进制数字可以被解释成不同的符号。因此，要想打开一个文本文件，就必须知道它的编码方式，否则用错误的编码方式解读，就会出现乱码。
-       Unicode的好处：一种编码，将世界上所有的符号都纳入其中。每一个符号都给予一个独一无二的编码，使用Unicode没有乱码的问题。
-       Unicode的缺点：一个英文字母和一个汉字都占用2个字节，这对于存储空间来说是浪费。

3. ***UTF-8***
-       UTF-8 是在互联网上使用最广的一种Unicode 的实现方式。
-       UTF-8是一种变长的编码方式。它可以使用1-6个字节表示一个符号，根据不同的符号而变化字节长度。
-       使用大小可变的编码字母占1个字节，汉字占3个字节
## 7.进制
1. ***进制与进制间的转换***
    关于进制
-   所有数字在计算机底层都以二进制形式存在。
-   对于整数，有四种表示方式：
-    二进制(binary)：0,1 ，以0b或0B开头。
-   十进制(decimal)：0-9 ，
-    八进制(octal)：0-7 ， 以数字0开头表示。
-   十六进制(hex)：0-9及A-F，以0x或0X开头表示。此处的A-F不区分大小写如：0x21AF +1= 0X21B0

![[Pasted image 20230321215338.png]]
![[Pasted image 20230321215342.png]]

2. ***十进制转其他进制***
只用拿进制数无限除十进制数即可
十进制：9  - >  二进制：1001
![[Pasted image 20230321215442.jpg]]

十进制：796   - >  八进制：1434

![[Pasted image 20230321215454.jpg]]

十进制：796   - >  十六进制：31c

![[Pasted image 20230321215502.jpg]]

-   注意：取余数和起来是从下到上

3. ***其他进制转十进制***

其他进制从0次幂开始乘

![[Pasted image 20230321215524.jpg|575]]

4. ***其他进制转二进制***

八进制  -  >   二进制

将八进制数的每一位转换成对应的3位二进制数

02(010)3(011)7(111)  - >ob10011111

十六进制  -  >   二进制

0x2(0010)3(0011)B(1011) - >0b001000111011

5. ***二进制转其他进制***
二进制  -  >   八进制

从低位开始，将二进制每3位一组转换成八进制数

ob11(3)010(2)101(5)  -  >325

二进制  -  >   十六进制

从低位开始，将二进制每4位一组转换成八进制数

ob1101(D)0101(5)  - >0xD5

6. ***二进制***
文章: 进制、原码 反码 补码、移位操作

-   Java整数常量默认是int类型，当用二进制定义整数时，其第32位是符号位；当是long类型时，二进制默认占64位，第64位是符号位
-   二进制的整数有如下三种形式：
-   原码：直接将一个数值换成二进制数。最高位是符号位
-   负数的反码：是对原码按位取反，只是最高位（符号位）确定为1。
-   负数的补码：其反码加1。计算机以二进制补码的形式保存所有的整数。

正数的原码、反码、补码都相同，负数的补码是其反码+1

为什么要使用原码、反码、补码表示形式呢？

计算机辨别“符号位”显然会让计算机的基础电路设计变得十分复杂! 于是人们想出了将符号位也参与运算的方法. 我们知道, 根据运算法则减去一个正数等于加上一个负数, 即: 1-1 = 1 + (-1) = 0 , 所以机器可以只有加法而没有减法, 这样计算机运算的设计就更简单了。

-   对于正数来讲：原码、反码、补码是相同的：三码合一。
-   计算机底层都是使用二进制表示的数值。

计算机底层都是使用的数值的补码保存数据的

## 8.用户输入
在java.util包中有Scanner类，用来接收输入。Scanner是一个简单文本扫描器
![[Pasted image 20230321215705.png]]

![[Pasted image 20230321215729.png]]

输入带空格的字符串，scanner.nextLine();

# 3_运算符
1. ***算术运算符***
   算术运算符的注意问题
-       如果对负数取模，可以把模数负号忽略不记，如：5%-2=1。但被模数是负数则不可忽略 -5%2=-1。此外，取模运算的结果不一定总是整数。
-       对于除号“/”，它的整数除和小数除是有区别的：整数之间做除法时，只保留整数部分而舍弃小数部分。例如：intx=3510;x=x/1000 * 1000; x的结果是？
-       “+”处理。
        支持连续赋值。
    扩展赋值运算符：+=, -=, * =, /=, %=

2. ***比较运算符***
![[Pasted image 20230321220050.png]]
   比较运算符的**结果都是boolean型**，也就是要么是true，要么是false。

3. ***逻辑运算符***
-   &—逻辑与
-   | —逻辑或
-   ！—逻辑非
-   && —短路与
-   || —短路或
-   ^ —逻辑异或

![[Pasted image 20230321220207.png]]

- 逻辑运算符用于连接布尔型表达式，在Java中不可以写成3<x<6，应该写成x>3 & x<6
- “&”和“&&”的区别：
	- 单&时，**左边无论真假，右边都进行运算**；
	- 双&时，如果左边为真，右边参与运算，如果左边为假，那么右边不参与运算。
- “|”和“||”的区别同理，||表示：当左边为真，右边不参与运算。
- 异或(^)与或( | )的不同之处是：当左右都为true时，结果为false。理解：异或，追求的是“异”!

4. ***位运算符***
   位运算是直接对整数的二进制进行的运算
-   << : 在一定范围内，每向左移一位，相当于 * 2
-   >> : 在一定范围内，每向右移一位，相当于 / 2
![[Pasted image 20230321220304.png]]

5. ***运算符的优先级***
   运算符有不同的优先级，所谓优先级就是表达式运算中的运算顺序。如右表，上一行运算符总优先于下一行。
          只有单目运算符、三元运算符、赋值运算符是从右向左运算的。
      ![[Pasted image 20230321220318.png|450]]

# 4_流程控制
注释：流程控制与c的结构都是一样的，只划出重点和区别

1. ***switch-case***
-   注意： switch结构中的表达式，只能是如下的六种数据类型之一：byte、short、char、int、枚举类型(JDK5.0)、String类型(JDK7.0)
-   不能是：long，float，double，boolean。

2. ***continue 语句***
-   continue只能使用在循环结构中
-   continue语句用于跳过其所在循环语句块的一次执行，继续下一次循环
-   continue语句出现在多层嵌套的循环语句体中时，可以通过标签指明要跳过的是哪一层循环

3. ***特殊流程控制语句说明***
-   break只能用于switch语句和循环语句中。
-   continue 只能用于循环语句中。
-   二者功能类似，但continue是终止本次循环，break是终止本层循环。
-   break、continue之后不能有其他的语句，因为程序永远不会执行其后的语句。
-   标号语句必须紧接在循环的头部。标号语句不能用在非循环语句的前面。
-   很多语言都有goto语句，goto语句可以随意将控制转移到程序中的任意一条语句上，然后执行它。但使程序容易出错。Java中的break和continue是不同于goto的。

# 5_数组
## 1.一维数组
定义一维数组：
![[Pasted image 20230410222443.png]]
```java
int[] a = {1,2,3};//直接赋值
int[] b = new int[3];//创建3个
int[] c = new int[]{1,2,3};
```
**注意**：
- 数组如果没有初始化，**系统会自动赋值**：整型：0，浮点：0.0，char：\\0000，boolean：false，String：null
- 数组属于**引用**，数组型数据是对象
- 直接赋值{1,2,3}只能在定义同时赋值，不能 c = {1,2,3}这样，因为c是个指针变量，里面存放的是地址

***数组赋值机制***
数组在默认情况下是引用传递，传的是地址
![[Pasted image 20230410221722.png]]

![[Pasted image 20230410222431.png]]
- 栈：存放局部变量  堆：存放new出来的值
- 数组里存放的是地址，调用的时候会指向堆里的数据
- 数组的相互赋值，赋的是地址，不会开辟新的存储空间。与cpp不同，cpp只能给数组赋值

***数组拷贝***
new一个后，遍历赋值
![[Pasted image 20230410222419.png]]

***数组反转***
![[Pasted image 20230410222226.png]]
-   把a\[0]和a\[8]进行交换{9,2,3,4,5,6,7,8,1}
-   然后依次n与8-n进行交换
-   一共要交换a.length/2次，即4次
-   每次交换时，对应的下标a\[i] 和a\[a.length -1 -i ]
![[Pasted image 20230410222244.png]]
最后a1指向a2的数据空间
原来的a1数据空间就没有变量引用，就会被当做垃圾销毁

***数组扩容***
直接新建一个更大的数组，然后原数组指向新数组
![[Pasted image 20230410222304.png]]

## 2.二维数组
![[Pasted image 20230410222327.png]]
![[Pasted image 20230410222344.png]]

![[Pasted image 20230410222354.png]]
注意：二维数组实际是由多个一维数组组成的，各个一维数组长度可以相同也可以不同

## 4.array工具类的使用


## 5.数组使用中常见异常


# 6_OOP  基础
## 1.类和对象
类：抽象的，代表一类事物。一种自建的数据类型
对象：具体的，是类中的一个实例。包含属性和行为
属性： 对象里面的变量。格式：访问修饰符  属性类型 属性名
**注意**：属性如果不赋值，会跟数组规则一样默认赋值

![[Pasted image 20230321224426.png]]

***对象分配机制***

![[Pasted image 20230321224433.png]]

***java内存的结构分析***
栈：一般存放基本数据类型（局部变量）
堆：存放new出来的对象（Student  s ， 数组等）
方法区：常量池（常量，比如字符串），类加载信息
```java
Student s /*在栈中声明一个对象s，但实际没有在内存中创建对象*/= new Student()/*在堆中创建一个新的类，对象s指向这个类*/;
 s.name = "Xia Lang";//将属性赋给堆中那个对象的属性
```

***java创建对象的流程***
先加载类信息（属性和方法信息，只加载一次）
在堆中分配空间，进行默认初始化
把地址赋给s，s就指向对象（所以也可以相互指向）

## 2.方法
本质就是函数，但Java中函数叫做方法
![[Pasted image 20230322233013.png]]

***方法调用原理***
![[Pasted image 20230322233017.png]]

- 基本数据类型的形参是值拷贝，不改变实际值。引用类型的形参是地址传递，可以改变实参值。
- 如果要传入基本数据类型并改变实参值，方法的返回值赋给这个变量。

![[Pasted image 20230322233022.png]]

克隆对象（用方法）
![[Pasted image 20230322233026.png]]

main方法以及类的解析：
一个程序可以没有公共类，但程序的整体模块是以类为代表的
一个类中至多有一个main方法（即主方法），程序首先进入主方法，通过方法体内的代码调用其他方法、变量、属性
一个程序中，进入了一个类的主方法后就不会再进入其他类的主方法

### 2.1.方法重载(overload)
同一个类中，多个方法的**方法名相同**，但**形参列表不同**(形参的数量、类型)
好处：减轻了起名、记名的不必要性
注意：返回类型与重载无关
```java
class Test{  
    void Print(int age){   //第一个方法
        System.out.println(age);  
    }  
    void Print(int age,String name ){  //第二个方法，方法名相同，参数列表不同
        System.out.println(age+","+name);  
    }  
    public static void main(String[]args){  
         Test t1 = new Test();  
         t1.Print(18);  
         t1.Print(18,"xia");  
    }  
}
```


### 2.2.可变参数
可以将一个类中多个同名但参数列表个数不同的方法，封装成一个方法
`访问修饰符  返回值  方法名  （数据类型...  形参名）`
```java
class Test{  
    void Print(int... name){  //int... 表示接收的是可变参数，类型是int且可接收多个
        for(int i = 0 ; i < name.length ; i++)  
    System.out.print(name[i]);  
    }  
    public static void main(String[] args) {  
    Test t = new Test();  
    t.Print(1,2,3,4);  
    }  
}
out:1234
```
**注意**：
		**本质就是数组**，把可变参数当数组使用
		可变参数和普通参数可以同时使用，**可变参数放在最后**
		形参列表**最多出现一个可变参数**


### 2.3.作用域
变量主要分为属性和局部变量（属性之外的变量）
- 属性的作用域在整个类中。属性不赋值有默认值，可以直接使用
- 局部变量的作用域在定义的代码块中。局部变量必须赋值后使用
**注意**：属性和局部变量可以重名，遵循**就近原则**
- 存在范围不同：
	- 属性伴随对象的创建和销毁存在，而局部变量随代码块存在
- 作用域范围不同：
	- 属性在本类和其他类中都可以使用
	- 局部变量只能在本类中使用
- 修饰符不同：
	- 属性可以加修饰符，局部变量不行


### 2.4.构造器（ 构造函数）
完成**对象初始化**，在创建对象时直接给属性赋值
`修饰符  类名（参数列表）`{
方法体
}
```java
class Test{  
  String name;  
  int age;  
  public Test(String name,int age){  //构造器，方法名与类名一致
      this.name = name;//this表示这个对象的  
      this.age = age;  
  }  
    public static void main(String[] args) {  
        Test t = new Test("xia",19);  
    }  
}
```
- 构造器的**修饰符可以默认**
- **没有返回值**
- **方法名必须和类一样**
- **参数列表和方法的形参列表一致**
- 构造器的**调用由系统完成**

**注意**：
			一个类可以有多个构造器，参数列表必须不同，即构造器重载
		    如果没有定义构造器，系统会自动生成一个默认构造器 （  new  Person（）有个括号的原因   ）
```java
class Test{  
    int age;  
    String name;  
    public Test(int age){  
        this.age = age;  
        System.out.println("age = " +age  );  
    }  
    public Test(int age,String name){  
        this.age = age;  
        this.name = name;  
        System.out.println("age = " +age + "," + "name = " +name );  
    }  
    public static void main(String[]args){  
         Test t1 = new Test(3);  
         Test t2 = new Test(3,"xia");  
    }  
}
out:
	age = 3
	age = 3,name = xia
```


### 2.5.this关键字
java虚拟机会给每个**对象**分配一个**this代表当前对象**
```java
Public Person(String name,int age)//构造器
{
	this.name = name;//this.代表当前'对象'的属性
	this.age = age;
}
```

**注意**：
		this关键字可以用来访问本类的属性成员、方法、构造器
		this可以区分当前类的属性和局部变量
		访问方法：**this.方法名(参数列表)**
		访问构造器：**this(参数列表)**，**只能在构造器中访问另一个构造器，且必须放在第一条语句**（this调用另一个构造器）
		this**只能在类定义中使用**，不能在外部

```java
class Test{    //构造器调用this
  String name;  
  int age;  
  public Test(String name,int age){  
      this.name = name;  
      this.age = age;  
  }  
  public Test(){  
      this("jack",19);  
  }  
    public static void main(String[] args) {  
	    Test t = new Test("xia",18);  /*第一种初始化*/
	    Test t = new Test();          /*第二种初始化*/ 
	    System.out.println(t.name +","+ t.age);  
    }  
}
out: 
/*第一种初始化*/  xia,18
/*第二种初始化*/  jack,19
```


# 7_OOP  中级
## 包
***包的三大作用***
1. 区分相同名字的类
2. 当类很多时，可以很好的管理类
3. 控制访问范围

***基本语法***
`package  包名`

***包的本质***
实际就是创建不同的文件夹/目录来保存类文件

![[Pasted image 20230329202102.png]]

***包的命名***
- 命名规则
	- 只能包含数字、字母、下划线、圆点，不能数字开头
	- demo.class.12a错误：  class关键字，12a数字开头
- 命名规范
	- 小写字母+小圆点
	- 一般是：com.公司名.项目名.业务模块名（例如：com.sina.crm.user）

***常用的包***
- java.lang.*     基本包，**默认引入**，不需要自己引入
- java.util.*       系统提供的工具包
- java.net.*       网络包，用于网络开发
- java.awt.*      用于java界面开发GUI

***如何引入包***
`import  包`   import java.util.Scanner   （区分：包是全是小写字母，类是大写开头）
. * 表示引入包下的所有类（建议只引入需要用的类）

**注意**：
		package的作用是声明当前类所在的包，需要放在类的最上面，一个类最多只有一句package
		import放在package下面，在类的前面

## 访问修饰符
用于控制方法和属性的访问权限
- public，对**所有**公开。
- protected，不同包的子类和同包的类。
- 默认 ，前面无符号，只有同包的类。
- private  只有**本类**可以访问。
![[Pasted image 20230329203258.png]]

**注意**：
		修饰符可以修饰类中的属性、方法及类
		只有默认和public才能修饰类

```java
pacakage com
public class Test {  
    int Default ;  
    protected int Protected;  
    public int Public;  
    private int Private;  
  
    public static void main(String[] args) {  
        Test test = new Test();  
        //同类下可以访问所有属性方法
        System.out.println(test.Public);  
        System.out.println(test.Default);  
        System.out.println(test.Private);  
        System.out.println(test.Protected);  
    }  
}
public class In extends Test {  
    public static void main(String[] args) {  
        Test test = new Test();  
        In in = new In();  
        // new父类不能访问protected，即使继承了
        System.out.println(test.Public);  //pakage com.1 在不同包下和同包下
        System.out.println(test.Protected);  //pakage com  在同包下可以使用
		System.out.println(test.Default);    //pakage com  在同包下可以使用
        // 可以通过new子类访问public和protected（在不同包下
        System.out.println(in.Protected);  //package com.1
        System.out.println(in.Public);  
        // 同一个包下，可以访问default  
        System.out.println(in.Default);   //pakage com 在同包下 
        //super调用都是可以直接访问父类的对象，不用new
        super.Public;
        super.Protected;
        super.Default;
    }  
}
```

## OOP三大特征
### 封装
封装就是把属性和方法封装在一起，数据被保护在内部，程序的其他部分只有通过被授权的方法才能对数据进行操作
好处：可以对数据进行验证，保证安全合理
实现步骤：
1. 将属性进行私有化private（使不能直接修改属性）
2. 提供一个public set方法，用于对属性判断并赋值
```java
public void setXxx(数据类型 参数名){
	//验证数据的合理性
	属性 = 参数名;
}
```
3. 提供一个public get方法，用于获取属性的值
```java
public 数据类型 getXxx(){
	return 数据;
}
```

封装演示
```java
package test;  
 class Person {  
     public String name;  
     private int age;  //  “private”实现对属性的保护管理
     private double salary;  
       
     //构造器中判断赋值是否合理  
     public Person(String name, int age, double salary) {  
         setName(name);  
         setAge(age);  
         setSalary(salary);  
     }  
     //给（私有）属性赋值  
     public void setName(String name) {  
         this.name = name;  
     }  
     public void setAge(int age) {  
         if(age >= 18 && age <= 60)//判断传入的值是否合理  
         this.age = age;  
         else  {
         System.out.print("输入的数字错误，给予默认值");
         this.age = 18;  
         }
     }  
     public void setSalary(double salary) {  
         this.salary = salary;  
     }  
     //传出属性的值  
     public int getAge() {  
         return age;  
     }  
     public double getSalary() {  
         return salary;  
     }  
 }
```

### 继承
继承能提高代码复用性，当多个类中存在相同的属性和方法时，可以总结出拥有相同属性和方法的父类。子类不用再定义父类中的内容，只需要继承父类即可。
![[Pasted image 20230406205759.png]]

基本语法
```java
class 子类 extends 父类{
}
```

注意：
1. 子类继承了所有的属性与方法，非私有的属性和方法可以在子类直接访问，但**私有属性和方法不能直接访问**，要通过父类提供的公共方法去访问
2. **子类必须调用父类的构造器，完成父类的初始化**
3. 当子类创建对象时，不管使用子类的哪个构造器，**默认下总会去调用父类的无参构造器**。如果父类没有提供无参构造器（就是父类有已经定义的有参构造器），则必须**在子类的构造器中用super去指定使用父类的哪个构造器**完成对父类的初始化，否则编译出错
4. 如果希望调用指定父类的某个构造器，需要显式的调用 super（参数列表）
5. super在使用时，必须放在构造器第一行。this()也只能放在第一行，所以**两个方法不能共存在同一个构造器里**
6. **java中所有类都是Object的子**类  ，将一直往上追溯直到Object类
7. 子类最多能继承一个父类，如果在想让A类同时有B类和C类的属性方法，可以让B类先继承C类，然后A类继承B类

```java
//1:私有属性的访问
private score;
public float getScore() { //得到私有值  
    return score;  //返回值
}  
public void setScore(float score) { //输入私有值  
    this.score = score;  //输入值
}

//2:私有方法的访问
private void Private(){  
    System.out.println("我是私有方法");  
}  
public void getPrivate(){  //调用这个公共方法就可以访问私有方法
    Private();  
}

//3：子类的构造器会最先调用父类的无参构造器
父类：
	public Test1(){//无参构造器
		System.out.println("调用父类无参构造器"); }
子类：
     main(): Test2 t = new Test(); //子类调用自己的无参构造器，然后默认调用super()父类无参构造器
==>：
	调用父类无参构造器

//4：子类构造器可以通过super去指定用父类的哪个构造器
父类：
	public Test1(int age){   //有参构造器  
}
子类：
	public Test2(String name) {  
    super(15);    //先调用父类构造器，再调用子类的
    this.name=name;
}
	
//5：子类一定要调用父类的构造器，否则会出错
父类：
	public Test1(int name){}
子类：
	public Test2(){super();}
**此时程序会出错，因为父类的有参构造器掩盖了无参构造器，而子类super是调用父类不存在的无参构造器，所以会出错
*改：public Test2(){super(12);}
```

继承的本质
![[Pasted image 20230406221603.png]]


#### super关键字
super代表**父类的引用**，用于访问父类的成员、方法、构造器。

基本语法
- 访问成员：super.父类成员  (不能访问private)
- 访问方法：super.方法()
- 访问父类构造器：super()  **只能放在子类构造器第一句**
注意：这个父类不限于父子，是跨多级的

注意事项：
找f()方法或成员时，调用f()和this.f()的效果是一样的。先查找本类，再往后查找父类，没有就顺继承关系依次查找
super.f()会直接查找父类，跳过本类，其他的一致

super的好处：
1. 分工明确，调用父类构造器
2. 当子类有与父类重名的，可以用super避免覆盖

#### 方法重写/覆盖 override
子类的一个方法与父类的**方法名、参数类型、返回类型**相同时，就称子类覆盖了父类的方法 
或者，子类的返回类型是父类的返回类型的子类
比如，父类是Object，子类是String
子类方法不能缩小父类方法的访问权限
public>protected>default>private

### 多态
对方法调用由于对象的不同所导致的行为不同，比如人吃饭习惯，中国人用筷子，西方人用刀叉，人种就是对象的差异。
- **多态是方法的多态，与属性无关**
- 存在的3个必要条件：继承、方法重写、父类引用指向子类
- 父类引用指向子类对象后，用该父类引用调用子类重写方法，体现出多态

```java
class Animal{
	 public void shot(){
		 System.out.println("动物在叫");
	 }
}
class Dog extends Animal{
	 public void shot(){
		 System.out.println("小狗在汪汪叫");
	 }
	 public void see(){
		 System.out.println("很漂亮");
	 }
}
class Cat extends Animal{
	 public void shot(){
		 System.out.println("小猫在喵喵叫");
	 }
}
	public void Test(Animal a){
		a.shot();//通过重写实现多态，运行子类的（运行类型的）
	}
Main:
	Animal a1 = new Dog();
	Animal a2 = new Cat();
	Test(a1);
	Test(a2);
	Dog dog = (Dog) a1;//强制转换才能调用子类特有方法
	dog.see(); 
```

方法的多态
重写和重载体现多态

对象的多态
![[Pasted image 20230513210738.png]]

```java
Animal animal = new Dog();
//编译类型是Animal，运行类型是Dog
animal = new Cat();
//改变运行类型为Cat
```



#### 转型(Casting)
Java 转型主要是用在**继承和接口实现**的场景，Java 转型可分为**向上转型和向下转型**，区别如下：“
- 向上转型：通过子类对象实例化父类对象，这属于自动转换。
- 向下转型：通过父类对象实例化子类对象，这属于强制转换。
只要记住一句话即可，父类引用指向子类对象，即 <父类型> <引用变量名> = new <子类型>()

1. 向上转型
子类的引用对象转换为父类类型称为向上转型。向上转型后的父类引用**只能调用父类的属性**，若子类重写了父类的方法，则通过父类引用**调用的是子类重写后的方法**，该调用过程即为“**动态绑定**”。
`Animal animal = new Dog() （Dog --> Animal向上)`
因为编译器先把animal看成Animal类的，而运行的是Dog类，所以只能运行Animal中的方法，不能运行Dog中特有的方法
```java
public class Parent {
    public int i = 10;
    public void print(){
        System.out.println("我是父类的方法");
    }
    public void printA(){
        System.out.println("我是父类的方法，子类中没有重写该方法");
    }
}

public class Son extends Parent {
    public int i = 20;
    public void print() {
        System.out.println("我是子类的方法，我重写了父类的方法");
    }
    public void printSelf() {
        System.out.println("我是子类独有的方法，父类中没有该方法");
    }“
    pu？
    blic static void main(String[] args) {；         Son son = new Son();
        Parent parent = son;
        System.out.println(son.i);
        son.print();
        son.printA();
	    son.printSelf();	            System.out.println("================================");
        System.out.println(parent.i);
        parent.print();
        parent.printA();
    }
}
```
```结果
20
我是子类的方法，我重写了父类的方法
我是父类的方法，子类中没有重写该方法
我是子类独有的方法，父类中没有该方法
================================
10
我是子类的方法，我重写了父类的方法
我是父类的方法，子类中没有重写该方法
```

2. 向下转型
将一个父类类型的引用**强制**转换为子类类型的过程称为向下转型。但并不是所有的对象都可以向下转型，只有当这个对象原本就是子类对象通过向上转型得到的时候才能够成功转型，在向下转型前，通过`instanceof` 判断某对象是否是某类的实例。此外，大部分情况下，不推荐进行向下转型。示例如下所示：4
`子类类型 引用名 = （子类类型） 父类引用`
```java
//编译类型Animal，运行类型Cat
Animal animal = new Cat();
//编译类型Cat，运行类型Cat
Cat cat = (Cat) animal;//理解为编译器将编译类型Animal转换为Cat
//animal要指向Cat类
//cat就可以使用自己Cat类特有的方法
```
属性没有重写一说，体现在编译类型

#### instanceof运算符
用法：`对象 instanceof 类`  (instance：实例)
当对象是右边类的实例或子类的实例,返回true，否则false
```java
class Animal{}
class Dog extends Animal{}
Dog dog = new Dog();
dog instanceof Animal//dog是Animal子类的实例
dog instanceof Dog//dog是Dog类的实例
//都返回true
```

#### 多态的应用
多态数组

多态参数
方法定义的形参类型是父类类型，实参类型允许为子类类型


### Object类
所有类都是Object的子类，所以Object类方法所有类都可以使用。
1. equals方法
\=\=和equals
\=\=是一个比较运算符
既可判断基本类型，也可以判断引用类型(地址)即判断是不是同一个对象。
```java
//    ==判断基本类型
int a =10,b=20;
System.out.print(a==b); //false
//    ==判断引用类型
A a=new a();
A b=new b();
A c=a;
System.out.print(a==b); //false，指向不同，运行类型不同
System.out.print(a==c); //true，都指向a
```

equals是Object类中的方法，只能判断引用类型
![[Pasted image 20230515224032.png]]
默认判断的是地址是否相等，使用的话一般重写方法，用于判断内容是否相等

2. hashcode方法
1) 提高具有哈希结构的容器的效率！
2) 引用指向的是同一个对象，哈希值一样
3) 引用指向的是不同对象，哈希值是不一样
4) 哈希值主要根据地址转换来的的！不能完全将哈希值等价于地址。
5) 后面在集合中hashCode 如果需要的话，也会重写, 在讲解集合时，老韩在说如何重写hashCode()
```java
Test t1 =new Test();  
Test t2 =new Test();  
Test t3 =t1;
System.out.println(t1.hashCode());//460141958
System.out.println(t2.hashCode());//1163157884
System.out.println(t3.hashCode());//460141958
```

3. toString方法
默认返回：全类名+@+哈希值的十六进制 
子类往往重写toString 方法，**直接输出实例名返回对象的属性信息**
重写toString 方法，打印对象或拼接对象时，都会自动调用该对象的toString 形式
当直接输出一个对象时， toString 方法会被默认的调用, 比如System.out.println(monster) ； 就会默认调用monster.toString()
![[Pasted image 20230515225305.png]]
getClass().getName()表示全类名：包名+类名
2)Integer.toHexString(hashCode()) 将对象的hashCode 值转成16 进制字符串
```java
//默认toString方法
Test t1 =new Test();  
System.out.println(t1.toString());//Test@1b6d3586
//重写toString
class Test{  
    String name;  
    public Test(String name) {  
        this.name = name;  
    }  
    @Override  //重写toString方法,直接alt+insert快捷  
    //输出这个类的属性信息  
    public String toString() {  
        return "Test{" +  
                "name='" + name + '\'' +  
                '}';  
    }  
    public static void main(String[] args) {  
        Test t1 =new Test("xia");  
        System.out.println(t1.toString()); 
        //System.out.println(t1) 的结果同样是toString()的返回值
    }  
}
```

4. finalize方法
1) 当对象被回收时，系统自动调用该对象的finalize 方法。子类可以重写该方法，做一些释放资源的操作
2) 什么时候被回收：当某个对象没有任何引用时，则jvm 就认为这个对象是一个垃圾对象，就会使用垃圾回收机制来
销毁该对象，在销毁该对象前，会先调用finalize 方法。
3) 垃圾回收机制的调用，是由系统来决定(即有自己的GC 算法), 也可以通过System.gc() 主动触发垃圾回收机制
老韩提示： 我们在实际开发中，几乎不会运用finalize , 所以更多就是为了应付面试.

### 断点调试(debug)



# 8_OOP高级
## 1.static关键字
目的：用于内存管理
使用范围：变量、方法、代码块和嵌套类
作用范围：static关键字**属于类**，而不是类的实例（对象）
static修饰：
变量：类变量、静态变量
方法：称为类方法、静态方法
代码块：称为静态代码块
嵌套类：称为静态内部类

静态变量：
类的成员变量可以分为以下两种：
1.  静态变量（或称为类变量），指被 static 修饰的成员变量。
2.  实例变量，指没有被 static 修饰的成员变量。

静态变量与实例变量的区别如下：
1）静态变量
运行时，Java 虚拟机只为静态变量分配一次内存，加载类过程中完成静态变量的内存分配。
在类的内部，可以在任何方法内直接访问静态变量。
在其他类中，可以通过类名访问该类中的静态变量。
不能用this访问，可以用**类名**访问。
当代码块中有同名变量，会被**就近原则覆盖**掉。

2）实例变量
每创建一个实例，Java 虚拟机就会为每个实例变量分配一次内存。
在类的内部，可以在非静态方法中直接访问实例变量。
在本类的静态方法或其他类中则需要通过类的实例对象进行访问。//那还要先创建个对象

静态变量在类中的作用如下：
静态变量可以被类的所有对象共享，因此静态变量可以作为实例之间的共享数据，增加实例之间的交互性。
如果类的所有实例都包含一个相同的常量属性，则可以把这个属性定义为静态常量类型，从而节省内存空间。例如，在类中定义一个静态常量 PI。

this是指这个对象本身的，而静态变量是在整个类中，一个类中静态变量是不变的，所以不能用this来访问静态变量
如果改变静态变量的值，那么对于这个类来说就是永久改变了
**静态变量的好处：它能使程序存储器高效(即它节省内存)。**


静态方法：

同成员变量，成员方法也可以分为以下两种：
静态方法（或称为类方法），指被 static 修饰的成员方法。
实例方法，指没有被 static 修饰的成员方法。

静态方法与实例方法的区别：
静态方法，属于类，而不属于类的对象。
1）它通过类直接被调用，无需创建类的对象。
2）静态方法中，不能使用 this 关键字，也不能直接访问所属类的实例变量和实例方法；
3）静态方法中，可以直接访问所属类的静态变量和静态方法，**不能引用非静态的实例方法和实例变量**。
4）同this 关键字，super 关键字也与类的实例相关，静态方法中不能使用 super 关键字。
实例方法，可直接访问所属类的静态变量、静态方法、实例变量和实例方法。
子集可以访问全集，而全集不能访问子集

静态方法与静态变量好处：
1. 属于类级别，无需创建对象就即可直接使用，使用方便。
2. 全局唯一，内存中唯一，静态变量可以唯一标识某些状态。
3. 类加载时候初始化，常驻在内存，调用快捷方便。

静态方法与静态变量缺点：
1. 静态方法不能调用非静态的方法和变量。//不能随着属性的改变而改变，静态应该是不变的不然应该就是实例方法
2. 不能使用this和super关键字。

静态方法与静态变量适用场景：
1. 静态方法，最适合工具类中方法的定义；比如文件操作，日期处理方法等。
2. 静态方法，适合入口方法定义；比如单例模式，因从外部拿不到构造函数，所以定义一个静态的方法获取对象非常有必要。
3. 静态变量适合全局变量的定义；举例：用一个布尔型静态成员变量做控制标志。


5、静态代码块
定义：静态代码块，是 Java 类中的 static{ } 修饰的代码。
作用：用于类初始化时，为类的静态变量赋初始值，提升程序性能。

静态代码块的特点如下：
静态代码块，有点类似于一个方法，但不可以存在于任何方法体内。
静态代码块，可以置于类中的任何地方，类中可以有多个静态初始化块。 
Java 虚拟机在加载类时执行，将只需要进行一次初始化的操作放在 static 代码块。
类中含多个静态代码块，Java虚拟机将按它们在类中出现的顺序依次执行，且都执行一次。
同静态代码块与静态，不能直接访问类的实例变量和实例方法，需通过类的对象访问。

而且
静态代码块不用创建对象就可以调用。只要有静态代码块，程序会自动按从上到下顺序执行静态代码块中的内容。而普通代码块只会在创建对象后自动执行
静态代码块最先执行，创建对象后才会出现非静态代码。即有类，静态代码块就会执行。有对象，非静态代码块才会执行
```java
class StaticCode {  
    public static int count = 0;  
    {  
        count++;  
        System.out.println("非静态代码块 count=" + count);  
    }  
    static {  
        count++;  
        System.out.println("静态代码块1 count=" + count);  
    }  
    static {  
        count++;  
        System.out.println("静态代码块2 count=" + count);  
    }  
    public static void main(String[] args) {  
    }  
}
out：
	静态代码块1 count=1
    静态代码块2 count=2
//如果创建对象：
      public static void main(String[] args) {  
       System.out.println("*************** StaticCode1 执行 ***************");
       StaticCode sct1 = new StaticCode();  
       System.out.println("*************** StaticCode2 执行 ***************");
       StaticCode sct2 = new StaticCode()  
out:
	静态代码块1 count=1
	静态代码块2 count=2
	*************** StaticCode1 执行 ***************
	非静态代码块 count=3
	*************** StaticCode2 执行 ***************
	非静态代码块 count=4

    }

```

6、静态类
 java中一个类要被声明为static的，只有一种情况，就是静态内部类（内嵌类）。如在外部类声明为static的，程序会编译都不会通过。
1、静态内部类，跟静态方法一样，只能访问静态成员变量和方法，不能访问非静态方法和属性。

2、普通内部类，可以访问任意外部类的成员变量和方法。

3、静态内部类，可以声明普通成员变量和方法，而普通内部类不能声明static成员变量和方法。

4、静态内部类，可以单独初始化。

**适用场景**：当外部类需要使用内部类，而内部类无需外部类资源，并且内部类可以单独创建时，考虑采用静态内部类的设计，在知道如何初始化静态内部类。

静态内部类，调用外部类的构造函数来构造外部类；静态内部类可被单独初始化，于是在外部就可以有下面的实现
静态类**总结**：

**1.如果类的构造器或静态工厂中有多个参数，设计这样类时，最好使用Builder模式，特别是当大多数参数都是可选的时候。**

**2.如果现在不能确定参数的个数，最好一开始就使用构建器即Builder模式。**

静态导入
可以直接导入到静态方法的级别
```java
import static 包名.类名.方法名
```
- 方法必须是静态的
- 当有多个同名静态方法时，就必须加前缀使用了，即用静态导入的方法是唯一的

## 2.代码块
代码块确定了局部变量的作用域。代码块内外不能使用重名的属性，代码块可以使用外部的变量，外部不能使用代码块的属性

## 3.单例设计模式

## 4.final关键字
final表示最终的、不可变的
可以修饰变量、方法、类
```java
//修饰类（无法继承）
final class A{
}
class B extends A{
    //出错，无法继承A
}

//修饰方法（无法被子类覆盖、重写）
class A{
	public final void f(){
	System.out.print("ABC");
	}
}
class B extends A{
	public void f(){
	System.out.print("A");
	}
	//出错，无法重写
}

//修饰变量
final int i = 1;
	//i相当于常数，不能再做赋值运算符的左值（真的常数都要大写）

//实例函数可以通过构造器赋值
class A{
final int i;
public A(i){
this.i = i;
}
}
```

## 5.抽象方法/类
在OOP中，对象都是通过类来描述，但并不是所有的类都可以用来描述对象，当一个类中没有足够的信息去描述对象时，这样的类就是抽象类，那么只有子类继承抽象类才能得到一个对象。

抽象--->少

1. *声明格式*
```java
abstract class 类名{
	成员变量;
	方法() {方法体}; //成员方法
	abstract 方法();//抽象方法 没有方法体!
}
```

2. *特点*
1. 抽象类**不允许直接实例化**，换句话说抽象类不能创建对象，它**只能作为其他类的父类**。 但可以通过向上转型，指向实例化。  
2. 抽象方法只有声明，不能有实现，也就是**仅有方法头，而没有方法体和操作实现**。  如：abstract double area( );   (加分号)

3. *定义抽象类的意义*
- 为其子类提供一个公共的类型（父类引用指向子类对象）；  
- 封装子类中的重复内容（成员变量和方法）；  
- 将父类设计成抽象类后，既可借由父子继承关系限制子类的设计随意性，在一定程度上避免了无意义父类的实例化

4. *注意事项*
- 抽象类不能被实例化
- 抽象类不一定要包含abstract方法，但**抽象方法只能在抽象类中**
- abstract只能修饰类和方法，不能修饰其他的
- 抽象类可以有任意成员(本质还是类)，比如构造器，静态属性
- 如果**一个类继承了抽象类**，则它**必须实现抽象类的所有抽象方法**，除非它自己也声明为抽象类
- 抽象方法**不能使用private、final、static修饰**， 因为这与抽象的特性相违背，如果使用了子类就不能继承
  
## 6.接口
接口就是规范，定义的是一组规则，实现就必须做。OOP的精髓是对对象的抽象，最能体现的就是接口，更加规范地对子类进行约束。抽象类提供了某些具体实现(有常规方法)，接口不提供任何实现，接口中所有方法都是抽象方法，抽象是完全面向规范的，规定了一批类具有的公共方法的规范。接口和实现类不是父子关系，是实现规则的关系。
其他类的区别：
普通类：具体实现
抽象类：具体实现，规范
接口：规范

1. *定义和使用*
```java
[访问修饰符] interface 接口名 [extends 父接口1,父接口2]{
	常量;
	方法;
}
```
- 访问修饰符只能是public或默认
- 接口名与类名一样命名规则
- extends可以多继承接口，但不能继承类
- 属性只能是public static final 常量，不写也默认是
- 方法只能是public abstract ，不写也默认是

2. *注意*
子类通过implements来实现接口中的规范
接口不能创建实例，但可用于声明引用变量类型
**普通类实现了接口，就必须实现接口中所有方法**，并且这些方法只能是public。如果是abstract类可以不用实现接口的方法
JDK1.7之前的版本，接口中只能包含静态常量和抽象方法
JDK1.8之后的版本，接口中包含普通的静态方法

## 7.内部类
内部类是特殊的类，它定义在一个类的内部。在实际开发中，为方便使用外部类的属性和方法，通常需要定义一个内部类。
**内部类可以使用public,defalut,protected,private,static修饰，而普通类只能public和默认**
内部类只是一个编译时的概念，一旦编译成功就会成为完全不同的两个类，且会出现两个字节码文件。它是独立于外部类的存在，属性方法可以与外部类重名
```java
class Out{
	int age = 10;
	String name = "xia";
	class In{
		int age = 17;
		String name = "lang";
	}
}
```

1. *内部类的作用*
1) 内部类提供了更好的封装，只能由外部类直接访问，而不允许同一个包中的其他类直接访问。
2) 内部类可以直接访问外部类的**私有属性**，**内部类被当成其外部类的成员**。但**外部类不能访问内部类的属性**。
3) 接口只是解决了多重继承的部分问题，而内部类使得多重继承的解决方案更加完整。

2. *使用场合*
1) 由于内部类具有更好的封装性，且可以很方便地访问外部类的属性，所以，在**只为外部类提供服务**的情况下可以优先考虑使用内部类。
2) 使用内部类间接实现**多重继承**。每个内部类都能独立地继承一个类或实现某些接口，无论外部类是否继承了某个类或实现了接口，都对内部类没有影响。

3. *分类*
1) 成员内部类
非静态内部类 
不能有静态方法、属性、代码块
外部类的静态方法、代码块不能访问非静态内部类

成员变量访问
内部类里的方法的局部变量：变量名
内部类属性：this.变量名
外部类属性：外部类名.this.变量名
内部类的访问
在外部类中定义内部类：new Inner()
在外部类以外的地方使用非静态内部类：Outer.Inner varname = new Outer().new Inner()
```java
class Outer{
	//在内部类中访问成员变量
    private int age = 10;  
    class Inner{  
        int age = 20;  
        public void show(){  
            int age = 30;  
            System.out.println("内部类方法里的局部变量age:"+age);  
            System.out.println("内部类的成员变量age:"+this.age);  
            System.out.println("外部类的成员变量age:"+Outer.this.age);  
        }  
    }  
  //内部类的访问
    public static void main(String[] args) {  
        Outer.Inner inner = new Outer().new Inner();  
        inner.show();  
        Outer outer = new Outer();  
        Outer.Inner inn = outer.new Inner();  
        inn.show();  
    }  
}
```

静态内部类
```java
Static class 类名{}
```
一个静态内部类对象存在，并不一定存在队形的外部类对象，因此，静态内部类的实例方法不能直接访问外部类的实例方法
静态内部类可看作是外部类的一个静态成员，因此外部类的方法中可以通过“静态内部类.名字” 访问静态内部类的静态成员，通过new静态内部类 访问静态内部类的实例

1) 匿名内部类
适用于只需要使用一次的类
```java
new 父类构造器()/接口(){
}

this.addWindowListener(new WindowAdapter()){
	public void windowClosing(WindowEvent e){
		System.exit(0);
	}
}

```
匿名内部类没有访问修饰符
没有构造器、名字

3) 局部内部类
定义在方法内部，作用域仅限此方法
主要是用来解决比较复杂的问题。局部内部类和成员内部类一样被编译，只是它的作用域发生了改变，只能在该方法中使用
在实际开发中很少运用





# 9_枚举和注解（常用类）
所有的枚举类型隐性地继承自java.lang.Enum。枚举实质还是类，而每个被枚举的成员实质就是一个枚举类型的实例，都是默认由public static final修饰，可以直接通过枚举类型名使用它们 

当需要定义一组常量时，可以使用枚举类型
```java
enum 枚举名{
	SPRING,SUMMER,AUTUMN,WINDTER
	//或
	星期一,星期二，星期三，星期四
}
```

### 注解
注解(Annotation)是一种引用数据类型，编译后生成.class文件。Java 注解是附加在代码中的一些元信息，用于一些工具在编译、运行时进行解析和使用，起到说明、配置的功能。注解不会也不能影响代码的实际逻辑，仅仅起到辅助性的作用。

注解定义语法
```
[修饰符列表] @interface 注解类型名{
}
```

注解使用语法
```
@ 注解类型名
```

• @Override这个注解只能注解方法，这个注解是给编译器参考的，和运行阶段没有关系，凡是java中的方法带有这个注解的，编译器都会进行编译检查，如果这个方法不是重写父类的方法，编译器就会报错

• 用来标注“注解类型”的注解称为元注解

• @Target注解是一个元注解，用来标注“被标注的注解”可以出现在哪些位置上

```
@Target(ElementType.METHOD)//被标注的元素只能出现在方法上
@Target(ElementType.ANNOTATION_TYPE)//被标注的元素只能出现在注解类型上
@Target(ElementType.TYPE)//被标注的元素只能出现在类上
@Target(ElementType.FIELD)//被标注的元素只能出现在字段上
@Target(ElementType.PARAMETER)//被标注的元素只能出现在参数上
@Target(ElementType.CONSTRUCTOR)//被标注的元素只能出现在构造方法上
@Target(ElementType.LOCAL_VARIABLE)//被标注的元素只能出现在局部变量上
@Target(ElementType.PACKAGE)//被标注的元素只能出现在包上
@Target(ElementType. MODULE)//被标注的元素只能出现在模块上
```

- @Retention注解是一个元注解，用来标注“被标注的注解”最终保存在哪里
```

@Retention(RetentionPolicy.SOURCE)//被标注的元素只被保存在java源文件中

@Retention(RetentionPolicy.CLASS)//被标注的元素只被保存在class文件中

@Retention(RetentionPolicy.RUNTIME)//被标注的元素只被保存在class文件中，并且可以被反射机制所读取
```

- @Deprecated注解用来标注已过时的元素

注解中定义属性
```
属性类型 属性名();//表示该属性名只能被赋值该属性类型的数据

public @interface MyAnnotation
{
	int value();
	String name();
	String address() default "";//给address属性赋默认值，在该注解使用时可省略不写
}
```
• 如果一个注解当中有属性，那么在使用该注解时必须给该注解中的属性赋值（除非该属性使用default指定默认值就可省略赋值）

• 如果一个注解的属性名为value且只有这一个属性或其余属性有默认值时，那么在使用该注解的这个属性时，属性名（value）可以省略不写，但属性值必须要有

注解使用
```
@ 注解类型名(属性名=属性值, 属性名=属性值......)

@MyAnnotation(value = 9, name = "xxx", address = "dddd")
class Person
{
	@MyAnnotation(value = 9, name = "xxx" )//因属性address有默认值可省略
	public void run()
	{
		
	}
}
```
• 注解当中的属性可以是这些类型：byte、short、int、long、float、double、boolean、char、String、class、枚举以及以上每种类型的数组类型

• 在使用注解中数组型的属性时如果属性值只有一个值，大括号{ }可省略不写

反射注解
```
判断这个注解是否在此类上
//括号里填注解类型的字节码，
public boolean isAnnotationPresent(Class<? extends Annotation> annotationClass);//返回true表示在此类上有此注解，false表示没有

获取该注解对象
public <A extends Annotation> A getAnnotation(Class<A> annotationClass);//返回该注解类型，可能需强转
```

# 10_异常
异常指的是程序运行过程中不正常的情况。所谓异常处理，就是程序在出现问题时依然可以正确执行完。
在java异常处理机制中，引进了很多用来描述和处理异常的类，称为异常类，之中包含了该类异常的信息和对异常的处理方法。

- 抛出异常：指在执行一个方法时，如果发生异常，则这个方法生成代表该异常的一个对象，停止当前执行路径，并把异常对象交给JRE。
- 捕获异常：JRE得到异常后，寻找相应的代码来处理该异常。JRE在方法的调用栈中查找生产异常的方法开始回溯，直到找到相应的异常处理代码为止。

1. *异常的分类*
所有异常的根类为java.lang.**Throwable**，派生有ERROR和Exception两个子类
![[Pasted image 20230516132343.png]]

1) *ERROR*
程序无法处理的错误，出现较严重的问题。大多数错误是代码运行时JVM出现的问题。ERROR表明JVM已经处于不可恢复的崩溃状态，不需理会。

2) *Exception*
程序本身能够处理的异常
分为RuntimeException**运行时异常**和CheckedException**已检查(编译时)异常**以及IOException
RuntimeException是程序本身出现错误，而IOException是程序本身没有问题，只是IO出现问题

***运行时异常***
算术异常ArithmeticException
```java
int b=0;
1/b; //除以0
```

空指针异常NullPointerException
当程序访问一个空对象/数组的成员时产生异常
```java
String str=null;
str.charAt(0);
//通常是增加非空判断来避免
if（str!=null){
}
```

类型转换异常ClassCastException
在引用数据类型转换时，可能发生异常
```java
Animal a = new Dog();
Cat cat = (Cat)a; //转换错误
```

下标越界异常ArraryIndexOutOfBoundsException
当访问数组的范围超出时
```java
int [] a ={1,2,3};
a{3};
```

数字格式异常NumberFormatException
在使用包装类将字符串转换成基本数据类型时，如果字符串格式不正确，就会出现异常
```java
String str = "1234efd";
System.out.print(Integer.parseInt(str));
```

2. *处理方式*
1) *捕获异常*
**try-catch-finally语句：**
用try来执行一段程序，如果出现异常，系统将抛出一个异常，用catch捕获处理，最后用finally为异常处理提供一个统一的出口。**无论有无异常**，finally代码都要被执行（finally代码最多只有一条也可以没有finally）
**catch中常用方法:**
均继承自Throwable类
- toString()：显示异常的类名和产生异常的原因
- getMessage()：显示产生异常的原因
- printStackTrace()：用来跟踪异常事件发生时堆栈的内容
**finally中:**
通常关闭程序块已打开的资源，例如关闭文件流，释放数据库连接
```java
try{
	int n1=10,n2=0,n3,n4;
	n3=n1/n2;//算术异常，直接被catch捕获，代码终止
	n4=n1+n2;//这段代码不会运行
}catch(ArithmeticException e){
	e.printStackTrace();
	//System.exit(0);    不会执行finally
	//return;   不会执行finally后的语句
	//因为把try-catch-finally看作一个语句
}catch(Exception e){//可以写多个catch不同的异常，但是父类异常要写子类在后面
	e.printStackTrace();
}finally{
	System.out.print("finally");
}
```

2) *声明异常*
CheckedException时，可以**throws**(声明)出去，不用处理
不处理发生的异常，而是将异常传递给调用它的方法来处理

子类方法重写时注意：
子类重写父类方法时，声明的异常只能是父类异常的同一种或子类。
```java
 public static void readFile(String file) throws FileNotFoundException//直接Exception也可以
//读文件的操作可能产生异常
FileInputStream fis =new FileInputStream("d://a.txt");
}
```

3. *自定义异常类*
JDK提供的标准异常类可能无法充分描述用户想要表达的问题，可以自己创建异常类
自定义异常类名**要继承Exception或RuntimeException**
- 继承Exception，编译异常
- 继承RuntimeException，运行时异常（一般继承这个）
通常，自定义异常类包含两个构造器：一个是默认的构造器，另一个是带有详细信息的构造器

```java
class AgeException extends RuntimeException{
	public AgeException(String message){//带有详细信息的构造器
		super(message);
}
}
public static void main(String[] args){
	int age = 180;
	if(!(age>=18 && age<=120)){
		throw new AgeException("age:18~120");
	}//年龄异常就抛出异常
	System.out.println("the age is correct");
}
```

4. *throw和throws*

| |意义|位置|后面跟的东西|
|----|----|----|----|
|throws|异常处理的一种方式|方法声明处|异常类型|
|throw|手动生成异常的关键字|方法体内|异常对象|
```java
class Test01{  
    static void methodA(){  
        try{  
            System.out.println("AAA");  
            throw new RuntimeException("make the Exception");  
        }finally{  
            System.out.println("A.finally");  
        }  
    }  
    static void methodB(){  
        try{  
            System.out.println("BBBB");  
            return;  
        }finally{  
            System.out.println("B.finally");  
        }  
    }  
    public static void main(String[] args) {  
        try{  
            Test01.methodA();  
        }catch (Exception e){  
           System.out.println(e.getMessage());  
        }  
        Test01.methodB();  
    }  
}
```


# 11_常用类
## 包装类
Java在设计类时为每个基本数据类型设计了一个与之对应的类，这个类就称为包装类。

|  基本数据类型| 包装类  |
|  ----  | ----  |
| byte   | Byte |
| boolean| Boolean |
| short  |  Short  |
|char|Character|
|int|Integer|
|long|Long|
|float|Float|
|double|Double|
这8个类名，除**Integer**和**Character**外，都是改变首字母大写
除Character和Boolean外，其他类都是"数字类"都是java.lang.**Number**的子类。由于Number类是抽象类，因此它的所有子类必须实现它的抽象方法。
Number类方法如下：
![[Pasted image 20230605184647.png]]
这意味着所有"数字类"都可以相互转型。

1. *好处*
1) 作为基本数据类型对应的类型存在，方便设计对象的操作。
2) 包含每种基本数据类型的相关属性，如最大值和最小值等，以及相关的操作方法，这些操作方法的作用是在基本数据类型、包装类对象、字符串之间相互转化。

2. *装箱和拆箱*
```java
//手动装箱
int n1 = 100;
Integer integer = new Integer(n1);//方法一
Integer i = Integer.valueOf(n1);//方法二   Integer的n1值
//手动拆箱
int n2 = integer.intValue();//可以将intValue的int看做返回值，返回的是int基本类型
//自动装箱
Integer integer1 = n1;//本质没变，系统自动进行
//自动拆箱
int n3 = integer1;

//包装类转换成其他基本数据类型
double n3 = integer.doubleValue();
```
- 自动拆箱装箱指的是在基本数据类型和包装类之间进行自动地转换，这个概念是JDK1.5版本后提出的。
- 自动装箱：是指Java自动将基本数据类型的数据转化为相应的包装类对象，而不需要手动转换。
- 自动拆箱：自动装箱的反过程，对应的包装类对想自动转化为基本数据类型的数据，不需要手动转换。
- 自动装箱过程是通过调用包装类的valueOf()(**用来返回相应的对象**)实现，而自动拆箱过程则是通过调用包装类的xxxValue()(**用来返回基本数据类型**)实现。
- 自动装箱与拆箱的功能实际是借助编译器来实现的

3. *包装类与字符串之间的转换*
```java
//基本数据类型转换String类
int c = 10;
String str1 = Integer.toString(c);//使用包装类的toString()方法
String str2 = String.valueOf(c);//使用String类的valueOf()方法
String str3 = c + "";//一个空字符串加上基本类型
//字符串转换成基本数据类型
String str = "8";
int d = Integer.parseInt(str);//使用包装类的parseXxx()方法
int e = Integer.valueOf(str);//使用包装类的valueOf()方法转换为基本数据类型的包装类
//a.valueOf(b)将b类型值转换成a类型
```

4. *Integer创建机制*
```java
Integer i = new Integer(1);
Integer j = new Integer(1);
i == j //false ，i和j是两个引用，里面存放的是地址值
Integer m = 1;//底层原理:Integer.valueOf(1)
Integer n = 1;//在-128～127之间直接返回原值。超出范围返回Integer对象
m == n //true
//若是128，就不相等了
```

5. *包装类空指针异常问题*
```java
Integer i=null;//可以编译通过，但会出现空指针运行异常
int j=i;
//上面的相当于以下代码
Integer i=null;
int j=i.intValue();
```
null表示i没有指向任何对象的实体，但作为对象名称是合法的（不管这个对象名称是否指向了某个对象的实体）由于实际上 i 并没有指向任何对象的实体，所以也就不可能操作intValue()方法，因此上面的写法在运行时就会出现NulIPointerException错误。

6. *包装类的缓存问题*

```java
System.out.println(Integer.MIN_VALUE);  
System.out.println(Integer.MAX_VALUE);  
System.out.println(Character.isDigit('a'));  
System.out.println(Character.isLetter('a'));  
System.out.println(Character.isUpperCase('a'));  
System.out.println(Character.isLowerCase('B'));  
System.out.println(Character.isWhitespace('a'));  
System.out.println(Character.toUpperCase('a'));  
System.out.println(Character.toLowerCase('A'));
```


## 字符串类
字符串的字符使用Unicode字符编码，一个字符(字母、汉字)**都占2个字节**。

1. *创建String对象的两种方式*
```java
String s1 = "xia";//直接赋值,指向常量池的"xia"
//先从常量池查看是否有"xia"数据空间，如果有就直接指向，如果没有则创建指向。s1指向常量池的空间地址。
String s2 = new String("YiLang");//调用构造器，栈中引用指向堆中对象
//先在堆中创建空间，里面维护了value属性，指向常量池的YiLang空间，如果常量池里没有这个字符串，重新创建。如果有，直接通过value指向

//两种创建方式的区别
String i = "xia";
String j = "xia";
i == j //True，指向的地址相同
String n = new String("xia");
String m = new String("Xia");
m == n //False，存放两个不同的堆地址
n.equals(m); //True
i = n.intern();//True，new出来的字符串可以用String.intern()来返回一个字符串
n == n.intern();//False，n是堆中的地址，而n.intern()是字符串

//intern()方法：当调用 intern 方法时，如果池已经包含一个等于此 `String` 对象的字符串，则返回池中的字符串。否则，将此 `String` 对象添加到池中，并返回此 `String` 对象的引用。最终返回的是常量池中字符串的地址
```

![[Pasted image 20230525182604.png|585]]

2. *String特性*
String类是一个final类。且字符串是不可变的，一个字符串对象一旦被分配，其内容是不可变的。

3. *String类常见方法*
String类、StringBuilder类、StringBuffer类是与字符串相关的类。String类对象代表不可变的字符序列，StringBuilder类和StringBuffer类代表可变字符序列。

```java
String str1 = "abc";
String str2 = "efg";
//charAt()指定下标输出字符串的字符
str1.charAt(0);//a

//compareTo()比较两字符串大小,compareToIgnoreCase()忽略大小写
//按字典顺序比较两个字符串。如果str1位于str2之前，返回正整数。如果str1位于str2之后，返回负整数。如果相等，返回0
str1.compareTo(str2);//-3

//concat()将str2连接到str1的末尾  (concatenate:连接)  注意：concat本质不是将str2加到str1变量上，因为字符串是final数组存储是常量。
str1.concat(str2);//abcefg

//equals()两个字符串是否相等
str1.equals(str2);//false

//返回字符在字符串中的下标
str1.indexOf("b");//返回第一次出现的下标
str1.lastIndexOf("b");//返回最后一次出现的下标

//isEmpty()判断是不是空
str1.isEmpty()//false

//length()返回str1的长度    注意：数组是 a.length不加()的 ，而String的length需要加()
str1.length();//3

//trim()去掉前后空格  (trim:修剪、修整)
String str = "  a b  c  ";
str.trim()//"a b  c"

//toXxxxxCase()转换成大/小写
str1.toUpperCase();//ABC
str1.toLowerCase();//abc

//substring()返回子列
String str = "01234567";
str1.substring(3);//34567  开始下标:3 包括3后面的所有
str1.substring(3,6);//345  开始下标:3 结束下标:6 包括3后面的，从6结束(不包括6)
```


1) *String类*
String类对象代表不可变的Unicode字符序列，因此可以将String对象称为"不可变对象"。
![[Pasted image 20230605191021.png]]
字符串内容全部存储到 final value\[\]数组中。如果要改变字符串，就必须每次开拓新的内存空间，改变地址。

2) *StringBuffer*
- StringBuffer是final类，不能被继承
- 实现了Serializable接口，即对象可以串行化，即可以网络传输或保存到文件。
- 字符串是放在父类AbstractStringBuilder中的value数组中，创建在堆中。value数组是可变的，所以字符串变化不用更改地址，效率高于String
- StringBuffer是synchronized的，线程同步更安全。多用于多线程
![[Pasted image 20230613221205.png]]

![[Pasted image 20230613221310.png]]

![[Pasted image 20230613232409.png]]

初始化StringBuffer
```java
//方式一：构建一个大小为16的数组存放字符串内容
StringBuffer sb = new StringBuffer();
//方式二：构造器指定初始容量
StringBuffer sb = new StringBuffer(100);//初始容量为100
//方式三：构造器指定内容  (初始长度:str.length() + 16)
StringBuffer sb = new StringBuffer("str");
```

String和StringBuffer转换
```java
//String --> StringBuffer
//方式一：使用构造器
StringBuffer sb = new StringBuffer(str);
//方式二：使用StringBuffer的append()
StringBuffer sb1 = sb.append(str);

//StringBuffer --> String
//方式一：使用构造器
String str = new String(sb);
//方式二：使用StringBuffer的toString()
String str = sb.toString();
```

StringBuffer常用方法   (String有的省略)
```java
StringBuffer sb = new StringBuffer("xia");
//添加
sb.append(',');
sb.append("yi").append(123).append("你好");

//删除
sb.delete(1,4); //删除下标1-3的元素，[1,4)
sb.deleteChatAt(5); //删除下标为5的字符
//替换
sb.replace(4,6,"av"); //下标4-5元素替换为"av",[4,6)

//插入
sb.insert(9,"ab"); //在下标为9的位置插入"ab"，原来9的内容后移
```

3) *StringBuider*
- StringBuilder是final类，不能被继承
- 实现了Serializable接口，即对象可以串行化，即可以网络传输或保存到文件。
- 字符串是放在父类AbstractStringBuilder中的value数组中，创建在堆中。value数组是可变的，所以字符串变化不用更改地址，效率高于String
- StringBuffer不保证同步，用在字符串缓冲区被单个线程使用。比StringBuffer要快
- 与StringBuffer方法一致
![[Pasted image 20230613233447.png]]

String  VS  StringBuffer  VS  StringBuilder
1) StringBuffer和StringBuilder非常类似，操作一样
2) String：不可变字符序列，效率低，但复用性高(相同内容都可指向一个方法池)
3) StringBuffer：可变字符序列，效率高(尤其增删)，线程安全
4) StringBuilder：可变字符序列，效率最高，线程不安全
5) String注意事项：  String str ="a";
str += "b";丢弃了原先的"a"字符，又产生新的字符。如果多次执行改变操作，会导致大量字符串对象存留在内存中，降低效率，如果在循环中会极大影响程序性能。
**如果对String做大量修改，不要使用String**

## 3. Math类


## 4. Arrays类


## 5. System类


## 6. 日期类
时间是单向一维的，可以用刻度尺表达度量时间。计算机中，把1970.01.01 00:00:00 定位基准时间，每个度量单位是毫秒。
java用long类型的变量来表示时间。
现在时刻的"时刻数值" `long now = System.currentTimeMills()`
这是所有时间类的核心值，年、月、日都是根据这个"数值"计算出来

Date时间类(java.util.Date)

# 12_集合
数组的长度在开始时就已经指定，不能更改。集合就能**动态保存任意元素**，增减删除更方便。
- 集合类都实现Iterable、Collection接口。
- 集合主要分两种，单列集合、双列集合，List(有序可重复)和Set(无序不重复)是单列，Map是双列

![[IMG_0597 1.jpeg]]

![[IMG_0598.jpeg]]

• ArrayList：底层数据结构是动态数组，默认初始化容量为10（底层先创建了一个长度为0的数组，当添加第一个元素的时候，初始化容量为10），自动扩容（扩容到原容量的1.5倍），支持随机访问，查询快，增删慢，非同步，线程不安全，效率高
• Vector：底层数据结构是动态数组，查询快，增删慢，同步，线程安全，效率低
• LinkedList：底层数据结构是双向链表，不支持随机访问，查询慢，增删快，非同步，线程不安全，效率高

### Collection Interface
1. *Collection接口实现类的特点*
1) Collection实现子类可以存放多个元素，每个元素可以是Object类
2) 有些实现类可以存放重复的元素，有的不可以
3) 有些实现类是有序的(List)，有些是无序的(Set)
4) 类不能直接实现Collection接口，只能通过子接口List和Set来实现

2. *Collection常用功能*
```java
1、添加功能
boolean add(Object obj);//添加一个元素
boolean addAll(Collection c);//添加一个集合的元素

2、删除功能
void clear();//移除所有元素
boolean remove(Object o);//移除一个元素
boolean removeAll(Collection c);//移除一个集合的元素，只要有一个元素被移除就返回true

3、判断功能
boolean contains(Object o);//判断集合中是否包含指定元素
boolean containsAll(Collection c);//判断集合中是否包含指定的集合元素，只有包含所有元素才叫包含，才返回true
boolean isEmpty();//判断集合是否为空

4、长度功能
int size();//这里获取的是元素的实际个数，不是集合的容量

5、交集功能
/*
	设有两个集合A、B
	A.retainAll(B);
	若A、B之间有交集就把交集保存到集合A中，若无交集，那么集合A就为空，
	至于返回结果则取决于保存交集的A集与保存之前的集合内容是否有变化，
	有变化就返回true，没有变化就返回false
*/
boolean retainAll(Collection c);

6、集合转数组
Object[] toArray();//转型后的数组中每一个元素都是Object类型的
```

### 迭代器
- Iterator对象成为迭代器，用于遍历集合的元素。
- 所有实现了Collection接口的集合类都有一个Iterator()方法，用以返回一个实现了Iterator接口的对象，即可以返回一个迭代器
- Iterator仅用于遍历集合，本身并不存放对象

1. *Iterator接口中的方法*
```java
boolean hasNext(); //判断是否还有元素，如果仍有元素可以迭代返回true
Object next(); //获取元素后，自动后移
void remove();//移除集合中最后一个元素
```

举例
```java
List c = new ArrayList();
//方式一，结构清晰
Iterator it = c.iterator();
while(it.hasNext()){
	System.out.println(it.next());
}
//方式二，效率更高，运行更快
for(Iterator it = c.iterator() ; it.hasNext()；){
	System.out.println(it.next());
}
```

问：迭代器为什么不定义成一个类，而定义成一个接口？  
答：Java中提供了很多的集合类，而这些集合类的数据结构是不同的，意味着它们的存储方式和遍历方式也各不相同，遍历一个集合应当具备判断功能和获取功能，因每种集合的方式不太一样，所以把这两个功能提取出来，这种方式就是接口，这个接口的实现类是以内部类的方式体现的

### List
- List集合：有序的Collection（也称为序列），此接口的用户可以对列表中每个元素的插入位置进行精确控制，用户可以根据元素的整数索引（在列表中的位置）访问元素，并搜索列表中的元素，与Set不同的是List允许重复的元素
• List集合的特点：1、有序（存储和取出的元素顺序一致）；2、可重复


• List三种遍历
```java
//方式一：使用iterator
Iterator it = list.iterator();
while(it.hasNext()){
	Object o = it.next();
}
//方式二：使用增强for
for(Object o : list){
	
}
//方式三：使用普通for
for(int i = 0 ; i < list.size() ; i++){
Object o = list.get(i);
}
```

- List特有的迭代器
```java
列表迭代器：ListIterator listIterator();
该迭代器继承了Iterator迭代器，所以也可直接使用hasNext()和next()

列表迭代器特有的功能：
逆向遍历：
	Object previous();//获取上一个元素
	boolean hasprevious();//判断是否有元素
正向遍历：
	Object next();
	boolean hasNext();

注：ListIterator可以实现逆向遍历，但是必须同一迭代器正向遍历之后才能进行逆向遍历，无实际意义，一般不使用
```

#### ArrayList
1) 可以加入任何元素，包括不限于null,ArrayList，并且多个
2) ArrayList是通过数组实现存储数据的
3) ArrayList基本等同于Vector，除了ArrayList线程不安全(执行效率高)。在多线程下，不建议使用ArrayList

底层操作机制
1) ArrayList是用Object类型的elementData数组实现的存储数据
2) 当创建ArrayList对象时，如果使用的是无参构造器，则初始容量为0，每次扩容添加1.5倍。如果使用指定大小的构造器，则初始容量为指定大小，之后扩容是指定大小的1.5倍
3) 特点：查询效率高，增删效率低，线程不安全
![[Pasted image 20230530154412.png]]

#### LinkedList
1) LinkList底层是用双向链表来存储数据
2) 特点：查询效率低，增删效率高，线程不安全
3) 可以添加任意元素
4) 线程不安全，没有实现同步

LinkedList特有功能
```java
1、添加功能
public void addFirst(Object o);//开头添加
public void addLast(Object o);//结尾添加

2、获取功能
public Object getFirst();//获取开头元素
public Object getLast();//获取结尾元素

3、删除功能
public Object removeFirst();//删除开头元素并返回被删除元素
public Object removeLast();//删除结尾元素并返回被删除元素
```

#### Vector

1) Vector底层也是一个elementData数组，是一个长度可以动态增长的对象数组
2) Vector是线程同步的，即线程安全。即Vector类的方法带有synchroniazed。
3) 在开发中，需要线程同步安全时，多使用Vector

![[IMG_0603.jpeg]]

### Set

1) 无序（存入和取出的顺序不同），没有索引
2) 不能添加重复元素，最多有一个null

Set遍历
```java
Set set = new HashSet();
set.add(“xia”);
set.add(“xu”);
set.add(“xia);
set.add(null);
//方式一：使用iterator
Iterator it = set.iterator();
while(it.hasNext()){
	System.out.println(it.Next());
}
//方式二：使用for增强
for(Object o : set){
	System.out.println(o);
}
/*注意：最后结果都是：
xia null xu
说明存入和取出顺序不一致，且相同元素会只保存一个。最后的结果都是一个顺序，不会因为不同次输出而改变顺序
*/
```

#### HashSet
1) HashSet实现了Set接口
2) HashSet实际上是HashMap
3) HashSet不保证元素是有序的，取决于hash后，再确定索引的结果


#### LinkHashSet
1) LinkHashSet是HashSet 的子类
2) 底层是一个LinkHashMap，底层维护了一个 数组+双向链表
3) LinkedHashSet根据元素的hashCode值来决定元素的存储位置，同时使用链表维护元素的ci x



#### TreeSet
TreeSet集合底层实际上是一个TreeMap，也就是一个二叉树，放到TreeSet集合中的元素等同于放到TreeMap集合的Key（键）部分了，TreeSet集合中的元素无序不重复，可以按照元素的大小顺序自动排序



### Map
- Map和Collcetion并列存在。保存具有映射关系的数Key-Value
- Key和Value可以是任何引用类型的数据，会封装到HashMap$Node中
- Key不能重复，Value可以重复
- Key和Value之间是一对一的关系，通过Key一定能找到对应的Value
- String类总为Key
• 当访问的值不存在的时候，方法就会抛出一个NoSuchElementException异常
• 当对象的类型和Map里元素类型不兼容时，方法就会抛出一个ClassCastException异常
• 当在不允许使用Null对象的Map中使用Null对象时，方法就会抛出一个NullPointerException异常

```java
Map map = new HashMap();
map.put(“no.1”,1);
map.put(“no.1”,2);
System.out.println(map.get(“no.1”));//2
```


Map常用功能
```java
1、添加
/*
（key表示键，value表示值）如果键是第一次存储就直接存储元素并返回null，
如果键不是第一次存储就用现在的值把以前的值替换掉并返回以前的值
*/
v put(k key, v value);

2、删除
void clear();//移除所有的键值对元素
v remove(Object key);//根据键删除键值对元素并把值返回

3、判断
boolean containsKey(Object key);//判断集合中是否包含指定的键
boolean containValue(Object value);//判断集合是否包含指定的值
boolean isEmpty();//判断集合是否为空

4、长度
int size();//返回集合中键值对的对数

5、获取
v get(Object key);//根据键来获取值
Set<K> keySet();//获取集合中所有键的集合
Collection<V> values();//获取集合中所有值的集合
Set<Map.Entry<K,V>> entrySet();//返回的是键值对对象的集合
```

Map的遍历
```java
//方式一
//1、获取集合中所有键的集合
//2、遍历键的集合，得到每个键
//3、根据键找值
Map<String,Integer> map = new HashMap<>();
Set<String> keyset = map.keyset();
for(String key : keyset){
	Integer value = map.get(key);
		System.out.println(key+ ”———” + value);
}
//方式二
//1、获取集合中所有键值对对象的集合
//2、遍历键值对对象的集合，得到每个键值对对象
//3、根据键值对对象获取键和值
Set<Map.Entry<String,Integer>> set = map.entrySet();
for(Map.Entry<String,Integer>) m : set){
	String key = m.getKey();
	Integer value = m.getValue();
	System.out.println(key+ ”———” + value);
}
```



#### HashMap

#### HashTable

#### TreeMap

#### Properties


# 13_泛型
1. *传统方式集合赋值的问题*
不能对加入到集合ArrayList中的数据类型进行约束（不安全）
遍历的时候需要进行类型转换，当数据量较大时，对效率有影响


1) 泛型又称参数化类型，是JDK5出现的新特性，解决数据安全性
2) 在类声明或实例化时只用指定需要的数据类型
3) 可以保证在编译时没警告，运行就不会抛出ClassCastException异常
4) 泛型的作用是：可以在类声明时指定类中某个value的类型
5) 如果数据类型输错，编译器会报错，显示编译异常


*泛型的格式*
```
class 类名<T>/<K,V>
interface 接口名<T>/<K,V>
```

*泛型的好处*
1、编译时，检查元素的类型，提高了安全性；2、避免了强制类型转换；3、将运行异常搬到编译异常
```java
Person<Integer> stringPerson = new Person<Integer>(1);  //指定Person里面的E是Integer类型
System.out.println(stringPerson.f());  
stringPerson.show();  //显示的运行类型是Integer
}
class Person<E> {  
    E a;  
    public Person(E a){  
        this.a = a;  
    }  
    public E f(){  
        return a;  
    }  
    public void show(){  
        System.out.println(a.getClass());//显示a的运行类型 
    }
```

#### 自定义泛型

#### 泛型的继承和通配符
• < ? >：任意类型，如果没有明确，那么就是Object以及任意的Java类了
• 泛型如果明确时前后必须一致
• ？表示任意的类型都可以（后面new的类型是任意引用类型）

```java
Collection<?> c1 = new ArrayList<Object>();
Collection<?> c2 = new ArrayList<Animal>();
Collection<?> c3 = new ArrayList<Dog>();
```

\<? extends E>：向下限定，后面new的类型必须是E及其子类
```java
Collection<? extends Animal> c = new ArrayList<Dog>();//Dog继承类Animal
```
\<? super E>：向上限定，后面new的类型必须是E及其父类


# 14_多线程
解释：
- 程序：一段代码集合，能完成某种功能。
- 进程：程序的一次执行的动态过程，或是正在运行的一个程序。
- 线程：进程可进一步细化为线程，是一个程序内部的一条执行路径，同时它也是程序使用CPU的最基本单位。（进程中要同时干几件事情，每一件事情的执行就是一个线程）
-  并行：多个CPU同时处理多个不同的任务。
-  并发：一个CPU**交替处理多个任务**，造成“貌似同时”的错觉，**一时间只运行一个任务**。比如：人只能专心做一件事，两件事一起做注意力会交替集中。
-  单线程：同一时刻，只允许执行一个线程。
-  多线程：同一时刻，可以执行多个线程。比如：qq进程可以打开多个聊天窗口。

进程就像是工厂中的生产线，每个进程都有自己的资源（如内存、文件等），并且拥有独立的执行环境。一个进程可以看作是一个程序的一次执行实例。

线程就像是工厂中的机器，同一时刻只允许一个线程运行。多个线程可以共享进程的资源，比如内存和文件等，因此可以提高程序的并发度和效率。

并行就像是多条生产线同时工作，可以提高生产效率和速度。在计算机中，多个处理器可以并行地执行不同的任务，从而提高系统的处理能力。

并发就像是多个顾客在同一家餐厅排队点餐，每个顾客都需要等待自己的轮到被服务，但同时其他顾客也可以点餐或者等待自己的轮到被服务。在计算机系统中，多个任务可以同时进行，但是需要通过同步机制来保证数据的正确性和一致性。

注：
-  线程是依赖于进程而存在的，只有运行的程序才会出现进程。
-  多进程的意义在于提高CPU的使用率。
-  多线程的意义在于提高程序的处理效率。
-  不同的进程内存独立不共享。
-  在内存当中多个线程共享堆内存和方法区内存，而每一个线程都有自己的栈内存，栈内存不共享，一个线程一个栈。
- 并发、并行可以同时发生。
-  Java程序运行原理：Java命令会启动JVM，JVM可看作是一个应用程序，等同于启动了一个应用程序，也就是启动了一个进程，该进程会自动启动一个主线程，然后主线程会调用某个类的main方法，所以main方法运行在主线程中，然后再启动垃圾回收线程用来看护主线程，JVM至少启动了这两个线程，所以JVM是多线程的。

每开一个程序，就会多一个进程。
![[Pasted image 20230606210336.png]]
## 线程使用
两种方法：
1. 继承Thread类，重写run方法。
2. 实现Runnable接口，重写run方法。
![[Pasted image 20230606210814.png]]

```java
public class Main {  
    public static void main(String[] args) {  
        Cat cat1 = new Cat();
        Cat cat2 = new Cat(); 
        //进程开始，底层结构是start0()  
        cat.start();  
        //如果用cat.run()运行的线程是Main方法的线程。不是专门创建的线程  
        //当start后，不会等cat.start线程结束，会直接往下运行代码，cat线程和下面代码同时运行  
        Dog dog = new Dog();  
        //将Dog对象放入Thread实例中  
        Thread thread1 = new Thread(dog);  
        Thread thread2 = new Thread(cat1);  
        //实现Runnable接口只能这样运行进程  
        thread1.start();  
        thread2.start();  
    }  
}  
//方法一：继承Thread类表示这就是一个线程  
class Cat extends Thread{  
    @Override//重写run方法  
    public void run() {  
        System.out.println(Cat.currentThread().getName());  
        while(true) {  
            System.out.println("喵喵喵");  
            try {  
                //休眠1s  
                Thread.sleep(1000);  
            } catch (InterruptedException e) {  
                throw new RuntimeException(e);  
            }  
        }  
    }  
}  
//方法二：实现Runnable接口
class Dog implements Runnable{  
    @Override  
    public void run() {  
        while(true){  
            System.out.println("汪汪汪");  
            try {  
                Thread.sleep(1000);  
            } catch (InterruptedException e) {  
                throw new RuntimeException(e);  
            }  
        }  
    }  
}
```

• 在线程中只有run()方法中的代码才会被线程执行。
• 直接调用run()方法就是普通方法调用。
• start()方法的作用：启动一个分支线程，在JVM中开辟一个新的栈空间，只要新的栈空间开出来了，start()方法就结束了，启动成功的线程会自动调用run()方法，并且run()方法在分支栈的栈底部（压栈），这时main()方法在主栈的底部，所以run()方法与main()方法是平级的。

*Thread类和Runnable接口*
- 两种方法从创建线程本质上没有区别，且Thread类本身就实现了Runnable接口
- **实现Runnable接口更好**，因为避免了Java单继承带来的局限性，适合多个相同程序的代码去处理同一个资源。把线程同程序的代码、数据有效分离，较好的体现了面向对象的设计思想


线程常用方法

|方法|用处|
|----|----|
|setName()|改变进程名称|   
|getName()|返回进程名称|
|start()|使进程开始执行|
|run()|调用线程对象run方法|
|setPriority()| 改变线程优先  |
|getPriority()|获取线程优先级|
|sleep()|在指定毫秒数内让正在运行的线程休眠|
|interrupt()|中断线程|
注意：
- start底层会创建新的线程，调用run。如果普通调用run就是一个简单的方法调用，不会启动新的进程
- 优先级范围从小到大是：1~10 (线程优先级高仅仅表示线程获取到CPU时间片的概率高，优先级高的不代表绝对快速执行，只是先执行的概率更高)
- interrupt中断线程，但并没有真正的结束进程。一般用于中断正在休眠的进程

线程插队

|方法|用法|
|----|----|
|yield|线程礼让。线程让出CPU，先让其他线程执行，但礼让时间不确定，礼让也不一定成功。当资源紧张时，成功率大|
|join|线程插队。一旦线程插队成功，就会停下未执行完的代码，先执行插队线程|


方式三：实现Callable接口（JDK8新特性）
```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.FutureTask;

/**
 * 实现线程的第三种方式：实现Callable接口
 * 
 * 这种方式的优点是：可以获取到线程的执行结果
 * 这种方式的缺点是：在获取线程结果时容易引起当前线程阻塞，效率较低
 */
public class Lianxi_02
{
	public static void main(String[] args)
	{
		MyThread1 mt = new MyThread1();
		
		//创建一个“未来类”对象
		FutureTask task = new FutureTask(mt);
		
		//创建线程对象
		Thread t = new Thread(task);
		
		t.start();
		
		try{
			//通过get()方法获取线程返回值
			System.out.println(task.get());
		} catch (InterruptedException e){
			e.printStackTrace();
		} catch (ExecutionException e){
			e.printStackTrace();
		}
		//get()方法会导致当前线程阻塞，所以此方法效率比较低
		//因为get()方法需要等线程结束后拿到线程返回值
		//所以main()方法这里的代码需要等get()方法结束才能执行，也就是要等以上线程结束后才执行
		System.out.println("结束了");
	}
}

//实现Callable接口
class MyThread1 implements Callable<String>
{
	//这里的call()方法就相当于run()方法
	public String call() throws Exception
	{
		String str = "hhhh";
		Thread.sleep(5000);
		System.out.println("2222");
		Thread.sleep(5000);
		System.out.println("3333");
		return str;
	}	
}
```

## 线程状态和生命周期
线程的生命周期：
1. NEW：新生状态。new一个对象后，该线程对象就处于新生状态，通过调用start()进入就绪状态。
2. RUNNABLE：就绪状态。处于就绪状态的线程已经具备了运行条件，但还没有分配到CPU，就绪等待系统分配CPU。一旦获得CPU，线程就进入运行状态并自动调用run()。
 下面原因进入RUNNABLE：
- 新建线程：调用start()，进入就绪状态
- 阻塞线程：阻塞解除休眠解除，进入就绪状态
- 运行线程：调用yield()，进入就绪状态
- 运行线程：JVM将CPU资源从本线程切换到其他线程
3. BLOCKED：阻塞状态。暂停一个线程的执行以等待某个班条件发生
 下面原因进入BLOCKED：
 - 执行sleep()，线程休眠进入阻塞状态。
 - 执行wait()，使线程进入阻塞状态，notify()唤醒后进入就绪状态
 - 线程运行时，某个操作进入阻塞状态。例如：执行IO流操作
 - join()线程联合
4. RUUNING：运行状态。线程运行run()中的代码。如果在给定的时间片内没有执行完毕，线程会被换下到就绪状态
5. WAITING：等待状态
6. TERMINATED：终止状态

![[Pasted image 20230606223535.png]]
![[Pasted image 20230607104252.png]]

*线程终止*
- 当线程完成任务后，会自动结束。
- 经常也可以通过boolea的终止变量来停止线程。
```java
class Main{
	 Test test = new Test();
	 Thread.sleep(10000);
	 test.terminate();
}
class Test extends Thread{
public void run() {  
    while(live) {  
        count++;  
        System.out.println(+count);   
            //休眠1s  
            Thread.sleep(1000);  
    } 
    public void terminate(){  
	    live = false;  
}  
}
//用live终止变量，在run()输出10次后终止线程
```



合并线程
`public final void join()`

```java
在以下代码，合并线程的作用是：t1线程进入阻塞状态，t2线程执行，直到t2线程结束，t1线程才可以正常执行

public class Lianxi_02
{
	public static void main(String[] args)
	{
		Thread t1 = new Thread(new Myth1());
		t1.setName("t1");
		t1.start();
	}
}

class Myth1 implements Runnable
{
	public void run()
	{
		Thread t2 = new Thread(new Myth2());
		
		t2.setName("t2");
		//启动t2线程
		t2.start();
		
		//合并t2
		try{
			t2.join();//t1进入阻塞，t2执行
		} catch (InterruptedException e){
			
			e.printStackTrace();
		}
		
		//t1的线程代码
		for(int i = 0; i < 5; i++)
		{
			System.out.println(Thread.currentThread().getName() + "---->" + i);
		}
	}
}

class Myth2 implements Runnable
{
	public void run()
	{
		//t2的线程代码
		for(int i = 0; i < 5; i++)
		{
			System.out.println(Thread.currentThread().getName() + "---->" + i);
		}
	}
}

执行结果：
t2---->0
t2---->1
t2---->2
t2---->3
t2---->4
t1---->0
t1---->1
t1---->2
t1---->3
t1---->4
```



用户线程和守护线程
用户线程：也叫工作线程，当线程的任务执行完或通知方式结束
守护线程：一般是为工作线程服务的，当所有的用户线程结束，守护线程自动结束。比如垃圾回收机制


*守护线程*
Java语言中线程分为两大类：
1 用户线程（如主线程main方法）
2 守护线程（后台线程，如垃圾回收线程）
守护线程的特点：一般的守护线程是一个死循环，所有的用户线程只要结束，守护线程就自动结束
将该线程标记为守护线程或用户线程，当正在运行的线程都是守护线程时，Java 虚拟机退出
```java
java.lang.Thread中的方法
public final void setDaemon(boolean on);//true表示守护线程，false表示用户线程
```



## 线程同步
在多线程中，一些敏感数据不允许被多个线程同时访问。就要使用同步技术，保证数据在一时刻最多只有一个线程访问

synchronized
```java
//方式一：同步代码块
synchronized(对象){
}
//方式二：同步方法
public synchronized void m(){
}
```

注意：
- 非静态同步方法：默认锁对象为this
- 静态方法：默认锁对象为 当前类.class


注：
• 局部变量永远都不会存在线程安全问题，因为局部变量在栈中不共享，一个线程一个栈
• 实例变量在堆内存中，静态变量在方法区内存中，堆内存和方法区内存都是多线程共享的，所以可能存在线程安全问题
• 同步机制虽然可以解决数据安全问题，但其缺点在于当线程相当多时，因为每个线程都会去判断同步上的锁对象，极其耗费资源，无形中会降低程序的运行效率
synchronized在开发中最好不要嵌套使用，可能会导致死锁（指两个或两个以上的线程在执行的过程中，因争夺资源产生的一种相互等待现象）

以下代码是死锁示例


**解决线程安全问题的方案**：
1. 尽量使用局部变量代替实例变量和静态变量
2. 如果必须是实例变量，那么可以考虑创建多个对象，一个线程一个对象，这样实例变量的内存就不共享了
3. 如果不能使用局部变量，对象也不能创建多个，这个时候就只能选择synchronized同步机制了


## 任务定时调度
定时器的作用：间隔特定的时间，执行特定的程序
```java
import java.util.Date;
import java.util.Timer;
import java.util.TimerTask;

public class ThreadTest
{
	public static void main(String[] args)
	{
		//创建定时器对象
		Timer ti = new Timer();
		
		//创建定时任务对象
		TimerTask task = new MyThread();
		
		//任务第一次执行的时间
		Date firstTime = new Date();
		
		//任务task从时间date开始执行，每隔2000ms执行一次
		ti.schedule(task, firstTime, 2000);
		
	}
}


//定时任务类
class MyThread extends TimerTask
{
	//指定定时任务run()代码块
	public void run()
	{
		System.out.println("hhhh");
	}
}


```

Object中的wait方法和notify方法

wait()和notify()不是线程对象的方法，是Java中任何一个Java对象都有的方法，因为这两个方法是Object类中自带的

• wait()：让对象上活动的线程进入等待状态，并释放对象锁

`public final void wait();`

• notify()：唤醒对象上等待的单个线程（若有多个线程等待，则随机选择一个线程唤醒），不释放锁

`public final void notify();`

• notifyAll()：唤醒对象上等待的所有线程，不释放锁

`public final void notifyAll();`

注：

• 唤醒并不表示线程可以立马执行，还要抢夺CPU时间片

• 这些方法都与线程有关，所以一般用在锁对象上，通过锁对象来控制线程

sleep()与wait()的区别：sleep()只能通过线程对象调用，且必须指定睡眠时间，不释放锁。wait()方法可以通过任意对象调用，且可指定时间，也可不指定时间，释放锁

*获取文件绝对路径*
采用以下的代码可以拿到一个文件的绝对路径，前提是文件必须在当前类路径下（在当前src下），这种写法无论在哪个系统上都可获得绝对路径，是通用的
```java
String path = Thread.currentThread().getContextClassLoader()
.getResource("从当前类路径开始的文件路径（相对路径）").getPath();
		
//Thread.currentThread();表示获取当前线程对象
//getContextClassLoader();表示获取当前线程的类加载器对象
//getResource();获取资源，当前线程的类加载器默认从类的根路径下加载资源


直接返回流
InputStream path = Thread.currentThread().getContextClassLoader()
.getResourceAsStream("从当前类路径开始的文件路径（相对路径）");
```


# 资源绑定器
Java.util包下提供了一个资源绑定器，便于获取属性配置文件（.properties）中的内容，使用以下方法的前提是配置文件必须在当前类路径下，且此方法只适用于配置文件，注意：在写路径时路径后的扩展名不能写
```java
ResourceBundle bundle = ResourceBundle.getBundle("db");//不能写成db.properties
		
String driver = bundle.getString("driver");
```

# 15_IO流
## 基本概念
数据源是提供数据的原始媒介。常见的数据源有数据库、文件、其他程序、内存、IO设备。

流的分类

按流的方向（以内存作为参照物）
- 输入流：数据从数据源到程序
- 输出流：数据从程序到数据源

按处理的数据单元
- 字节流：以字节为单位获取数据，命名以Stream结尾都是字节流。一次读取一个字节byte，等同于一次读取8个二进制位，这种流是万能的，什么类型的文件都可以读取，包括：文本文件、图片、声音文件、视频文件。
- 字符流：以字符为单位获取数据，命名以Reader/Writer结尾都是字符流。一次读取一个字符，这种流是为了方便读取普通文本文件而存在的，但这种流不能读取：图片、声音、视频等文件，只能读取纯文本文件，也读不了word文件。

按处理对象不同
- 节点流：可以直接从数据源或目的地读写数据，如FileInputStream、FileReader
- 处理流：不直接连接到数据源或目的地，是“处理流的流”，通过对其他流的处理提高程序的性能，如BufferedInputStream、BufferedReader

IO

# 反射
反射就是通过字节码文件对象把java类中的各种成分（变量、方法、构造方法）映射成一个个java对象，实际上是通过class对象反向获取该类的信息，即通过类的字节码文件动态的解析类

获取Class对象的三种方式（在运行期间，一个类只有一个class对象产生）：
```
方式一：会导致类加载，类加载静态代码块执行
Class c = Class.forName("带有包名的完整类名");

方式二：会执行静态代码块
Class c = 对象.getClass();

方式三：java语言中任何一种类型，包括基本数据类型都有.class属性 不会执行静态代码块（不会静态初始化）
Class c = 任何类型.class;
```

以下所有方法中若要获取私有成员时就在Declared之后调用解除私有限定（安全检查管理器）方法
```
public void setAccessible(boolean flag);
flag为true时表示关闭检查，可调用私有
flag为false时表示打开检查，不可调用私有
```

通过class对象获取构造方法对象
```
java.lang.reflect.Constructor<T>

获取批量的构造方法对象
public Constructor<?>[] getConstructors();//所有公有的构造方法
public Constructor<?>[] getDeclaredConstructors();//获取所有的构造方法（包括私有、受保护、默认、公有）


获取单个指定的构造方法对象
//Class<?>... parameterTypes表示参数类型的字节码，如String.class、int.class

public Constructor<T> getConstructor(Class<?>... parameterTypes);//获取单个指定的公有构造方法
public Constructor<T> getDeclaredConstructor(Class<?>... parameterTypes);//获取单个指定不限修饰符的构造方法

创建新对象
public T newInstance(Object... initargs);//括号里的是填实际参数

```

通过class对象获取成员变量对象
```
java.lang.reflect.Field

获取批量的成员变量对象
public Field[] getFields();//获取公有的成员变量
public Field[] getDeclaredFields();//获取所有成员变量，包括：私有、受保护、默认、公有

通过变量名获取单个指定的成员变量对象
public Field getField(String name);//获取指定公有的成员变量
public Field getDeclaredField(String name);//获取单个指定成员变量、不限修饰符

获取变量的值，如果是私有就需要关闭安全检查
public Object get(Object obj);//括号里表示对象,返回该对象的某个变量的值

给获取的变量赋值
public void set(Object obj, Object value);//obj表示变量所在的对象，value表示要为变量赋的值



```


通过class对象获取成员方法对象
```
java.lang.reflect.Method

获取批量的成员方法对象
public Method[] getMethods();//获取公有的成员方法，包含了父类的公有成员方法
public Method[] getDeclaredMethods();//获取所有的成员方法，包含了私有成员方法，不包括继承的

获取单个指定成员方法对象
public Method getMethod(String name, Class<?>... parameterTypes);//获取公有的指定成员方法，name是方法名，后面填的是形参类型字节码
public Method getDeclaredMethod(String name, Class<?>... parameterTypes);//获取所有的成员方法

调用该成员方法
public Object invoke(Object obj, Object... args);//obj表示要调用方法的对象，args表示调用方法时传递的实际参数
```

```
获取类的父类对象
public Class<? super T> getSuperclass();
```

```
获取类实现的所有接口对象
public Class<?>[] getInterfaces();
```
反射的核心是：JVM 在运行时才动态加载类或调用方法/访问属性，它不需要事先（写代码的时候或编译期）知道运行对象是谁


反射的优点

• 可扩展性特性：应用程序可以通过使用它们的完全限定名称创建可扩展性对象的实例来使用外部的、用户定义的类。

• 类浏览器和可视化开发环境：类浏览器需要能够枚举类的成员。可视化开发环境可以受益于利用反射中可用的类型信息来帮助开发人员编写正确的代码。

• 调试器和测试工具：调试器需要能够检查类的私有成员。测试工具可以利用反射来系统地调用定义在类上的可发现集 API，以确保测试套件中的高水平代码覆盖率。

反射的缺点

• 性能开销：由于反射涉及动态解析的类型，因此无法执行某些 Java 虚拟机优化。因此，反射操作的性能比非反射操作慢，应避免在对性能敏感的应用程序中频繁调用的代码段中使用。

• 安全问题：反射调用方法时可以忽略权限检查，因此可能会破坏封装性而导致安全问题。

• 内部暴露：由于反射允许代码执行非反射代码中非法的操作，例如访问私有字段和方法，使用反射会导致意想不到的副作用，这可能会使代码功能失调并可能破坏可移植性.反射代码打破了抽象，因此可能会随着平台的升级而改变行为。

# 设计模式
• 简单工厂模式：又叫静态工厂方法模式，它定义一个具体的工厂负责创建一些类的实例  
优点：客户端不需要负责对象的创建，从而明确了各个类的职责（功能）  
缺点：这个静态工厂类负责所有对象的创建，如果有新的对象增加，或者某些对象的创建方式不同，就需要不断的修改工厂类，不利于后期的维护

• 工厂方法模式：工程方法模式中抽象工厂类负责定义创建对象的接口，具体对象的创建工作由继承抽象工厂的具体类实现  
优点：客户端不需要负责对象的创建，从而明确了各个类的职责，如果有新的对象增加，只需要增加一个具体的类和具体的工厂类即可，不影响已有的代码，后期维护容易，增强了系统的扩展性  
缺点：需要额外的编写代码，增加了工作量

• 单例设计模式：单例设计模式就是要确保类在内存中只有一个对象，该实例必须自动创建，并且对外提供  
优点：在系统内存中只存在一个对象，因此可以节约系统资源，对于一些需要频繁创建和销毁的对象，单例模式无疑可以提高系统的性能  
缺点：没有抽象层，因此扩展很难，职责过重，在一定程度上违背了单一职责原则



# 问题
为什么要转换
![[Pasted image 20230530153438.png]]
