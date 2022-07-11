---
title: Javascript基础
date: 2022-05-15
updated: 2022-06-01
tags:
  - 小白的前端之路
  - JavaScript基础
categories: 前端开发
keywords: 
description: 
top_img: ./img/bg22.jpg
cover: ./img/bg4.jpg

---
# Javascript基础



## 编程基础

**「计算机语言」**分为机器语言，汇编语言，高级语言。计算机内部最终执行的都是机器语言，由`0`和`1`这样的二进制数构成。

**「数据存储单位」**8bit(比特) = 1B(Byte)字节  千字节1KB = 1024B

**「翻译器」**高级语言编写的程序不能被计算机识别，需要经过转换，将源代码程序翻译成`机器语言`才能运行。浏览器里面的js解释器就是这样的一个翻译器。

**「程序运行」**

- 打开某个程序时，先从硬盘中把程序的代码加载到内存中
- CPU执行内存中的代码
- 注意：之所以要内存的一个重要原因，是因为 cpu运行太快了，如果只从硬盘中读数据，会浪费cpu性能，所以，才使用存取速度更快的内存来保存运行时的数据。（内存是电，硬盘是机械）

## 初识JavaScript

**「创始人」**布兰登·艾奇(Brendan Eich),起初命名为`LiveScript`后来与Sun公司合作改名为`JavaScript`。

**「JavaScript」**运行在客户端的脚本语言，不需要编译，由js解释器(js引擎)逐行解释执行。Node.js也可以用于服务器端编程。

**「JavaScript组成」**ECMAScript(JavaScript语法)、DOM(文档对象模型)、BOM(浏览器对象模型)

**「JavaScript的作用」**

- 表单动态校验(密码强度检测)
- 网页特效
- 服务端开发(Node.js)
- 桌面程序(Electron)、App(Cordova)、控制硬件-物联网(Ruff)、游戏开发(cocos2d-js)

**「JavaScript书写位置」**

> JS有3种书写位置，分别为行内、内嵌和外部。

1. 行内

   ```html
   <input type="botton" value="点我试试" 
   	onclick="alert('Helo World!')"/>
   ```

2. 内嵌

   ```html
   <script>
   	alret('Hello World!');
   </script>
   ```

3. 外部

   ```html
   引用外部js文件
   <script src="my.js"> </script> 
   ```

   

**「注释」**

1. 单行注释

   ```javascript
   // 我是单行注释 （ctrl + /）
   ```

2. 多行注释

   ```js
   /*
     获取用户年龄和姓名
     并通过提示框显示出来
     点击vscode左下角管理-键盘快捷方式-切换块注释
     (默认快捷键 alt + shift + a) 修改为 (ctrl + shift + /)
   */
   ```
## 输入和输出语句

   | 函数                      | 说明                     | 归属   |
   | ------------------------- | ------------------------ | ------ |
   | prompt(‘输入’);           | 浏览器弹出输入框         | 浏览器 |
   | alert(‘输出’);            | 浏览器弹出警示框         | 浏览器 |
   | console.log(‘控制台输出’) | 浏览器控制台打印输出信息 | 浏览器 |

   

```html
<script>
	//输入框
    prompt('请输入');
    //弹出警示框，输出的展示给用户
    alert('计算的结果是');
    //控制台输出，给程序员测试用
    console.log('控制台显示');
</script>
    
```

# 变量

## **变量概述**

变量是程序在内存中申请的一块用于存放数据的空间。变量是用于存放数据的容器，可以通过变量名获取数据，甚至修改数据。

白话讲，变量就是一个装东西的盒子。

## 变量的使用

变量在使用时分为两步，声明和赋值

### **「1. 声明变量」**

```js
//声明变量
var age; //声明一个名称为age的变量
```

var是一个JS关键字，用来声明变量(variable变量的意思)。num是我们定义的变量名，可以通过变量名来访问内存中分配的空间。

### **「2. 赋值」**

```js
age = 10;//给age变量赋值为10
```

### **「3. 变量的初始化」**

```js
var age = 10;//声明变量并赋值为10
```

### 小案例

```js
//声明
var age;
//赋值
age=10;
//输出结果
console.log(age);
```

```js
//用户输入姓名，存到一个myname的变量中
var myname=prompt('请输入你的名字')；
//输出这个用户名
alert(myname);
```

### **「4. 变量语法扩展」**

```js
// 1.一个变量被重新赋值后，它原有的值会被覆盖掉，变量值以最后一次赋的值为准。
var age=10;
age=18;
// 2.同时声明多个变量(只需要写一个var,多个变量名之间用英文逗号隔开)
var num=10,age=18,name='name';
```

声明变量特殊情况

| 情况                       | 说明                     | 结果      |
| -------------------------- | ------------------------ | --------- |
| var age; console.log(age); | 只声明，不赋值           | undefined |
| console.log(age);          | 不声明，不赋值，直接使用 | 报错      |
| age=10;console.log(age);   | 不声明，只赋值           | 10        |

### **「5. 变量命名规范」**

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202205302255403.png)

### 小案例

```js
//小案例，交换两个变量的值
var temp;//引入临时变量
var apple1='青苹果',apple2='红苹果'；
temp=apple1;
apple1=apple2;
apple2=temp;
console.log(apple1);
console.log(apple2);
```

# 数据类型

分为两类：简单数据类型(Number,String,Boolean,Undefined,Null)和复杂数据类型(object)。

| 简单数据类型 | 说明                      | 默认值    |
| ------------ | ------------------------- | --------- |
| Number       | 数字型，包含整数和浮点数  | 0         |
| String       | 字符串类型                | “ ”       |
| Boolean      | 布尔值类型                | false     |
| Undefined    | 声明但不赋值，a=undefined | undefined |
| Null         | var a=null; 声明a为空值   | null      |

## Number数字型

### **「数字型进制」**

```js
// 1.在JS中八进制前面加0，十六进制前面加 0x
var num1 = 07;   // 对应十进制的7
// 2.十六进制数字序列范围：0~9以及A~F
 var num = 0xA; //对应十进制10
```

### **「数字型范围」**

JavaScript中的数值有最大值和最小值

- 最大值:`Number.MAX_VALUE`，值为：1.7976931348623157e+308
- 最小值:`Number.MIN_VALUE`，值为：5e-32
- 特殊值：`Infinity` 无穷大 `-Infinity` 无穷小 `NaN` 代表一个非数字（not a number）
- isNaN(): 用来判断一个变量是否为非数字的类型。非数字型为true,数字型为false。

```js
console.log(Number.MAX_VALUE);//数字的最大值
console.log(Number.MIN_VALUE);//数字的最小值
//无穷大
console.log(Number.MAX_VALUE*2);//Infinity 无穷大
//无穷小
console.log(Number.MIN_VALUE*2);//-Infinity 无穷小
//非数字
console.log('pink老师'-100)；//NaN
```



```js
var usrage = 21;
var isOK = isNaN(usrage);
console.log(isOK); //false 21不是一个非数字
var usrname = "andy";
console.log(isNaN(usrname));//true "andy"是一个非数字
```

## String字符串型

```js
// 1.字符串型可以是引号中的任意文本，语法为 单引号 和 双引号
var msg = '我的名字叫';
var name = "fan";
```

由于HTML标签属性是双引号，这里推荐使用单引号，常见错误未使用引号，会被认定是js代码，但js没有这些语法。

### **「字符串引号嵌套」**

js可以使用单引号套双引号，或者使用双引号套单引号（外双内单，外单内双）

```js
var str1="我是'程序员'";
var str2='我是"程序员"';
//常见错误
var str3='我是程序员";//报错，不能单双引号搭配
```



### **「1. 字符串转义符」**

都是以 \ 开头，详细如下

| 转义符 | 说明                     |
| ------ | ------------------------ |
| \n     | 换行符，n是newline的意思 |
| \ \    | 斜杠\                    |
| \ '    | 单引号‘                  |
| \ "    | 双引号 “                 |
| \t     | tab缩进                  |
| \b     | 空格，b是blank 的意思    |

```js
//字符串转义字符，都是\开头，写在引号里面
var str="我是\n程序员";
console.log(str);
```

### **「2. 字符串长度」**

  字符串是由若干字符组成的，这些字符的数量就是字符串的长度，通过length属性可以获取整个字符串长度。

```js
var str='我是程序员';
alert(str.length);//显示5
```

### **「3. 字符串拼接」**

-   多个字符串之间可以使用 + 进行拼接，其拼接方式为 字符串 + 任何类型 = 拼接之后的新字符串。
-   拼接前会把与字符串相加的任何类型转成字符串，再拼接成一个新的字符串

```js
//1.1 字符串 "相加"
alert('hello' + ' ' + 'world'); // hello world
//1.2 数值字符串 "相加"
alert('100' + '100'); // 100100
//1.3 数值字符串 + 数值
alert('11' + 12);     // 1112 +号口诀：数值相加，字符相连
//1.4 数值相加
alert(12+12); //24
// 1.5 字符串拼接加强
var age = 18;
alert("你" + age +"岁了"); //变量和字符串引引加加
```

**+号口诀：数值相加，字符相连**

### 案例：字符串拼接加强

```js
//弹出一个输入框，输入年宁
//把输入年龄与字符串相接
//输出结果
var age=prompt('请输入年龄');
var str='您今年已经'+ age + '岁了';
alert(str);
```

## Boolean布尔型

  布尔类型有两个值：true 和 false ，其中 true 表示真（对），而 false 表示假（错）。
  布尔型和数字型相加的时候， true 的值为 1 ，false 的值为 0。

```js
console.log(true + 1); // 2
console.log(false + 1); // 1
```

## Undefined 和 Null

  一个变量声明后没有赋值会有一个默认值undefined（如果相连或者相加时，注意结果）

```js
  var variable;
  console.log(variable); // undefined
  console.log("你好" + variable); // 你好undefined
  console.log(11 + variable); // NaN
  console.log(true + variable);// NaN
```

  一个变量声明并赋值null,里面存的值为空

```js
  var var2 = null;
  console.log(var2); // null
  console.log("你好" + var2); // 你好null
  console.log(11 + var2); // 11
  console.log(true + var2);// 1
```

## 获取变量类型及转换

### **「获取变量类型」**

-  检测变量的数据类型语法`typeof`

```js
var num = 10;
console.log(typeof num);//结果为 number
var str = 'pink';
console.log(typeof str);//结果为 string
var flag = 'true';
console.log(typeof flog);//结果为 boolean
var vari = undefined;
console.log(typeof vari);//结果为 undefined
var timer = null;
console.log(typeof timer); //结果为 object
//prompt 取过来的值是字符型的
var age = prompt('请输入年龄');
console.log(age);
conloge.log(typeof age);
```

**prompt 取过来的值是字符型的**

`字面量`:是源代码中一个固定值的表示法，就是字面量如何去表达这个值。通过数据的格式特征可以判断数据的类型

- 有数字字面量:8,9,10
- 字符串字面量:'饭老板'，"前端开发"
- 布尔字面量:true,false

### **「数据类型转换」**

#### 转换为字符串

| 方式           | 说明                         | 案例 |
| -------------- | ---------------------------- | ---- |
| toString()     | 转换成字符型                 |      |
| String()       | 强制转换                     |      |
| 加号拼接字符串 | 和字符型拼接的结果都是字符型 |      |

toString()和String()使用方式不一样

**三种转换方式更喜欢用第三种，被称为隐式转换**

```js
//1,数字型转换字符串 变量.toString()
var num = 10;
var str = num.toString();
console,log(str);
console,log(typeof str);
//2，String()
var num = 10;
var str = String(num);
console,log(typeof str);
//3，加号拼接字符串
var num = 10;
console.log(num + '');
```

#### 转换为数字型

| 方式                   | 说明               | 案例 |
| ---------------------- | ------------------ | ---- |
| parseInt(String)函数   | 转化为整数型       |      |
| parseFloat(String)函数 | 转化为浮点型       |      |
| Number()强制转换函数   | 强制转换数值型     |      |
| js隐式转换（- * /)     | 算数因算符转换数值 |      |

```js
//1，parseInt(变量) 得到的是整数
console.log(parseInt('3.14'));//3 取整
console.log(parseInt('3.93'));//3 取整
console.log(parseInt('120px'));//120 会去掉px单位
console.log(parseInt('rem120px'));//NaN
//2，parseFloat(变量) 得到的是浮点数
console.log(parseFloat('3.14'));//3.14
console.log(parseFloat('120px'));//120 去掉单位
console.log(parseFloat('rem120px'));//NaN
//3，Number(变量)
var str = '123';
console.log(Number(str));//123
console.log(Number('12'));//12
//4，利用算数运算符
console.log('12'-0);//12
console.log('123'-'120');//3
console.log('123'*1);//123
```

#### 案例：简单加法器

```js
var num1 = prompt('请输入第一个数');
var num2 = prompt('请输入第二个数');
var result = parseFloat(num1) + parseFloat(num2);
console.log('您的结果是' + result);
```

#### 案例：计算年龄

```js
var year = prompt('请输入生日年份')；
var age = 2022 - year; //隐式转换
alert('你的年龄'+ age + '岁了');
```



#### 转换为布尔型

1. 代表空、否定的值会被转换为false，如' '、0、NaN、null、undefined 
2. 其余值都会被转换为true。

| 方式          | 说明               | 案例            |
| ------------- | ------------------ | --------------- |
| Boolean()函数 | 其他类型转换布尔型 | Boolean(‘true’) |

```js
console.log(Boolean(''));//false
console.log(Boolean(0));//false
console.log(Boolean(NaN));//false
console.log(Boolean(null));//false
console.log(Boolean(undefined));//false
console.log(Boolean('小白'));//true
console.log(Boolean('12'));//true
```

# 关键字和保留字

**「标识符」**指开发人员为变量、属性、函数、参数取得名字。标识符不能是关键字或保留字。

**「关键字」**指 JS本身已经使用了的字，不能再用它们充当变量名、方法名

> 包括：break、case、catch、continue、default、delete、do、else、finally、for、function、if、in、instanceof、new、return、switch、this、throw、try、typeof、var、void、while、with 等。

**「保留字」**实际上就是预留的“关键字”，意思是现在虽然还不是关键字，但是未来可能会成为关键字，同样不能使用它们当变量名或方法名。

> boolean、byte、char、class、const、debugger、double、enum、export、extends、fimal、float、goto、implements、import、int、interface、long、mative、package、private、protected、public、short、static、super、synchronized、throws、transient、volatile 等。
>
> 注意：如果将保留字用作变量名或函数名，那么除非将来的浏览器实现了该保留字，否则很可能收不到任何错误消息。当浏览器将其实现后，该单词将被看做关键字，如此将出现关键字错误。

# 运算符

## **「运算符」**

是用于实现赋值、比较和执行算数运算等功能的符号。常用运算符分类如下

- 算数运算符
- 递增和递减运算符
- 比较运算符
- 逻辑运算符
- 赋值运算符

| 运算符 | 描述         | 案例                |
| ------ | ------------ | ------------------- |
| +      | 加           | 10+20=30            |
| -      | 减           | 10-20=-10           |
| *      | 乘           | 10*20=200           |
| /      | 除           | 10/20=0.5           |
| %      | 取余（取模） | 返回除法的余数9%2=1 |

### 浮点数的精度问题

```js
  var result = 0.1 + 0.2;    // 结果不是 0.3，而是：0.30000000000000004
  console.log(0.07 * 100);   // 结果不是 7，  而是：7.000000000000001
//浮点数不能用来比较是否相等
var num = 0.1 + 0.2;
console.log(num == 0.3);//false
```

浮点数值的最高精度是17位小数，但是在进行算数运算时其精确度远远不如整数,所以不要直接判断两个浮点数是否相等!

### **表达式与返回值**

1. 表达式：由数字、运算符和变量组成的式子。
2. 返回值：每一个表达式经过相应的运算之后，会有一个最终结果，称为表达式的返回值

```js
console.log(1+1);//2
console.log(1-1);//0
console.log(1*1);//1
console.log(1/1);//1
//取余
console.log(4%2);//0
console.lpg(5%3);//2
console.log(3%5);//3
//
console.log(1+1);//2为返回值
var num = 1 + 1;//右边表达式计算完毕把返回值给左边

```

## **「递增和递减运算符」**

  反复给变量增加或减去1，可以使用递增（++）或递减（- -）运算符，分为前置和后置，必须配合变量使用。

- 递增运算符

```js
//前置递增 
var  num = 10;
alert(++num + 10);   // 21 使用口诀：先自加，后返回值
 //后置递增 
var  num1 = 10;
alert(10 + num1++);  // 20 使用口诀：先返回原值，后自加 
```

```js
  var num = 1;
  var num2 = ++num + num++; //num = 2
  console.log(num2);//4
  
  var num = 1;
  var num1 = 1;
  var num2 = num++ + num1++; // 1 + 1
  console.log(num2);//2
  
  var num = 1;
  var num2 = num++ + num++;// 1 + 2 
  console.log(num2); // 3  
```

## **「比较运算符」**

返回的是布尔值（true || false）

| 运算符 | 描述             | 案例         | 结果  |
| ------ | ---------------- | ------------ | ----- |
| <      | 小于号           | 1<2          | true  |
| >      | 大于号           | 1>2          | false |
| >=     | 大于等于号       | 2 >= 2       | true  |
| <=     | 小于等于号       | 3 <= 2       | false |
| ==     | 等判号（会转型） | 15 == ‘15’   | true  |
| !=     | 不等号           | 37 != 37     | false |
| ===    | 全等             | 37 === ‘37’  | false |
| !===   | 全不等           | 37 !=== ‘37’ | true  |

注意：

- ==判断两边值是否相等（有隐式转换）
- ===判断两边值和数据类型是否完全相同

```js
//==默认转换数字类型，会把字符串型转换成数字型，要求值相等即可
console.log(3 == 5);//false
console.log('pink' == '我');//false
console.log(18 == 18);//true
console.log(18 == '18');//true
console.log(18 != 18);//false
//===要求值和数据类型完全一样
console.log(18 === 18);//true
console.log(18 === '18');//false
```

## **「逻辑运算符」**

  逻辑运算符是用来进行布尔值运算的运算符
  短路运算:当有多个表达式（值）时,左边的表达式值可以确定结果时,就不再继续运算右边的表达式的值;

| 运算符 | 描述                   | 案例           | 特点                 |
| ------ | ---------------------- | -------------- | -------------------- |
| &&     | “逻辑与”，简称“与” and | true && false  | 两边都true才返回true |
| \|\|   | “逻辑或”，简称“或” or  | true \|\| true | 有真为真             |
| !      | “逻辑非”，简称“非” not | ! true         | 取反                 |

```js
//1,&&
console.log(3 > 5 && 3 > 2);//false
console.log(3 < 5 && 3 > 2);//true
//2,||
console.log(3 > 5 || 3 > 2);//true
console.log(3 < 5 || 3 < 2);//false
//3,!
console.log(!true);//false
```

```js
//逻辑与短路运算 如表达式1结果为真，则返回表达式2，如果表达式1结果为假，则返回表达式1
console.log(123 && 456);//	456
console.log(0 && 456);//	0
console.log(0 && 1+2 && 456*789);//	0
console.log('' && 1+2 && 456*789);//	''
//有空的或者否定的是假，其余为真 0 '' null undefined NaN
//逻辑或短路运算 如表达式1结果为真，则返回表达式1，如果表达式1结果为假，则返回表达式2
console.log(123 || 456);//	123
console.log(123 || 456 || 456+789);//	123
console.log(0 || 456 || 456+789);//	456
//逻辑中断很重要，会影响程序运行结果
var num = 0;
console.log(123 || num++);//num++ 运行中断
console.log(num);//0
```

## **「赋值运算符」**

| 运算符   | 描述                 | 案例                   |
| -------- | -------------------- | ---------------------- |
| =        | 直接赋值             | var name = ‘fan’       |
| +=  -=   | 加一个数后在赋值     | var age = 5; age += 5; |
| *= /= %= | 乘，除，取模后在赋值 | var age = 5; age *= 5; |

```js
var age = 10;
age += 5;//相当于age = age + 5;
age -= 5;//age = age - 5;
age *= 10;//age = age * 10;
```

## **「运算符优先级」**

| 优先级 | 运算符     | 顺序         |
| ------ | ---------- | ------------ |
| 1      | 小括号     | ()           |
| 2      | 一元运算符 | ! ++ - -     |
| 3      | 算数运算符 | 先* / % 后+- |
| 4      | 关系运算符 | > >= < <=    |
| 5      | 相等运算符 | == != === != |
| 6      | 逻辑运算符 | 先&&后\|\|   |
| 7      | 赋值运算符 | =            |
| 8      | 逗号运算符 | ,            |

- 一元运算符里面逻辑非优先级最高
- 与比或高











