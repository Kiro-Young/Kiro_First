# NEU DSA HM
# HM2(20221007)

2.3
   * 查询操作多；插入，删除，更新操作少的数据适合用顺序表，因为顺序表是随机存取的存储结构，按元素位置序号访问数据元素时顺序表速度更快
   
2.11
``` C
Status ListInsert(SqList &va, ElemType e){
    int i;  //插入位置
    if(va.length == va.MAXSIZE){
        return ERROR;   //已满则无法添加
	}
    for(i = va.length; i > 0, e < va.elem[i-1]; i--){
        //从后往前找，一边找有序一边挪动表，效率高
		va.elem[i] = va.elem[i-1];
    }   //找到位置后退出循环
	va.elem[i] = e; //插入值e
	++va.length;    //表长+1
    //感悟：如果从0开始找i，则找的时候不能挪动，找到i之后还得再挪动i之后的表
    //再进行插入，不如直接从后往前找i！
	return OK;
}
```
 2.12
``` C
Status Compare(SqList &A, SqList &B){
    int i, k, j;
    k = A.length > B.length ? A.length : B.length;  //取AB表的最大长度
    for (i = 0; i < k; i++){
        if (A.elem[i] > B.elem[i])
            j = 1;
        if (A.elem[i] < B.elem[i])
            j = -1;
    }
    if (A.length > k)
        j = 1;  //A大
    if (B.length > k)
        j = -1; //B大
    if (A.length == B.length)
        j = 0;  //一样大
    return j;
}
```

2.15
``` C
void Link(LinkList &ha, LinkList &hb, LinkList &hc){
    LinkList TempA, TempB;
    TempA = ha; TempB = hb; //复制两临时链表
    while (TempA->next && TempB->next){
        TempA = TempA->next;
        TempB = TempB->next;
    }
    if (!TempA->next){
        hc = hb;
        while (TempB->next)
            TempB = TempB->next;
        TempB->next = ha->next;
    }else{
        hc = ha;
        while (TempA->next)
            TempA = TempA->next;
        TempA->next = hb->next;
    }
}
//算法时间复杂度为O(n)
```

2.21
``` C
Status Oppose_Sq(SqList &L){
    int i;
    ElemType x;
    for (i = 0; i < L.length / 2; i++){
        x = L.elem[i];
        L.elem[i] = L.elem[L.length - 1 - i];
        L.elem[L.length - 1 - i] = x;
    }
    return OK;
}
```

2.22
``` C
Status Oppose_L(LinkList &L){
    LinkList p, q;
    p = L; p = p -> next;
    L -> next = NULL;
    while (p){
        q = p;
        p = p->next;
        q->next = L->next;
        L->next = q;
    }
    return OK;
}
```

2.24
``` C
Status MergeOppose(LinkList &A, LinkList &B, LinkList &C){
    LinkList TempA, TempB, ta, tb;
    TempA = A;   TempB = B;
    ta = TempA;  tb = TempB; 
    TempA = TempA->next;
    TempB = TempB->next;
    A->next = NULL;
    C = A;
    while (TempA && TempB){
        if (TempA->data < TempB->data){
            ta = TempA;
            TempA = TempA->next;
            ta->next = A->next; 
            A->next = ta;
        }else{
            tb = TempB;
            TempB = TempB->next;
            tb->next = A->next; 
            A->next = tb;
        }
    }while (TempA){
        ta = TempA;
        TempA = TempA->next;
        ta->next = A->next;
        A->next = ta;
    }
    while (TempB){
        tb = TempB;
        TempB = TempB->next;
        tb->next = A->next;
        A->next = tb;
    }
    TempB = B;
    free(TempB);
    return OK;
}
```

2.29
``` C
Status Delete(SqList &D, SqList &A, SqList &B, SqList &C){
    SqList Temp;
    InitList_Sq(Temp);  //初始化
    ListCross_L(B, C, Temp);    //找BC共有元素
    ListMinus_L(A, Temp, D);
}
//时间复杂度应该是O(n)
```

2.30
``` C
//链表感觉没学太明白，目前还不太能用链表写这道题，我后续将继续研究
```

2.33
``` C
//今天刚学循环链表有点懵，写不出来，我后续将继续研究
```