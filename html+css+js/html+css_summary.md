## HTML

### 换行与水平线

<br：换行

<hr：水平分割线



### 文本格式

<strong</> <b</>：黑体

<em</> <i</>：斜体

<ins</> <u</>：下划线

<del</> <s</>：删除线



### 图片

<img

src = ""：图片位置

alt = ""：图片未加载时显示的文字

title = ""：鼠标悬停时显示的文字

width / height = ""：图片长宽（系统自动等比例缩放）



### 超链接

<a</>

href = ""：跳转地址

 target="_blank"：新标签页打开

#：空链接



### 音频

<audio</>

src = ""：音频位置

controls= ""：显示控制面板

loop= ""：循环播放

autoplay= ""：自动播放



### 视频

<video</>

src = ""：视频位置

controls= ""：显示控制面板

loop= ""：循环播放

muted= ""：静音播放

autoplay= ""：自动播放（需要属性muted）



### 列表

#### 无序列表

<ul</>

<li</>：列表条目

#### 有序列表

<ol</>

<li</>：列表条目

#### 定义列表

<dl</>

<dt</>：列表标题

<dd</>：列表条目



### 表格

<table</>

<tr</>：行

<th</>：表头单元格

<td</>：内容单元格

<thead</>：表格头部

<tbody</>：表格主体

<tfoot</>：表格底部

示例：

<table><!--表格-->
    <thead><!--表头-->
        <tr><!--行-->
            <th>表头1</th><!--内容单元格-->
            <th>表头2</th>
            <th>表头3</th>
        </tr>
    </thead>
    <tbody><!--表格主体-->
        <tr>
            <td>内容1</td>
            <td>内容2</td>
            <td>内容3</td>
        </tr>
    </tbody>
    <tfoot><!--表格底部-->
    	<tr>
            <td>内容1</td>
            <td>内容2</td>
            <td>内容3</td>
        </tr>
    </tfoot>
</table>
<hr>

#### 合并单元格

rowspan = ""：上合并下（合并单元格个数，1为不合并）

colspan = ""：左合并右（合并单元格个数，1为不合并）



### 表单

#### input标签

<input

type = "text"：单行文本框

type = "password"：密码框（输入隐藏）

type = "radio"：单选框（需要属性name）

`<input type="radio" name="gender"> 男`
`<input type="radio" name="gender"> 女`

type = "checkbox"：多选框

type = "file"：上传文件（可用属性multiple上传多个文件）

placeholder=""：未输入时显示的信息

background-color: transparent：背景透明

outline: none：取消勾选时边框

checked：默认勾选

#### 下拉菜单

<select</>

<option</>：选项

checked：默认勾选

示例：

<select>
<option>北京</option>
<option>上海</option>
<option>广州</option>
<option>深圳</option>
<option>武汉</option>
</select>

#### 文本域（多行输入文本）

<textarea</>

#### label标签（扩大点击范围）

写法一：

`<input type="radio" id="man">`
`<label for="man">男</label>`

写法二：

`<label><input type="radio"> 女</label>`

#### 按钮

<button</>

type = "submit"：点击后提交数据至后台（默认）

type = "reset"：点击后恢复表单为默认值

type = "button：普通按钮，默认没有功能



## CSS

内部样式：位于title下方：<style</>

外部样式：位于title下方：<link rel="stylesheet" href="（CSS路径）"

行内样式：body内标签的 style 属性值里：<div style="color: red; font-size:20px;"</>



### 文字属性

font-size：文字大小（单位：px）

color：文字颜色（red/rgb()/rgba()/#）

font-style：文字是否倾斜（normal/italic）

line-height：行高（单位：px/none）

font-family：字体（楷体）

text-indent：文本缩进（单位：px/em）

text-align：文本对齐（left/center/right）

text-decoration：文本修饰（none/underline）

#### font复合属性

font: 是否倾斜 是否加粗 字号/行高 字体

例如：font: italic 700 30px/2 楷体;



### 盒子属性

width：宽度

height：高度

display：转换显示属性（block/inline-block/none）



#### 背景图

##### 背景颜色

**background-color**：背景颜色



##### 背景图

**background-image**：url(路径)



##### 平铺方式

**background-repeat**：no-repeat/repeat/repeat-x/repeat-y



##### 背景图位置

**background-position**：left/right/top/bottom/center/px

left==0%

right==100%

百分比：背景图百分比位置与盒子百分比位置对齐



##### 背景图缩放

**background-size**：cover/contain

cover：盒子被图片覆盖，盒子内无缝隙

contain：盒子包含图片，盒子内有缝隙



##### 背景图固定

**background-attachment**：fixed



##### 背景图复合属性

background: 背景色 背景图 背景图平铺方式 背景图位置/背景图缩放 背景图固定

例如：background: pink url(./images/1.png) no-repeat right center/cover;



#### 盒子模型组成

##### 多值写法：

| 取值个数 | 例如                          | 含义                                   |
| -------- | ----------------------------- | -------------------------------------- |
| 一个值   | padding: 10px;                | 四个方向均为10px                       |
| 四个值   | padding: 10px 20px 40px 80px; | 上：10px；右：20px；下40px；左：80px； |
| 三个值   | padding: 10px 40px 80px;      | 上：10px；左右40px；左：80px；         |
| 两个值   | padding: 10px 80px;           | 上下：10px；左右：80px；               |

##### padding：内边距

padding / padding-方位名词

例如：padding: 30px;

例如：padding-top: 10px;

##### border：边框线

四个方向：border（solid/dashed/dotted）

border：边框线粗细  线条样式  颜色（不区分顺序）

例如：border: 5px solid brown;

单方向边框线：border-方位名词

border-方位名词：边框线粗细  线条样式  颜色（不区分顺序）

例如：border-top: 2px solid red;

##### margin：外边距

margin / margin-方位名词

例如：margin: 30px;

例如：margin-top: 10px;

##### 滚动条

overflow: (hidden/auto)

##### 圆角

border-radius: (数字+px / 百分比)

| 取值个数 | 例如                                | 含义                                           |
| -------- | ----------------------------------- | ---------------------------------------------- |
| 一个值   | border-radius: 10px;                | 四个角均为10px                                 |
| 四个值   | border-radius: 10px 20px 40px 80px; | 左上：10px；右上：20px；右下40px；左下：80px； |
| 三个值   | border-radius: 10px 40px 80px;      | 左上：10px；右上&左下：40px；右下：80px；      |
| 两个值   | border-radius: 10px 80px;           | 左上&右下：10px；右上&左下：80px；             |

##### 阴影

box-shadow: (X 轴偏移量  Y 轴偏移量  模糊半径  扩散半径  颜色  内外阴影(内阴影为inset))

例如：box-shadow: 2px 5px 10px 0 rgba(0, 0, 0, 0.5) inset;

##### 版心居中

**margin: 0 auto;**

##### 清除默认样式

```css
/* 清除默认内外边距 */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
/* 清除列表项目符号 */
li {
  list-style: none;
}
```

##### 外边距塌陷现象

解决方法：

* 取消子级margin，父级设置padding
* 父级设置 overflow: hidden
* 父级设置 border-top



### 选择器

#### 标签选择器

例如：p, h1, div, a, img...... {}



#### 类选择器

例如：

声明：.class_selector {}

调用：<div class = "class_selector"</>



#### id选择器

配合javascript

例如：

声明：#class_selector {}

调用：<div id = "class_selector"</>



#### 通配符选择器

选择页面所有标签

例如：* {}



#### 复合选择器

##### 后代选择器（空格隔开）

后代选择器：选择父类后所有满足条件的后代

div span {}

##### 子代选择器（>隔开）

子代选择器：选择父类后所有满足条件的子代

div>span {}

##### 并集选择器（，隔开）

并集选择器：选择满足任一条件的元素

div,span {}

##### 交集选择器（不隔开）

交集选择器：选择满足所有条件的元素

div.class_selector {}

##### 伪类选择器（：隔开（hover））

伪类选择器：超链接访问状态

link：访问前

visited：访问后

hover：鼠标悬停时

active：鼠标点击时

first-child：查找第一个元素

last-child：查找最后一个元素

nth-child()：查找第n个元素

##### 伪元素选择器（::隔开）

伪元素选择器：在元素前后插入元素

before：元素前

after：元素后

例如：div::before {content = "";}



### Flex布局

**display: flex**



#### ~主轴对齐

**justify-content**

center：盒子延主轴居中排列

space-between：盒子之间距离等分

space-aroud：空白间距均分在盒子两侧

space-evenly：盒子之间、盒子与容器之间间距相等

flex-end：盒子从终点开始依次排序



#### ~行内对齐（侧轴）

**align-content**

center：盒子延主轴居中排列

space-between：盒子之间距离等分

space-aroud：空白间距均分在盒子两侧

space-evenly：盒子之间、盒子与容器之间间距相等

flex-end：盒子从终点开始依次排序



#### ~盒子换行

**flex-wrap: wrap**



#### 侧轴对齐

**align-items**：当前弹性容器内**所有**弹性盒子的侧轴对齐方式（给**弹性容器**设置）

**align-self**：单独控制**某个弹性盒子**的侧轴对齐方式（给**弹性盒子**设置）

stretch：盒子延侧轴拉伸至铺满容器

center：盒子延侧轴居中排列

flex-start：盒子从起点开始依次排序

flex-end：盒子从终点开始依次排序



#### 修改主轴方向

**flex-direction**

row：水平，从左向右（默认）

**column**：垂直，从上向下

row-reverse：水平，从右向左

column-reverse：垂直，从下向上



#### ~弹性伸缩比

**flex: 1**

整数数字代表子级盒子占父级比例，无flex属性的子级盒子压缩至其中元素宽度



### CSS高级

#### 相对定位

**position: relative**

left/right/top/bottom：设置盒子位置

特点：

* 不脱标，占用自己原来位置
* 显示模式特点保持不变
* 设置边偏移则相对自己原来位置移动



#### 绝对定位

**position: absolute**（父级必须设为relative）

left/right/top/bottom：设置盒子位置

特点：

* 脱标，不占位
* 显示模式具备行内块特点
* 设置边偏移则相对最近的已经定位的祖先元素改变位置
* 如果祖先元素都未定位，则相对浏览器可视区改变位置

##### ~定位居中

```css
position: absolute;
left: 50%;
top: 50%;
transform: translate(-50%, -50%);
```



#### 固定定位（弹窗）

**position: fixed**

特点：

* 脱标，不占位
* 显示模式具备行内块特点
* 设置边偏移相对浏览器窗口改变位置



#### 堆叠层级（z-index）

**z-index: 1**

默认值为0，取值越大，层级越高



#### 垂直对齐（vertical-align）

**vertical-align**

top：顶部对齐

middle：居中对齐

bottom：底部对齐



#### 过渡

**transition: all 1s**

过渡属性（不要设给hover），花费时间（s）



#### 透明度

**opacity**

0：完全透明（元素不可见）

1：不透明

0-1之间小数：半透明



#### 光标

**cursor**

pointer：小手

text：工字形

move：十字光标



#### 平面转换

##### 平移

**transform: translate**(X轴移动距离, Y轴移动距离);

百分比：图片向右移动该百分比的距离



##### 旋转

**transform: rotate**(旋转角度 deg);



##### 缩放

**transform: scale**(缩放倍数);
**transform: scale**(X轴缩放倍数, Y轴缩放倍数);



##### 倾斜

**transform: skew**(角度度数 deg);



##### 转换原点

**transform-origin**: 水平原点位置 垂直原点位置;

适用于旋转/缩放



##### 多重转换

**transform: translate() rotate();**

先平移再旋转

多重转换原理：以第一种转换方式坐标轴为准转换形态

* 旋转会改变网页元素的坐标轴向
* 先写旋转，则后面的转换效果的轴向以旋转后的轴向为准，会影响转换结果



#### 渐变

##### 线性渐变

**background-image: linear-gradient**(渐变方向, 颜色1 终点位置, 颜色2 终点位置, ...);

渐变方向：可选（默认为向上）

* to 方位名词
* 角度度数

终点位置：可选

* 百分比



##### 径向渐变

**background-image: radial-gradient**(半径 at 圆心位置, 颜色1 终点位置, 颜色2 终点位置, ...);

