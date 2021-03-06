---
title: CSS基础
date: 2022-04-20
updated: 2022-07-04
tags:
  - 小白的前端之路
  - CSS基础
categories: 前端开发
keywords: 
description: 
top_img: ./img/bg14.jpg
cover: ./img/bg7.jpg

---
# CSS字体样式

## **「1. font-size」**

- font-size属性用于设置字号(字体大小)
- `谷歌浏览器`默认的文字大小为16px
- 不同浏览器可能默认显示的字号大小不一致，我们尽量给一个明确值大小，不要默认大小。一般给body指定整个页面文字的大小。

```css
p { font-size:20px; }
```

**单位**

相对长度单位、绝对长度单位

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202207081954476.png)

## **「2. font-family」**

font-family属性用于设置哪一种字体。

```css
p { font-family:"微软雅黑";}
```

指定多个字体，如果浏览器不支持第一个字体就会尝试下一个直到找到合适的字体，如果都没有，以电脑默认字体为准。

```css
p {font-family: Arial,"Microsoft Yahei", "微软雅黑";}
```

CSS Unicode字体

- 在 CSS 中设置字体名称，直接写中文是可以的。但是在文件编码（GB2312、UTF-8 等）不匹配时会产生乱码的错误。
- xp 系统不支持 类似微软雅黑的中文。
- 解决方案：英文来替代。比如`font-family:"Microsoft Yahei"`。在 CSS 直接使用 Unicode 编码来写字体名称可以避免这些错误。使用 Unicode 写中文字体名称，浏览器是可以正确的解析的。

```css
font-family: "\5FAE\8F6F\96C5\9ED1";   表示设置字体为“微软雅黑”。
```

## **「3. font-weight」**

| 属性值  | 描述                                                        |
| ------- | ----------------------------------------------------------- |
| normal  | 默认值（不加粗的）                                          |
| bold    | 定义粗体（加粗的）                                          |
| 100~900 | 400 等同于 normal，而 700 等同于 bold  (数字表示粗细用的多) |

## **「4. font-style」**

font-style属性用于定义字体风格，如设置斜体、倾斜或正常字体，其可用属性值如下：

| 属性   | 作用                                                    |
| ------ | ------------------------------------------------------- |
| normal | 默认值，浏览器会显示标准的字体样式  font-style: normal; |
| italic | 浏览器会显示斜体的字体样式。                            |

## **「5. font:综合设置字体样式」**

```css
选择器 { font: font-style  font-weight  font-size/line-height  font-family;}
```

**注意：**

- 使用font属性时，必须按上面语法格式中的顺序书写，不能更换顺序，各个属性以`空格`隔开
- 其中不需要设置的属性可以省略(取默认值),但必须保留`font-size`和`font-family`属性，否则font属性将不起作用

- 

## **「6. font总结」**

| 属性        | 表示     | **注意点**                                                   |
| ----------- | -------- | ------------------------------------------------------------ |
| font-size   | 字号     | 我们通常用的单位是px 像素，一定要跟上单位                    |
| font-family | 字体     | 实际工作中按照团队约定来写字体                               |
| font-weight | 字体粗细 | 记住加粗是 700 或者 bold  不加粗 是 normal 或者  400  记住数字不要跟单位 |
| font-style  | 字体样式 | 记住倾斜是 italic   不倾斜 是 normal  工作中我们最常用 normal |
| font        | 字体连写 | 1. 字体连写是有顺序的  不能随意换位置 2. 其中字号 和 字体 必须同时出现 |

# CSS外观属性

## **「1. color」**

color属性用于定义文本的颜色
其取值方式有以下3种：

实际工作中，用16进制的写法是最多的，且我们更喜欢简写方式比如#f0代表红色。

| 表示           | 属性值                        |
| -------------- | ----------------------------- |
| 预定义的颜色值 | red，green，blue，pink        |
| 十六进制       | \#FF0000，#FF6600，#29D794    |
| RGB代码        | rgb(255,0,0)或rgb(100%,0%,0%) |

## **「2.text-align」**

text-align属性用于设置文本内容的水平对齐方式，相当于html中的align对齐属性。

注意：是让盒子里面的文本内容水平居中， 而不是让盒子居中对齐

其可用属性值如下：

| 属性   | 解释             |
| ------ | ---------------- |
| left   | 左对齐（默认值） |
| right  | 右对齐           |
| center | 居中对齐         |

## **「3. line-height」**

line-height属性用于设置行间距，就是行与行之间的距离，即字符的垂直间距，一般称为行高。

- line-height常用的属性值单位有三种，分别为像素px，相对值em和百分比%，实际工作中使用最多的是像素px

```css
一般情况下，行距比字号大7--8像素左右就可以了。
line-height: 24px;
```

### 行高测量

行高测量方法：

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202207082015839.png)

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202207082016559.png)

行高我们利用最多的一个地方是：**可以让单行文本在盒子中垂直居中对齐**。

**文字的行高等于盒子的高度**行高  =  上距离 +  内容高度  + 下距离
上距离和下距离总是相等的，因此文字看上去是垂直居中的。

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202207082017497.png)

### 行高与高度的三种关系

- 如果 行高 等 高度  文字会 垂直居中
- 如果行高 大于 高度  文字会 偏下
- 如果行高小于高度  文字会  偏上

```css
  /*line-height 要设置在font属性下面，否则无效，例如：*/
  height: 80px;
  text-align: center;
  font: normal bold 30px "宋体";
  line-height: 80px;
```

可以使用display:flex;布局方式让文字水平垂直居中

```css
  display: flex;
  align-items: center;     /* 侧轴对齐方式*/
  justify-content: center; /* 主轴对齐方式 */
```

## **「4. text-indent」**

text-indent属性用于设置首行文本的缩进

- 其属性值可为不同单位的数值、em字符宽度的倍数、或相对于浏览器窗口宽度的百分比%，允许使用负值。
- 建议使用em作为设置单位。
- 1em 就是一个字的宽度。如果是汉字的段落，1em 就是一个汉字的宽度

```css
p {
      /*行间距*/
      line-height: 25px;
      /*首行缩进2个字  em  1个em 就是1个字的大小*/
      text-indent: 2em;  
 }
```

## **「5. text-decoration」**

文本的装饰text-decoration,通常我们用于给链接修改装饰效果

| 值           | 描述                                                  |
| ------------ | ----------------------------------------------------- |
| none         | 默认。定义标准的文本。取消下划线（最常用）            |
| underline    | 定义文本下的一条线。下划线 也是我们链接自带的（常用） |
| overline     | 定义文本上的一条线。（不用）                          |
| line-through | 定义穿过文本下的一条线。（不常用）                    |

## **「6. CSS外观属性总结」**

| 属性            | 表示     | 注意点                                                 |
| --------------- | -------- | ------------------------------------------------------ |
| color           | 颜色     | 我们通常用  十六进制  比如 而且是简写形式 #fff         |
| line-height     | 行高     | 控制行与行之间的距离                                   |
| text-align      | 水平对齐 | 可以设定文字水平的对齐方式                             |
| text-indent     | 首行缩进 | 通常我们用于段落首行缩进2个字的距离  text-indent: 2em; |
| text-decoration | 文本修饰 | 记住 添加 下划线  underline  取消下划线  none          |

# 标签显示模式

`标签显示模式`是标签以什么方式进行显示。HTML标签一般分为块标签和行内标签两种类型，它们也称为块元素和行内元素

**标签显示模式转换 display**

- 块转行内：display:inline;
- 行内转块：display:block;
- 块、行内元素转换为行内块：display: inline-block;

## **「1. 块级元素(block-level)」**

```html
常见的块元素有<h1>~<h6>、<p>、<div>、<ul>、<ol>、<li>等，其中<div>标签是最典型的块元素。
```

### 块级元素的特点

- 独占一行
- 高度，宽度，外边距以及内边距都可以控制。
- 宽度默认是容器(父级宽度)的100%
- 是一个容器及盒子，里面可以放行内或者块级元素
- **注意**：只有文字才能组成段落，因此p标签里面不能放块级元素，特别是p不能放div。同理，还有h1~h6，dt,它们都是文字类块级标签，里面不能放其他块级元素。

## **「2. 行内元素(inline-level)」**

```html
有的地方也称为内联元素

常见的行内元素有<a>、<strong>、<b>、<em>、<i>、<del>、<s>、<ins>、<u>、<span>等，其中<span>标签最典型的行内元素。
```

### 行内元素的特点

1. 相邻行内元素在一行上，一行可以显示多个。
2. 高度、宽度直接设置是无效的。
3. 默认高度就是它本身内容的宽度。
4. 行内元素只能容纳文本或其他行内元素。

###### 注意

- 链接里面不能再放链接
- 特殊情况a里面可以放块级元素，但是给a转换一下块级模式最安全。

## **「3. 行内块元素(inline-block)」**

```html
在行内元素中有几个特殊的标签——<img>、<input >、<td>，可以对它们设置宽高和对齐属性，有些资料可能会称它们为行内块元素。
```

### **行内块元素的特点**

1. 和相邻行内元素(行内块)在一行上，但是之间会有空白风险。一行可以显示多个
2. 默认宽度就是它本身内容的宽度。
3. 高度，行高，外边距以及内边距都可以控制。



## 三种模式总结

| 元素模式   | 元素排列                 | 设置样式         | 默认宽度         | 包含                   |
| ---------- | ------------------------ | ---------------- | ---------------- | ---------------------- |
| 块级元素   | 一行只能放一个块级元素   | 可以设置宽度高度 | 容器的100%       | 容器级可以包含任何标签 |
| 行内元素   | 一行可以放多个行内元素   | 不可设置宽度高度 | 它本身内容的宽度 | 容纳文本或其他行内元素 |
| 行内块元素 | 一行可以放多个行内块元素 | 可以设置宽度高度 | 它本身内容的宽度 |                        |

# CSS背景(background)

1. 

## **「1. 背景颜色」**

```css
background-color: 颜色值;   默认的值是 transparent  透明的
```

## **「2. 背景图片(image)」**

```css
语法：
background-image : none | url (url) ;
例如:
background-image: url(images/1.png);
```

## **「3. 背景平铺（repeat）」**

```css
background-repeat : repeat | no-repeat | repeat-x | repeat-y 
```

| 参数      | 作用                                 |
| --------- | ------------------------------------ |
| repeat    | 背景图像在纵向和横向上平铺（默认的） |
| no-repeat | 背景图像不平铺                       |
| repeat-x  | 背景图像在横向上平铺                 |
| repeat-y  | 背景图像在纵向平铺                   |

## **「4. 背景位置(position)」**

```css
background-position : length || length
background-position : position || position 
```

| 参数     | 值                                                           |
| -------- | ------------------------------------------------------------ |
| length   | 百分数 \| 由浮点数字和单位标识符组成的长度值                 |
| position | top \| center \| bottom \| left \| center \| right  方位名词 |

**注意：**

- 必须先指定background-image属性
- position 后面是x坐标和y坐标。可以使用方位名词或者 精确单位。
- 如果指定两个值，两个值都是方位名字，则两个值前后顺序无关，比如left  top和top  left效果一致
- 如果只指定了一个方位名词，另一个值默认居中对齐。
- 如果position 后面是精确坐标， 那么第一个，肯定是 x 第二个一定是y
- 如果只指定一个数值,那该数值一定是x坐标，另一个默认垂直居中
- 如果指定的两个值是 精确单位和方位名字混合使用，则第一个值是x坐标，第二个值是y坐标

### 背景简写：

- background：属性的值的书写顺序官方没有强制的标准。为了可读性，建议如下写：
- background: 背景颜色 背景图片地址 背景平铺 背景滚动 背景位置;

```css
/* 有背景图片背景颜色可以不用写*/
background: transparent url(image.jpg) repeat-y  scroll center top ;
```

## **「5. 背景半透明(CSS3)」**

```css
background: rgba(0, 0, 0, 0.3);
background: rgba(0, 0, 0, .3);
```

- 等同于background-color: rgba(0, 0, 0, .3)
- 最后一个参数是alpha 透明度 取值范围 0~1之间
- 我们习惯把0.3 的 0 省略掉 这样写 background: rgba(0, 0, 0, .3);
- 注意：背景半透明是指盒子背景半透明，盒子里面的内容不受影响
- 低于IE 9的版本不支持

### 盒子半透明 opacity

设置opacity元素的所有后代元素会随着一起具有透明性，一般用于调整图片或者模块的整体不透明度

```css
opacity: .2;
```

## **「6. 背景总结」**

| 属性                  | 作用             | 值                                                           |
| --------------------- | ---------------- | ------------------------------------------------------------ |
| background-color      | 背景颜色         | 预定义的颜色值/十六进制/RGB代码                              |
| background-image      | 背景图片         | url(图片路径)                                                |
| background-repeat     | 是否平铺         | repeat/no-repeat/repeat-x/repeat-y                           |
| background-position   | 背景位置         | length/position   分别是x  和 y坐标， 切记 如果有 精确数值单位，则必须按照先X 后Y 的写法 |
| background-attachment | 背景固定还是滚动 | scroll/fixed                                                 |
| 背景简写              | 更简单           | 背景颜色 背景图片地址 背景平铺 背景滚动 背景位置;  他们没有顺序 |
| 背景透明              | 让盒子半透明     | background: rgba(0,0,0,0.3);  后面必须是 4个值               |



