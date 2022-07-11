---
title: JavaScript DOM
date: 2022-06-16
updated: 2022-06-30
tags:
  - 小白的前端之路
  - JavaScript基础
  - JavaScript API
  - DOM
categories: 前端开发
keywords: 
description: 
top_img: ./img/bg20.jpg
cover: ./img/bg12.jpg

---
# DOM简介



## **「1.1什么是DOM」**

文档对象模型(Document Object Model ，简称DOM)，是W3C组织推荐的处理扩展标记语言(HTML或者XML)的编程接口。

W3C已经定义了一系列的DOM接口，通过这些接口可以改变网页的内容，结构和样式。

1. 对于JavaScript，为了能够使JavaScript操作HTML，JavaScript就有了一套自己的DOM编程接口
2. 对于HTML，DOM使得HTML形成了一颗DOM树，包含文档，元素，节点。
3. 我们获取过来的DOM元素是一个对象（Object），所以称为 文档对象模型

## **「1.2DOM树」**

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202206141517149.png)

- 文档：一个页面就是一个文档，DOM中用document表示
- 元素：页面中所有标签都是元素，DOM中用element表示
- 节点：网页中所有内容都是节点(标签，属性，文本，注释)，DOM中使用node表示

DOM把以上内容都看作是对象

# 获取元素

## **「2.1如何获取页面元素」**

DOM在实际开发中主要用来操作元素

有如下几种方式

- 根据ID获取
- 根据标签名获取
- 通过HTML5新增方法获取
- 特殊元素获取

## **「2.2根据id」**

```html
// document.getElementById('id名');
<div id="time">2022</div>
<script>
    // 1.因为我们文档页面从上往下加载，所以先有标签，script标签写在下面
    // 2.get 获得 Element 元素 By 通过 "驼峰命名法"
    // 3.参数 id是一个大小写敏感的字符串
    // 4.返回的是一个元素对象
    var timer = document.getElementById('time');
	console.log(timer);
	console.log(typeof timer); // Object
	// 5.console.dir 打印我们返回的元素对象，更好的查看里面的属性和方法
	console.dir(timer);
</script>

```

## **「2.3根据标签名」**

返回的是带有指定标签名的对象的集合，

- 因为是集合，所以使用时要遍历
- 得到元素对象是动态的

```js
 document.getElementsByTagName('标签名');
```

还可以获取某个元素（父元素）内部所有指定标签名的子元素，父元素必须是单个对象（必须指明是哪一个元素对象），获取时不包括父元素自己

```js
 element.getElementByName('标签名');
//element为父元素，标签名是子元素
```



```html
// document.getElementsByTagName('标签名');
// element.getElementsByTagName('标签名');
<body>
    <ul>
        <li>知否知否应是等你好久1</li>
        <li>知否知否应是等你好久2</li>
        <li>知否知否应是等你好久3</li>
        <li>知否知否应是等你好久4</li>
        <li>知否知否应是等你好久5</li>
    </ul>
    <ol id = "ol">
        <li>生僻字</li>
        <li>生僻字</li>
        <li>生僻字</li>
        <li>生僻字</li>
        <li>生僻字</li>
    </ol>
    <script>
        // 1.返回的是 获取过来元素对象的集合 以伪数组的形式存储
        var lis = document.getElementsByTagName('li');
        console.log(lis);
        console.log(lis[0]);
        // 2.要依次打印里面的元素，可以采用遍历
        for (var i = 0;i < lis.length; i++) {
            console.log(lis[i]);
        }
        // 3.如果页面中只有一个li，返回的还是伪数组的形式 
        // 4.如果页面中没有这个元素 返回的是空的伪数组形式
// 5.element.getElementsByTagName('标签名');
        var ol = document.getElementsByTagName('ol'); // [ol]
        console.log(ol[0].getElementsByTagName('li')); //父元素必须指明具体元素，不能是数组
        // 或者ol指定一个id
        var ol = documnet.getElementsById('ol');
        console.log(ol.getElementsByTagName('li'));
    </script>
</body>
```

## **「2.4通过H5获取」**

```js
document.getElementsByClassName('类名'); //根据类名返回元素对象集合
```

```js
document.querySelector('选择器'); //根据指定选择器返回第一个元素对象
```

```js
documnet.querySelectorAll('选择器'); //根据指定选择器返回所有元素对象
```

```html
<body>
    <div class="box">盒子1</div>
    <div class="box">盒子2</div>
    <div id="nav">
        <ul>
            <li>首页</li>
            <li>产品</li>
        </ul>
    </div>
    <script>
        // 1.documnet.getElementsByClassName('类名'); 
        var boxs = documnet.getElementsByClassName('box');
        console.log(boxs);
        // 2.document.querySelector('选择器'); 返回第一个，里面选择器要加相应符号
        var firstbox = document.querySelector('.box');
        console,log(firstbox);
        var nav = documnet.querySelector('#nav');
        console.log(nav);
        var li = documnet.querySelector('li');
        console.log(li);
        // 3.documnet.querySelectorAll('选择器'); //返回所有元素对象集合
        var allBox = document.querySelectorAll('.box');
        console.log(allBox);
    </script>
</body>
```

## **「2.5获取特殊元素（body，html）」**

- 获取body元素

  ```js
  document.body  // 返回body元素对象
  ```

  

- 获取html元素

  ```js
  document.documentElement   // 返回html元素对象
  ```

  

```html
<body>
    <script>
        // 1.获取body元素
        var bodyEle = document.body;
        console.log(bodyEle);
        console.dir(bodyEle);
        // 2.获取html元素
        var htmlEle = document.documentElement;
        console.log(htmlEle);
    </script>
</body>
```

# 事件基础

## **「3.1事件概述」**

JavaScript使我们有能力创建静态页面，而事件是可以被JavaScript侦测搭配的行为

简单理解：触发….响应机制

网页中每个元素都可以产生某些可以触发JavaScript的事件，例如我们可以在用户点击某按钮时产生一个事件，然后去执行某些操作

## **「3.2事件三要素」**

```html
<body>
    <botton id="btn">唐伯虎</botton>
    <script>
        //点击一个按钮
        //1.事件是由三部分组成，事件源 事件类型 事件处理程序 我们称为事件三要素
        //(1) 事件源 事件被触发的对象
        var btn = document.getElementById('btn');
        //(2) 事件类型 如何触发 比如鼠标点击（onclick）还是鼠标经过还是键盘按下
        //(3) 事件处理程序 如何通过一个函数赋值的方式 完成
        btn.onclick = function() {
            alert('点秋香');
        }
    </script>
</body>
```

## **「3.3执行事件的步骤」**

1. 获取事件源
2. 注册事件（绑定事件）
3. 添加事件处理程序（采取函数赋值形式）

常见鼠标事件

| 鼠标事件    | 触发条件         |
| ----------- | ---------------- |
| onclick     | 鼠标点击左键触发 |
| onmouseover | 鼠标经过触发     |
| onmouseout  | 鼠标离开触发     |
| onfocus     | 获得鼠标焦点触发 |
| onblur      | 失去鼠标焦点触发 |
| onmousemove | 鼠标移动触发     |
| onmouseup   | 鼠标弹起触发     |
| onmousedown | 鼠标按下触发     |

```html
<body>
    <div>盒子</div>
    <script>
        // 获取事件源
        var div = document.querySelector('div');
        // 绑定事件 div:onmouseover
        // 添加事件处理程序
        div:onmouseover = function() {
            alert ('我被选中了');
        }
    </script>
</body>
```

# 操作元素

JavaScript的DOM操作可以改变网页内容，结构和样式，我们可以利用DOM操作元素里面的内容属性等。注意一下都是属性。

## **「4.1改变元素内容」**

```js
elememt.innerText  // 从起始位置到终止位置的内容，但它会去除html标签，同时空格和换行也会去掉
```

```js
elemetn.innerHTML  // 起始位置到终点位置的全部内容，包括html标签同时保留空格和换行
```

### 案例：改变元素内容

```html
    <style>
        div,p {
            width: 300px;
            height: 30px;
            line-height: 30px;
            color: #fff;
            background-color: pink;
        }
    </style>

<body>
    <botton>显示系统当前时间</botton>
    <div>某个时间</div>
    <p>123</p>
    <script>
        // 当我们点击了按钮，div里面的文字会发生变化
        // 1.获取元素
        var btn = document.querySelector('button');
        var div = document.querySelector('div');
        // 2.注册事件
        btn:onclick = function() {
            div.innerHTML = getDate();
        }
        function getDate() {
            var date = new Date();
            var year = date.getFullYear();
            var month = date.getMonth() + 1;
            var dates = date.getDate();
            var arr = ['星期日','星期一','星期二','星期三','星期四','星期五','星期六'];
            var day = date.getDay();
            return '今天是：' + year + '年' + month + '月' + dates + '日' + arr[day];
        }
        // 元素也可以不用添加事件修改内容
        var p = document.querySelector('p');
        p.innerHTML = getDate();
    </script>
</body>
```

## **「4.2常用元素的属性操作」**

```
innerText innerHTML 改变元素内容
src href
id alt title
加一个 . 符号
```

### 案例：分时显示图片，显示不同问候语

```html
<body>
    // 根据系统不同时间判断
    // 利用多分支语句设置不同的图片内容
    // 需要一个图片，并根据时间修改图片，操作元素属性
    // 需要div元素显示不同问候语
    <img src="#" alt="好" title="上午好">
    <div>好好写代码</div>
    <script>

        // 1.获取元素
        var img = document.querySelector('img');
        var div = document.querySelector('div');
        // 2.得到当前小时数
        var date = new Date();
        var h = date.getHours();
        // 3.判断小时数改变图片文字信息
        if(h < 12) {
            img.src = '#';
            img.title = '上午好';
            div.innerHTML = '亲，上午好，好好写代码';
        } else if(h < 18) {
            img.src = '#';
            img.title = '下午好';
            div.innerHTML = '亲，下午好，好好写代码';
        } else {
            img.src = '#';
            img.title = '晚上好';
            div.innerHTML = '亲，晚上好，好好写代码';
        }
    </script>
</body>
```

## **「4.3表单元素属性操作」**

```
利用DOM可以操作如下表单元素属性
type value checked selected disabled
```

```html
<body>
    <button>按钮</button>
    <input type="text" value="输入内容">
    <script>
        //1.获取元素
        var btn = document.querySelector('button');
        var input = document.querySelector('input');
        //2.注册事件
        btn:onclick = function() {
            //input.innerHTML = '被点击了' 这个是普通盒子
            //表单里的值和文字是通过value来修改的
            input.value = '被点击了';
            //禁止点击
            this.disabled = true;
            //this 指向的是事件函数的调用者 btn
        }
    </script>
</body>
```

### 案例：仿京东显示隐藏密码

```

```



## **「4.4样式属性操作」**

我们可以通过JS修改元素大小，颜色，位置等样式

```js
element.style.属性  //行内样式操作
element.className  //类名样式操作
```

注意：

1. 如果样式修改较多，可以采用操作类名方式更改元素样式
2. class是一个保留字，因此使用className来操作类名属性
3. className会直接更改元素类名，会覆盖原先的类名

```html
<body>
    <div class="first">文本</div>
    <script>
//1.使用 element.style 修改样式，样式比较少或者功能简单情况下使用
        var test = document.querySelector('div');
        test:onclick = function() {
            this.style.backgroundColor = 'purple';
            this.style.color = '#fff';
            this.style.fontSize = '25px';
            this.style.marginTop = '100px';

// 2.使用element.className更改元素样式，适用于样式较多或者功能复杂的情况
            // 修改类名为change
            // 3.如果想要保留原来的类名，可以使用多类名选择器
            this.className = 'change';
            this.className = 'first change';
        }
    </script>
</body>
```



![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202206141824210.png)

## **「4.5排他思想」**

如果有同一组元素，我们想要某一个元素实现某种样式，需要用到循环的排他思想算法

1. 给所有元素全部清除样式（干掉其他人）
2. 给当前元素设置样式（留下我自己）
3. 注意顺序不能颠倒，首先干掉其他人，在设置自己

```html
<body>
    <button>按钮1</button>
    <button>按钮2</button>
    <button>按钮3</button>
    <button>按钮4</button>
    <button>按钮5</button>
    <script>
        //1.获取所有按钮元素
        var btns = document.getElementsByTagName('button');
        // btns得到的是伪数组，里面的每一个元素 btn[i]
        for(var i = 0; i < btns.length; i++) {
            btns[i].onclick = function() {
                //(1)先把所有按钮颜色去掉
                for(var i = 0; i < btns.length; i++) {
                    btns[i].style.backgroundColor = '';
                }
                //(2)然后让当前元素背景颜色为pink
                this.style.backgroundColor = 'pink';
            }
            
        }
        //2.排他算法
    </script>
</body>
```

### 案例：百度换肤效果

- 这个案例是给一组元素注册事件
- 给四个小图片利用循环注册点击事件
- 当我们点击了这个图片，让我们背景颜色改为当前的图片
- 核心算法：把当前图片的src 路径取过来，给body 作为背景即可

```html
	<style>
        *{
            margin: 0;
            padding: 0;
        }
        body{
            background: url(img/1.jpg) no-repeat center top;
        } 
        li {
            list-style: none;
        }
        .baidu {
            overflow: none;
            margin: 100px auto;
            background-color: #fff;
            width: 400px;
            padding-top: 3px;
        }
        .baidu li{
            float:left;
            margin: 0 1px;
            cursor: pointer;
        }
        .baidu img {
            width: 100px;
        }
    </style>
<body>
    <ul class="baidu">
        <li><img src="img/1.jpg" alt="无图片1"></li>
        <li><img src="img/2.jpg" alt="无图片2"></li>
        <li><img src="img/3.jpg" alt="无图片3"></li>
        <li><img src="img/4.jpg" alt="无图片4"></li>
    </ul>
    <script>
        //1.获取元素
        var imgs = document.querySelector('.baidu').querySelectorAll('img');
        //2.循环注册事件
        for (var i = 0; i < imgs.length; i++) {
            imgs[i].onclick = function() {
                // this.src就是我们点击图片的路径
                // console.log(this.src)
                // 把这个路径 this.src给body
                document.body.style.backgroundImage = 'url('+ this.src +')';
            }
        }
	</script>
</body> 
```

### 案例：表格隔行变色效果

- 用到鼠标经过事件和鼠标离开事件
- 核心思路：鼠标经过tr行，当前行变背景颜色，鼠标离开去掉当前背景颜色
- 注意：第一行（thead里面的行）不需要变换颜色

```html
    <style>
        table{
            width: 800px;
            margin: 100px auto;
            text-align: center;
            border-collapse: collapse;
            font-size: 14px;
        }
        thead tr {
            height: 30px;
            background-color: skyblue;
        }
        tbody tr {
            height: 30px;
        }
        tbody td{
            border-bottom: 1px solid #d7d7d7;
            font-size: 12px;
            color: blue;
        }
        .bg {
            background-color: pink;
        }
    </style>
<body>
    <table>
        <thead>
            <tr>
                <td>代码</td>
                <td>名称</td>
                <td>最新公布净值</td>
                <td>累计净值</td>
                <td>前单位净值</td>
                <td>净值增长率</td>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>003526</td>
                <td>农银金辉</td>
                <td>1.075</td>
                <td>1.254</td>
                <td>1.548</td>
                <td>1.5556</td>
            </tr>
            <tr>
                <td>003526</td>
                <td>农银金辉</td>
                <td>1.075</td>
                <td>1.254</td>
                <td>1.548</td>
                <td>1.5556</td>
            </tr>
        </tbody>
    </table>
<script>
// 1.获取元素 获得tbody里面的tr
var trs = document.querySelector('tbody').querySelectorAll('tr');
// 2.利用循环注册事件
for(var i = 0; i < trs.length; i++) {
    // 3.鼠标经过事件 onmouseover
    trs[i].onmouseover = function() {
        this.className = 'bg';
    }
    trs[i].onmouseout = function() {
    // 4.鼠标离开事件 onmouseout
        this.className = '';
    }
}
</script>
</body>
```

### 案例：全选或反选

- 全选或取消全选的做法：让下面的所有复选框的checked属性（选中状态）跟随全选按钮即可
- 下面复选框需要全部选中，上面全选才能选中的做法：给下面所有复选框绑定点击事件，每次点击，都要循环查看下面所有复选框是否有未选中的，如果有一个未选中的，上面的全选就不选中
- 可以设置一个变量，来控制全选是否选中

```html
   <style>
            table{
            width: 800px;
            margin: 100px auto;
            text-align: center;
            font-size: 14px;
        	}
    </style>
<body>
        <table>
            <thead>
                <tr>
                    <td><input type="checkbox" id="j_cbAll"></td>
                    <td>商品</td>
                    <td>价格</td>
                </tr>
            </thead>
            <tbody id="j_tb">
                <tr>
                    <td><input type="checkbox"></td>
                    <td>iPhone6</td>
                    <td>8000</td>
                </tr>
                <tr>
                    <td><input type="checkbox"></td>
                    <td>ipad</td>
                    <td>5000</td>
                </tr>
                <tr>
                    <td><input type="checkbox"></td>
                    <td>watch</td>
                    <td>2000</td>
                </tr>
            </tbody>
        </table>
<script>
    // 1.全选和取消全选的方法，让下面所有复选框的checked属性跟随全选按钮即可
    // 获取元素
    var j_cbAll = document.getElementById('j_cbAll'); //全选按钮
    var j_tb = document.getElementById('j_tb').getElementsByTagName('input'); //下面所有的复选框
    // 注册事件
    j_cbAll.onclick = function() {
        //this.checked 可以得到复选框的选中状态，如果是true则是选中如果是false则未选中
        console.log(this.checked);
        for(var i = 0; i < j_tb.length; i++) {
            j_tb[i].checked = this.checked;
        }
    }
    // 2.下面复选框需要全部选中，上面全选才能选中的做法
    for(var i = 0; i < j_tb.length; i++) {
        j_tb[i].onclick = function() {
            //flag控制全选按钮是否选中
            var flag = true;
            //每次点击复选框都要循环检查三个小按钮是否全被选中
            for(var i = 0; i < j_tb.length; i++) {
                if(!j_tb[i].checked) {
                    flag = false;
                    break;
                }
            }
            j_cbAll.checked = flag;
        }
    }

</script>    	
</body>
```

## **「4.6自定义属性操作」**

### 1.获取元素属性

- element.属性;  获取内置属性值（元素本身自带的属性）
- element.getAttribute(‘属性’); 主要获取自定义属性

### 2.设置属性值

- element.属性 = ‘值’ ;  设置内置属性值
- element.getAttribute(‘属性’, ‘值’);   主要设置自定义属性

### 3.移除属性

- element.removeAttribute(‘属性’); 

```html
    <div id="demo" index="1" class="nav"></div>
    <script>
        var div = document.querySelector('div');
        // 1.获取元素属性值
        // (1)element.属性
        console.log(div.id);
        // (2)element.getAttribute('属性')  "get得到 Attribute属性 程序员自己添加的属性称为自定义属性 index"
        console.log(div.getAttribute('id'));
        console.log(div.getAttribute('index'));
        // 2.设置元素属性值
        // (1) element.属性 = '值'
        div.id = 'test';
        div.className = 'navs';
        // (2) element.setAttribute('属性','值')  主要针对自定义属性
        div.setAttribute('index','2');
        div.setAttribute('class','footer'); //class特殊 这里写的事class 而不是className
        // 3.移除属性 removeAttribute('属性')
        div.removeAttribute('index');
    </script>
```

## **「4.7 H5自定义属性」**

自定义属性目的：为了保存并使用数据，有些数据可以保存到页面中而不用保存在数据库中

有些自定义属性容易引起歧义，不容易判断是否是元素的内置属性还是自定义属性，所以H5新增了自定义属性

### 1.设置H5自定义属性

H5规定自定义属性必须以**data-**开头作为属性名并赋值

### 2.获取H5自定义属性

1. 兼容性获取 element.getAttribute(‘data-index’)
2. H5新增 element.dataset.index或者 element.dataset[‘index’]

```html
    <div getTime="20" data-index="2" data-list-name="andy"></div>
    <script>
        // console.log(div.getTime);
        console.log(div.getAttribute('getTime'));
        div.setAttribute('data-time','20');
        console.log(div.getAttribute('data-index'));
        console.log(div.getAttribute('data-list-name'));
        // H5新增的获取自定义属性的方法 
        console.log(div.dataset);
        console.log(div.dataset.index);
        console.log(div.dataset['index']);
        // 如果自定义属性里面有多个-连接的单词，我们获取的时候采用驼峰命名法
        console.log(div.dataset.listName);
        console.log(div.dataset['listName']);
    </script>
```

### 案例：tab栏切换

```

```

# 节点操作

## **「5.1为什么学节点操作」**

获取元素通常使用两种方式

1. 利用DOM提供的方法获取元素
2. 利用节点层级关系获取元素

## **「5.2节点概述」**

网页中所有内容都是节点（标签，属性，文本，注释等），在DOM中，节点使用node表示。

HTML DOM树中所有节点均可通过JavaScript进行访问，所有HTML元素（节点）均可被修改，也可以创建或删除

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202206211618584.png)

一般的，节点至少拥有nodeType（节点类型），nodeName（节点名称），nodeValue（节点值）这三个基本属性

- 元素节点 nodeType 为1
- 属性节点 nodeType 为2
- 文本节点 nodeType 为3

实际开发中，节点操作主要操作元素节点

## **「5.3节点层级」**

利用DOM树可以把节点划分成不同的层级关系，常见的是父子兄层关系

### 1.父级节点

```js
node.parentNode
```

- parentName 属性可返回某节点的父节点件，注意是最近的一个父节点
- 如果指定的节点没有父节点则返回null

```html
    <div class="demo">
        <div class="box">
            <span class="erweima"></span>
        </div>
    </div>
    <script>
        var erweima = document.querySelector('.erweima');
        //得到的是离元素最近的父级节点（亲爸爸） 找不到就返回null
        console.log(erweima.parentNode);
    </script>
```

### 2.子节点

- 标准


```js
1.parentNode.childNodes // 标准
```

返回包含指定节点的子节点的集合，该集合为即时更新的集合。

注意：

返回值里包含所有的节点，包括元素节点，文本节点等

如果只要获取元素节点，需要专门处理，所以一般不提倡使用childNodes

```js
var ul = document.querySelector('ul');
for (var i = 0;i < ul.childNodes.length; i++) {
    if(ul.childNodes[i].nodeType = 1) {
        // ul.childNodes[i] 是元素节点
        console.log(ul.childNodes[i]);
    }
}
```

- 非标准(重点)


```js
2.parentNode.children // 非标准
```

parentNode.chileren 是一个只读属性，返回所有子元素节点，它只返回子元素节点，其余节点不返回（这是我们重点掌握的）

虽然children是一个非标准，但得到各个浏览器支持

```js
3.parentNode.firstChild
4.parentNode.lastChild
```

返回第一个（最后一个）**子节点**，找不到返回null，同样返回的是所有节点

```
5.parentNode.firstElementChild
6.parentNode.lastElementChild
```

返回的是第一个（最后一个）**子元素节点**，找不到返回null

#### 案例：下拉菜单

```

```

### 3.兄弟节点

```js
node.nextSibling
node.previousSibling
```

返回的是当前元素的下一个（上一个）**兄弟节点**，找不到则返回null, 是包含所有节点

```js
node.nextElementSibling
node.previousElementSibling
```

返回的是当前元素的上一个（下一个）**兄弟元素节点**，找不到返回null

## **「5.4创建与添加节点」**

### 创建节点

```js
document.createElement('tagName')
```

document.createElement(‘tagName’)方法创建由tagName指定的HTML元素，因为这些元素原先不存在，是根据我们的需求动态产生的，所以也称之为动态创建元素节点

### 添加节点

```js
node.appendChild(child)
```

node.appendChild(child)方法将一个节点添加到指定父节点的子节点列表末尾。类似CSS的after伪元素

```js
node.inserBefore(child,指定元素)
```

node.inserBefore(child,指定元素)方法将一个节点添加到父节点的指定子节点的前面，类似CSS的before伪元素

```html
    <ul>
        <li>123</li>
    </ul>
    <script>
        //1.创建节点元素
        var li = document.createElement('li');
        //2.添加节点 node.appendChild(child)
        var ul = document.querySelector('ul');
        ul.appendChild(li);
        //3.添加节点 node.inserBefore(child,指定元素)
        var lili = documentquerySelector('li');
        ul.inserBefore(lili,ul.children[0]);
        // 我们想要在页面添加一个新的元素：1，创建元素 2，添加元素
    </script>
```

### 案例：简单版发布留言

```html

```



## **「5.5删除节点」**

```js
node.removeChild(child)
```

node.removeChild()方法从DOM中删除一个子节点，返回删除的节点

```html
<ul>
    <li></li>
    <li></li>
    <li></li>
</ul>
<script>
    

</script>
```

### 案例：删除留言板

```html

```

## **「5.6复制节点（克隆节点）」**

```js
node.cloneNode()
```

node.cloneNode() 方法返回调用该方法的节点的一个副本，也称为克隆节点或者复制节点

注意：

1. 如果括号内参数为空或者false，则是浅拷贝，只克隆复制节点本身，不克隆里面的字节点
2. 如果括号内参数为true，则是深拷贝，会克隆复制节点本身以及里面所有的子节点

### 案例：动态生成表格

```html

```



## **「5.8三种动态创建元素的区别」**

- document.write()
- element.innerHTML()
- document.createElement()

区别：

1. document.write() 是直接将内容写入页面的内容流，但是文档流执行完毕，它会导致页面全部重绘
2. innerHTML() 是将内容写入某个DOM节点，不会导致页面全部重绘
3. innerHTML() 创建多个元素效率更高（不要拼接字符串，采取数组的形式拼接），结构稍微复杂
4. createElement() 创建多个元素效率稍微低一点，但是结构清晰
5. 不同浏览器下，innerHTML比createELement效率高

# DOM重点核心

关于DOM操作，我们主要针对于元素的操作，主要有创建，增，删，改，查，属性操作，事件操作

## **「6.1创建」**

1. document.write
2. innerHTML
3. createELement

## **「6.2增」**

1. appendChild
2. insertBefore

## **「6.3删」**

1. removeChild

## **「6.4改」**

主要修改DOM的元素属性，DOM元素的内容，属性，表单的值等

1. 修改元素属性：src，href，title等
2. 修改普通元素内容：innerHTMl，innerText
3. 修改表单元素：value,type,disabled等
4. 修改元素样式：style,className

## **「6.5查」**

主要获取查询DOM元素

1. DOM提供的API方法：getElementById, getElementByTagName, 古老用法不太推荐
2. H5提供的新方法：querySelector, querySelectorAll  提倡使用
3. 利用节点操作获取元素：父（parentNode）, 子（children）, 兄（previousElementSibling, nextElementsibling） 推荐使用

## **「6.6属性操作」**

主要针对自定义属性

1. setAttribute: 设置DOM的属性值
2. getAttribute: 得到DOM的属性值
3. removeAttribute: 移除属性

## **「6.7事件操作」**

给元素注册事件，采取 

事件源. 事件类型 = 事件处理程序
