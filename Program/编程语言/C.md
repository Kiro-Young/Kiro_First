# C语言学习笔记

# 数据类型
## int型
* 范围：-2^31~2^31(-2147483648-2147483647)
* 数据溢出时，如大于2147483647后，则从-2147483648开始增加
* 转换说明：%u(unsigned int),%ld(long)


## double型
* 默认%f可以精确到小数点后6位；0.x小数用%.xf最多可以精确到第16位；总位数也精确16位

## char型
* 实际存储为整数，利用ASCII码转换
* 声明时用单引号括起来，如`char ddd = 'A'`,双引号括字符串，不括则为变量，均不正确
* 打印非打印字符方法：①直接打印ASCII码；②打印转义序列
* 7-蜂鸣字符
* 65-A
* 

# 常用库函数（函数名-返回值类型-说明）
## <stdio.h>
### scanf()
* 有返回值，返回值为成功输入的变量个数；输入结束后，无法读取时将返回0，可配合while循环输入未知数目的一组数字

### 输入输出
* 输入输出重定向至文件：freopen("文件名","读写方式",stdin/stdout)
* 本机测试时使用文件重定向，提交前自动删除重定向语句：程序起始定义`#define LOCAL`，再将freopen()写在`#ifdef LOCAL`和`#endif`之间，含义是只有定义符号LOCAL，才编译中间部分的语句。若要求标准输入输出则删掉`#define LOCAL`即可
* 要求文件输入输出，但禁止使用重定向的方式：
``` C
FILE  *fin,*fout;
fin = fopen("data.in","rb");
fout = fopen("data.out","wb");
……
fscanf(fin,"%d",&x);
fprintf(fout,"%d",x);
fclose(fin);
fclose(fout);
```
重定向写法简单，但不能同时读写文件和标准输入输出；fopen写法较繁琐，但灵活性大，如反复打开并读写文件。若想改fopen版程序为读写标准输入输出，只需赋值`fin = stdin; fout = stdout;`即可，不要调用fopen和fclose

## <stdlib.h>
* malloc()-size-void*-分配size个字节的内存空间,并返回所分配内存的指针

## <math.h>
* abs(x)-int-返回int参数i的绝对值
* fabs(x)-double-返回double参数i的绝对值
* cos(x)-double-返回x的余弦cos(x)值,x为弧度！(sin,tan,cot等同理)
* pow(x,y)-double-返回指数函数(x的y次方)的值，x，y均为double
* floor(x)-?-?-返回不超过x的最大整数

## <string.h>
* memcpy(b, a, sizeof(a))-数组a全部复制到数组b中
* memset(a, 0, sizeof(a))-清零数组a


## <time.h>
* clock()-/-clock_t-返回程序目前为止运行的时间。在程序结束前调用此函数，可获得整个程序的运行时间；用此时间除以常数CLOCKS_PER_SEC(C语言)/CLK_TCK(较通用伪代码)后的值则以秒为单位(该常数也在<time.h>头文件内)


# 小操作
* ^是异或，不能用于乘方计算，C语言用pow函数算乘方
* crtl + z Windows下结束输入
* 简单调试程序中间加printf最后提交时可注释掉，以防仍需调整
* 嵌套代码块有同名变量时，内层变量会屏蔽外层变量，容易出bug！
* 转义序列：\a-警报；\b-退格；\f-换页；\n-换行；\r-回车；\t-Tab