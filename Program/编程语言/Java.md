# Java学习笔记
# JavaSE基础
## 基础定义
* JVM（Java Virtual Machine）即Java虚拟机，负责执行指令，管理数据、内存、寄存器，包含在JDK中。是JVM使Java能“一次编译，到处运行”。
* JDK（Java Development Kit）即Java开发工具包。JDK = JRE + Java的开发工具（java,javac等）
* JRE(Java Runtime Environment)即Java运行环境。JRE = JVM + Java的核心类库（类）
* 安装JDK后要配置环境变量path。DOS（Disk Operating System，即磁盘操作系统。cmd即command缩写，为Windows命令提示符，是Windows输入DOS命令的程序）命令行执行时先在当前目录下查找，如果没有便去找path环境变量指定的目录去找。搜索环境变量（改个人的不容易改坏，一般人也不是多账户，建议改个人环境变量而不是系统的），增加JAVA_HOME的环境变量，路径填JDK安装的目录。再编辑path环境变量，增加%JAVA_HOME%\bin路径。再打开cmd，任意目录下输入javac，java，以及java -version**(注意java后有个空格！)**来验证环境变量是否配置成功即可。

## DOS基础操作
* 路径：相对路径：从当前目录开始定位形成的路径（访问上一级用..）绝对路径：从顶级目录盘符开始定位形成的路径
* 常用命令
  1. **dir**，查看当前目录有什么内容
  2. **cd**，切换到其它盘下
  3. **tree**，查看指定目录下所有子级目录
  4. **cls**，清屏
  5. **exit**，退出DOS
  6. **md**，创建目录
  7. **rd**，删除目录
  8. **copy**，拷贝文件
  9. **del**，删除文件
  10. **echo**，输入内容到文件
  11. **move**，剪切

* 用cmd调用编译，在待编译的.java文件目录下，于地址栏输入cmd调出DOS命令行。"javac xx.java"编译（c即代表compiler编译器），有中文注释时要注意要改编辑器保存的编码格式，必须改成GBK！"java xx"编译，不要再带后缀.class！java运行是运行那个“类”，自己会带.class而无需自己多此一举。
* 编译前的.java文件可称为源文件，编译后的.class文件可称为字节码文件，字节码文件才可交给JVM运行
* cmd输入指令时，可以用方向上键选择之前输过的指令；也可以输入文件名的前两个字母再按Tab键自动补全文件名节省时间

## Java开发注意事项和细节说明
1. Java源文件以.java为扩展名，源文件的基本组成部分是类（class）。
2. Java应用程序的执行入口是main()方法，有固定的书写格式public static void main(String[] args) {...}
3. Java语言严格区分大小写
4. Java语句以分号结尾
5. 一个源文件中最多只能有一个public类，但其它类的个数不限。也可以将main方法写在非public类中，然后指定运行非public类，这样入口方法就是非public的main方法
6. 如果源文件包含一个public类，则文件名必须按该类名命名！

### Java转义字符
常用（与C类似）
1. \t:一个制表符，实现对齐功能（固定空格数）
2. \n：换行符
3. \\：一个\
4. \r：一个回车（把光标挪到当前行的第一个位置）
5. 单引号双引号同样需要转义输出

### Java代码规范
1. 类、方法的注释，要以javadoc的方式来写
2. 非javadoc的注释，给代码维护者看，告知为何如此写，如何修改，注意什么问题等
3. 选中多行按Tab一起缩进，按Shift+Tab一起向左移动（VSCode中Ctrl+]/[功能类似）
4. 运算符两边加空格
5. 源文件用UTF-8编码
6. 行宽不要超过80字符
7. 次行风格（另起一行写大括号）和行尾风格（行尾接大括号），韩推荐行尾风格

#### 标识符命名规则与规范
##### 规则（必须遵守）
1. 由26个英文字母大小写、0~9、_和$组成
2. 不能由数字开头
3. 不能使用关键字和保留字(现有Java版本未使用，但以后可能使用)，但可包含
   * 保留字：byValue,cast,future,generic,inner,operator,outer,rest,var,goto,const
4. Java严格区分大小写，长度无限制
5. 不能含有空格

##### 规范（更加专业）
1. 包名:多单词组成时，所有字母都小写（school.bus.bike）
2. 类名、接口名:多单词组成时,所有单词首字母大写【大驼峰法】(SchoolBus)
3. 变量名、方法名：多单词组成时，第一个单词首字母小写，第二个单词开始每个单词首字母大写【小驼峰法/驼峰法】(schoolBus)
4. 常量名：所有字母都大写。多单词组成时，每个单词用下划线连接(SCHOOL_BUS)
5. 其它细节可查阅文档

#### 注释
1. 单行注释：//
2. 多行注释：/*……*/
3. 文档注释：注释内容被JDK工具javadoc解析，生成一套以网页文件形式体现的该程序的说明文档，一般写在类
>1. 基本格式：
/**
\* @javadoc标签
\* @javadoc标签
\*/ 
>2. 生成文档注释方法：
    javadoc -d 文件夹名（路径） -javadoc标签 -javadoc标签 文件名.java
>3. 使用：打开文件夹下的index.html即可
>4. javadoc标签集合：@author    @version    （后续补充）



## 基础语法
### 变量
* 类型
  1. 局部变量：方法内变量，方法结束后即销毁
  2. 成员变量：定义于类中，方法体之外
  3. 类变量：定义于类中，方法体之外，但必须声明为static类型     

* 加号使用
  1. 左右两边均数值，则加法
  2. 左右两边有一方为字符串，则拼接

### 数据类型
1. 基本数据类型
  数值型：byte(1),short(2),int(4),long(8),float(4),double(8)
  字符型：char(2)
  布尔型：boolean(1)
2. 引用数据类型 
  类(class)，接口(interface),数组([])，字符串(string)

#### 整型
* byte(-128~127)
* short(-2^15~2^15-1)
* int(-2^31~2^31-1)
* long(-2^63~2^63-1)

#### 浮点型
* Java的浮点型常量（具体值）默认为double型，声明float型常量则需在后面加f或F
* 浮点型科学计数法表示：5.12e2 = 512.0，即5.12*10的二次方；5.12E-2 = 0.0512，即5.12*10的负二次方
* 浮点型计算结果可能无限接近数学正常计算结果，但由于精度问题无法相等，注意比较两小数是否相等时应注意！若必须比较，则应以两个数的差值的绝对值（Math.abs()），在某个精度范围内判断,即规定该绝对值 < 0.0000001即认为相等诸如此类

#### char型
* char本质是一个整数,可参与运算
* 想输出字符对应编码，需要强制类型转换，如`(int)char`
* 字符型可直接存放一个数字，但输出内容是该数字对应编码的字符
* Java的char类型对应Unicode码
* 常见编码表：
  >ASCII，一个字节表示，一个字节可表示256个字符，但ASCII只用了128个；
  >Unicode，两个字节表示，字母和汉字均占用两字节，较浪费空间；但不会乱码；且0-127字符与ASCII码相同，兼容ASCII码
  >UTF-8，1-6个字节表示一个符号，根据不同的符号改变字节长度；Unicode的改进；互联网使用最广

#### boolean型
* 布尔类型只能取值true和false，无null
* 占1个字节；适用于逻辑运算
* 不能用0或非0的整数代替false和true，和C语言不同

#### 数组
* for循环遍历时，写i < n而不写i ≤ n-1,写n表示数组元素个数更清晰
* 可用 数组名.length 得到数组的长度
* 使用方式
  1. 动态初始化
    > 数据类型 数组名[] = new 数据类型[大小]，如int a[] = new int[5]【声明+创建】
    > 数据类型 数组名[]; 数组名 = new 数据类型[大小];【先声明再创建，声明完是null】
  2. 静态初始化
    > 数据类型 数组名[] = {元素值，元素值……}
##### 使用注意事项和细节
1. 数组是多个相同数据类型的组合，实现对这些数据的统一管理
2. 数组中的元素可以使任何数据类型(基本和引用)，但不能混用！
3. 数组创建后如果没有赋值，则有默认值：int,short,byte,long = 0; float,double = 0.0;char = \u0000; boolean = false; String = null;
4. 数组为引用类型，数组型数据是对象(object)
5. 赋值机制
   * 基本数据类型赋值就是值传递，相互不影响
   * 数组在默认情况下是引用传递，赋的值是地址
6. 数组拷贝不能直接赋值数组，需要循环遍历一一赋值
##### 数组扩容与缩减
* 扩容思路
  1. 定义新数组`int[] arrNew = new int[arr.length + 1]`
  2. 遍历arr数组，把arr元素拷贝到arrNew
  3. 把新值赋给arrNew[arrNew.length - 1]
  4. 让arr指向arrNew，则老arr数组被销毁

``` Java
//自己写的一段动态扩容实例
//升级内容：原数组升序，则添加元素后同样升序
int[] arr = {1, 22, 57};
  Scanner ms = new Scanner(System.in);
  for (int i = 0; i < arr.length; i++) {
    System.out.print(arr[i] + "\t");
  }
  System.out.println();
  while(true){
    int[] arrNew = new int[arr.length + 1];
    System.arraycopy(arr, 0, arrNew, 0, arr.length);
    int New = ms.nextInt();
    int NewIndex = -1;
    for (int i = 0; i < arr.length; i++) {
        if(New <= arr[i]){
            NewIndex = i;
            arrNew[NewIndex] = New;
            break;
        }
    }
    if(NewIndex == -1){
        NewIndex = arr.length;
        arrNew[NewIndex] = New;
    }
    for (int i = NewIndex; i < arr.length; i++) {
        arrNew[i+1] = arr[i];
    }
    arr = arrNew;
    for (int i = 0; i < arr.length; i++) {
        System.out.print(arr[i] + "\t");
    }
    System.out.println("输入y/n选择是否结束添加");
    if(ms.next().equals("n")) break;
  }
```

* 缩减
``` Java
//自己写的删除数组元素实例
int[] arr = {1, 2, 3, 4, 5};
Scanner ms = new Scanner(System.in);
System.out.println("目前的arr数组如下：");
for (int i = 0; i < arr.length; i++) {
    System.out.print(arr[i] + "\t");
}
while(true){
    System.out.println("输入y/n选择是否结束删除");
    if(ms.next().toString().equals("n")) break;
    if(arr.length == 1){
        System.out.println("已经删没啦！程序要结束啦！");
        break;
    }
    int[] arrNew = new int[arr.length - 1];
    for (int i = 0; i < arrNew.length; i++) {
        arrNew[i] = arr[i];
    }
    arr = arrNew;
    System.out.println("目前的arr数组如下：");
    for (int i = 0; i < arr.length; i++) {
        System.out.print(arr[i] + "\t");
    }
}
```

##### 二维数组
* 定义：二维数组的每一个元素都是一个一维数组。
  * 语法：数据类型[][] 数组名 = new 数据类型[大小][大小];`int[][] arr = {{0, 1}, {1, 2}};`
    ``` Java
    //三种定义形式
    int[][] arr;
    int arr[][];
    int[] arr[];
    //案例
    int[] x, y[];
    //则x为一维数组，y为二维数组，勿混淆！

    //列数不定(一维数组元素数不定)
    int[][] arr = new int[3][];
    //创建二维数组，有3个一维数组，但每个一维数组为空
    for(int i = 0; i < arr.length; i++){
      //给一维数组new开空间，若不开则arr[i]指向null
      arr[i] = new int [i + 1];
    }
    ```

* 遍历(输出)
``` Java
for(int i = 0; i < arr.length; i++){
  //arr.length表示二维数组的元素(一维数组)个数
  for(int j = 0; j < arr[i].length; j++){
    //arr[i].length表示二维数组的元素一维数组的长度
    System.out.println(arr[i][j] + " ");
  }
  System.out.println();//换行
  //arr[i]表示二维数组的第i+1个元素(一维数组)
}
```

实例：杨辉三角
``` Java
int[][] YangHui = new int[13][];

  for (int i = 0; i < YangHui.length; i++) {
      YangHui[i] = new int[i + 1];
      for (int j = 0; j < YangHui[i].length; j++) {
          if(j == 0 || j == YangHui[i].length - 1) YangHui[i][j] = 1;
              else YangHui[i][j] = YangHui[i - 1][j - 1] + YangHui[i - 1][j];
      }
  }
  for (int i = 0; i < YangHui.length; i++) {
      for (int j = 0; j < YangHui[i].length; j++) {
          System.out.print(YangHui[i][j] + "\t");
      }
      System.out.println();
  }
```

### 基本数据类型转换
#### 自动类型转换
* 赋值或运算时，低精度自动向高精度转换
* char-int-long-float-double
* byte-short-int-long-float-double
* 自动提升原则：多种类型数据混合运算时，系统将先把所有类型转换成容量最大的数据类型，再进行计算
* (byte,short)和char不能相互自动转化；但他们之间可以计算，计算时首先转换为int类型
* 精度大赋值给精度小的数据类型时会报错，反之则自动类型转换
* boolean不参与转换
* 赋值具体数据系统会进行判断是否处于范围内，用变量赋值则直接先判断变量范围。如`int a = 1; byte b = 1;//true byte c = a;//false`
#### 强制类型转换
* 强制转换符"()",可能造成数据精度降低或溢出
* `int a = (int)1.9`则 a = 1;
* 强转符号只针对最近的操作数有效，不过也可用括号提升优先级
* char可以保存int常量值，但不能保存int变量值，需要强转
#### 基本数据类型和String类型的转换
* 基本转String：`基本类型值+""`后加引号即可
* String转基本：通过基本类型的包装类调用parsexx方法即可`String s = "123"; int a = Integer.parseInt(s); double b = Double.parseDouble(s);`
* String转char：把String第x个字符赋给char`char c = s.charAt(0)`,同数组从0开始

### 算术运算符





### 进制
* 整数四种进制
  1. 二进制：0，1；满2进1；以0b或0B开头
  2. 十进制：0~9；满10进1 
  3. 八进制：0~7；满8进1；以0开头表示
  4. 十六进制：0~9和a(10)~F(15)；满16进1；以0x或0X开头表示；此处A~F不区分大小写

#### 进制转换
* 转十进制
  1. 二转十：从最低位(右边)开始，每个位上的数提取出来，乘2的(位数-1)次方，再求和。如：0b1011 = 1 * 2^(1-1) + 1 * 2^(2-1) + 0 * 2^(3-1) + 1 * 2^(4-1) = 1 + 2 + 8 = 11
  2. 八转十：从最低位(右边)开始，每个位上的数提取出来，乘8的(位数-1)次方，再求和。如：0234 = 4 + 24 + 128 = 156
  3. 十六转十：从最低位(右边)开始，每个位上的数提取出来，乘16的(位数-1)次方，再求和。如：0x23A = 10 + 48 + 32*16 = 570

* 十进制转
  1. 十转二：将该数不断除以2，直到商为0为止，再将每步所得余数倒过来。如：34 = 0b100010(实际应凑够4位的整数倍为0b0010 0010)
  2. 十转八：将该数不断除以8，直到商为0为止，再将每步所得余数倒过来。如：131 = 0203
  3. 十转十六：将该数不断除以16，直到商为0为止，再将每步所得余数倒过来。如：237 = 0xED

* 二进制转
  1. 二转八：从最低位(右边)开始，将二进制数每3位一组，转成对应八进制数即可。如：0b1101 0101 = 0325
  2. 二转十六：从最低位(右边)开始，将二进制数每4位一组，转成对应十六进制数即可。如：0b1101 0101 = 0xd5

* 转二进制
  1. 八转二：八进制数每1位，转成对应的一个3位的二进制数。如：0237 = 0b 010 011 111(实际凑够4位整数倍添0或删0为0b1001 1111)
  2. 十六转二：十六进制数每1位，转成对应的一个4位的二进制数。如：0x23B = 0b 0010 0011 1011【简单算法：每一位都先写1111，再看差多少再改多少】

* 位运算
符号：1 >> 2(1右移2位)；1 << 2(1左移2位)；3 >>> 2(3算术右移2位)；~2(按位取反)；2 & 3(按位与3)；2 | 3(按位或3)；-3 ^ 3(按位异或3)

### 原码、反码与补码
#### 有符号
1. 二进制的最高位是符号位，0正1负
2. 正数的原码、反码、补码都一样(三码合一)
3. 负数的反码 = 原码符号位不变，其它位取反(0、1互换)
4. 负数的补码 = 反码 + 1；负数的反码 = 补码 - 1
5. 0的反码、补码还是0
6. Java没有无符号数，均有符号
7. 计算机运算时，均以补码的方式运算
8. 看运算结果要看原码


# 面向对象编程(OOP,Object-Oriented programming)
## 类与对象
* 为什么要用类与对象——现有技术（单独定义变量或数组存储）效率低，不利于数据的管理
### 类的定义完善
``` Java
package 包名;//4
class 类名 extends 父类名 implements 接口名{//5、7
  成员变量;//1
  构造方法;//2
  成员方法;//3
  代码块//6
}
```
* 类是一种抽象数据类型(Cat)，类有属性和行为
``` Java
//定义一个猫类
Class Cat{
  String name;
  int age;
}
```
* 对象是类的一个具体实例(HelloKitty)
``` Java
//创建一个猫对象（实例化一只猫）

//先声明再创建
Cat cat1;//声明对象
cat1 = new Cat();//没有new就不分配空间

//直接创建
Cat cat1 =  new Cat();
//1.new Cat() 创建了一只猫
//2.Cat cat1 =  new Cat(); 把创建的这只猫赋给cat1, cat1就是一个实例化对象(名)

cat.name = "neko";
cat.age = 2;

//不用名的创建对象为匿名对象，只能使用一次，用后即销毁
new Cat().eat
```
* 对象在内存中的存在形式
  cat1（对象名/对象引用）->地址1(包含属性的基本数据类型值和非基本数据类型的地址2->非基本数据类型的值)，地址1的所有内容加起来是对象
* 对象1->对象2，则对象1指向对象2的地址1，对象1和对象2将是一体的。而非单纯把对象2的值赋给对象1
* 类之间的关系
  1. 依赖(dependence,"use-a")：一个类的方法使用或操纵另一个类的对象，则这个类依赖于另一个类
  2. 聚合(aggregation,"has-a"):一个类的对象包含另一个类的对象
  3. 继承(inheritance,"is-a"):一个类被另一个类继承拓展
* UML(Unified Modeling Language)统一建模语言，用来绘制类图，描述类之间的关系
* 类什么时候被加载！
  1. 创建对象实例时(new)
  2. 创建子类对象实例时，父类也会被加载
  3. 使用类的静态成员时(属性、方法)

### 类与对象的内存分配机制
#### Java的内存结构分析
1. 栈：一般存放基本数据类型（局部变量）
2. 堆：存放对象
3. 方法区：常量池，类加载信息
4. 示意图
#### Java创建对象的流程简单分析
1. 先加载Cat类信息（属性和方法信息，Cat.class，只加载一次）
2. 在堆中分配空间（地址），
3. 完成对象初始化【默认初始化；显式初始化；构造器初始化】
4. 把对象在堆中的地址赋给cat1，cat1就指向对象

### 属性
* 属性 = 成员变量 = field(字段);属性是类的一个组成部分
* 若属性不赋值，有默认值，规则与数组一致

## (成员)方法(Method)
* 定义
访问修饰符 返回数据类型 方法名(形参列表){
    方法体语句;
}
* 创建示例
``` Java
Class Cat{
  String name;
  int age;
//1.public表示方法公开;void表示方法无返回值
//2.speak()：speak方法名，()形参列表
  public void speak(){
    System.out.println("我是一只好猫");
  }
}
  public int getSum(int x, int y){
      int sum = x + y;
      return sum;
  }
```
* 调用示例
``` Java
//先创建对象，才能调用方法
  Class cat1 = new Cat();
  cat1.speak();
  int s = cat1.sum(2,4);
```
### 方法的调用机制
1. 当程序执行到方法时，会开辟一个独立的栈空间
2. 当方法执行完毕，或执行到return语句时就会返回到调用方法的地方，并释放方法所调用方法的栈空间
3. 返回后继续执行后面的方法，当main方法（栈）执行完毕，则程序结束，main方法栈空间也释放
### 方法使用细节
1. 一个方法只能有一个返回值（若想返回多个值，可以考虑用数组存储结果）
2. void方法不写return或单写return
3. 方法不能嵌套定义
4. 定义在同一个类中的方法相互调用时，直接调即可，不需要创建对象
5. 跨类定义中调用方法时，需要通过对象名调用（即需要先创建对象）【也与访问修饰符有关】
### 方法的传参机制
* 引用类型传递的是地址（传递的也是值，但值是地址），可以通过形参影响实参【但形参引用类型置空，只是形参置空而不影响主栈实参！】
* 可以通过对象比较看是否为同一个对象 

### overload(方法重载)
* 介绍：Java中允许同一个类中，有多个同名方法的存在，但要求形参列表不一致！例如：System.out.println();其中out是PrintStream类型
* 作用：减少了起名和记名的麻烦
* 注意事项
  1. 方法名必须相同
  2. 参数列表必须不同（参数类型或顺序，起码有一个不同，参数名无要求）
  3. 返回类型无要求
### 可变参数
* 概念：Java允许将同一个类中多个同名同功能但参数个数不同的方法封装成一个方法，就可通过可变参数实现。此时用可变参数优化方法重载
* 基本语法：访问修饰符 返回类型 方法名(数据类型... 形参名){}
* 示例
``` Java
//1."int..."表示接受的是可变参数，类型是int，即可接收多个int(0~多个)
//2.可变参数可以当数组使用，即nums可当做数组
  public int sum(int... nums){
    System.out.println("接收的参数个数"  + num.length);
    return 0;
  }
```
* 细节
  1. 实参可以为0~任意多个
  2. 实参可以为数组
  3. 可变参数本质就是数组
  4. 可变参数可以和普通参数一起放在形参列表，但必须让可变参数出现在最后
  5. 一个形参列表只能出现一个可变参数
 
### Constructor(构造器/构造方法)
* 是类的一种特殊方法，完成对新对象的初始化，而非创建对象
* 【修饰符】 方法名(形参列表){
      方法体}

* 示例
``` Java
//创建对象并调用构造器初始化
Person p1 = new Person("Kiro",80);

class Person{
    String name;
    int age;
//构造器无返回值，也不能写void
//构造器名称和类Person相同
//构造器参数列表和成员方法一样
    public Person(String pName, int pAge){
      System.out.println("构造器被调用，完成对象的属性初始化");
      name = pName;
      age = pAge;
    }
  }
```
1. 构造器修饰符可以默认可以自己加
2. 构造器的调用，由系统完成，自己不能去用
3. 构造器总与new一起调用
4. 一个类可以定义多个不同的构造器，即构造器重载
5. 若未定义构造器，系统会自动给类生成一个默认无参构造器（也叫默认构造器），比如Person(){};可以用javap指令反编译验证
6. 一但自己定义了构造器，会覆盖默认构造器，不可再使用，除非再显式地定义一下，即Person(){};

## Scope(作用域)
1. 全局变量(属性)，作用域为整个类体，可不赋值，因为有默认值
2. 局部变量一般是指在成员方法中定义的变量或代码块中定义的变量，必须赋值后使用，因为无默认值
3. 属性和局部变量可以重名，访问时遵循就近原则
4. 属性与对象同生共死，局部变量与代码块（方法）同生共死
5. 全局变量可被本类和其它类使用（通过对象调用）
6. 局部变量只能在本类对应的方法中使用
7. 属性可加访问修饰符而局部变量不可

## this
* Java虚拟机会给每个对象分配this，代表当前对象
* 用this使构造器代码更易懂简洁
``` Java
Person p1 = new Person("Kiro",80);
class Person{
    String name;
    int age;

    public Person(String name, int age){
      //this.name就是当前对象的属性name；age同理
      this.name = name;
      this.age = age;
    }
}
```
* this是每个对象都有的隐藏属性，指向自己的地址
* 哪个对象调用，this就代表哪个对象
* 可以用hashCode（地址用整数表示，近似可看成地址）方法验证`System.out.println(p1.hashCode());`
* this细节
  1. this可以用来访问本类的属性、方法、构造器
  2. this用于区分当前类的属性和局部变量
  3. 访问成员方法的语法：this.方法名(参数列表);
  4. 访问构造器语法：this(参数列表);**只能在构造器中使用（在构造器中访问另一个构造器）！并且这条语句必须放在第一条**
  5. this不能在类定义的外部使用，只能在类定义的方法中使用

## Package(包)
* 包的三大作用
  1. 区分相同名字的类
  2. 当类很多时方便管理类
  3. 控制访问范围
* 基本语法`package 包名`
* 本质：创建不同的文件夹来保存类文件
* 用同名类时要注明包或者提前导入包
### 包的命名
* 规则：只能包含数字、字母、下划线、点号，但不能用数字开头，不能是关键字或保留字
* 规范：一般是小写字母+点号“com.公司名.项目名.业务模块名”

* 常用包
1. java.lang：基本包，默认引入
2. java.util：系统的提供工具包，如Scanner
3. java.net：网络包
4. java.awt:java界面开发，GUI

### 使用细节
* 导入包：import 包，可以引入整个包，也可以只引入包下面所需要的类，建议需要什么导啥
* Package作用是声明当前类所在的包，需要放在类（文件）的最上面，一个类中最多只有一句Package
* import语句放在Package语句下面，条数顺序无影响

## Modifier(访问修饰符)
* 作用是控制方法访问权限（使用范围）；不写则是default默认
* 访问权限特点

|访问控制修饰符|同类|同包|子类|不同包|
|--|--|--|--|--|
|public|√|√|√|√|
|protected|√|√|√|×|
|默认|√|√|×|×|
|private|√|×|×|×|
* 注意事项
  1. 访问修饰符可修饰类中的属性，成员方法和类
  2. 只有默认和public才能修饰类，并遵循上述访问权限特点
  3. 成员方法访问规则同属性

## Encapsulation(封装)
* 封装就是把抽象出的数据(属性)和对数据的操作(方法)封装在一起，数据被保护在内部，程序的其它部分只有通过被授权的操作(方法)，才能对数据进行操作
* 好处：隐藏实现细节；可对数据验证，保证其安全合理
### 封装实现步骤
1. 将属性进行私有化【不能直接修改属性】
2. 提供一个公共的(public)set方法，用于对属性判断并赋值
``` Java
public void setXxx(类型 参数名){
  //Xxx即为该属性
  //加入数据验证的业务逻辑
  属性 = 参数名;
}
``` 
3. 提供一个公共的(public)get方法，用于获取属性的值
``` Java
public 数据类型 getXxx(){
  //权限判断，Xxx即为该属性
  return xx;
}
```
* 自己写太慢，可以用IDEA快捷键插入模板
* 单纯构造器可以绕过封装，把set方法放入构造器中即可

## Inheritance(继承)[Extends]
* 多个类的属性方法有较多相似，抽象出Parent class(父类)、Superclass(超类)或Base class(基类)，在其中定义共有的属性方法，则所有继承父类的Subclass(子类)、Child class(孩子类)或Derived class(派生类)不需要再重新定义这些属性和方法
* 基本语法：`class 子类 extends 父类{}`
* 解决代码复用性问题，提高代码扩展性和维护性
### 细节
1. 子类继承了所有的属性和方法，但私有属性和方法不能在子类直接访问，要用通过公共方法间接去访问
2. 子类必须调用父类的构造器，完成父类的初始化
3. 创建子类对象时，不管用子类的哪个构造器，默认总会调用父类的无参构造器（隐藏一句`super()`）若父类没有无参构造器，则必须在子类构造器中用super指定使用父类的哪个构造器完成对父类的初始化工作
4. 若想指定调用父类某个构造器，则显式调用：`super(参数列表)`
5. `super()`使用时必须放在构造器的第一行（优先调用父类构造器），也只能在构造器中使用
6. super()和this()都只能放在构造器第一行，所以不能共存于同一构造器。有this()则先执行this而无默认super()
7. Java所有类都是Object类的子类，Object是所有类的基类(父类)
8. 父类构造器调用不限于直接父类，将一直往上追溯直到Object类(顶级父类)
9. 子类最多只能继承一个父类(直接继承)，即Java是单继承机制
10. 不能滥用继承，子类和父类必须满足is-a的关系(子类xx是父类xx)
### 查找关系
* 访问子类属性，按照查找关系返回信息
1. 先看子类是否有该属性
2. 若有且可访问，则返回该信息
3. 若无，则看父类是否有该属性
4. 若有则2
5. 若无，则3继续找上级父类，直到Object
6. 若碰到私有无法访问，则直接报错，不会跳过继续查找
``` Java
class Grandpa{
  String name = "ye";
  String hobby = "play";
}
class Father extends Grandpa{
  String name = "ba";
  int age = 49;
  private int money = 0;
}
class Son extends Father{
  String name = "er";
}
Son son = new Son();
son.name = ?    //er
son.age = ?     //49
son.hobby = ?   //play
son.money = ?   //error，无法访问
```

## Super
* super代表父类的引用，用于访问父类的属性、方法、构造器
### 基本语法
1. `super.属性名`，访问父类属性，但不能访问父类private属性
2. `super.方法名(参数列表)`，访问父类方法，但不能访问父类private方法
3. `super(参数列表)`访问父类构造器，只能放在构造器的第一句，只能出现一句
### 使用细节
1. 调用父类构造器，分工明确，各自初始化
2. 当子类中有和父类中成员(属性和方法)重名时，访问父类成员必须通过super。若没有重名，则super、this、直接访问是一样效果【方法调用先找本类，无则找父类，与属性访问】
3. super访问不局限于父类，父类无则继续会往上查找
4. this和super极其相似，一个从本类查，一个从父类查，机制大体相似

## override(方法重写/覆盖)
* 方法覆盖就是子类有一方法与父类某一方法的名称、参数和返回类型（有特例）都一样，则称该子类方法覆盖了父类那个方法
* 子类方法返回类型和父类方法返回类型一样，或是父类返回类型的子类；如父类返回Object，子类返String
* 子类方法不能缩小父类方法的访问权限

## Polymorphism(多态)
* 方法或对象具有多种形态，是OOP的第三大特征，多态建立在封装和继承的基础之上
### 具体体现
1. 方法的多态：overload、override
2. 对象的多态（重难点）
   1. 一个对象的编译类型和运行类型可以不一致
   2. 编译类型在定义对象时就确定了，无法改变；而运行类型是可以变化的
   4. 编译类型看定义时=的左边，运行类型看=的右边
   `Animal animal = new Dog();`animal编译类型是Animal，运行类型是Dog
   `animal = new Cat();`animal的运行类型变成Cat，但编译类型仍是Animal
### 细节
* 前提：两个对象(类)存在继承关系
* 多态的向上转型
  1. 本质：父类的引用指向了子类的对象
  2. 语法：`父类类型 引用名 = new 子类类型();`
  3. 特点
     1. 编译类型看左边，运行类型看右边
     2. 可以调用父类中的所有成员(需遵守访问权限)
     3. 不能调用子类中特有成员
     4. 最终运行效果看子类的具体实现 
* 多态的向下转型
  1. 语法：`子类类型 引用名 = (子类类型)父类引用`
  2. 只能强转父类的引用，不能强转父类的对象
  3. 要求父亲的引用必须指向的是当前目标类型的对象
  4. 当向下转型后，可以调用子类类型中的所有成员
* 属性无重写之说，属性的值看编译类型
* 可用getclass()方法查看运行类型
* instanceOf比较操作符，用于判断对象的运行类型是否为xx类型或xx类型的子类型`aa instanceof bb`,返回bool类型值
* Java的动态绑定机制
  * 当调用对象方法时，该方法会合该对象的内存地址/运行类型绑定
  * 当调用对象属性时，没有动态绑定机制，哪里声明，哪里使用
### 应用
#### 多态数组
数组定义类型为父类类型，保存实际元素类型为子类类型
* 用instanceof判断，向下转型来调用子类特有方法
#### 多态参数
方法定义的形参为父类类型，实参类型允许为子类类型

## Object类
### equals()
* "=="比较运算符
  1. 既可以判断基本类型，又可以判断引用类型
  2. 若基本类型则判断值是否相等
  3. 若引用类型则判断地址是否相等，即判断是否为同一个对象
* equals只能判断引用类型，默认(Object)判断地址是否相等，子类(String,Integer等)重写该方法，判断值是否相等
* 可看JDK中源码自己判断
* 也可自己根据需要override equals方法
### hashCode()
1. 提高具有Hash结构的容器的效率
2. 两个引用，如果指向同一个对象，则Hash值一样
3. 两个引用，如果指向不是同一对象，则Hash值不同
4. Hash值主要根据地址号来，Hash值不等价于地址
5. 集合中，有需要也会override
### toString()
* 默认返回：全类名(包名+类名)+@+十六进制Hash
* 子类往往override，用于返回对象的属性信息
* 当直接输出一个对象时，toString方法会被默认调用
### finalize()貌似要被删
* 当对象成为垃圾时(没有任何引用)，垃圾回收器就会回收(销毁)对象。销毁对象前，会调用该对象的finalize方法
* 可以重写finalize，写自己的业务逻辑代码，如释放资源，数据库连接，打开文件等操作
* 垃圾回收机制调用是由系统决定，也可以通过System.gc()主动触发垃圾回收机制
* 实际开发几乎不用，应付面试而已

## Debug(断点调试)
* 断点调试过程中是运行状态，是以对象的运行类型来执行的
* 定义：在程序某一行设置断点(Breakpoint)，调试时程序运行到断点就会停止，自己可以一步一步往下调试，找Bug

## 类变量/静态变量
* 对应概念：普通属性、普通成员变量、非静态属性、非静态成员变量、实例变量
* 类变量会被该类的所有对象实例共用
* 类变量可以通过对象名/类名（推荐）来访问
* 定义语法：`访问修饰符 static 数据类型 变量名`
* 类变量在类加载时就初始化了，即使未创建对象也可使用；类无则无，与对象无关

## 类方法/静态方法
* 大部分与类变量相似，类比即可
* 定义语法`访问修饰符 static 数据类型 变量名`
* 当方法中不涉及到和对象相关的成员时，可将其设计为静态方法，提高开发效率。例如工具类utils里面的Math、Array、Collection类方法
* 类方法里无this，super这样与对象有关的关键字
* 静态方法中只能访问静态变量/静态方法

## main方法语法
### 语法解释
* `public static void main(String[] args)`
1. public: main方法是JVM调用的,不在一个类，所以要用public
2. static: 执行时不必创建对象，故用static
3. void: JVM不需要返回值
4. main：主方法名，也有提示作用
5. String[] args：字符串数组，接受参数，参数从命令行传入（idea等也可以），即java xxx a b c，"a,b,c"即为传入的三个参数，传入String[] args数组内了。由于args是形参名，所以实际上随便写都可以嘿嘿！
### 提示
* main方法中，可以直接调用main方法所在类的静态方法或静态属性
* 但同样不能直接访问该类中的非静态成员，必须借助对象！

## 代码块
* 又名初始化块，属于类中成员，类似于方法。但无方法名，无返回，无参数，只有方法体，而且不用通过对象或类显式调用，而是加载类或创建对象时隐式调用
* 基本语法：`[修饰符]{代码};`（修饰符可选，写的话也只能写static）（分号也可写可不写）
### 优点（用处）
* 相当于对构造器的补充机制，可以做初始化操作
* 应用场景：若多个构造器内都有重复语句，可以抽取到初始化块中，减少代码冗余
### 细节
* 代码块先于构造器运行
* static静态代码块，作用就是对类进行初始化操作，随类的加载而执行，并且只会执行一次
* 普通代码块，则每创建一个对象就会执行一次，但只是类加载则不调用
* 创建一个对象时，在一个类的调用顺序：
  1. 调用静态代码块和静态属性初始化（二者优先级相同，同时有多个，则按定义顺序调用）
  2. 调用普通代码块和普通属性初始化（二者优先级相同，同时有多个，则按定义顺序调用）
  3. 调用构造方法
* 构造器最前面不但隐含一个super()，还调用了普通代码块，最后再执行构造方法
* 创建一个子类对象时，调用顺序：
  1. 父类的静态代码块和静态属性初始化
  2. 子类的静态代码块和静态属性初始化
  3. 父类普通代码块和普通属性初始化
  4. 父类构造方法
  5. 子类普通代码块和普通属性初始化
  6. 子类构造方法
* 静态代码块只能直接调用静态成员，普通代码块可调用任意成员











## 单例设计模式(Singleton)
* 定义：采取一定的方法，保证在整个软件系统中，对某个类只能存在一个对象实例，并且该类只提供一个取得其对象实例的方法。有饿汉式和懒汉式
### 饿汉式(先创建对象，着急)
* 通常是重量级对象，类一加载就会创建对象，饿汉式可能造成创建了对象但没有使用
* 步骤
  1. 构造器私有化(防止直接new对象)
  2. 类的内部创建对象
  3. 向外暴露一个静态的公共方法(getInstance)
* 示例
``` Java
class GirlFriend{
  private String name;
  //类的内部创建对象;为了能在静态方法中返回gf对象，需要将其修饰为static
  private static GirlFriend gf = new GirlFriend("mn");
  //构造器私有化
  private GirlFriend(String name){
    this.name = name;
  }
  //提供一个公共的static方法返回gf对象
  public static GirlFriend getInstance(){
    return gf;
  }
}
```
### 懒汉式
* 示例
``` Java
class GirlFriend{
  private String name;
  //类的内部创建对象;为了能在静态方法中返回gf对象，需要将其修饰为static
  private static GirlFriend gf;
  //构造器私有化
  private GirlFriend(String name){
    this.name = name;
  }
  //提供一个公共的static方法返回gf对象
  public static GirlFriend getInstance(){//只有当用户使用getInstance时才创建GirlFriend对象，后面再次调用直接返回
    if(gf == null){
      gf = new GirlFriend("mn");
    }
    return gf;
  }
}
```
### 区别
* 创建对象时机不同
* 饿汉式不存在线程安全问题，懒汉式存在
* 饿汉式存在浪费资源的可能，懒汉式不存在
* JavaSE标准类中java.lang.Runtime就是经典单例模式


## final
### 使用场景
1. 不希望类被继承时，可用final
2. 不希望父类某个方法被子类重写时，可用final
3. 不希望类的某个属性值被修改，可用final
4. 不希望某个局部变量被修改，可用final
### 使用细节
1. final修饰的属性也叫常量，一般用大写字母加下划线分割命名
2. final修饰的属性定义时必须赋初值，并且以后不能再修改







## 接口
* 接口即给出一些未实现的方法，封装在一起，等某个类需要使用时，再根据具体情况把这些方法写出
* 若一个类要实现某接口，则需要将该接口的所有抽象方法都实现
* 语法
``` Java
//定义接口
interface 接口名{
  //属性
  //方法（抽象方法、默认实现方法、静态方法）
}
//实现接口
class 类名 implements 接口名{
  自己属性;
  自己方法;
  必须实现的接口的抽象方法  
}
```
### 注意事项
* 接口无法被实例化
* 接口中所有方法是public方法(默认，可写可不写)
* 接口中抽象方法可以省略abstract关键字(默认，可写可不写)
* 一个类可以同时实现多个接口
* 接口中的属性只能是final的，而且是public static final修饰符。比如`int a = 1;`，实际是`public static final int a = 1;`
* 接口属性访问形式同类，接口名.属性名
* 接口不能继承其它的类，但是可以继承多个别的接口
* 接口的多态
  1. 多态参数，接口引用可以指向实现了接口的类的对象
  2. 多态数组
  3. 多态传递
* `class C extends B implements A`C继承B且实现A，当A、B同时有变量x且C中要访问时，访问接口x用A.x(静态的)，访问父类x用super.x


## 泛型程序设计(Generic Programming)
* 意味着编写的代码可以对多种不同类型的对象重用

## Annotation(注解)
1. 注解(Annotation)也被称为元数据(Metadata),用于修饰解释包、类、方法、属性、构造器、局部变量等数据信息
2. 和注释一样，注解不影响程序逻辑，但注解可以被编译或运行，相当于嵌入在代码中的补充信息
3. 在JavaSE中，注解的使用目的比较简单，例如标记过时的功能，忽略警告等。在JavaEE中注解占据了更重要的角色，例如用来配置应用程序的任何切面，代替javaEE旧版中所遗留的繁冗代码和XML配置等
4. 使用Annotation时要在其前面加@符号，并把该Annotation当成一个修饰符使用，用于修饰它支持的程序元素
5. 三个基本的Annotation
   1. @Override：限定某个方法，是重写父类方法，该注解只能用于方法
   2. @Deprecated：表示某个程序元素已过时
   3. @SuppressWarning：抑制编译器警告






## IO流
### File(文件)
#### 创建文件
* 相关方法
  1. new File(String pathname)//根据路径构建一个File对象
  2. new File(File parent, String child)//根据父目录文件+子路径构建
  3. new File(String parent, String child)//根据父目录+子路径构建
  4. createNewFile//创建新文件
``` Java
//第一种
public void create1(){
  //
  String filePath1 = "d:\\file1.txt";
  //只在内存中生成了file1对象
  File file1 = new File(filePath1);
  //在硬盘上生成了file1文件
  file.createNewFile();
  //还得catch一下才行
}
//第二种
public void create2(){
  File parentFile = new File("e:\\");
  String fileName = "file2.txt";
  File file2 = new File(parentFile, fileName);
  file.createNewFile();
}
//第三种
public void create3(){
  String parentPath = "d:\\";
  String fileName = "file3.txt";
  File file3 = new File(parentPath, fileName);
  file3.createNewFile();
}
```
#### 获取文件相关信息
* getName()
* getAbsolutePath()
* getParent()
* length() //文件大小，单位为byte
* exists()
* isFile() //是否为文件
* isDirectory() // 是否为目录
#### 目录操作与文件删除
mkdir创建一级目录
mkdirs创建多级目录
delete删除空目录或文件【Java目录也类似可当做文件】
#### 流
|抽象基类|字节流|字符流|
|--|--|--|
|输入流|InputStream|Reader|
|输出流|OutputStream|Writer|
* 这四个都是抽象类，IO流40多个类，都是由以上四类派生，且子类名都是以其父类名作为子类名后缀
* FileInputStream




# 集合
## 分类
### Iterable(单列集合)
* Collection
 * 实现子类可以存放多个元素，每个元素可以是Object
 * Collection接口没有直接实现子类，通过子接口Set和List实现
 * 遍历元素方式
  1. 使用Iterator(迭代器)
    Iterator称为迭代器，重要用于遍历Collection集合的元素
    所有实现了Collection接口的集合类都有一个iterator()方法，用以返回一个实现了Iterator接口的对象，即返回一个迭代器
    Iterator仅用于遍历集合，本身并不存放对象
  ``` Java
  Collection col = new ArrayList();
      //现在遍历col集合
      //1.先得到col对应的迭代器
      Iterator iterator = col.iterator();
      //2.使用while循环遍历
      while(iterator.hasNext()){//判断是否还有数据，不判断会抛出异常
          Object obj = iterator.next();
          System.out.println("obj=" + obj);
      }
      //3.退出while循环后，iterator指向最后的元素
      //4.如果希望再次遍历，需要重置iterator
      iterator = col.iterator();
  ```

#### List
##### ArrayList
* 常用方法
  1. add：添加单个元素
  2. remove：删除指定元素（index或元素名）
  3. contains：查找元素是否存在
  4. size：获取元素个数
  5. isEmpty：判断是否为空
  6. clear：清空
  7. addALL：添加多个元素（接收集合）
  8. containsAll：查找多个元素是否都存在（接收集合）
  9. removeAll：删除多个元素（接收集合）
##### Vector
##### LinkedList

#### Set
##### TreeSet
##### HashSet

### Map(双列集合)
#### HashMap
##### LinkedHashMap

#### TreeMap
#### HashTable
##### Properties



# Swing
## 基础概念
* 顶层窗口，即没有包含在其他窗口中的窗口，称为Frame(窗体)
* AWT库有Frame类
* Swing包有JFrame类
* 大多数Swing类都有J开头，忘加与AWT类混合容易出错
* Frame是容器
* Panel是面板，不能单独存在，必须依赖于容器
``` Java
//最最基础，显示一个空窗格的示例
public class SimpleFrameTest {
  public static void main(String[] args) {
    /*所有Swing组件必须由事件分派线程(event dispatch thread)配置
    这是控制线程，将鼠标点击和按键等事件传递给用户接口组件
    以下代码段用来执行事件分派线程中的语句
    EventQueue.invokeLater(() ->{
      statements
    });
    */
    EventQueue.invokeLater(() ->{
      var frame = new SimpleFrame();
      //定义用户关闭窗体的响应动作
      frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
      //仅构建窗体不会自动显示，需要主动使他显示
      frame.setVisible(true);
    });
  }
}
//定义JFrame的子类，主要设置了默认窗体大小（默认0×0），别的没啥改变
class SimpleFrame extends JFrame {
  private static final int DEFAULT_WIDTH = 300;
  private static final int DEFAULT_HEIGHT = 200;

  public SimpleFrame(){
      setSize(DEFAULT_WIDTH, DEFAULT_HEIGHT);
  }
}
```
* JFrame类本身只包含若干改变窗体外观的方法，大多处理窗体大小和位置的方法来自其超类，主要包括：
  1. setLocation和setBounds设置窗体位置
  2. setIconImage告诉窗口系统在标题栏、任务栏切换窗口等位置显示哪个图标
  3. setTitle改变标题栏文字
  4. setResizable用一个boolean值确定是否允许用户改变窗体大小

## 常用操作
``` Java
import javax.swing.*;
import java.awt.*;

public class SimpleFrameTest {
public static void main(String[] args) {
    //JFrame使用
    var jf = new JFrame("登录");
    jf.setBounds(500, 500, 300, 150);

    //JFrame布局
    //流式布局FlowLayout，组件像流一样一个一个排放，排满一行之后排下一行
//        jf.setLayout(new FlowLayout());//流式布局(默认居中对齐)
    jf.setLayout(new FlowLayout(FlowLayout.LEFT));//流式布局左对齐
    //边界布局BorderLayout，默认布局，将容器分为东西南北中五个区域
    //网格布局GridLayout，可指定行列数以及间隔

    //JButton使用
//        var jb1 = new JButton("登录");
//        var jb2 = new JButton("清空");
//        var jb3 = new JButton("退出");
//        jb1.setEnabled(true);//设置是否可点击，默认可
//        jb1.setBorderPainted(false);//设置是否有边界，默认有
//        jf.add(jb1);
    //单选组件框
//        var jrb1 = new JRadioButton("帅");
//        var jrb2 = new JRadioButton("很帅");
//        var bg = new ButtonGroup();
//        bg.add(jrb1);
//        bg.add(jrb2);
//        jf.add(jrb1);
//        jf.add(jrb2);
//        //复选组件框
//        var jcb1 = new JCheckBox("吃饭",true);//默认是否选中
//        var jcb2 = new JCheckBox("睡觉",false);
//        var jcb3 = new JCheckBox("乒乓球",false);
//        jf.add(jcb1);
//        jf.add(jcb2);
//        jf.add(jcb3);
//        //下拉列表组件
//        var jcbb = new JComboBox();
//        jcbb.addItem("陕西省");
//        jcbb.addItem("辽宁省");
//        jcbb.addItem("湖北省");
//        jf.add(jcbb);

//        //菜单栏
//        //一级菜单(菜单项依附于菜单，菜单依附于菜单条)
//        var jmb = new JMenuBar();//创建菜单条
//        var jm1 = new JMenu("文件");//创建菜单
//        var jm2 = new JMenu("编辑");
//        var jmi1 = new JMenuItem("新建");//创建菜单项
//        var jmi2 = new JMenuItem("打开");
//        jm1.add(jmi1);
//        jm1.add(jmi2);
//        jmb.add(jm1);
//        jf.add(jmb);

    //JTextField文本组件
//        var jtf = new JTextField("账号为2-4个汉字的姓名", 10);
//        jf.add(jtf);
    //JPasswordField密码框组件
//        var jpf = new JPasswordField("", 10);
//        jpf.setEchoChar('*');//手动设置回文字符
//        jf.add(jpf);
    //JTextArea文本域组件
//        var jta = new JTextField("请输入内容", 10);
//
//        jta.getText();//获取文本框输入的内容(文本域文本框等都可以)
//        jf.add(jta);


    //Jpanel使用
//        var jp = new JPanel(new FlowLayout());
//        jp.add(jb1);
//        jp.add(jb2);
//        jp.add(jb3);
//        jf.add(jp);

    //JScrollPane使用
//        var jsc = new JScrollPane(jb1);
//        jf.add(jsc);

    //JDialog使用
//        var jd = new JDialog(jf, "注册界面");
//        jd.setBounds(400, 300, 500, 500);
//        jd.setVisible(true);
//        jd.setDefaultCloseOperation(WindowConstants.DISPOSE_ON_CLOSE);

    //JLabel使用
//        var jl = new JLabel("账号： ", SwingConstants.LEFT);
//        //CENTER水平居中，LEFT左对齐
//        jf.add(jl);

    //事件监听
    /*
    事件模型有三个对象：事件源（事件发生的地方），事件（要发生的事情），监听程序
    事件处理——针对发生的事情做出的处理方案
    事件监听——把事件源和事件关联起来
    动作事件监听器(ActionListener()）
    焦点事件监听器(FocusListener())
      */
//        JTextArea jta2 = new JTextArea(20, 10);
//        var jb4 = new JButton("偷袭!");
//        jf.add(jta2);
//        jf.add(jb4);
//        jb4.addActionListener(new AbstractAction() {//用了匿名内部类
//            @Override
//            public void actionPerformed(ActionEvent e) {
////                jta2.setText("耗子尾汁");//setText()会重置文本内容
//                jta2.append("耗子尾汁");//append()则追加
//            }
//        });

    //综合实战小demo登录界面
    var jl1 = new JLabel("账号：");
    var jl2 = new JLabel("密码：");
    var jtf1 = new JTextField("", 20);
    var jtf2 = new JTextField("登陆状态", 25);
    var jpf = new JPasswordField("", 20);
    var jb = new JButton("登陆");
    jb.setSize(20, 20);

    jf.add(jl1);
    jf.add(jtf1);
    jf.add(jl2);
    jf.add(jpf);
    jf.add(jtf2);
    jf.add(jb);

    jf.setResizable(false);//禁止修改窗口大小
    jf.setVisible(true);
    jf.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

  }
}

```

# 未分类小知识点
## 键盘输入语句
* 步骤
  1. 导入Scanner类所在的包,即java.util
    > import java.util.Scanner;
  2. 创建Scanner对象（声明变量）
    > Scanner myScanner = new Scanner(System.in);
  3. 接收用户输入，使用相关方法(next等)
    > String name = myScanner.next();

## Java API文档
* API(Application Programming Interface 应用程序编程接口)

## 常用类、方法
* equals()
* Math.PI
* Random.nextInt(a);返回0~a之间的随机int数
* Math.random()

## null引用
* 对null值应用方法会产生一个NullPointerException异常。可以捕获异常但尽量一开始就不要带来异常
* 定义一个类时，最好清楚地知道哪些字段可能为null(如name)
* 对此有两种解决方法：
  1. “宽容型”：把null参数转换为一个适当非null值，如`if(n == null) name = "unknown"; else name = n;`;Java9中提供了一个便利方法：`name = Objects.requireNonNullElse(n, "unknown");`
  2. “严格型”：拒绝null参数，如`Objects.requireNonNull(n,"The name cannot be null");name = n;`
* 若接受一个对象引用作为构造参数，问问自己是不是真的希望接受一个可有可无的值，若不是则“严格型”


# 实操Program Project思路
* 先完成代码业务，再考虑完善其鲁棒性
* 当方法返回值为double，检验输入为空数组或null时，可改返回类型为Double（类），再可以返回null，并先用一个值来接收
* 方法中判断数组为空或null(arr != null && arr.length > 0)

## 设计模式
### 分层模式
* 界面层：程序入口、菜单界面
* 业务层：工具类
* 数据层：model
* 其它notes：目前练习，所用类较少，但实际工程则需要各个分层建包便于管理，可以提前养成这样的好习惯



# Java版本新特性
* JDK8后，可以有默认实现方法，但要用default修饰
* JDK8后，可以有静态方法

## JDK10
* 如果可以从变量的初始值推导出其类型，则可以用var声明局部变量而无需指定类型，如`var jb1 = new JButton()`。切记仅方法中的局部变量，而参数和属性的类型必须声明

P1-P62-
P82-P99-
-P154


P155-361
P362-372 房屋出租系统（有空再看）
P373-392

P403-412 接口

P413- 内部类

P611- 文件


# 参考资料
1. [b站动力节点韩顺平零基础Java课](https://www.bilibili.com/video/BV1fh411y7R8?p=11&share_source=copy_web)）
2. [菜鸟教程JAVA课程](https://www.runoob.com/java/java-basic-syntax.html)