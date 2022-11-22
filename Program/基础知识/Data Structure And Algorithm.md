# Data Structure And Algorithm（数据结构与算法分析）

# 《数据结构 C语言版》——严蔚敏
# 绪论
## 基本概念和术语
Data, Data Element, Data Item, Data Object
### Data Structure
1. 逻辑结构：集合、线性、树、图结构
2. 存储结构（物理结构）：顺序、链式存储结构
### Data Type
* 以C为例，整型、实型、字符型、数组、结构体、指针等
### Abstract Data Type, ADT
* ADT定义格式
  ADT 抽象数据类型名{
    数据对象：<数据对象的定义>
    数据关系：<数据关系的定义>
    基本操作：<基本操作的定义> 
    }ADT 抽象数据类型名
* 基本操作定义格式
  基本操作名(参数表)
    初始条件:<初始条件描述>
    操作结果:<操作结果描述>

抽象数据结构示例——复数
``` C
//定义
typedef struct{
    float RealPart;
    float ImagePart;
} Complex;
//构造Complex
void Create(&Complex C, float x, float y){
    C.RealPart = x;
    C.ImagePart = y;
}
//获取实部值
    float GetReal(C){
    return C.RealPart;
}
//求和
Complex Add(C1, C2){
    Complex Sum;
    Sum.RealPart = C1.RealPart + C2.RealPart;
    Sum.ImagePart = C1.ImagePart + C2.ImagePart;
    return Sum;
}
```


















# 浙大数据结构
## 零散知识点
### 算法效率
* 测一个函数运行时间可用clock()函数，示例：
``` C
#include <stdio.h>
#include <time.h>

void Myfuc(){
    printf("OK\n");
}

int main(){
    clock_t start,stop;
    // clock_t是clock()函数的返回值的变量类型
    double second;
    start = clock();
    Myfuc();
    stop = clock();
    second = (stop - start) / CLK_TCK;
    printf("%f",second);
}
```
但由于计算机运行速度快，导致所用时间极少，所测值可能为0。故可重复运行函数再统计时间再除以次数来得出时间


# 参考资料
1. 《大话数据结构》
2. 