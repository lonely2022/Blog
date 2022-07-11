---
title: JavaScript函数
date: 2022-06-09
updated: 2022-06-10
tags:
  - 小白的前端之路
  - JavaScript基础
categories: 前端开发
keywords: 
description: 
top_img: ./img/bg25.jpg
cover: ./img/bg3.jpg

---
# 函数

## **「1.函数的概念」**

封装了一段可被重复调用执行的代码块，通过函数可以实现大量代码的重复使用。函数是一种数据类型。

## **「2.函数的使用」**

函数的使用分为两步：**声明函数**和**调用函数**

- 声明函数

```js
// 1. 通过function关键字定义函数 -- 命名函数
  function 函数名() {
    函数体代码
  }
  // 1.1 function 是声明函数的关键字，必须小写
  // 1.2 函数名 命名为动词形式 例: getSum
  
// 2. 通过函数表达式定义函数 ---匿名函数
  var fn = function() {};
  // 2.1 fn是变量名，不是函数名
  // 2.2 fn是变量，只不过变量存储的是函数
  // 2.3 函数表达式创建的函数可以通过 变量名() 来调用
  // 2.4 函数表达式也可以定义形参和调用传入实参。

```

```js
  // 匿名函数使用的有第二种方式- -匿名函数自调用
  ( function() {
      alert(123);
  })
  ();
```

- 调用函数

```js
// 2.调用函数
  函数名(); 
  // 通过调用函数名来执行函数体代码
  // 调用时不要忘记添加小括号
  // 函数不调用，自己不执行
```



### 案例：函数封装求1-100和

```js
//函数计算1-100的和
function getSum() {
    var sum = 0;
    for (var i = 1; i <= 100; i++) {
        sum += i;
    }
    console.log(sum);
} //声明
getSum(); //调用
```

## **「3.函数的参数」**

- 形式参数：函数定义时，传递的参数（实参值传递给形参，不用声明的变量）

- 实际参数：函数调用时，传递的参数

```js
// 带参数的函数声明
function 函数名(形参1,形参2,形参3...) {
    函数体;
}
// 带参数的函数调用
函数名(实参1,实参2,实参3...);
```

**函数形参和实参数量不匹配时**

| 参数个数    | 说明                                 |
| ----------- | ------------------------------------ |
| 实参 = 形参 | 输出正确结果                         |
| 实参 > 形参 | 只取到形参的个数                     |
| 实参 < 形参 | 多的形参定义为 undefined，结果为 NaN |

```js

      function getSum(a, b, c) {
        return a + b + c;
      }
      // js中形参的默认值是undefined。
      // 调用函数
      var n = getSum(1, 2);// n = NaN
      var n = getSum(1, 2, 3, 4); //1 + 2 +3 = 6

```

## **「4.函数的返回值」**

```js
// 1.函数是做某件事或者实现某种功能
function cook(aru) {
    console.log(aru);
}
cook('大肘子');

// 2.函数的返回值格式
function 函数名() {
    return 需要返回的结果;
}
函数名();
// (1)我们函数只是实现某种功能，最终的结果需要返回给函数的调用者 函数名() 通过return实现
// (2)只要函数遇到return 就把后面的结果返回给函数的调用者 函数名() = return返回的结果

// 3.代码演示
function getResult() {
    return 666;
}
getResult(); // getResult() = 666
console.log(getResult());

function cook(aru) {
    return aru;
}
console.log(cook('大肘子'))；
```

### 案例：求两个数最大值

```js
// 利用函数，求两个数最大值
function getMax(num1,num2) {
    if(num1 > num2) {
        return num1;
    } else {
        return num2;
    }
    // return num1 > num2 ? num1 : num2;
}
console.log(getMax(1,3));
```

### 案例：求数组中最大值

```js
// 利用函数求数组['5','2','99','101','67','77'] 中的最大值
function getArrMax(arr) {
    var max = arr[0];
    for (var i = 1; i <= arr.length; i++) {
        if(arr[i] > max) {
            max = arr[i];
        }
    }
    return max;
}
getArrMax(['5','2','99','101','67','77']); //实参是一个数组送过去
// 在实际开发中，我们经常用一个变量来接收函数的返回结果
var re = getArrMax(['5','2','99','101','67','77']);
console.log(re);
```

### **函数返回值注意事项**

```js
// 1.return终止函数
function getSum(num1,num2) {
    return num1 + num2; // return后面的代码不会被执行
    alert('我是不会被执行的');
}
console.log(getSum(1,2));

// 2.return只能返回一个值
function fn(num1,num2) {
    return num1,num2; // 返回的结果是最后一个
}
console.log(fn(1,2));

// 3.求任意两数加减乘除的结果
function gerResult(num1,num2) {
    return [num1+num2, num1-num2,num1*num2, num1/num2];
}
var re = getResult(1,2); // 返回的是一个数组
console.log(re);

// 4.函数没有return，返回undefined
function fun() {
    
}
console.log(fun()); // 函数返回的结果是undefined
```

### break,continue,return的区别

- break: 结束当前的循环体 (如for、while)
- continue: 跳出本次循环，继续执行下次循环
- return: 不仅可以退出(函数体内)循环，还能够返回return语句中的值，同时还可以结束当前的函数体内的代码

```js
//避免踩坑 return只能结束函数体内的代码
  function breakDown() {
    for (var i = 0; i < 10; i++) {
      if (i == 5) {
        return 1;
      }
    console.log(i);
    }
  }
  breakDown();
  
//避免踩坑2 函数如果有return 则返回的是 return 后面的值；
// return d,a,b; 返回的是b的值
//如果函数没有 return语句，则返回undefined

```

## **「5.arguments的使用」**

  当不确定有多少个参数传递的时候，可以用 arguments 来获取。JS中，arguments实际上它是当前函数的一个内置对象。所有函数都内   置了一个 arguments 对象，arguments 对象中存储了传递的所有实参。arguments展示形式是一个伪数组，因此可以进行遍历。

伪数组具有以下特点：

1. 具有length属性
2. 按索引方式存储数据
3. 不具有数组的push，pop等方法

```js
// arguments的使用 只有函数才有arguments对象，而且每个函数都内置arguments
  function fn() {
    //arguments 里面存储了所有传递过来的实参
    console.log(arguments);// [1,2,3...]
    console.log(arguments[1]); // 2
    console.log(arguments.length); // 3
    
    //我们可以按照数组的方式 遍历argument  
    for(var i = 0; i <= arguments; i++) {
        console.log(arguments[i]);
    }
  }
  fn(1, 2, 3);

// 伪数组并不是真正意义上的数组
```

### 案例：利用函数求最大值

```js
 // 用伪数组 实现求最大值
 function getMax() {
    var max = arguments[0];
    for (var i = 1; i < arguments.length; i++) {
      if (arguments[i] > arguments[0]) {
        max = arguments[i];
      }
    }
    return max;
  }
  var result = getMax(1,3,77,5,85)
  colsole.log(result);
```

### 案例：利用函数翻转数组

```js
//利用函数翻转任意数组  reverse 翻转
function reverse(arr) {
    var newArr = [];
    for (var i = arr.length - 1; i <= 0; i--) {
        newArr[newArr.length] = arr[i];
    }
    return newArr;
}
var arr1 = reverse([1,3,4,6,9]);
console.log(arr1);
var arr2 = reverse(['red','pink','blue']);
console.log(arr2);
```

### 案例：利用函数冒泡排序

```js
// 利用函数冒泡排序
function sort(arr) {
    for (var i = 0; i <= arr.length - 1; i++) {
        for(var j = 0;j <= arr.length - i- 1; j++) {
            if (arr[j] > arr[j+1]) {
                var temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
    }
    return arr;
}
var arr1 = sort([1,3,5,7]);
console.log(arr1);
var arr2 = sort([2,3,5,1,88]);
console.log(arr2);
```

### 案例：利用函数判断闰年

```js
// 利用函数判断闰年
function isRunYear(year) {
    //如果是闰年返回true，否则返回false
    var flag = false;
    if (year % 4 == 0 && year % 100 != 0 || year % 400 == 0) {
        flag = true;
    } 
    return flag;
}
console.log(isRunYear(2000));
console.log(isRunYear(1999));
```

**函数是可以相互调用的**

### 案例：输出年份的二月份天数

```js
//用户输入年份，输出该年份二月份的天数
function backDay() {
    var year = prompt('请您输入年份');
    if (isRunYear(year)) {  // 调用函数需要加小括号
        alert('当前年份是闰年2月份有29天');
    } else {
        alert('当前年份是平年2月份有28天');
    }
}
function isRunYear(year) {
    //如果是闰年返回true，否则返回false
    var flag = false;
    if (year % 4 == 0 && year % 100 != 0 || year % 400 == 0) {
        flag = true;
    } 
    return flag;
}
backDay();
```



# 作用域

## 作用域

**「作用域」**一段程序代码中所用到的名字并不总是有效和可靠的，而限定这个名字的可用性代码范围就是这个名字的作用域。

- 作用域的使用提高了程序逻辑的局部性，增强了程序的可靠性，减少了名字冲突。
- ES6之前作用域有两种 `全局作用域`和`局部作用域`(函数作用域)

**「全局作用域」**作用于所有代码执行的环境(整个 script 标签内部)或者一个独立的 js 文件。

**「局部作用域」**作用于函数内部的代码环境，就是局部作用域。因为跟函数有关系，所以也被称为`函数作用域`。

**「JS没有块级作用域」**

- 块作用域由 {} 包括
- 在其他编程语言，if语句中，循环语句创建的变量，仅仅只能在本if语句，本循环语句中使用，如下

```java

  if(true){
    int num = 123;
    System.out.print(num); //123
  }
  System.out.print(num);//报错
```

以上java代码会报错，因为代码中 {}是一块作用域，其中声明的变量num，在{}之外不能使用，而JavaScript代码则不会报错

Js中没有块级作用域 (在ES6之前)

```js
 if(true){
    var num = 123;
    console.log(num); // 123
  }
  console.log(num);// 123
```

## 变量的作用域

在JavaScript中，根据作用域的不同，变量可以分为两种:

- `全局变量`
- `局部变量`

**「全局变量」**在全局作用域下声明的变量(在函数外部定义的变量)

- 全局变量在代码的任何位置都可以使用
- 在全局作用域下 var 声明的变量 是全局变量
- 特殊情况下，在函数内不使用var声明的变量也是全局变量(不建议使用)。

**「局部变量」**在局部作用域下声明的变量(在函数内部定义的变量)

- 局部变量只能在函数内部使用
- 在函数内部 var声明的变量是局部变量
- 函数的形参实际上就是局部变量

**「全局变量和局部变量的区别」**

- `全局变量:`在任何一个地方都可以使用，只有在浏览器关闭时才会销毁，因此比较占内存
- `局部变量:`旨在函数内部使用，当其所在的代码块被执行时，才会被初始化；当代码块运行结束后，就会被销毁，因此更节省内存空间。

## 作用域链

**「作用域链」**只要是代码都在一个作用域中，写在函数内部的局部作用域，未卸载仍和行数内部即在全局作用域中；如果函数中还有函数，那么在这个作用域中就又可以诞生一个作用域；根据`[内部函数可以访问外部函数变量]` 的这种机制，用链式查找决定哪些数据能被内部函数访问，就称作作用域链。

```js

  function f1() {
      var num = 123;
      function f2() {
          console.log( num );
      }
      f2();
  }
  var num = 456;
  f1();//123
```

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202206102305503.png)

`作用域链`采取就近原则的方式来查找变量最终的值

```js
  var a = 1;
  function fn1() {
      var a = 2;
      var b = '22';
      fn2();
      function fn2() {
          var a = 3;
          fn3();
          function fn3() {
              var a = 4;
              console.log(a); //a的值 4
              console.log(b); //b的值 '22'
          }
      }
  }
  fn1();
```

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202206102306310.png)

# 预解析

**「预解析相关概念」**JavaScript代码是由浏览器中的JavaScript解析器来执行的。JavaScript解析器在运行JavaScript代码的时候分为两步:预解析和代码执行。

- **「预解析」**在当前作用域下，JS代码执行之前，浏览器会默认把带有 var 和 function声明的变量在内存中进行提前声明或定义。
- **「代码执行」**从上往下执行JS语句

预解析会把变量和函数的声明在代码执行之前完成，**预解析也叫做变量、函数提升**。



























