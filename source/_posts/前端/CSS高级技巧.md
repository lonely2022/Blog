---
title: CSS高级技巧
date: 2022-05-28
updated: 2022-05-28
tags:
  - 小白的前端之路
  - CSS基础
categories: 前端开发
keywords: 
description: 
top_img: ./img/bg11.jpg
cover: ./img/bg21.jpg

---
# 元素的显示与隐藏

让一个元素在页面中隐藏或显示出来

共有三个属性

| 属性       | 属性值                              |
| ---------- | ----------------------------------- |
| display    | none \| display                     |
| visibility | hidden \| visible                   |
| overflow   | visible \| hidden \| scroll \| auto |

display属性隐藏后会脱标，不占有原来位置

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202205282000945.png)

visibility属性隐藏后不会脱标，继续占有原来位置

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202205282001733.png)

overflow属性针对溢出，visible | hidden | scroll | auto

| overflow属性值 | 描述                                 |
| -------------- | ------------------------------------ |
| visible        | 不剪切内容不添加滚动条               |
| hidden         | 隐藏超出对象尺寸的内容               |
| scroll         | 总分是显示滚动条                     |
| auto           | 超出内容自动显示滚动条，不超出不显示 |

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202205282002302.png)

# 精灵图技术

## 「概述」

- 图所示为网页的请求原理图，当用户访问一个网站时，需要向服务器发送请求，网页上的每张图像都要经过一次请求才能展现给用户。
- 然而，一个网页中往往会应用很多小的背景图像作为修饰，当网页中的图像过多时，服务器就会频繁地接受和发送请求，这将大大降低页面的加载速度。

为了有效地减少服务器接受和发送请求的次数，提高页面的加载速度。CSS 精灵其实是将网页中的一些背景图像整合到一张大图中（精灵图），然而，各个网页元素通常只需要精灵图中不同位置的某个小图，要想精确定位到精灵图中的某个小图。这样，当用户访问该页面时，只需向服务发送一次请求，网页中的背景图像即可全部展示出来。

## 「需要的属性」

- background-image、
- background-repeat
- background-position属性进行背景定位，
- 其中最关键的是使用`background-position` 属性精确地定位。

## 「核心总结」

首先我们知道，css精灵技术主要针对于背景图片，插入的图片img 是不需要这个技术的。

1. 精确测量，每个小背景图片的大小和位置。
2. 给盒子指定小背景图片时，背景定位基本都是 负值。

# 字体图标

网页中的一些小图标通常用字体图标iconfont来显示，字体图标本质上是字体，现实的是图标。

**字体图标下载网站**

- icomoon字库 https://icomoon.io 
- 阿里iconfont字库 https://www.iconfont.cn

1. 在字体图标网站选中图标下载后，需要将其引入到，将下载包里的fonts文件夹放入页面根目录下
2. 在CSS样式中全局声明字体，把这些字体文件通过CSS引入到我们页面中，一定要注意字体文件路径问题

**声明代码如下**

```css
@font-face {
font-family: ‘icomoon’;
src: url(‘fonts/icomoon.eot?7kkyc2’);
src: url(‘fonts/icomoon.eot?7kkyc2#iefix’) format(‘embedded-opentype’),
url(‘fonts/icomoon.ttf?7kkyc2’) format(‘truetype’),
url(‘fonts/icomoon.woff?7kkyc2’) format(‘woff’),
url(‘fonts/icomoon.svg?7kkyc2#icomoon’) format(‘svg’);
font-weight: normal;
font-style: normal;
}
span {
    font-family: 'icomoon';
    font-size: 100px;
    color: pink;
}
```

```html
<spam> </spam>  /复制图标网站上的源码
```

字体图标的追加：把压缩包中slection.json重新上传，然后选中自己想要更新的图标，重新下载压缩包，并途欢原来的文件即可。

# CSS三角

1. 我们用css 边框可以模拟三角效果
2. 宽度高度为0
3. 我们4个边框都要写， 只保留需要的边框颜色，其余的不能省略，都改为 transparent 透明就好了
4. 为了照顾兼容性 低版本的浏览器，加上 font-size: 0;  line-height: 0;

```css
div {

    width: 0; 

    height: 0;
    line-height:0；
    font-size: 0;
   border-top: 10px solid red;

   border-right: 10px solid green;

   border-bottom: 10px solid blue;

   border-left: 10px solid #000; 

     }
```

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202205281959548.png)

# CSS用户页面样式

## 「鼠标样式cursor」

设置或检索在对象上移动的鼠标指针采用何种系统预定义的光标形状。

| 属性   | 属性值      | 描述       |
| ------ | ----------- | ---------- |
| cursor | default     | 小白(默认) |
|        | pointer     | 小手       |
|        | move        | 移动       |
|        | text        | 文本       |
|        | not-allowed | 禁止       |

```css
<ul>
  <li style="cursor:default">我是小白</li>
  <li style="cursor:pointer">我是小手</li>
  <li style="cursor:move">我是移动</li>
  <li style="cursor:text">我是文本</li>
  <li style="cursor:not-allowed">我是文本</li>
</ul>
```

## 「轮廓线outline」

是绘制于元素周围的一条线，位于边框边缘的外围，可起到突出元素的作用。

```css
outline : outline-color || outline-style || outline-width 
```

但是我们都不关心可以设置多少，我们平时都是去掉的。
最直接的写法是 ： outline: 0;  或者  outline: none;

## 「防拖拽文本域resize」

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202205282012600.png)



```html
/*css行内式写法*/
<textarea style="resize: none;"> </textarea>
```

## 「vertical-align属性应用」

vertical-align 垂直对齐，它只针对于**「行内元素」**或者**「行内块元素」**

可以用来设置**图片表单文字对齐**和**去除图片底侧空白空袭**

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202205282016270.jpg)

```css
设置或检索对象内容的垂直对其方式。
vertical-align : baseline |top |middle |bottom 
```

**注意**

- vertical-align 不影响块级元素中的内容对齐，它只针对于**「行内元素」**或者**「行内块元素」**
- 特别是行内块元素， 通常用来控制图片/表单与文字的对齐。
- 有宽度的块级元素居中对齐，是margin: 0 auto;
- 让文字居中对齐，是 text-align: center;

## 「溢出文字省略号显示」

**三个步骤**

1. 先强制一行内显示文本
2. 超出的部分隐藏
3. 文字用省略号替代超出的部分

white-space属性设置或检索对象内文本显示方式。通常我们使用于强制一行显示内容

```css
white-space:normal ；默认处理方式

white-space:nowrap ； 强制在同一行内显示所有文本，直到文本结束或者遭遇br标签对象才换行。
```

text-overflow属性设置或检索是否使用一个省略标记（...）标示对象内文本的溢出

```css
text-overflow : clip ；不显示省略标记（...），而是简单的裁切 

text-overflow：ellipsis ； 当对象内文本溢出时显示省略标记（...）
```

```css
  /*1. 先强制一行内显示文本*/
      white-space: nowrap;
  /*2. 超出的部分隐藏*/
      overflow: hidden;
  /*3. 文字用省略号替代超出的部分*/
      text-overflow: ellipsis;
```

# 常见布局技巧

1. margin负值的运用
2. 文字环绕浮动元素
3. 行内块元素巧妙运用
4. CSS三角强化

