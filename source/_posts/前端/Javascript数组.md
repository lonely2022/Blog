---
title: Javascript数组
date: 2022-06-06
updated: 2022-06-07
tags:
  - 小白的前端之路
  - JavaScript基础
categories: 前端开发
keywords: 
description: 
top_img: ./img/bg12.jpg
cover: ./img/bg12.jpg

---
# **「1. 数组的概念」** 



一组数据的集合，其中的每个数据被称作`元素`，在数组中可以存放任意类型的元素。数组是一种将一组数据存储在单个变量名下的优雅方式。数组中可以存放任意类型的数据

# **「2. 创建数组」**

- 利用new关键字创建数组

```js
var 数组名 = new Array([n]);//[]代表可选 若写n，则代表数组的长度
var arr = new Array();//创建了一个名为 arr 的空数组
```



- 利用数组字面量创建数组

```js
// 1. 使用数组字面量方式创建空的数组
var 数组名 = [];//若写n，则代表数组的长度
    
//2. 使用数组字面量方式创建带初始值的数组
//3. 声明数组并赋值称为数组的初始化
var arr =['1','2','3','4'];
var arr2 = ['fan',true,17.5];//数组中可以存放任意类型的数据
```



# **「3. 访问数组元素」**

索引(下标):用来访问数组元素的序号。索引从 `0` 开始

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202206070836311.png)

```js
// 定义数组
var arrStus = [1,2,3];
// 获取数组中的第2个元素 
alert(arrStus[1]); 
// 如果访问数组时没有和索引值对应的元素(数组越界)，
// 返回值为undefined
```

# **「4. 遍历数组」**

把数组中的元素从头到尾都访问一次。

```js
var arr = ['red','green','blue'];
for (var i = 0; i < 3; i++) {
    console.log(arr[i]);
}
//1.数组索引号从零开始，所以i必须从零开始
//2.输出结果的时候 arr[i]， i 计数器当索引号使用
```

# **「5.数组长度」**

```js
// 数组名.length
var arr = ['甲','乙','丙','戍','己','庚','辛'];
for (var i = 0; i < 7; i++) {
    console.log(arr[i]);
}
console.log(arr.length);
for (var i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}
//1. 数组的长度是元素个数，不要跟索引号混淆
//2. arr.length 动态监测数组元素个数

```

## 案例：求数组中最大值

```js
//求数组中最大值
//声明一个保存最大元素的变量max
//默认最大值可取数组中第一个元素
//遍历这个数组，把里面的每个元素与max比较
//如果该数组元素大于max，把这个元素保存到max里面
//最后输出max
var arr = ['2','6','1','77','52','25','7'];
var max = arr[0];
for (var i = 1; i < arr.length; i++) {
    if (arr[i] > arr[0]) {
        max = arr[i];
    }
}
console.log('该数组中最大的是' + max);
```

## 案例：数组转换为字符串

```js
//将数组转换为字符串，并用*分割
//1.需要一个新变量存放转换完成的字符串
//2.遍历原来的数组，分别把里面的数组元素取出来，加到字符串里面
//3.同时在后面多加一个*
var arr = ['red','green','blue','pink'];
var str = '';
var sep = '*';
for (var i = 0; i < arr.length; i++) {
    str += arr[i] + sep;
}
console.log(str);
```



# **「6.数组新增元素」**

可以通过修改length长度以及索引号增加数组元素

- **「修改length属性」**

```js
// 1.新增数组元素，修改length长度
var arr = ['red','green','blue'];
console.log(arr.length);
arr.length = 5; // 把数组元素长度修改为5，里面应该有5个元素
console.log(arr[3]);
console.log(arr[3]); // 新增空间没有给值，所以是undefined
console.log(arr[4]); // undefined
```

- **「修改数组索引」**

```js
// 2.新增数组元素，修改索引号，追加数组元素
var arr1 = ['red','green','blue'];
arr1[3] = 'pink';
console.log(arr1);
arr1[4] = 'hotpink';
console.log(arr1);
arr1[0] = 'yellow'; // 这里是替换原来的数组元素
console.log(arr1);
arr1 = '有点意思';
console.log(arr1); // 不要直接给数组名赋值，会覆盖掉以前的数据，数组里面的数组元素都没有了
```



## 案例：数组中存放1-100个值

```js
//新建一数组，存放1-100个值
//核心原理：使用循环追加数组
//1.声明一个空数组 arr
//2.循环中计数器 i 可作为数组元素存入
//3.由于数组索引号是从0开始，因此计数器从0开始合适，存入的数组元素需要 + 1
var arr = [];
for (var i = 0; i < 100; i++) {
    arr[i] = i + 1;
}
console.log(arr);
```

## 案例：筛选数组

```js
//将数组['2','0','6','1','77','0','52','0','25','7','6']中大于等于10 的元素选出来放入新数组
// 1.声明一个新的数组用于存放新数据 newArr
// 2.遍历原来旧的数组，找出大于等于 10 的元素
// 3.依次追加给新数组 newArr
var arr = ['2','0','6','1','77','0','52','0','25','7','6'];
var newArr = [];
var j = 0;
for (var i = 0; i < arr.length; i++) {
    if (arr[i] >= 10) {
        // 新数组索引号从0开始，依次递增
        newArr[j] = arr[i];
        j++;
    }
}
console.log(newArr);
// 方法二
var arr = ['2','0','6','1','77','0','52','0','25','7','6'];
var newArr = [];
// 刚开始 newArr.length 就是0
for (var i = 0; i < arr.length; i++) {
    if (arr[i] >= 10) {
        // 新数组索引号应该从0开始，依次递增
        newArr[newArr.length] = arr[i];
    }
}
console.log(newArr);
```

## 案例：翻转数组

```js
//将数组
// 1.声明一个新数组 newArr
// 2.把旧数组索引号4个取过来（arr.length - 1），给新数组索引号第0个元素（newArr.length）
// 3.采用递减的方式 i++
var arr = ['red','green','blue','pink','purple'];
var newArr[];
for (var i = arr.length - 1; i >= 0; i--) {
    newArr[newArr.length] = arr[i];
}
console.log(newArr);
```

## 案例：冒泡排序 把数组从大到小或从小到大重新排序 

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202206070959111.png)

```js
// 冒泡排序 从小到大排序
// var arr = [5, 4, 3, 2, 1];
var arr = [4, 1, 2, 3, 5,];
for (var i = 0; i <= arr.length - 1; i++) { // 外层循环负责趟数
    for (var j = 0; j <= arr.length - i - 1; j++) { // 内层循环负责每一趟的交换次数
        // 内部交换两个变量的值，第一个和后面一个数组元素相比较
        if (arr[j] > arr[j + 1]) {
            var temp = arr[j];
            arr[j] = arr[j + 1];
            arr[j + 1] = temp;
        }
    }
}
console.log(arr);
```









