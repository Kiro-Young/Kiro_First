# Markdown使用方法
# 基础篇
## 标题
* #+空格：标题
* #越多，级数越高

## 段落格式
* 空行换行（两回车）或两空格加回车换行
* *斜体*；_斜体_（插件快捷键<kbd>Ctrl</kbd>+<kbd>I</kbd>）
* **粗体**；__粗体__（插件快捷键<kbd>Ctrl</kbd>+<kbd>B</kbd>）
* ***粗斜体***；___粗斜体___
* 三个以上的*、-、_：分割线（中间可有空格）如
  --- - - -
* ~~删除线~~：两端各两个~~
* <u>下划线</u>：前开后闭
* ==高亮==（仅Markdown Preview Enhanced有）

## 列表
1. 无序列表：*、+、-加空格
2. 有序列表：数字加.（点号）
   * 列表嵌套：前面三/四空格，一Tab或VScode快捷键<kbd>Ctrl</kbd>+<kbd>]</kbd>或<kbd>[</kbd>）
3. Markdown Preview Enhanced 拓展功能：任务列表:
- [x] 已经完成的事 1
- [ ] 仍未完成的事 2

## 区块
* 区块：段落开头用>加空格
> 区块可嵌套，>的数量决定嵌套层数
>> 数量越多，层数越多
>>> 可以更多
> * 区块中可直接使用列表
* 列表中用区块要换行，且加两空格或一Tab
  > 比如这样

## 代码
* 用两反引号``前后包单函数或片段代码，如
    `printf() for(i=1;i<5;i++)`
* 代码区块则前后三个`，并在起始同行可注明语言，如
```C
#include<stdio.h>
int main()
{
  printf("Hello,Markdown!"\n);
}
```
* Markdown Preview Enhanced 拓展功能：代码行数的显示:
```javascript {.line-numbers}
function add(x, y) {
  return x + y
}
```

## 链接
* [链接名称](链接地址)

可以使用网址和图床:
[OrangeX4's Blog](https://orangex4.cool/)

![OrangeX's Avatar](https://orangex4.cool/images/icons/profile.jpg)

也可以在本地用相对地址:
[Other](other.md)

![OrangeX's Avatar](images/profile.jpg)

## 图片
* ![图片提示语](图片地址)，最后还可以用引号包住并加上选择性的 'title' 属性的文字，如：
![RUNOOB 图标](http://static.runoob.com/images/runoob-logo.png)

* 剪贴板图片插入（Paste Image 插件）
使用之前做一点小调整:设置窗口输入 Paste Image Path 并搜索, 将框内的文本改成 ${currentFileDir}/image.按下<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>V</kbd>就能把图片自动保存到当前目录下, 并以正确的格式粘贴到当前的 Markdown 文件中。如果你需要上传到图床, 便于在互联网中分享的话, 也可以用 Better Markdown & Latex Shortcuts 中的功能, 按下快捷键 <kbd>Shift</kbd>+<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>V</kbd>, 就可以上传到图床并自动以正确格式粘贴到当前 Markdown 文件中.
* 图片可以用本地也可以用网图，本地文件路径不可动，网络需要上传到图床，也存在丢失风险。个人认为要么用OneNote、Word等专用软件去处理图片，要么将图片放在md文件同目录下，好找好传不易丢。
  
## 表格
* 制作表格使用“|”来分隔单元格，使用“-”来分隔表头和其他行。语法格式如下：（表格要另起一行且至少再空一行）

|  表头   | 表头  |
|  ----  | ----  |
| 单元格  | 单元格 |
| 单元格  | 单元格 |

快捷键:自动表格对齐: Shift + Alt + F

# 进阶篇
## 支持的 HTML 元素
不在 Markdown 涵盖范围之内的标签，都可以直接在文档里面用 HTML 撰写。目前支持的 HTML 元素有：“kbd”（键盘文本）、“b”、“i”、“em”、“sup”、“sub”、“br”等 （使用时引号换<>），如：使用 <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Del</kbd> 重启电脑

## 转义
Markdown使用了很多特殊符号来表示特定的意义，如果需要显示特定的符号则需要使用转义字符，Markdown 使用反斜杠\转义特殊字符，如：**文本加粗** ，\*\* 正常显示星号 \*\*
Markdown 支持以下这些符号前面加上反斜杠来帮助插入普通的符号：\  反斜线，`  反引号，*  星号，_  下划线，{}  花括号，[]  方括号，()  小括号，#  井号，+  加号，-  减号，.  英文句点，!  感叹号

## 注释
注释不会被渲染出来，可以随手做点草稿, 如果还想保留着, 但是不显示, 就可以按下快捷键<kbd>Ctrl</kbd> + <kbd>\\</kbd> 将当前行注释 <kbd>\/</kbd> 反注释.
注释语法:
<!-- 你看不见我 -->
<!-- 多行注释
就像这样 -->
VSCode 会在你每次修改代码之后, 重新渲染一遍.
如果有很多很多的数学公式, 渲染会很慢, 这时候有两个建议:分成多个文件, 避免单文件过大；或者将暂时不看的部分注释掉, 加快渲染速度!

## 数学公式
* Markdown 的数学公式吸纳了大部分的 Latex 语法, 你可以以一种简单的方式在 VSCode 中书写数学公式.
**行内公式（两个\$\$包夹）**，如：
单位圆 $x^2+y^2=1$
**公式块（两端各两个\$\$包夹）**，如：
$$
\begin{cases}
x=\rho\cos\theta \\
y=\rho\sin\theta \\
\end{  cases}
$$

### 可能不太常用的数学公式编辑方法
* VSCode 有着非常便捷好用的自动补全功能, 只需要简单地打出你想打的内容的几个字母 (乱序也行), 再使用 ↑ ↓ 进行选择, 最后按下回车就可以打出你想要的内容。还有, 不要在公式内使用中文, 除非是 \text{中文} (但也不推荐)
1. 上标和下标
上标 $x^2 + y^{12} = 1$
下标 $x_1 + y_{12} = 1$
2. 分式
较小的行内行分数 $\frac{1}{2}$
展示型的分式 $\displaystyle\frac{x+1}{x-1}$
其中 \displaystyle 用于将行内展示转为块状展示.
3. 根式
开平方 $\sqrt{2}$
开 $n$ 次方 $\sqrt[n]{2}$
4. 空格
数学公式中的空格和换行都会在编译时被忽略.
输入空格:
紧贴 $a\!b$
没有空格 $ab$
小空格 $a\,b$
中等空格 $a\;b$
大空格 $a\ b$
quad 空格 $a\quad b$
两个 quad 空格 $a\qquad b$
5. 累加, 累乘和积分
累加 $\sum_{k=1}^n\frac{1}{k}  \quad  \displaystyle\sum_{k=1}^n\frac{1}{k}$

累乘 $\prod_{k=1}^n\frac{1}{k}  \quad  \displaystyle\prod_{k=1}^n\frac{1}{k}$

积分 $\displaystyle \int_0^1x{\rm d}x  \quad  \iint_{D_{xy}}  \quad  \iiint_{\Omega_{xyz}}$
6. 括号修饰
用 \left 和 \right 可以让括号适配内部大小

圆括号 $\displaystyle \left(\sum_{k=1}^{n}\frac{1}{k} \right)^2$

方括号 $\displaystyle \left[\sum_{k=1}^{n}\frac{1}{k} \right]^2$

花括号 $\displaystyle \left\{\sum_{k=1}^{n}\frac{1}{k} \right\}^2$

尖括号 $\displaystyle \left\langle\sum_{k=1}^{n}\frac{1}{k} \right\rangle^2$
7. 多行算式对齐
居中:

$$
\begin{aligned}
y &=(x+5)^2-(x+1)^2 \\
&=(x^2+10x+25)-(x^2+2x+1) \\
&=8x+24 \\
\end{aligned}
$$

左对齐:

$
\begin{aligned}
y &=(x+5)^2-(x+1)^2 \\
&=(x^2+10x+25)-(x^2+2x+1) \\
&=8x+24 \\
\end{aligned}
$
8. 方程组
$$
\begin{cases}
k_{11}x_1+k_{12}x_2+\cdots+k_{1n}x_n=b_1 \\
k_{21}x_1+k_{22}x_2+\cdots+k_{2n}x_n=b_2 \\
\cdots \\
k_{n1}x_1+k_{n2}x_2+\cdots+k_{nn}x_n=b_n \\
\end{cases}
$$

9.   特殊字符：搜索 "Latex 符号表"
10.   公式编号与引用
$$
x+2 \tag{1.2}
$$

$$
\begin{equation}
x^n+y^n=z^n
\end{equation}
$$

由公式 $(1.2)$ 可得到结论
11.  零碎的重要语法
点乘 $\cdot$, 叉乘 $\times$, 异或 $\otimes$, 直和 $\oplus$, 加减 $\pm$, 复合 $\circ$.
小于等于 $\leq$, 大于等于 $\geq$, 不等 $\neq$, 恒等 $\equiv$, 约等 $\approx$, 等价 $\cong$, 相似 $\sim$, 相似等于 $\simeq$, 点等 $\doteq$.
逻辑与 $\land$, 逻辑或 $\lor$, 逻辑非 $\lnot$, 蕴涵 $\to$, 等价 $\leftrightarrow$.
因为 $\because$, 所以 $\therefore$, 存在 $\exist$, 任意 $\forall$.
左小箭头 $\leftarrow$, 右小箭头 $\rightarrow$, 左大箭头 $\Leftarrow$, 右大箭头 $\Rightarrow$, 右长箭头 $\xrightarrow[fgh]{abcde}$.
属于 $\in$, 包含于 $\subset$, 真包含于 $\subseteq$, 交 $\cap$, 并 $\cup$, 空集 $\empty$
短向量 $\vec{x}$, 长向量 $\overrightarrow{AB}$, 上横线 $\overline{p}$.
无限 $\infty$, 极限 $\lim$, 微分 ${\rm d}$, 偏导 $\partial$, 点求导 $\dot{y}$, 点二阶导 $\ddot{y}$, 变化量 $\Delta$, 梯度 $\nabla$.
横省略 $\cdots$, 竖省略 $\vdots$, 斜省略 $\ddots$.
常见函数 $\sin$, $\cos$, $\tan$, $\arcsin$, $\arccos$, $\arctan$, $\ln$, $\log$, $\exp$.

## 云端存储+Git控制版本


# 参考资料
1. [菜鸟教程](https://www.runoob.com/markdown/md-tutorial.html)
2. [知乎](https://zhuanlan.zhihu.com/p/366596107)
  >使用推荐插件：Markdown-Notes-Pack涵盖下列插件
   * Markdown Preview Enhanced
   * Markdown All in One
   * Better Markdown & Latex Shortcuts
   * Bracket Pair Colorizer 2
   * Paste Image
   * Code Spell Checker
   * Vscode Icons

# 源子于2022.02.12基本完善