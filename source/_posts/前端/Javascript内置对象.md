---
title: JavaScript内置对象
date: 2022-06-13
updated: 2022-06-14
tags:
  - 小白的前端之路
  - JavaScript基础
categories: 前端开发
keywords: 
description: 
top_img: ./img/bg20.jpg
cover: ./img/bg2.jpg

---
# 内置对象概述

JavaScript 中的对象分为3种：**自定义对象** 、**内置对象**、 **浏览器对象**
前面两种对象是JS基础内容，属于ECMAScript;第三个浏览器对象属于JS独有的，JS API讲解内置对象就是指 js语言自带的一些对象，这些对象供开发者使用，并提供了一些常用的或是最基本而非必要的功能(属性和方法),内置对象最大的优点就是帮助我们快速开发。

- JavaScript提供了多个内置对象：Math，Data，Array，String等

## **「查文档」**

学习一个内置对象的使用，只要学会其常用成员的使用即可，我们可以通过查文档学习。
`MDN:`https://developer.mozilla.org/zh-CN/

# **Math对象**

**「Math对象」**不是构造函数，它具有数学常数和函数的属性和方法，跟数学相关。

| 属性. 方法名          | 功能                                   |
| --------------------- | -------------------------------------- |
| Math.PI               | 圆周率                                 |
| Math.floor()          | 向下取整                               |
| Math.ceil()           | 向上取整                               |
| Math.round()          | 四舍五入，就近取整，注意-3.5 结果是 -3 |
| Math.abs()            | 绝对值                                 |
| Math.max()/Math.min() | 求最大值和最小值                       |
| Math.random()         | 获取范围在【0，1） 内的随机数          |

```js
// Math数学对象不是一个构造函数，所以我们不需要new 来调用，而是直接使用里面的属性和方法即可
//Math对象最大值
console.log(Math.PI); // 一个属性 圆周率
console.log(Math.max(1,99,3)); // 99
console.log(Math.max(-1,-10)); // -1
console.log(Math.max(1,99,'pink老师')); //NaN
console.log(Math.max()); // -Infinity
```

## 案例：封装自己的数学对象

```js
// 利用对象封装自己的数学对象 里面有PI最大值和最小值
var myMath = {
    PI: 3.1415926535,
    max: function() {
        max = arguments[0];
        for (var i = 1; i < arguments.length; i++){
            if (arguments[i] > max) {
                max = arguments[i];
            }
        }
        return max;
    },
    min: function() {
        min = arguments[0];
        for (var i = 1; i <= arguments - 1; i++) {
            if (arguments[i] < min) {
                min = arguments[i];
            }
        }
        return min;
    }
}
console.log(myMath.PI);
console.log(myMath.max(1,3,6));
console.log(myMath.min(3,5,1,5));
```



```js
// Math绝对值和三个取整方法
//1.绝对值方法
console.log(Math.abs(1)); // 1
console.log(Math.abs(-1)); // 1
console.log(Math.abs('-1')); // 1 隐式转换，会把字符型转换为数字型
console.log(Math.abs('pink')); // NaN
//2.三个取整方法
//(1)Math.floor() '地板' 向下取整，往最小了取值
console.log(Math.floor(1.2)); //1
console.log(Math.floor(1.8)); //1
//(2)Math.ceil() '天花板' 向上取整，往最大了取值
console.log(Math.ceil(1.2)); // 2
console.log(Math.ceil(1.8)); // 2
//(3)Math.round() 四舍五入 其他数字都是四舍五入，但是.5特殊，它往大了取
console.log(Math.round(1.1)); // 1
console.log(Math.round(1.5)); // 2
console.log(Math.round(1.9)); // 2
console.log(Math.round(-1.1)); // -1
console.log(Math.round(-1.5)); // 这个结果是 -1
```



```js
// 1.Math对象随机数方法， random() 返回一个随机小数 0 <= i <1
// 2.这个方法里面不跟参数
// 3.代码验证
console.log(Math.random());
// 4.两数之间随机数，包含两数
// Math.floor(Math.random() * (max - min + 1)) + min;
function getRandom(min,max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
}
console.log(getRandom(1,10));
// 5.随机点名
var arr = ['甲','乙','丙','丁','戊','己','庚'];
console.log(arr[getRandom(0,arr.length - 1)]);
```

## 案例：猜数字游戏

```js
//猜数字游戏
//1.随机生成一个1-10的整数，我们需要用到Math.random()方法
//2.需要一直菜刀正确为止，所以要一直循环
//3.while循环更简单
//4.核心算法：使用if else if 多分支语句来判断大于雄安与等于
function getRandom(min,max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
}
var random = getRandom(1,10);
while (true) { //死循环
    var num = prompt('你来猜？请输入1-10之间的一个数字');
    if(num > random) {
        alert('你猜大了');
    } else if(num < random) {
        alert('你猜小了')；
    } else {
        alert('猜对了');
        break; // 退出整个循环结束程序
    }
}
```

# **Data对象**

  Date 对象和 Math 对象不一样，Date是一个**构造函数**，所以使用时需要实例化后才能使用其中具体方法和属性。Date 实例用来处理日期和时间

## **使用Date实例化日期对象**

- 获取当前时间必须实例化
- 获取指定时间的日期对象

```js
// Data() 日期对象，是一个构造函数，必须使用new来调用创建我们的日期对象
var arr = new Array(); // 创建一个数组对象
var obj = new Object(); // 创建一个对象实例

// 1.使用Data 如果没有参数，返回系统当前时间
var data = new Data();
console.log(data);

// 2.参数常用的写法，数字型 2022,06,11 或者是字符串型 '2022-06-11 00:00:00'
var data1 = new Data(2022,06,11);
console.log(data1); //返回的是7月，不是6月
var data2 = new Data('2022-06-11 00:00:00');
console.log(data2);
```

## **日期格式化**

获取日期的指定部分，通过日期对象里面的属性和方法手动得到这种格式

- 使用Date实例的方法和属性
- getMonth()方法获取到的月份 + 1 = 当月

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202206111942811.png)

格式化日期

```js
//日期格式化
// 格式化日期 年 月 日
      var date = new Date();
      console.log(date.getFullYear()); //返回当前日期的年 2022
      console.log(date.getMonth() + 1); //月份 返回的月份小1个月，记得月份加1呦
      console.log(date.getDate()); //返回的是 几号
      console.log(date.getDay); //周一返回的是1 周六返回的是6 周日返回的是0
//我们写一个 2022年 6月 11日 星期六（当前日期）
      var year = date.getFullYear();
      var month = date.getMonth() + 1;
      var dates = date.getDate();
      var arr = ['星期日','星期一','星期二','星期三','星期四','星期五','星期六']；
      var day = date.getDay();
      console.log("今天是" + year + "年" + month + "月" + dates + "日" + arr[day]);
```



```js
//格式化日期 时分秒
      var date = new Date();
      console.log(date.getHours()); //时
      console.log(date.getMinutes()); //分
      console.log(date.getSeconds()); // 秒

//封装一个函数返回当前的 时 分 秒 格式 08:08:08
      function getTimer() {
        var time = new Date();
        var h = time.getHours();
        var h = h < 10 ? "0" + h : h;

        var m = time.getMinutes();
        var m = m < 10 ? "0" + m : m;

        var s = time.getSeconds();
        var s = s < 10 ? "0" + s : s;
        return h + ":" + h + ":" + s;
      }
      console.log(getTimer());
```

## 时间戳

**获取Date日期总的毫秒数(时间戳)**
基于1970年1月1日(世界标准世界)起的毫秒数

```js
  // 实例化Date对象
  var now = new Date();
  // 1. 通过 value() getTime()
  console.log(now.valueOf());
  console.log(now.getTime());
  // 2. 简单写可以这么做 (最常用的)
  var now = + new Date();   
  // 3. HTML5中提供的方法，有兼容性问题
  var now = Date.now();
```

### 案例：倒计时效果

```js
//  倒计时案例
//  1. 核心算法：输入的时间减去现在的时间就是剩余的时间，即倒计时，但不能拿时分秒相减。
//  2.用时间戳来做，用户输入时间总的毫秒数减去现在时间的总的毫秒数，
//   得到的就是剩余时间的毫秒数
//  3.把剩余时间总的毫秒数转换为天、时、分、秒  (时间戳转换时分秒)
//    转换公式如下：
//    d = parseInt(总秒数/60/60/24) // 计算天数
//    h = parseInt(总秒数/60/60%24) // 计算小时
//    m = parseInt(总秒数/60%60);   // 计算分钟  
//    s = parseInt(总秒数%60);      // 计算当前秒数 

      // 倒计时案例 封装函数实现
      function countDown(time) {
        var nowTime = +new Date(); // 返回的是当前时间总的毫秒数
        var inputTime = +new Date(time); // 返回的是用户输入时间总的毫秒数
        var times = (inputTime - nowTime) / 1000; // times是剩余时间总的秒数
        var d = parseInt(times / 60 / 60 / 24); // 天
        d = d < 10 ? "0" + d : d;
        var h = parseInt((times / 60 / 60) % 24); //时
        h = h < 10 ? "0" + h : h;
        var m = parseInt((times / 60) % 60); // 分
        m = m < 10 ? "0" + m : m;
        var s = parseInt(times % 60); // 当前的秒
        s = s < 10 ? "0" + s : s;
        return d + "天" + h + "时" + m + "分" + s + "秒";
      }
      console.log(countDown("2022-10-1 18:00:00"));
      var date = new Date();
      console.log(date);

```

# **数组对象**

## **「创建数组的两种方式」**

- **1. 字面量方式**`var arr = [1,"test",true];`
- **2. 实例化数组对象 new Array()**`var arr = new Array();`

**注意：**

1. 上面代码中 arr 创建出的是一个空数组，如果需要使用构造函数Array创建非空数组，可以在创建数组时传入参数
2. 如果只传入一个参数(数字)，则参数规定了数组的长度。
3. 如果传入了多个参数，则参数称为数组的元素。

```js
// 1.利用数组字面量
var arr = [1,2,3];
console.log(arr[0]);

// 2.利用new Array()
var arr1 = new Array(); // 创建了一个空数组
var arr1 = new Array(2); // 这个2表示数组长度为2 里面有两个空的数组元素
var arr1 = new Array(2,3); // 等价于[2,3] 这样写表示 里面有两个数组元素 是2和1 
console.log(arr1);
```

## **「检测是否为数组」**

- **1. instanceof 运算符**

instanceof 可以判断一个对象是否是某个构造函数的实例

```js
  var arr = [1, 23];
  var obj = {};
  console.log(arr instanceof Array); // true
  console.log(obj instanceof Array); // false
```

- **2. Array.isArray()**

Array.isArray()用于判断一个对象是否为数组，isArray() 是 HTML5 中提供的方法

```js
  var arr = [1, 23];
  var obj = {};
  console.log(Array.isArray(arr));   // true
  console.log(Array.isArray(obj));   // false
```

- **3. 注意 typeof用法**

typeof 用于判断变量的类型

```js
 var arr = [1, 23];
  console.log(typeof arr) // object 对象arr是构造函数的实例因此是对象数据类型
```

## **「添加删除数组元素的方法」**

- 数组中有进行增加、删除元素的方法，部分方法如下表

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202206121009271.png)

```js
// 添加删除素组元素的方法
// 1.push() 在数组的末尾添加一个或者多个数组元素，
var arr = [1,2,3];
arr.push(4,'pink');
console.log(arr.push(4,'pink'));
console.log(arr);
// (1)push可以给数组追加新的元素
// (2)push() 参数直接写数组元素就可以
// (3)push完毕后，返回的结果是 新数组的长度
// (4)原数组也会发生变化

// 2.unshiift是可以给数组前面追加新元素
console.log(arr.unshift('red','blue'));
console.log(arr);
// 和push同理

// 3.pop() 可以删除数组里最后一个元素
console.log(arr.pop());
console.log(arr);
// (1)pop是可以删除数组最后一个元素，但一次只能删除一个元素
// (2)pop() 没有参数
// (3)pop完毕之后，返回的结果是删除的那个元素
// (4)原数组也会发生变化

// 4.shift() 可以删除数组的第一个元素
console.log(arr.shift());
console.log(arr);
// 和pop同理
```

### 案例：筛选数组

```js
// 有一个包含工资的数组[1500,1200,2000,2100,1800]，要求把超过2000的删除，剩余的放到新数组里
var arr = [1500,1200,2000,2100,1800];
var newArr = [];
for (var i = 1; i < arr.length; i++) {
    if (arr[i] < 2000) {
        // newArr[newArr.length] = arr[i];
        newArr.push(arr[i]);
    }
}
console.log(newArr);
```

## **「数组排序」**

数组中有对数组本身排序的方法，部分方法如下表

| 方法名    | 说明                       | 是否修改原数组              |
| --------- | -------------------------- | --------------------------- |
| reverse() | 颠倒数组中元素顺序，无参数 | 会改变原来数组，返回新数组  |
| sort()    | 对数组元素进行排序         | 会改变原来数组， 返回新数组 |

```js
// 数组排序
// 1.翻转数组
var arr = ['pink','red','blue'];
arr.reverse();
console.log(arr);

// 2.数组排序(冒泡排序)
var arr1 = [13,4,77,1,77];
arr1.sort(function(a,b){
    // return a - b; // 升序的顺序排列
    return b - a; // 降序的顺序排列
});
console.log(arr1);
```

**注意：**

- **sort方法需要传入参数(函数)来设置升序、降序排序**
- 如果传入“function(a,b){ return a-b;}”，则为升序
- 如果传入“function(a,b){ return b-a;}”，则为降序

## **「数组索引方法」**

- 数组中有获取数组指定元素索引值的方法，部分方法如下表

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202206121049869.png)

```js
// 返回数组元素索引号的方法 indexOf(数组元素)  作用就是返回该数组元素的索引号 从前面开始查找
// 它只返回第一个满足条件的索引号
// 如果在数组里面找不到元素，则返回的结果是-1
//var arr = ['red','green','blue','pink','blue'];
var arr = ['red','green','pink'];
console.log(arr.indexOf('blue')); //-1
// 返回数组元素索引号的方法 lastindexOf(数组元素)  作用就是返回该数组元素的索引号 从后面开始查找
var arr = ['red','green','blue','pink','blue'];
console.log(arr.lastindexOf('blue')); // 4
```

### 案例：数组去重

```js
// 数组去重 ['c','a','z','a','x','a','x','c','b'] 要求去除重复元素
// 1.目标：把旧数组里面不重复的元素取出来放进新数组，重复的元素只保留一个，放到新数组里去重
// 2.核心算法：遍历旧数组，然后拿旧数组元素查询新数组，如果该元素在新数组里没有出现过，我们就添加，否则不添加
// 3.如何知道该元素有没有存在？利用 新数组.indexOf(数组元素) 如果返回-1 ，说明数组里没有该元素
// 封装一个去重函数 unique '独一无二的'
function unique(arr) {
    var newArr = [];
    for (var i = 0; i < arr.length; i++) {
        if (newArr.indexOf(arr[i]) === -1) {
            newArr.push(arr[i]);     
        }
    }
    return newArr;
}
var demo = unique(['c','a','z','a','x','a','x','c','b']);
console.log(demo);
```

## **「数组转换为字符串」**

- 数组中有把数组转化为字符串的方法，部分方法如下表
- 注意：join方法如果不传入参数，则按照 “ , ”拼接元素

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202206121108168.png)

```js
// 1.toString(
)    
var arr = [1, 2, 3, 4];
var str = arr.toString(); // 将数组转换为字符串   
console.log(str); // 1,2,3,4

// 2.join(分隔符)
var arr2 = [1, 2, 3, 4];
var str2 = arr2.join("|");//按照键入字符将数组转换为字符串    
console.log(str2); // 1|2|3|4
```

## **「其他方法」**

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202206121111243.png)

```js

    var arr = [1, 2, 3, 4];
    var arr2 = [5, 6, 7, 8];
    var arr3 = arr.concat(arr2);
    console.log(arr3); // [1,2,3,4,5,6,7,8]

    // slice(begin,end) 是一种左闭右开区间 [1,3)
    // 从索引1出开始截取，到索引3之前
    var arr4 = arr.slice(1, 3);
    console.log(arr4); // [2,3]

    var arr5 = arr2.splice(0, 3);
    console.log(arr5); // [5,6,7]
    console.log(arr2); // [8]   splice()会影响原数组
```



# **字符串对象**

## **「基本包装类型」**

为了方便操作基本数据类型，JavaScript 还提供了三个特殊的引用类型：String、Number和 Boolean。
  `基本包装类型就是把简单数据类型包装成为复杂数据类型`，这样基本数据类型就有了属性和方法。

```js
  // 下面代码有什么问题？
  var str = 'andy';
  console.log(str.length); // 4
```

  按道理基本数据类型是没有属性和方法的，而对象才有属性和方法，但上面代码却可以执行，这是因为 js 会把基本数据类型包装为复杂数据类型，其执行过程如下 ：

```js
  // 1. 生成临时变量，把简单类型包装为复杂数据类型
  var temp = new String('andy');
  // 2. 赋值给我们声明的字符变量
  str = temp;
  // 3. 销毁临时变量
  temp = null;
```

## **「字符串的不可变」**

- 指的是里面的值不可变，虽然看上去可以改变内容，但其实是地址变了，内存中新开辟了一个内存空间。
- 当重新给字符串变量赋值的时候，变量之前保存的字符串不会被修改，依然在内存中重新给字符串赋值，会重新在内存中开辟空间，这个特点就是字符串的不可变。
- 由于字符串的不可变，在**「大量拼接字符串」**的时候会有效率问题

## **「根据字符返回位置」**

字符串通过基本包装类型可以调用部分方法来操作字符串，以下是返回指定字符的位置的方法：

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202206121130186.png)

```js
    var str = "anndy";
    console.log(str.indexOf("d")); // 3
    //指定从索引号为4的地方开始查找字符"d"
    console.log(str.indexOf("d", 4)); // -1
    
    console.log(str.lastIndexOf("n")); // 2
```



### 案例：查找字符串"abcoefoxyozzopp"中所有o出现的位置以及次数

```js
//核心算法：先查找第一个o出现的位置
//然后 只要indexOf 返回的结果不是 -1 就继续往后查找
//因为indexOf 只能查找到第一个，所以后面的查找，利用第二个参数，当前索引加1，从而继续查找
var str = "oabcoefoxyozzopp";
var index = str.indexOf("o");
var num = 0;
while (index !== -1) {
    console.log(index);
    num++;
    index = str.indexOf("o", index + 1);
}
console.log('o出现的次数是' + num);
```

## **「根据位置返回字符」**

字符串通过基本包装类型可以调用部分方法来操作字符串，以下是根据位置返回指定位置上的字符：

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202206121136083.png)



```js
      // 根据位置返回字符
      // 1. charAt(index) 根据位置返回字符
      var str = 'andy';
      console.log(str.charAt(3)); // y
      // 遍历所有的字符
      for (var i = 0; i < str.length; i++) {
          console.log(str.charAt(i));
      } // a n d y
      
      // 2. charCodeAt(index)  
      //返回相应索引号的字符ASCII值 目的： 判断用户按下了那个键 
      console.log(str.charCodeAt(0)); // 97
      // 3. str[index] H5 新增的
      console.log(str[0]); // a
```



### 案例：判断一个字符串 'abcoefoxyozzopp' 中出现次数最多的字符，并统计其次数



```js
//核心算法：利用 charAt(） 遍历这个字符串
//把每个字符都存储给对象， 如果对象没有该属性，就为1，如果存在了就 +1
//遍历对象，得到最大值和该字符 注意：在遍历的过程中，把字符串中的每个字符作为对象的属性存储在对象中，对应的属性值是该字符出现的次数     
	 var str = "abcoefoxyozzopp";
      var o = {};
      for (var i = 0; i < str.length; i++) {
        var chars = str.charAt(i); // chars 是 字符串的每一个字符
        if (o[chars]) {
          // o[chars] 得到的是属性值
          o[chars]++;
        } else {
          o[chars] = 1;
        }
      }
      console.log(o);
      // 2. 遍历对象
      var max = 0;
      var ch = "";
      for (var k in o) {
        // k 得到是 属性名
        // o[k] 得到的是属性值
        if (o[k] > max) {
          max = o[k];
          ch = k;
        }
      }
      console.log(max);
      console.log("最多的字符是" + ch);
```

## **「字符串操作方法」**

字符串通过基本包装类型可以调用部分方法来操作字符串，以下是部分操作方法：

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202206122119052.png)

```js
      // 字符串操作方法
      // 1. concat('字符串1','字符串2'....)
      var str = 'andy';
      console.log(str.concat('red')); // andyred

      // 2. substr('截取的起始位置', '截取几个字符');
      var str1 = '改革春风吹满地';
      // 第一个2 是索引号的2 从第几个开始  第二个2 是取几个字符
      console.log(str1.substr(2, 2)); // 春风
```

```js
    // 1. 替换字符 replace('被替换的字符', '替换为的字符')  它只会替换第一个字符
    var str = "andyandy";
    console.log(str.replace("a", "b")); // bndyandy
    // 有一个字符串 'abcoefoxyozzopp'  要求把里面所有的 o 替换为 *
    var str1 = "abcoefoxyozzopp";
    while (str1.indexOf("o") !== -1) {
      str1 = str1.replace("o", "*");
    }
    console.log(str1); // abc*ef*xy*zz*pp

    // 2. 字符转换为数组 split('分隔符')    
    // 前面我们学过 join 把数组转换为字符串
    var str2 = "red, pink, blue";
    console.log(str2.split(",")); //[red,pink,blue]
    var str3 = "red&pink&blue";
    console.log(str3.split("&")); // [red,pink,blue]
```

