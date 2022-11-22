# Computer Architecture



## Number System 数制
* 整数四种数制
  1. Binary 二进制：0，1；满2进1；以0b或0B开头
  2. Decimal 十进制：0~9；满10进1 
  3. 八进制：0~7；满8进1；以0开头表示
  4. Hexadecimal 十六进制：0~9和a(10)~F(15)；满16进1；以0x或0X开头表示；此处A~F不区分大小写

### 进制转换
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

## 原码、反码与补码
### 有符号
1. 二进制的最高位是符号位，0正1负
2. 正数的原码、反码、补码都一样(三码合一)
3. 负数的反码 = 原码符号位不变，其它位取反(0、1互换)
4. 负数的补码 = 反码 + 1（取反加一）；负数的反码 = 补码 - 1
5. 求补码就是做减法，正数不需要补码
6. 0的反码、补码还是0
7. Java没有无符号数，均有符号
8. 计算机运算时，均以补码的方式运算
9. 看运算结果要看其原码
10. 补码N位数加法舍弃N+1位的值