# NEU DSA HM
# HM3(20221028)

3.1
(1). 可能得到123 321 231 132 213（即无312）
(2). 135426：SXSSXSSXXXSX可得到; 435612：SSSSXXSXSX后剩21,1不能比2先出，所以无法得到。

3.5
区分的一般准则：合法序列中无论从哪里设断点，往前数S的个数一定大于X的个数
证明：当两个序列仅有两个操作不一样时，如一个甲序列SX另一个乙序列XS，当其余操作都一样时，则到达区分点时的操作数设为x，上一个是x-1。则甲序列先入x并出x，乙序列则出x-1再入x，那么甲序列一定先出x再出x-1，乙序列一定先出x-1再出x，就导致这两个序列必定不同，证明了“两个不同的合法栈操作序列不可能得到相同的输出元素序列”。

3.6
证明：设i=1,j=2,k=3,则因为在输入序列为123时，不可能输出序列为312得证。

3.7


3.9
``` C
void digui(int n){
    while(1){
        if(n > 1){
            printf("%d", n--);
            digui(n);
        } else {
            break;
        }
    }
}
```

3.15
``` C
Status InitStack(TwoWayStack &tws, int size);
Status Push(TwoWayStack &tws, int i, SElemType x);
Status Pop(TwoWayStack &tws, int i, SElemType &x);
typedef struct{
    SElemType *elem;
    int top[2];
    int size;  // 分配给elem的总容量
} TwoWayStack; // 双端栈

Status InitStack(TwoWayStack &tws, int size){
    tws.elem = (SElemType *)malloc(sizeof(SElemType) * size);
    tws.size = size;
    tws.top[0] = 0;
    tws.top[1] = size - 1;
    return OK;
}

Status Push(TwoWayStack &tws, int i, SElemType x){
    int w = tws.top[0];
    if (w == tws.top[1])
        return ERROR;
    else if (i == 0){
        tws.elem[tws.top[0]] = x;
        tws.top[0] = tws.top[0] + 1;
    }
    else if (i == 1){
        tws.elem[tws.top[1]] = x;
        tws.top[1] = tws.top[1] - 1;
    }
    return OK;
}

Status Pop(TwoWayStack &tws, int i, SElemType &x){
    if (tws.top[1] == tws.size - 1 && i == 1)
        return ERROR;
    else if (tws.top[0] == 0 && i == 0)
        return ERROR;
    else if (i == 0){
        tws.top[0] -= 1;
        x = tws.elem[tws.top[0]];
    }
    else if (i == 1){
        tws.top[1] += 1;
        x = tws.elem[tws.top[1]];
    }
    return x;
}
```

3.17
``` C
bool Judge(char a[]){
    int i = 0;
    Stack stack;
    InitStack(stack);
    
    while (a[i] != '&' && a[i]){
        Push(stack, a[i]);
        i++;
    }
    if (a[i]){
        return false;
    }
    i++;
    
    ElemType x;
    while (a[i]){
        Pop(stack, x);
        if (x != a[i]){
            DestroyStack(stack);
            return FALSE;
        }
        i++;
    }
    return true;
}
```
3.18
``` C
bool Judge(char a[]){
    int i = 0;
    Stack stack;
    InitStack(stack);
    ElemType x;
    while (a[i]){
        switch (a[i]){
        case '(':
            Push(stack, a[i]);
            break;
        case '[':
            Push(stack, a[i]);
            break;
        case ')':
            GetTop(stack, x);
            if (x == '(')
                Pop(stack, x);
            else
                return FALSE;
            break;
        case ']':
            GetTop(stack, x);
            if (x == '[')
                Pop(stack, x);
            else
                return FALSE;
            break;
        default:
            break;
        }
        i++;
    }
    
    if (stack.size != 0)
        return false;
    return true;
}
```

3.21
``` C
void Change(char Buffer[]){
    Stack stack;
    InitStack(stack);
    int i = 0, j = 0;
    ElemType e;

    Push(stack, Buffer[i]);
    i++;
    while (Buffer[i] != '#'){
        if (!IsOperator(Buffer[i])){
            Buffer[j] = Buffer[i];
            i++;
            j++;
        } else {
            GetTop(stack, e);
            if (Compare(e, Buffer[i])){
                Pop(stack, e);
                Buffer[j] = e;
                j++;
            } else {
                Push(stack, Buffer[i]);
                i++;
            }
        }
    }
    while (!StackEmpty(stack)) {
        Pop(stack, e);
        Buffer[j] = e;
        j++;
    }
}

Status Compare(char c1, char c2){
    char ch[] = "#+-*/";
    int i = 0, j = 0;
    while (ch[i] && ch[i] != c1)
        i++;
    if (i == 2)
        i--; 
    if (i == 4)
        i--; 
    while (ch[j] && ch[j] != c2)
        j++;
    if (j == 2)
        j--;
    if (j == 4)
        j--;
    if (i >= j)
        return TRUE;
    else
        return FALSE;
}

Status Judge(char c){
    char *p = "#+-*/";
    while (*p){
        if (*p == c)
            return TRUE;
        p++;
    }
    return FALSE;
}
```

3.26
``` C
#include <iostream.h>
double Sqrt(double A, double p, double e);
int main(){
    double A, p, e;
    cout << "输入A p e:";
    cin >> A >> p >> e;
    cout << Sqrt(A, p, e) << endl;
    return 0;
}

double Sqrt(double A, double p, double e){
    if ((p * p - A) > -e && (p * p - A) < e)
        return p;
    else
        return Sqrt(A, (p + A / p) / 2, e);
}
```

3.27
(1).递归算法
``` C
unsigned int Ackerman(unsigned int m, unsigned int n){
    unsigned int g;
    if (m == 0){
        return n + 1;
    } else if (n == 0){
        return Ackerman(m - 1, 1);
    } else {
        g = Ackerman(m, n - 1);
        return Ackerman(m - 1, g);
    }
}
```
(2). 非递归算法
``` C
int Ackerman(int m, int n){
    Stack stack;
    InitStack(stack);
    ElemType e, e1, d;
    e.mval = m;
    e.nval = n;
    Push(stack, e);
    do {
        while (e.mval){
            while (e.nval){
                e.nval--;
                Push(stack, e);
            }
            e.mval--;
            e.nval = 1;
        }
        if (StackLength(stack) > 1){
            e1.nval = e.nval;
            Pop(stack, e);
            e.mval--;
            e.nval = e1.nval + 1;
        }
    } while (StackLength(stack) != 1 || e.mval != 0);
    
    return e.nval + 1;
}
```

3.28
``` C
typedef int ElemType;
typedef struct NodeType{
    ElemType data;
    NodeType *next;
} QNode, *QPtr;

typedef struct{
    QPtr rear;
    int size;
} Queue;

Status InitQueue(Queue &q){
    q.rear = NULL;
    q.size = 0;
    return OK;
}

Status EnQueue(Queue &q, ElemType e){
    QPtr p;
    p = new QNode;
    if (!p)
        return FALSE;
    p->data = e;
    if (!q.rear){
        q.rear = p;
        p->next = q.rear;
    } else {
        p->next = q.rear->next;
        q.rear->next = p;
        q.rear = p;
    }
    q.size++;
    return OK;
}

Status DeQueue(Queue &q, ElemType &e){
    QPtr p;
    if (q.size == 0)
        return FALSE;
    if (q.size == 1){
        p = q.rear;
        e = p->data;
        q.rear = NULL;
        delete p;
    } else {
        p = q.rear->next;
        e = p->data;
        q.rear->next = p->next;
        delete p;
    }
    q.size--;
    return OK;
}
```

3.30
``` C
#define MaxQSize 4
typedef int ElemType;
typedef struct{
    ElemType *base;
    int rear;
    int length;
} Queue;

Status InitQueue(Queue &q){
    q.base = new ElemType[MaxQSize];
    if (!q.base)
        return FALSE;
    q.rear = 0;
    q.length = 0;
    return OK;
}
Status EnQueue(Queue &q, ElemType e){
    if ((q.rear + 1) % MaxQSize == (q.rear + MaxQSize - q.length) % MaxQSize)
        return FALSE;
    else {
        q.base[q.rear] = e;
        q.rear = (q.rear + 1) % MaxQSize;
        q.length++;
    }
    return OK;
}

Status DeQueue(Queue &q, ElemType &e){
    if ((q.rear + MaxQSize - q.length) % MaxQSize == q.rear)
        return FALSE;
    else {
        e = q.base[(q.rear + MaxQSize - q.length) % MaxQSize];
        q.length--;
    }
    return OK;
}
```

3.31
``` C
Status Judge(char *p){
    Queue queue;
    if (!InitQueue(queue))
        return 0;
    Stack stack;
    InitStack(stack);
    ElemType e1, e2;
    while (*p){
        Push(stack, *p);
        EnQueue(queue, *p);
        p++;
    }
    while (!StackEmpty(stack)){
        Pop(stack, e1);
        DeQueue(queue, e2);
        if (e1 != e2)
            return FALSE;
    }
    return OK;
}
```
