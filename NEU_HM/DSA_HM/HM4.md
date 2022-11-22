# NEU DSA HM
# HM4(20221111)

4.2
答：应该可以，比如由求串长、串赋值、串连接、求子串、串比较构造。

4.3
s = "I AM A STUDENT"
t = "GOOD"
q = "WORKER"

StrLength(s) = 14
StrLength(t) = 4
SubString(s, 8, 7) = "STUDENT"
SubString(t, 2, 1) = "O"
Index(s, 'A') = 3
Index(s, t) = 0
Replace(s, "STUDENT", q) = "I AM A WORKER"
Concat(SubString(s, 6, 2), Concat(t, SubString(s, 7, 8))) = "A GOOD STUDENT"

4.4
a = "THIS", f = "A SAMPLE", c = "GOOD", d = "NE", b = " ", u = "ONE", g = "IS"

s = "THIS SAMPLE IS"
t = "A GOOD"
v = "THIS SAMPLE IS A GOOD ONE"
StrLength(s) = 14
Index(v, g) = 13
Index(u, g) = 0

4.6
s = "(XYZ)+*"
t = "(X+Z)*Y"

s1 = Replace(s, '+', '\*') = "(XYZ)\*\*"
s2 = Replace(s1, 'Y', '+') = "(X+Z)\*\*"
s3 = Concat(SubString(s2, 1, 6), SubString(s, 3,1)) = t

4.12
``` C
void replace(char s[], char t[], char v[]){
    int len_v = get_stringSize(v);
    int len_t = get_stringSize(t);
    int len_s = get_stringSize(s);

    if (len_s < len_t || len_v == 0 || len_t == 0 || len_s == 0) {
        printf("串不符合规定!\n");
        return;
    }

    int i = 0, j = 0;
    for (i = 0; s[i] != '\0'; i++){
        for (j = 0; t[j] != '\0'; j++){
            if (s[i + j] == t[j]){
                continue;
            }
            break;
        }

        if (t[j] == '\0'){
            // 如果要替换的串t 长度大于 替换串v
            if (len_t >= len_v){
                // 先替换 再腾位置
                // 替换
                for (int k = 0; k < len_v; k++){
                    s[i + k] = v[k];
                }
                // 因为 替换后仍有 无效数据，后面数据向前靠拢
                int sub = len_t - len_v; // 向前靠拢空间为 sub
                for (int k = i + len_v; k < len_s; k++){
                    s[k] = s[k + sub];
                } // 最后sub位 元素 会被自己赋值为空，省了赋空操作
            }
            else {// len_t < len_v要替换的串t 长度小于 替换串v
                // 先腾位置 再替换
                // 向后 腾位置
                int sub = len_v - len_t;
                for (int k = len_s - 1; k >= i + len_t; k--){
                    s[k + sub] = s[k];
                }
                // 位置腾出，开始替换
                for (int k = 0; k < len_v; k++){
                    s[i + k] = v[k];
                }
            }

            // 原s 串 的长度 发生了 变化，更新s串长度
            len_s = get_stringSize(s);
        }
        else
            ; // 没有找到 break结束
    }
    return;
}

```

4.13
``` C
void DelStr(char *src, char *dst){
    char *p = src;
    char *q = dst;
    int dstLen;
    dstLen = strlen(dst);
    while (*src != EOF){
        if (*q == '\0'){
            p -= dstLen;
            q = dst; // Q重新指向删除的字符
            continue;
        }
        else if (*src != *q){
            q = dst;
        }
        else{
            ++q;
        }
        *p++ = *src++; // 每次都用src来刷新p
        //如果p指针往回dstLen长度,匹配到的字符串会被覆盖掉
    }
    *p = '\0';
}
```