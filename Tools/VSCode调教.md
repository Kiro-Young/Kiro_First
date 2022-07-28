# VSCode调教

# VSCode 快捷键
## 原生快捷键
### 通用操作
    Ctrl + Shift + Z, 反撤销
    Shift + Alt + F, 整理代码
**Ctrl + /, 注释选中代码**
### 光标操作
    Ctrl + ← 将光标向左移动一个单词
    Ctrl + → 将光标向右移动一个单词
    Ctrl + Alt + U, 撤销上次光标操作
### 界面移动
    Ctrl + ↑ 向上移动当前界面
    Ctrl + → 向下移动当前界面
### 选中操作
    Shift + ← 向左选中 / 反选中一个字符(重要)
    Shift + → 向右选中 / 反选中一个字符(重要)
    Ctrl + Shift + ← 向左选中 / 反选中一个单词(重要)
    Ctrl + Shift + → 向右选中 / 反选中一个单词(重要)
    Ctrl + D当前有选中文本时, 将下一个与其相同的文本加入选中 (重要)
### 文本行操作
    Ctrl + C当前无选中文本时, 复制当前行
    Alt + ↑ 向上移动当前行, 当多行文本被选中时, 将当前多行文本向上移动 (重要)
    Alt + ↓ 向下移动当前行, 当多行文本被选中时, 将当前多行文本向下移动 (重要)

**选定区域代码，按Tab可以同时增加缩进；按Shift + Tab可以同时减少缩进！**

## 插件增加的快捷键
Markdown 语法
    Ctrl + M 进入数学公式模式 (加入美元符)
光标操作
Ctrl + Alt + U 将多选光标变为单选
选中操作
Shift + Alt + ← 向左复制当前选中文本 (重要)
Shift + Alt + → 向右复制当前选中文本 (重要)
Alt + ← 向左移动当前选中文本一个字符(重要)
Alt + → 向右移动当前选中文本一个字符(重要)
Ctrl + Alt + ← 向左移动当前选中文本一个单词(重要)
Ctrl + Alt + → 向右移动当前选中文本一个单词(重要)
计算器功能
Ctrl + Shift + Alt + E 计算当前选中表达式, 用等号连接并输出
Ctrl + Shift + Alt + R 计算当前选中表达式, 并替换当前选中表达式
Ctrl + Shift + Alt + D 定义当前选中表达式, 无输出
Python Brackets 带来的括号操作
Ctrl + Shift + Backspace 删除匹配的括号
Ctrl + Shift + / 选择匹配的括号

### 自己改的快捷键
#### C
* 编译：F7
* 编译并运行：F8
* 删除当前行：Ctrl + D
* Ctrl + Alt + ↑ 向上复制当前行, 当多行文本被选中时, 向上复制多行
  Ctrl + Alt + ↓ 向下复制当前行, 当多行文本被选中时, 向下复制多行
* Ctrl + Shift + Alt + ↑, 向上加入一个光标
  Ctrl + Shift + Alt + ↓, 向下加入一个光标
* 格式化文档：Alt + Shift + F

# 常用插件使用方法
## Better Comments(99%)
* //! 红色警戒 Alerts
* //? 蓝色疑问 Queries
* //todo 橙色 todo
* //* 绿色 
Highlights
    "tag": "//",
    "color": "#474747",
    "strikethrough": true,
    "underline": false,
    "backgroundColor": "transparent",
    "bold": false,
    "italic": false

## vscode-fileheader
* ctrl + alt + i 一键生成头文件注释

## 单词打字

