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

# 线性表
## 顺序表
### 基本操作实现
1. 初始化
    * 定义：顺序表初始化操作即构造一个空顺序表
    * 算法步骤：先为顺序表L动态分配一个预定义大小的数组空间，使elem指向这段空间的基地址。再将表的当前长度设为0
``` C
Status InitList(SqList &L){
    L.elem = new ElemType{MAXSIZE};//为顺序表分配一个大小为MAXSIZE的数组空间
    if(!L.elem) exit(OVERFLOW);//存储分配失败退出
    L.length = 0;//空表长度置为0
    return OK;
}
```
2. 取值
   * 算法步骤：先判断序号i值是否合理，不合理返回ERROR，合理赋给e，由e代为传值
``` C
Status GetElem(SqList L, int i, ElemType &e){
    if(i < 1 || i > L.length) return ERROR;
    e = L.elem[i - 1];
    return OK;
}
```
3. 查找
   * 定义：根据指定的元素值e, 查找顺序表中第1个与e相等的元素。若查找成功，则返回该元素在表中的位置序号；若查找失败，则返回0
   * 算法步骤：从第一个元素起，依次和e相比较，若找到与e相等的元素L.elem[i], 则查找成功，返回该元素的序号 i+l。若查遍整个顺序表都没有找到，则查找失败，返回0。
``` C
int LocateElem(SqList L, ElemType e){
    for(i = 0; i < L.length; i++){
        if(L.elem[i] == e)
            return i+1
    }
    return 0;
}
```
4. 插入
   * 算法步骤：判断插入位置i是否合法(合法范围i >= 1 && i <= n+1), 若不合法则返回ERROR。判断顺序表的存储空间是否已满，若满则返回ERROR。将第n个至第i个位置的元素依次向后移动一个位置，空出第i个位置(i=n+l时无需移动）。将要插入的新元素e放入第i个位置，表长加l。
``` C
Status ListInsert(SqList &L, int i, ElemType e){
    if(i < 1 || i > L.length + 1) return ERROR;
    if(L.length == MAXSIZE) return ERROR;
    for( j = L.length - 1; j >= i-1; j--)
        L.elem[j+1] = L.elem[j];
    L.elem[i-1] = e;
    ++L.length;
    return OK;
}
//未处理动态扩充，达到表最大长度则无法插入
```
5. 删除
   * 算法步骤：插入逆向操作即可
``` C
Status ListDelete(SqList &L, int i){
    if(i < 1 || i > L.length) return ERROR;
    for(j = i; j <= L.length - 1; j++)
        L.elem[j - 1] = L.elem[j];
    --L.length;
    return OK;
}
```

## 链表
### 单链表
* 存储结构
``` C
typedef struct LNode{
    ElemType data;  //结点的数据域
    struct LNode *next; //结点的指针域
}LNode, *LinkList; //LinkList为指向结构体LNode的指针类型
```
#### 基本操作
1. Initialize
``` C
Status InitList(LinkList &L){
    L = new LNode;  //生成新结点作为头结点，用头指针L指向头结点
    L -> next = NULL;   //头结点指针域置空
    return OK;
}
```
2. 取值
``` C
Status GetElem(LinkList L, int i, ElemType &e){
    //在带头结点的单链表L中根据序号i获取元素的值，用e返回L中第i个数据元素的值
    p = L -> next; j = 1;   //初始化，p指向首元结点，计数器j初值赋1
    while(p && j < 1){  //顺链域向后扫描，直到p为空或p指向第i个元素
        p = p -> next;  //p指向下一个结点
        ++j;    //计数器j相应加1
    }
    if(!p || j > i) return ERROR;   i值不合法i > n或 i <= 0;
    e = p -> data;  //取第i个结点的数据域
    return OK;
}
```
3. 查找
``` C
LNode *LocateElem(LinkList L, ElemType e){
    //在带头结点的单链表L中查找值为e的元素
    p = L -> next;  //初始化，p指向首元结点
    while(p && p -> data ！= e){    //顺链域向后扫描，直到p为空或p所指结点数据域等于e
        p = p ->next;   //p指向下一个结点
    }
    return p;   //查找成功返回值为e的节点地址p，查找失败p为NULL
}
```
4. 插入
``` C
Status ListInsert(LinkList &L, int i, ElemType e){
    //在带头结点的单链表L中第i个位置插入值为e的新结点
    p = L; j = 0;
    while(p && j < i-1){
        p = -> next; ++j;   //查找第i-1个结点，p指向该节点
    }
    if(!p || j > i - 1) return ERROR;   //i > n+1或 i < 1
    s = new LNode;  //生成新结点*s
    s -> data = e;  //将结点*s的数据域置为e
    s -> next = p -> next;  //将结点*s的指针域指向结点a
    p -> next = s;  //将结点*p的指针域指向结点*s
    return OK;
}
```
5. 删除
``` C
Status List Delete(LinkList &L, int i){
    //在带头结点的单链表L中，删除第i个元素
    p = L; j = 0;
    while(p -> next && j < i-1){
        p = p -> next; ++j  //查找第i-1个结点，p指向该结点
    }
    if(!(p -> next) || j > i - 1){
        return ERROR;   //当i>n或i<1时，删除位置不合理
    }
    q = p -> next;  //临时保存被删节点的地址以备释放
    p -> next = q -> next;  //改变删除结点前驱结点的指针域
    delete q;   //释放删除结点的空间
    return OK;
}
```
* 注意删除和插入的循环判断范围不同！

#### 创建单链表
##### 前插法
* 定义：新结点逐个插入链表的头结点之后；
* 注意：逆位序输入数据！才能正位序输出！
``` C
void CreateList_H(LinkList &L, int n){
    //逆位序输入n个元素的值，建立带表头节点的单链表L
    L = new LNode;
    L -> next = NULL; //先建立一个带头结点的空链表
    for(i = 0; i < n; ++i){
        p = new LNode;  //生成新结点*p
        cin >> p-> data;    //输入元素值赋给新结点*p的数据域
        p -> next = L ->next;   //将新结点*p插入到头结点之后
        L -> next = p;
    }
}
```
##### 后插法
* 定义：新结点逐个插入链表的头结点之后；
``` C
void CreateList_R(LinkList &L, int n){
    //正位序输入n个元素的值，建立带表头结点的单链表L
    L = new LNode;
    L -> next = NULL;   //先建立一个带头结点的空链表
    r = L;  //尾指针r指向头结点
    for(i = 0; i < n; ++i){
        p = new LNode;  //生成新结点
        cin >> p -> data;   //输入元素值赋给新结点*p的数据域
        p ->next = NULL; r -> next = p;   //将新结点*p插入尾结点*r之后
        r = p;  //r指向新的尾结点*p
    }

}
```




## Stack
### Sequence Stack
* Definition
``` C
# define MAXSIZE 100    //顺序栈存储空间的初始分配量
typedef struct{
    SElemType *base;
    SElemType *top;
    int StackSize;
}SqStack;
//当base = top时表示空栈
//非空时top始终指向栈顶元素的下一个位置
```

* Initialize
``` C
Status InitStack(SqStack &S){
    //构造空栈S
    S.base = new SElemType[MAXSIZE];    //为顺序栈动态分配一个最大容量为MAXSIZE的数组空间
    if(!S.base) exit(OVERFLOW); //存储分配失败
    S.top = S.base; //top初始为base，空栈
    S.StackSize = MAXSIZE;
    return OK;
}
```

* Push
``` C
Status Push(SqStack &S, SElemType e){
    //压e入栈
    if(S.top - S.base == S.StackSize)   return ERROR;   //栈满
    *S.top++ = e;
    return OK;
}
```

* Pop
``` C
Status Pop(SqStack &S, SElemType &e){
    //让栈顶元素e出栈
    if(S.top == S.base)   return ERROR;   //栈空
    e = *--S.top;
    return OK;
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