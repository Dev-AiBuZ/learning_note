## 注释（::/rem）

**方式一**：

::（双英文冒号）+注释内容

**方式二**：

rem（remark缩写）+注释内容



## 帮助（/?）

可以查看大部分命令参数

格式：命令+/?



## 标准格式

```bat
::去除盘符
@echo off

::脚本内容
echo "Hello World"

::保持窗口，适用于需要在窗口查看结果
pause
```



## 常见问题

### 加pause后依然闪退

在cmd（powershell不行）中执行a.bat（+参数一 +参数二），查看报错



### 输出中文乱码

记事本打开  ->  另存为  ->  修改编码为ANSI  ->  替换原文件



## 打开文件

### 打开文件

格式：type+文件名



### 新窗口打开文件

格式：start+文件名（+"title" ::新窗口名称）



### 调用其他bat

格式：call+a.bat（+参数一 +参数二）



## 多命令运算

### &&

命令一执行成功则执行命令二，命令一执行不成功则不执行命令二

格式：命令一&&命令二



### ||

命令一执行成功则不执行命令二，命令一执行不成功则执行命令二

格式：命令一||命令二



### &

顺序执行多条命令，而不管命令是否执行成功

格式：命令一&命令二&命令三



## 管道命令（|）

格式：命令一|命令二

```bat
::将上一个命令的输出作为下一个命令的输入
type a.txt | find "Hello World"
```



## set

```bat
::将字符串HelloWorld赋值给变量str
set str=HelloWorld
```

```bat
::/a表示存储数字内容，后续可参与计算
set /a result=1+1
```

```bat
::/p表示从键盘读取内容到**变量**
set /p input=
```



## echo

```bat
::打印字符串至命令行
echo "Hello World"
```

```bat
::打印变量至命令行
echo %str%
```



## find/findstr

find与findstr基本用法相同，常搭配|

```bat
::从输入中找到所有包含"Hello World"的行，并从命令行打印
find "Hello World"
```



## 变量引用（%%/!!）

**方式一**：%str%

```bat
::将变量打印
echo %str%
```

```bat
::将变量作为命令参数传入
find %str%
```

**方式二**：%0(0~9)

```bat
::接收命令行参数，将其作为变量（最多10个）
find %0
echo %1
```

**方式三**：!str!

```bat
::顺序执行多条命令时，保证变量str实时更新，常搭配&
setlocal enabledelayedexpansion
set var1=110
set var1=120&echo !var1!
```



## 重定向（>/>>）

### 字符串/变量>文件名

```bat
::将字符串/变量存入文件（覆写）
"str">a.txt(.xlsx)
%str%>a.txt(.xlsx)
```



### 字符串/变量>>文件名

```bat
::将字符串/变量存入文件（追加）
"str">>a.txt(.xlsx)
%str%>>a.txt(.xlsx)
```



### 合并文件

```bat
type *.txt>a.txt
```



## 字符串操作

### 字符串截取

```bat
%variable:~n,m%
```

n：开始截取字符串的偏移量；如果为正数，则从左边开始；如果为负数，则从右边开始；

m：要截取字符的个数。如果没有指定个数，则从偏移量位置开始截取剩下的所有字符。



### 字符串替换

```bat
%variable:str1=str2%
```

variable：原字符串

str1：被替换的字符串

str2：替换成的字符串，将使用该字符串去替换字符串中所有的 str1 字符串



### 字符串合并

```bat
::直接输出合并后的字符串
echo %A%%B%
```

```bat
::将合并后的字符串放入 C 变量中
set C=%A%%B%
```



## if

单行写法：

```bat
if exist %filename% (del %filename%) else echo %filename% missing
```

换行写法：

```bat
if exist %filename% (
    del %filename%
) else (
    echo %filename% missing
)
```



## for

```bat
for %%a in () do
```



### **/D**：遍历文件夹

```bat
::遍历当前目录下所有文件夹（包括子文件夹内文件夹）（不包括文件）
::%%a为文件夹名
for /d %%a in (*) do
```



### /R：遍历目标地址下文件

```bat
::遍历当前目录下所有文件（包括子文件夹内文件）（不包括文件夹）
::%%a为文件路径
for /r "C:\Desktop" %%a in (*) do
```



### /L：遍历数字

```bat
::(1,1,20)==(start,step,end)
for /l  %%a in (1,1,20) do
```



### /F：遍历文件内容

```bat
::%%a为文件中的行
for /f %%a in (a.txt) do
```



#### skip跳过前n行

```bat
for /f "skip=2" %%a in (a.txt) do (echo %%a)
```



#### eol跳过指定首字符的行

eol默认为;

```bat
for /f "eol=," %%a in (a.txt) do (echo %%a)
```



#### delims与tokens实现分段

- delims代表分割符，tokens代表被分割的第几段内容
- delims默认为空格,tokens从1开始且默认为1
- delims在行首时无效

```bat
::find输出的行被"[","]","\n"分为三段，%%a为"["与"]"中间的内容
for /f "delims=[] tokens=2" %%a in ('type a.txt ^| find "["') do (set content_within_brackets=%%a)
echo %content_within_brackets%
```



#### delims与多个tokens实现分段

- 声明循环变量时只能声明一个(%%a)
- 在do中的引用从声明的变量开始，按字母标顺序引用（%%m %%n %%o %%p）
- 在do中引用时必须调用每一个，若不够则最后一项会省略
- 连续的tokens可以用start-end简写，如：3-5==3,4,5

```bat
for /f "delims=[] tokens=1,3-5" %%a in ('type a.txt ^| find "["') do (echo %%a %%b %%c %%d)
```

例如：

a.txt：

a[bc[d]e]fgh

输出：

a d e fgh



#### delims与tokens实现部分内容分段

- 从某一tokens选择其之后所有内容可以用*代替，但无法用?占位
- 被代替的内容不会再参与delims与tokens的分段
- 无法选择某一tokens之前的所有内容
- 在do中引用时只能使用一次调用（%%b）

```bat
for /f "delims=[] tokens=1,3,*" %%a in ('type a.txt ^| find "["') do (echo %%a %%b)
```



#### 将find的结果存为变量

在单引号中，管道命令“|”和等号“=”前需要加转义字符”^“

```bat
for /f "delims=" %%a in ('type a.txt ^| find "a"') do (set line_with_a=%%a)
echo %line_with_a%
```





