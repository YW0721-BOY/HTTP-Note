# 第一章 JAVA 的基本程序设计结构

## 1.1一个简单的java应用程序

```java
public class FirstSample
{
    public static void main(String[] args)
    {
        System.out.println("This is FirstSample class__'Hello,World!'");
    }
}
```

+ 根据Java语言规范，main方法必须声明为public
+ Java语言规范是描述Java语言的官方文档。可以从网站http://docs.oracle.com/javase/specs上阅读或下载

## 1.2 注释

+ 与大多数程序设计语言一样，Java中的注释也不会出现在可执行程序中。
+ 在Java中，有3种标记注释的方式
  + 最常用的方式是使用//，其注释内容从//开始到本行结尾。
  + 当需要长篇的注释时，可以使用/\*和\*/将一段比较长的注释括起来。
  + 第3种注释可以用来自动地生成文档。这种注释以/**开始，以*/结束。

> 警告：在Java中，/* */注释不能嵌套。也就是说，不能简单地把代码用/*和*/括起来作为注释，因为这段代码本身可能也包含一个*/。

## 1.3 数据类型

+ Java是一种强类型语言。这就意味着必须为每一个变量声明一种类型。
+ 一共有8种基本类型（primitive type），其中有**4种整型**、 **2种浮点类型**、**1种**用于表示Unicode编码的字符单元的**字符类型char**和**1种用于表示真值的boolean类型**。

> Java有一个能够表示任意精度的算术包，通常称为“大数值”（big number）。虽然被称为大数值，但它并不是一种新的Java类型，而是一个Java对象。

### 1.3.1 整型

+ 整型用于表示没有小数部分的数值，它允许是负数。
+ JAVA提供了4中整型
  + **int类型**最常用；
  + 假如你要表示星球上的居住人数，要用**long类型**；
  + **byte和short类型**主要用于特定的应用场合
    + 底层的文件处理或者需要控制占用存储空间量的大数组。

+ 在Java中，整型的范围与运行Java代码的机器无关。这就解决了软件从一个平台移植到另一个平台，或者在同一个平台中的不同操作系统之间进行移植给程序员带来的诸多问题。
+ 长整型数值有一个后缀L或l（如4000000000L）。
+ 十六进制数值有一个前缀0x或0X（如0xCAFE）。
+ 八进制有一个前缀0，例如，010对应八进制中的8。

> 很显然，八进制表示法比较容易混淆，所以建议最好不要使用八进制常数。

+ 从Java 7开始，加上前缀0b或0B就可以写二进制数。例如，0b1001就是9。

> 注意，Java没有任何无符号（unsigned）形式的int、long、short或byte类型。

### 1.3.2 浮点类型

+ 浮点类型用于表示有小数部分的数值。在Java中有两种浮点类型
+ double表示这种类型的数值精度是float类型的两倍（有人称之为双精度数值）。绝大部分应用程序都采用double类型。
+ 在很多情况下，float类型的精度很难满足需求。
+ 实际上，只有很少的情况适合使用float类型，

> 例如，需要单精度数据的库，或者需要存储大量数据。

+ float类型的数值有一个后缀F或f（例如，3.14F）。没有后缀F的浮点数值（如3.14）默认为double类型。当然，也可以在浮点数值后面添加后缀D或d（例如，3.14D）。

### 1.3.3 char类型

+ char类型原本用于表示单个字符。不过，现在情况已经有所变化。如今，有些Unicode字符可以用一个char值描述，另外一些Unicode字符则需要两个char值。
+ char类型的字面量值要用单引号括起来。例如：'A’是编码值为65所对应的字符常量。它与"A"不同，"A"是包含一个字符A的字符串。

### 1.3.4 Unicode和char类型

+ 要想弄清char类型，就必须了解Unicode编码机制。Unicode打破了传统字符编码机制的限制。

  + 在Unicode出现之前，已经有许多种不同的标准：美国的ASCII、西欧语言中的ISO 8859-1、俄罗斯的KOI-8、中国的GB 18030和BIG-5等。

  + 这样就产生了下面两个问题：

    + 一个是对于任意给定的代码值，在不同的编码方案下有可能对应不同的字母；
    + 二是采用大字符集的语言其编码长度有可能不同。

    > 例如，有些常用的字符采用单字节编码，而另一些字符则需要两个或更多个字节。

+ 在Java中，char类型描述了UTF-16编码中的一个代码单元。

  > 我们强烈建议不要在程序中使用char类型，除非确实需要处理UTF-16代码单元。最好将字符串作为抽象数据类型处理

### 1.3.5 boolean 类型

+ boolean（布尔）类型有两个值：false和true，用来判定逻辑条件。整型值和布尔值之间不能进行相互转换。

## 1.4 变量

+ 在Java中，每个变量都有一个类型（type）。在声明变量时，变量的类型位于变量名之前。
  + double salary;
  + int vacationDays;
  + long earthPopulation;
  + boolean done;
+ 可以看到，每个声明以分号结束。由于声明是一条完整的Java语句，所以必须以分号结束。
+ 变量名必须是一个以字母开头并由字母或数字构成的序列。
  + 需要注意，与大多数程序设计语言相比，Java中“字母”和“数字”的范围更大。

> 如前所述，变量名对大小写敏感，例如，hireday和hireDay是两个不同的变量名。在对两个不同的变量进行命名时，最好不要只存在大小写上的差异。不过，在有些时候，确实很难给变量取一个好的名字。

### 1.4.1 变量初始化

+ 声明一个变量之后，必须用赋值语句对变量进行显式初始化，千万不要使用未初始化的变量。例如，Java编译器认为下面的语句序列是错误的：

```java
int vacationDays;
System.out.println(vacationDays);//ERRO--variable not initizlazed
```

+ 要想对一个已经声明过的变量进行赋值，就需要将变量名放在等号（=）左侧，相应取值的Java表达式放在等号的右侧。

```java
int vacationDays; 
vacationDays = 12;
```

+ 也可以将变量的声明和初始化放在同一行中。例如：

```java
int vacationDays = 12;
```

+ 最后，在Java中可以将声明放在代码中的任何地方。
+ 在Java中，变量的声明尽可能地靠近变量第一次使用的地方，这是一种良好的程序编写风格。

### 1.4.2 常量

+ 在Java中，利用关键字final指示常量。

```java
public class Constans
{
    public static void main(String[] args)
    {
        final double CM_PER_INCH = 2.54;
        double paperWidth = 8.5;
        double paperHeigh = 11;
    }
}
```

+ 关键字final表示这个变量只能被赋值一次。一旦被赋值之后，就不能够再更改了。习惯上，常量名使用全大写。
+ 在Java中，经常希望某个常量可以在一个类中的多个方法中使用，通常将这些常量称为类常量。可以使用关键字static final设置一个类常量。下面是使用类常量的示例：

```java
public calss Constans2
{
    public static final double CM_PRE_INCH = 2.54;
    public static void main(String[] args)
    {
        double paperWidth = 8.5;
        double paperHeigh = 11; 
        System.out.println("Paper size in centimeters:"+ paperWidth * CM_PER_INCH + "by" +paperHeight * CM_PER_INCH);
    }
}
```

+ 需要注意，类常量的定义位于main方法的外部。
+ 因此，在同一个类的其他方法中也可以使用这个常量。而且，如果一个常量被声明为public，那么其他类的方法也可以使用这个常量。

## 1.5 运算符

+ 在java中，使用算术运算符+、-、*、/表示加、减、乘、除运算。

  + 当参与/运算的两个操作数都是整数时，表示整数除法；否则，表示浮点除法。
  + 整数的求余操作（有时称为取模）用%表示。

  > 例如，15/2等于7,15%2等于1,15.0/2等于7.5。

+ 需要注意，整数被0除将会产生一个异常，而浮点数被0除将会得到无穷大或NaN结果。

> 可移植性是Java语言的设计目标之一。无论在哪个虚拟机上运行，同一运算应该得到同样的结果。对于浮点数的算术运算，实现这样的可移植性是相当困难的。double类型使用64位存储一个数值，而有些处理器使用80位浮点寄存器。这些寄存器增加了中间过程的计算精度。例如，以下运算：
>
> ```java
> double w = x * y / z;
> ```
>
> > 很多Intel处理器计算x * y，并且将结果存储在80位的寄存器中，再除以z并将结果截断为64位。这样可以得到一个更加精确的计算结果，并且还能够避免产生指数溢出。但是，这个结果可能与始终在64位机器上计算的结果不一样。因此，Java虚拟机的最初规范规定所有的中间计算都必须进行截断。这种行为遭到了数值计算团体的反对。截断计算不仅可能导致溢出，而且由于截断操作需要消耗时间，所以在计算速度上实际上要比精确计算慢。为此，Java程序设计语言承认了最优性能与理想结果之间存在的冲突，并给予了改进。在默认情况下，虚拟机设计者允许对中间计算结果采用扩展的精度。但是，对于使用strictfp关键字标记的方法必须使用严格的浮点计算来生成可再生的结果。例如，可以把main方法标记为
> >
> > ```java
> > public static strictfp void main(String[] args)
> > ```
> >
> > 于是，在main方法中的所有指令都将使用严格的浮点计算。如果将一个类标记为strictfp，这个类中的所有方法都要使用严格的浮点计算。

### 1.5.1 数学函数与常量

+ 在Math类中，包含了各种各样的数学函数。在编写不同类别的程序时，可能需要的函数也不同。

  + 要想计算一个数值的平方根，可以使用sqrt方法：

  ```java
  double x = 4;
  double y = Math.sqrt(x);
  System.out.println(y); //prints 2.0
  ```

  > println方法和sqrt方法存在微小的差异。println方法处理System.out对象。但是，Math类中的sqrt方法处理的不是对象，这样的方法被称为静态方法。

  + 在Java中，没有幂运算，因此需要借助于Math类的pow方法。

  ```java
  double y = Math.pow(x,a);
  ```

  > 将y的值设置为x的a次幂（xa）。pow方法有两个double类型的参数，其返回结果也为double类型。

  + floorMod方法的目的是解决一个长期存在的有关整数余数的问题。

    + 考虑表达式n % 2。所有人都知道，如果n是偶数，这个表达式为0；如果n是奇数，表达式则为1。当然，除非n是负数。如果n为负，这个表达式则为-1。为什么呢？设计最早的计算机时，必须有人制定规则，明确整数除法和求余对负数操作数该如何处理。
    + 数学家们几百年来都知道这样一个最优（或“欧几里德”）规则：余数总是要≥0。不过，最早制定规则的人并没有翻开数学书好好研究，而是提出了一些看似合理但实际上很不方便的规则。

    > 数学家们几百年来都知道这样一个最优（或“欧几里德”）规则：余数总是要≥0。不过，最早制定规则的人并没有翻开数学书好好研究，而是提出了一些看似合理但实际上很不方便的规则。

  + Math类提供了一些常用的三角函数:

    ```java
    Math.sin
    Math.cos
    Math.tan
    Math.atan
    Math.atan2
    ```

  + 还有指数函数以及它的反函数——自然对数以及以10为底的对数：

    ```java
    Math.exp
    Math.log
    Math.log10
    ```

  + 最后，Java还提供了两个用于表示π和e常量的近似值：

    ```java
    Math.PI
    Math.E
    ```

  > 在Math类中，为了达到最快的性能，所有的方法都使用计算机浮点单元中的例程。如果得到一个完全可预测的结果比运行速度更重要的话，那么就应该使用StrictMath类。它使用“自由发布的Math库”（fdlibm）实现算法，以确保在所有平台上得到相同的结果。有关这些算法的源代码请参看www.netlib.org/fdlibm（当fdlibm为一个函数提供了多个定义时，StrictMath类就会遵循IEEE 754版本，它的名字将以“e”开头）。

### 1.5.2 数值类型之间的转换

+ 经常需要将一种数值类型转换为另一种数值类型。

![image-20221114135410982](C:\Users\MYW\AppData\Roaming\Typora\typora-user-images\image-20221114135410982.png)

+ 在图中有6个实心箭头，表示无信息丢失的转换；有3个虚箭头，表示可能有精度损失的转换。例如，123 456 789是一个大整数，它所包含的位数比float类型所能够表达的位数多。当将这个整型数值转换为float类型时，将会得到同样大小的结果，但却失去了一定的精度。

```java
int n = 123456789;
float f = n; //f is 1.23456792E8
```

+ 当使用上面两个数值进行二元操作时（例如n + f,n是整数，f是浮点数），先要将两个操作数转换为同一种类型，然后再进行计算。
  + 如果两个操作数中有一个是double类型，另一个操作数就会转换为double类型。
  +  否则，如果其中一个操作数是float类型，另一个操作数将会转换为float类型。
  +  否则，如果其中一个操作数是long类型，另一个操作数将会转换为long类型。
  +  否则，两个操作数都将被转换为int类型

### 1.5.3 强制类型转换

+ 在上一小节中看到，在必要的时候，int类型的值将会自动地转换为double类型。但另一方面，有时也需要将double转换成int。在Java中，允许进行这种数值之间的类型转换。当然，有可能会丢失一些信息。
+ 在这种情况下，需要通过强制类型转换（cast）实现这个操作。
+ 强制类型转换的语法格式是在圆括号中给出想要转换的目标类型，后面紧跟待转换的变量名。例如：

```java
double x = 9.997;
int nx = (int)x; //nx = 9;
```

+ 这样，变量nx的值为9。强制类型转换通过截断小数部分将浮点值转换为整型。

+ 如果想对浮点数进行舍入运算，以便得到最接近的整数（在很多情况下，这种操作更有用），那就需要使用Math.round方法：

  ```java
  double x = 9.997;
  int nx = (int)Math.round(x); // nx = 10
  ```

  + 现在，变量nx的值为10。当调用round的时候，仍然需要使用强制类型转换（int）。
  + 其原因是round方法返回的结果为long类型，由于存在信息丢失的可能性，所以只有使用显式的强制类型转换才能够将long类型转换成int类型。

### 1.5.4 结合赋值和运算符

+ 可以在赋值中使用二元运算符，这是一种很方便的简写形式。例如，x += 4; 等价于：x = x + 4;
+ 一般地，要把运算符放在=号左边，如*=或%=
+ 如果运算符得到一个值，其类型与左侧操作数的类型不同，就会发生强制类型转换。例如，如果x是一个int，则以下语句x+ =3.5 是合法的，将把x设置为(int)(x + 3.5)。

### 1.5.5 自增与自减运算符

+ 当然，程序员都知道加1、减1是数值变量最常见的操作。在Java中，借鉴了C和C++的做法，也提供了自增、自减运算符：n++将变量n的当前值加1, n--则将n的值减1。

```java
int n = 12;
n++;  // n = 13
```

+ 将n的值改为13。由于这些运算符会改变变量的值，所以它们的操作数不能是数值。例如，4++就不是一个合法的语句。

+ 实际上，这些运算符有两种形式；上面介绍的是运算符放在操作数后面的“后缀”形式。还有一种“前缀”形式：++n。

+ 后缀和前缀形式都会使变量值加1或减1。但用在表达式中时，二者就有区别了。

  + 前缀形式会先完成加1；而后缀形式会使用变量原来的值。

  ```java
  int m = 7;
  int n = 7;
  int a= 2 * ++m;// now a is 16, m=8
  int b= 2 * n++;// now b is 14, n=8
  ```

  > 建议不要在表达式中使用++，因为这样的代码很容易让人困惑，而且会带来烦人的bug。

### 1.5.6 关系和boolean运算符

+ Java包含丰富的关系运算符。要检测相等性，可以使用两个等号==。例如， 3 == 7 的值为 false。

+ 另外可使用 != 检测不相等。例如：3 != 7的值为true。

+ 最后，还有经常使用的<（小于）、>（大于）、<=（小于等于）和>=（大于等于）运算符。

+ Java支持三元操作符？:，这个操作符有时很有用。

  ```java
  condition ? expression1 : expression2
  ```

  + 如果条件为true，上面的表达式就为第一个表达式的值，否则计算为第二个表达式的值。例如，

  ```java
  x < y ? x : y
  ```

  + 会返回x和y中较小的一个。

### 1.5.7 位运算符

+ 处理整型类型时，可以直接对组成整型数值的各个位完成操作。这意味着可以使用掩码技术得到整数中的各个位。

```java
&("and")  |("or")  ^("xor") ~("not")
```

+ 这些运算符按位模式处理。

> 应用在布尔值上时，&和|运算符也会得到一个布尔值。这些运算符与&&和||运算符很类似，不过&和|运算符不采用“短路”方式来求值，也就是说，得到计算结果之前两个操作数都需要计算。另外，还有>>和<<运算符将位模式左移或右移。需要建立位模式来完成位掩码时，这两个运算符会很方便。

> 最后，>>>运算符会用0填充高位，这与>>不同，它会用符号位填充高位。不存在<<<运算符。

### 1.5.8 括号与运算符级别

+ 如果不使用圆括号，就按照给出的运算符优先级次序进行计算。同一个级别的运算符按照从左到右的次序进行计算

![image-20221114145428342](C:\Users\MYW\AppData\Roaming\Typora\typora-user-images\image-20221114145428342.png)

### 1.5.9 枚举类型

+ 有时候，变量的取值只在一个有限的集合内。

  + 例如：销售的服装或比萨饼只有小、中、大和超大这四种尺寸。当然，可以将这些尺寸分别编码为1、2、3、4或S、M、L、X。但这样存在着一定的隐患。在变量中很可能保存的是一个错误的值（如0或m）。

+ 针对这种情况，可以自定义枚举类型。枚举类型包括有限个命名的值。例如，

  ```java 
  enum Size {SMALL,MEDIUM,LARGE,EXTRA_LARGE};
  ```

  + 现在，可以声明这种类型的变量：

  ```JAVA 
  Size s =Size.MEDIUM;
  ```

  + Size类型的变量只能存储这个类型声明中给定的某个枚举值，或者null值，null表示这个变量没有设置任何值。

## 1.6 字符串

+ 从概念上讲，Java字符串就是Unicode字符序列。例如，串“Java\u2122”由5个Unicode字符J、a、v、a和 TM。

+ Java没有内置的字符串类型，而是在标准Java类库中提供了一个预定义类，很自然地叫做String。每个用双引号括起来的字符串都是String类的一个实例

  ```java
  String e = ""; //an empty string
  String greeting = "Hello";
  ```

### 1.6.1 子串

+ String类的substring方法可以从一个较大的字符串提取出一个子串。

  ```java
  String greeting = "Hello";
  String s = greeting.substring(0,3);// prints "Hel"
  ```

  + substring方法的第二个参数是不想复制的第一个位置。这里要复制位置为0、1和2（从0到2，包括0和2）的字符。在substring中从0开始计数，直到3为止，但不包含3。
  + substring的工作方式有一个优点：容易计算子串的长度。字符串s.substring(a, b)的长度为b-a。例如，子串“Hel”的长度为3-0=3。

### 1.6.2 拼接

+ 与绝大多数的程序设计语言一样，Java语言允许使用+号连接（拼接）两个字符串。

  ```java
  String expletive = "Expletive";
  String PG13 = "deleted";
  String message = expletive + PG13; 
  ```

+ 当将一个字符串与一个非字符串的值进行拼接时，后者被转换成字符串

  ```java
  int age = 13;
  String rating = "PG" + age;
  ```

+ 如果需要把多个字符串放在一起，用一个定界符分隔，可以使用静态join方法：

  ```java
  String all = String.jion("/","S","M","L","XL");
  //all is the string "S/M/L/XL"
  ```

### 1.6.3 不可变字符串

+ String类没有提供用于修改字符串的方法。

+ 如果希望将greeting的内容修改为“Help! ”，不能直接地将greeting的最后两个位置的字符修改为‘p’和‘! '。

  + 在Java中实现这项操作非常容易。首先提取需要的字符，然后再拼接上替换的字符串：

  ```java
  greeting = greeting.substring(0,3) + "p!";
  ```

  + 上面这条语句将greeting当前值修改为“Help!”。

### 1.6.4 检测字符串是否相等

+ 可以使用equals方法检测两个字符串是否相等。

  ```java
  "Hello".equals(greeting)
  ```

+ 要想检测两个字符串是否相等，而不区分大小写，可以使用equalsIgnoreCase方法。

  ```java
  "Hello".equalsIgnoreCase("hello")
  ```

+ 一定不要使用==运算符检测两个字符串是否相等！这个运算符只能够确定两个字符串是否放置在同一个位置上。

### 1.6.5 空串与NULL串

+ 空串""是长度为0的字符串。可以调用以下代码检查一个字符串是否为空

  ```java
  if(str.length() == 0)
  if(str.equals(""))
  ```

+ 空串是一个Java对象，有自己的串长度（0）和内容（空）。

+ 有时要检查一个字符串既不是null也不为空串，这种情况下就需要使用以下条件:

  ```java
  if(str != null && str.length != 0)
  ```

### 1.6.6 码点与代码单元

+ Java字符串由char值序列组成。

+ char数据类型是一个采用UTF-16编码表示Unicode码点的代码单元。

+ 大多数的常用Unicode字符使用一个代码单元就可以表示，而辅助字符需要一对代码单元表示。

+ length方法将返回采用UTF-16编码表示的给定字符串所需要的代码单元数量。例如：

  ```java
  String greeting = "Hello";
  int n = greeting.length(); //is 5
  ```

+ 要想得到实际的长度，即码点数量，可以调用：

  ```java
  int cpCount = greeting.codePointCount(0,greeting.length());
  ```

+ 调用s.charAt(n)将返回位置n的代码单元，n介于0～s.length()-1之间。例如：

  ```java
  char first = greeting.charAt(0); //first is "H"
  ```

+ 要想得到第i个码点，应该使用下列语句

  ```java
  int index = greeting,offsetByCodePoints(o,i);
  int cp = greeting.codePointAt(index);
  ```

### 1.6.7 String API

+ Java中的String类包含了50多个方法。令人惊讶的是绝大多数都很有用，可以设想使用的频繁非常高。下面的API注释汇总了一部分最常用的方法。

> **API** java.lang.string 1.0

+ char charAt (int index)
  + 返回给定位置的代码单元。除非对底层的代码单元感兴趣，否则不需要调用这个方法。
+  int codePointAt(int index) 5.0
  + 返回从给定位置开始的码点。
+ int compareTo(String other)
  + 按照字典顺序，如果字符串位于other之前，返回一个负数；如果字符串位于other之后，返回一个正数；如果两个字符串相等，返回0。
+ boolean equals(Object other)
  + 如果字符串与other相等，返回true。
+ boolean equalsIgnoreCase(String other)
  + 如果字符串与other相等（忽略大小写），返回true。
+  int length( )
  + 返回字符串的长度。
+ String substring(int beginIndex, int endIndex)
  + 返回一个新字符串。这个字符串包含原始字符串中从beginIndex到串尾或endIndex-1的所有代码单元。
+ String toLowerCase( )
+ String toUpperCase( )
  + 返回一个新字符串。这个字符串将原始字符串中的大写字母改为小写，或者将原始字符串中的所有小写字母改成了大写字母。
+ String trim( )
  + 返回一个新字符串。这个字符串将删除了原始字符串头部和尾部的空格。
+ String join(CharSequence delimiter,CharSequence... elements) 8
  + 返回一个新字符串，用给定的定界符连接所有元素。

> 在API注释中，有一些CharSequence类型的参数。这是一种接口类型，所有字符串都属于这个接口。现在只需要知道只要看到一个CharSequence形参，完全可以传入String类型的实参

### 1.6.8 构建字符串

+ 有些时候，需要由较短的字符串构建字符串，例如，按键或来自文件中的单词。

+ 采用字符串连接的方式达到此目的效率比较低。每次连接字符串，都会构建一个新的String对象，既耗时，又浪费空间。

+ 使用StringBuilder类就可以避免这个问题的发生。

  ```java
  StringBuilder builder = new StringBuilder();
  ```

+ 当每次需要添加一部分内容时，就调用append方法。

  ```java
  builder.append(ch); // appends a single character
  ```

+ 在需要构建字符串时就调用toString方法，将可以得到一个String对象，其中包含了构建器中的字符序列。

  ```java
  String completedString = builder.toString();
  ```

## 1.7 输入输出

### 1.7.1 读取输入

+ 要想通过控制台进行输入，首先需要构造一个Scanner对象，并与“标准输入流”System.in关联。

  ```java
  Scanner in = new Scanner(System.in);
  ```

+ 现在，就可以使用Scanner类的各种方法实现输入操作了。例如，nextLine方法将输入一行。

  ```java
  System.out.print("What is your name?");
  String name = in.nextLine();    
  ```

  + 在这里，使用nextLine方法是因为在输入行中有可能包含空格。要想读取一个单词（以空白符作为分隔符），就调用

  ```java
  String firstName = in.next();
  ```

  + 要想读取一个整数，就调用nextInt方法。

  ```java
  System.out.print("How old are you? ");
  int age = in.nextInt();
  ```

  + 与此类似，要想读取下一个浮点数，就调用nextDouble方法。

> 因为输入是可见的，所以Scanner类不适用于从控制台读取密码。Java SE 6特别引入了Console类实现这个目的。要想读取一个密码，可以采用下列代码：
>
> ```java
> Console cons = System.console();
> String username = cons.readLine("User name: ");
> char[] passwd = cons.readPassword("Password: ");
> ```
>
> > 为了安全起见，返回的密码存放在一维字符数组中，而不是字符串中。在对密码进行处理之后，应该马上用一个填充值覆盖数组元素
>
> > 采用Console对象处理输入不如采用Scanner方便。每次只能读取一行输入，而没有能够读取一个单词或一个数值的方法。

### 1.7.2 格式化输出

+ 可以使用System.out.print(x)将数值x输出到控制台上。

+ 在printf中，可以使用多个参数，例如：

  ```java
  System.out.printf("Hello, %s. Next year, you`ll be %d",name,age);
  ```

  + 每一个以%字符开始的格式说明符都用相应的参数替换。格式说明符尾部的转换符将指示被格式化的数值类型：f表示浮点数，s表示字符串，d表示十进制整数。

### 1.7.3 文件输入与输出

+ 要想对文件进行读取，就需要一个用File对象构造一个Scanner对象，如下所示：

  ```java
  Scanner in = new Scanner(Paths.get("myfile.txt"),"UTF-8");
  ```

  + 如果文件名中包含反斜杠符号，就要记住在每个反斜杠之前再加一个额外的反斜杠：“c:\\mydirectory\\myfile.txt”。

+ 要想写入文件，就需要构造一个PrintWriter对象。在构造器中，只需要提供文件名：

  ```java
  PrintWriter out = new PrintWriter("myfile.txt","UTF-8");
  ```

  + 如果文件不存在，创建该文件。可以像输出到System.out一样使用print、println以及printf命令。

## 1.8 控制流程

+ Java使用条件语句和循环结构确定控制流程。

### 1.8.1 块作用域

+ 块（即复合语句）是指由一对大括号括起来的若干条简单的Java语句。

+ 块确定了变量的作用域。

+ 一个块可以嵌套在另一个块中。

  + 下面就是在main方法块中嵌套另一个语句块的示例。

    ```java
    public static void main(String[] args)
    {
        int n;
        ……
        {
            int k;
            ……
        } 
    }
    ```

  + 但是，不能在嵌套的两个块中声明同名的变量。

### 1.8.2 条件语句

