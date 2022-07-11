---
title: Javascript流程控制
date: 2022-05-25
updated: 2022-06-03
tags:
  - 小白的前端之路
  - JavaScript基础
categories: 前端开发
keywords: 
description: 
top_img: ./img/bg14.jpg
cover: ./img/bg13.jpg

---


# **流程控制**

在一个程序执行的过程中，各条代码的执行顺序对程序的结果是有直接影响的。很多时候我们要通过控制代码的执行顺序来实现我们要完成的功能。流程控制主要有三种结构，分别是**顺序结构**、**分支结构**和**循环结构**，代表三种代码执行的顺序。

![](https://cdn.jsdelivr.net/gh/lonely2022/picture/img/202205311435023.png)

# **分支结构**

js语言提供了两种分支结构语句

- if语句
- switch语句

## **「if 语句」**

```js
//条件成立执行代码，否则什么也不做
if(条件表达式){
    //条件成立执行代码语句
}
```

语句可以理解为一个行为，循环语句和分支语句就是典型的语句。一个程序由多个语句组成，一般情况下，会被分割成一个一个的语句。

```js
//执行思路，如果if里面的条件表达式结果为真，true，则执行大括号里面的执行语句
//如果if条件表达式结果为假，则不执行大括号里的语句，执行if语句后面的代码
//演示
if (3>2){
    alert('前端路漫漫');
}
```

## **「if else语句（双分支语句）」**

语法结构

```js
//条件成立，执行if里代码，否则执行else里代码
if(条件表达式){
    //if条件成立时执行的代码
}
else{
    //else执行的代码
}
//if里面的语句1和else里面的语句2，最终只能有一个语句被执行 2选1
//else后面直接跟大括号
```

### 案例：进入网吧

```js
//弹出prompt警示框，用户输入年龄，存入变量age
//使用if语句判断年龄，如年龄大于等于18，执行括号里内容
var age = prompt('请输入您的年龄')
if(age >= 18){
    alert('我想带你去网吧');
} else{
    alert('滚');
}
```

### 案例：判断闰年

```js
//算法：能被四整除且不能被100整除的为闰年 或着 能被400整除的是闰年
//弹出prompt输入框，输入年份存入白能量
//使用if语句判断
//注意&& 还有|| ，同时注意判断整除的方法是取余为0
var year = prompt('请输入年份');
if(year % 4 == 0 && year % 100 != 0 || year % 400 == 0){
    alert('您输入的年份是闰年');
}
else{
    alert('您输入的年份是平年');
}

```

## **「if else if 语句（多分支语句）」**

```js
//1.多分支语句，就是利用多个条件来选择不同的语句执行，得到不同的结果，多选一的过程
//2.if else if语句是多分支语句
//3.语法规范
if(条件表达式1){
    //语句1;
} else if(条件表达式2){
    //语句2;
} else if(条件表达式3){
    //语句3;
} else {
    //最后的语句;
}
//4.执行思路
/*	如果条件表达式1满足就执行语句1，执行完毕后，退出整个if分支语句
	如果条件表达式1不满足，则判断条件表达式2，满足的话执行语句2，以此类推
	如果上面条件都不满足，则执行else里的语句
*/
//5.注意点
/* 多分支语句是多选一，最后只能有一个语句被执行
	else if 理论上可以是任意多个
	
```

### 案例：判断成绩

```js
//(伪代码) 按从大到小的顺序
//弹出prompt输入框，让用户输入分数保存在变量中
//使用if else if多分支判断
var score = prompt('请输入成绩');
if(score >= 90){
    alert('A');
} else if(score >= 80){
    alert('B');
} else if(score >= 70){
    alert('C');
} else if(score >= 60){
    alert('D');
} else{
    alert('E');
}
```

## **「三元表达式」**

```js
//1.有三个运算符组成的式子我们成为三元表达式
//2.++num  3+5  ? :
//3.语法结构
条件表达式?表达式1:表达式2;
//4.执行思路
//如果条件表达式结果为真，则返回表达式1的值，如果条件表达式结果为假，则返回表达式2的值
//5.代码体验
var num = 10;
var result = num > 5 ? '是的' : '不是的';
console.log(result);
```

### 案例：数字补0

```js
//用户输入0-59之间的一个数字
//如果数字小于10，则在这个数字面前补0，（加0拼接），否则不做操作
//用一个变量接收这个返回值，输出
var time = prompt('请输入一个数字');
var result = time < 10 ? '0' + time : time;//把返回值赋值给第一个变量
alert(result);
```

## **「switch分支」**

switch语句也是多分支语句，它用于基于不同的条件来执行不同的代码，当要针对变量设置一系列的特定值的选项时，就可以使用switch

```js
//1.switch也是多分支，可以实现多线一
//2.语法结构  switch 转换，开关  case 小例子或选项的意思
switch(表达式){
    case value1:
        执行语句1;
        break;
    case value2:
        执行语句2;
        break;
    ...
    default:
    	执行最后的语句;
}
//3.执行思路，利用表达式的值和case后面的选项值相匹配，如果匹配上，就执行该case里面的语句，如果都没有匹配上，则执行default里面的语句
//4.代码验证
switch(2){
    case 1:
        console.log('这是1');
        break;
    case 2:
        console.log('这是2');
        break;
    case 3:
        console.log('这是3');
        break;
    default:
        console.log('无匹配结果');
}
```

### switch注意事项

```js
var num = 1;
switch(num){
    case 1:
        console.log(1);
        break;
    case 2:
        console.log(2);
        break;
    case 3:
        console.log(3);
        break;
    default:
        console.log('无匹配');
}
//1.开发里面，表达式经常写成变量
//2.num和case里值相匹配的时候要求全等，必须数值和数据类型一致才可以 num === 1
//3.break 如果当前case没有break，则不会退出switch，而是继续执行下一个case
```

### 案例：查询水果案例

```js
//弹出prompt输入框，输入水果名称存入变量
//将这个变量作为switch括号内的表达式
//case后面的值写几个不同水果的名称，注意一定要加引号，因为必须时全等匹配
//弹出不同价格即可，注意每个case后面的break语句
//将default设置成无此水果
var frult = prompt('请输入查询的水果');
switch(frult){
    case '苹果':
        alert('苹果的价格是3.5')；
        break;
    case '榴莲':
        alert('榴莲的价格是35');
        break;
    default:
        alert('无此水果');
}
```

### switch和if..else..if的区别

1. 一般情况下，可以互相替换

2. switch…case通常处理case比较确定的值的情况，而if…else…if更加灵活常用于范围判断

3. switch语句进行条件判断后直接执行条件语句，效率更高，而if else if有多少条件就要判断多少次

4. 当分支较少时，if…else执行效率比switch高

5. 当分支较多时，switch语句执行效率比较高，且结构清晰

   

   

# **循环结构**

js中主要由三种类型的循环语句

- for循环
- while循环
- do..while循环

## **「for循环」**

```js
//1.for循环重复执行某些代码，通常跟计数有关
//2.for循环语法结构
for(初始化变量;条件表达式;操作表达式){
    循环体;
}
//3.初始化变量 就是用var声明的一个普通变量，通常用作计数器使用
//4.条件表达式 就是用来决定每一次循环是否继续执行 ，就是终止的条件
//5.操作表达式 是每次循环最后执行的代码 经常用于我们计数器变量的更新（递增或者递减）
//6.代码体验
for(var i = 1; i <= 100; i++){
    console.log('你好吗');
}
```

for循环执行过程

1. 初始化变量，初始化操作在整个 for 循环只会执行一次。
2. 执行条件表达式，如果为true，则执行循环体语句，否则退出循环，循环结束。
3. 执行操作表达式,此时第一轮结束。
4. 第二轮开始，直接去执行条件表达式（不再初始化变量），如果为 true ，则去执行循环体语句，否则退出循环。
5. 继续执行操作表达式，第二轮结束。......

```js
//for循环执行相同代码
for(var i = 1; i <= 10; i++){
    console.log('我错了');
}
//让用户控制输出次数
var num = prompt('输入循环次数');
var(var i = 1; i <= num; i++){
    console.log('我错了');
}
```

```js
//for循环可以重复执行不同的代码 因为我们有计数器变量i的存在 i每次循环值都会变化
for(var i = 1; i <= 100; i++){
    if(i == 1){
        console.log('这个人今年1岁了，他出生了');
    } else if(i == 100){
        console.log('这个人今年100岁了，他死了');
    } else {
        console.log('这个人今年' + i + '岁了');//字符串与数字拼接
    }
}
```

### 案例：for循环求1-100累加和案例

```js
// 需要循环100次，我们需要一个计数器i
//需要一个储存结果的变量sum，初始值为0
//核心算法：1+2+3+4+...，sum = sum + i
var sum = 0;
for (var i = 1; i <= 100; i++) {
    sum = sum + i;
    //sum += i;
}
console.log(sum);


```

### 案例：for循环求1-100平均值

```js
var sum = 0;
var average = 0;
for (var i = 1; i <= 100; i++) {
    sum += i;
}
average = sum / 100;
console.log(average);
```

### 案例：求1-100所有奇数和偶数的和

```js
var even = 0;
var odd = 0;
for (var i = 1; i <= 100; i++) {
    if (i % 2 = 0) {
        even += i;
    } else {
        odd += i;
    }     
}
console.log('1-100之间所有的偶数的和是' + even);
console.log('1-100之间所有的奇数的和是' + odd);
```

### 案例：求1-100所有能被3整除的数字的和

```javascript
var result = 0;
for (var i = 1; i <= 100; i++) {
    if (i % 3 = 0) {
        result += i;
    }
} 
console.log('1-100之前能够被3整除的数字的和是' + result);
```

### 案例：求学生成绩案例

```js
//弹出输入框输入总的班级人数（num)
//依次输入学生成绩（保存起来 score），此时用到for循环
//for循环，弹出的次数跟输入的班级总人数有关系，条件表达式 i <= num
//进行业务处理：计算成绩，先求总成绩（sum），之后求平均成绩（average）
//弹出结果
var num = prompt('请输入班级总人数：'); // num 班级总人数
var sum = 0; // 求和的变量sum
var average = 0; // 平均值的变量average
for (var i = 1; i <= num; i++) {
    var score = prompt('请输入第' + i + '个学生成绩');
    // 因为从prompt取过来的数都是字符串型的，需要转换成数字型
    sum = sum + parseFloat(score);
}
average = sum / num;
alert('班级总成绩是' + sum);
alert('班级平均分是' + average);
```

### 案例：一行打印5个星星

```js
//一行打印5个星星(不能全部显示)
for (var i = 1; i <= 5; i++) {
    console.log('#');
}
//如果一行全部展示出星星，采用拼接字符串型
var str = '';
for (var i = 1; i <= 5; i++) {
    str = str + '#';
}
console.log(str);
//自定义输出个数
var num = prompt('请输入星星的个数');
var str = '';
for (var i = 1; i <= num; i++){
    str = str + '#';
}
console.log(str);
```

## **「双重for循环」**

循环嵌套是指在一个循环语句中再定义一个循环语句的语法结构，例如在for循环语句中，可以再嵌套一个for 循环，这样的 for 循环语句我们称之为双重for循环。

```js
//1.双重for循环语法结构
for (外层初始化变量; 外层条件表达式; 外层操作表达式) {
    for (里层初始化变量; 里层条件表达式; 里层操作表达式){
        //执行语句
    }
}
//2.我们可以把里面的循环看作是外层循环的语句
//3.外层循环循环一次，里面的循环执行全部
//4.代码验证
for (var i = 1; i <= 3; i++) {
    console.log('这是外层循环第' + i + '次');
    for (var j = 1; j <= 3; j++) {
        console.log('这是内层循环第' + j + '次');
    }
}
```

### 案例：打印5行5列星星

```js
//内层循环负责一行打印5个星星
//外层循环负责打印5行
var str = '';
for (var i = 1; i <= 5; i++) { //外层负责打印5行
    for ( var j = 1; j <= 5; j++){ // 内层负责一行打印5个星星
        str = str + '#';
    }
    //一行打完5个星星需要另起一行，加 \n
    str = str + '\n';
}
console.log(str);
```

### 案例：打印n行n列星星

```js
//打印n行n列
var rows = prompt('请您输入行数');
var cols = prompt('请您输入列数');
var str = '';
for (var i = 1; i <= rows; i++) {
    for (var j = 1; j <= cols; j++) {
        str = str + '#';
    }
    str += '\n';
}
console.log(str);
```

### 案例：打印倒三角

```js
//打印倒三角
//核心算法：j = i; j <= 10; j++
var str = '';
for (var i = 1; i <= 10; i++) { //外层控制行数
    for (var j = i; j <= 10; j++) { //内层循环打印个数不一样 j = i
        str = str + '';
    }
    str += '\n';
}
console.log(str);
```

### 案例：打印九九乘法表

```js
//九九乘法表
//一共有9行，但每行个数不一样，因此用到双重for循环
//外层for循环控制行数i，循环9次，可以打印9行
//内层for循环控制每行公式 j
//核心算法：每一行公式的个数正好和行数一样， j <= i
//每行打印完毕都需要重新换行
var str = '';
for (i = 1; i <= 9; i++) { //外层控制行数
    for (var j = 1; j <= i; j++) { //内层控制每一行个数 j <= i
        //1 × 2 = 2
        //str = str + '#'
        str += j + '×' + i + '=' + i * j + '\t'; //字符串拼接
    }
    str += '\t';
}
console.log(str);

```



## **「while循环」**

```js
//1.while循环语法结构  （while 当...时候）
while (条件表达式) {
    //循环体
}
//2.执行思路，当条件表达式结果为true时，则执行循环体，否则退出循环
//3.代码验证
var num = 1;
while (num <= 100) {
    console.log('循环');
    num++;
}
//4.里面需要添加计数器，初始化变量
//5.里面也需要操作表达式，完成计数器的更新，防止死循环
```

### 案例：打印人的一生

```js
var i = 1;
while (i <= 100) {
    console.log('这个人今年' + i + '岁了');
    i++;
}
```

### 案例：计算1-100整数的和

```js
var sum = 0;
var j = 1;
while (j <= 100) {
    sum += j;
    j++;
}
console.log(sum);
```

```js
var message = prompt('你爱我吗');
while (message !== '我爱你') {
    message = prompt('你爱我吗');
}
alert('我也爱你');
```

## **「do while循环」**

```js
//1.do while语法结构
do {
    //循环体
} while (条件表达式)
//2.执行思路，跟while不同的地方在于，do while先执行一次循环体，然后在判断条件，如果条件结果为真则继续执行循环体，否则退出循环
//3.代码验证
var i = 1;
do {
    console.log('你好吗');
    i++;
} while (i <= 100);
//4.do while循环体至少执行一次
```

### 案例：打印人的一生

```js
var i = 1;
do {
    console.log('这个人今年' + i + '岁了');
    i++;
} while (i <= 100)
```

### 案例：计算1-100所有整数的和

```js
var sum = 0;
var j = 1;
do {
    sum += j;
    j++;
} while(j <= 100)
console.log(sum)
```

## **「continue、break」**

1.   `continue` 关键字用于立即跳出本次循环，继续下一次循环（本次循环体中 continue 之后的代码就会少执行一次）。

2.   `break` 关键字用于立即跳出整个循环（循环结束）。

```js
//continue关键字 退出本次循环（当前次循环），继续执行剩余次数循环
for (var i = 1; i <= 5; i++) {
    if (i == 3) {
        continue;//只要遇见continue就退出本次循环，直接跳到i++
    }
    console.log('我正在吃第' + i + '个包子');
}

```

### 案例：求1-100之间，除了能被7整除之外的整数和

```js
var sum = 0;
for (var i = 1; i <= 100; i++) {
    if (i % 7 == 0) {
        continue;
    }
    sum += i;
}
console.log(sum);
```

```js
//break退出整个循环
for (var i = 1; i <= 5; i++) {
    if (i == 3) {
        break;//退出整个循环
    }
    console.log('我正在吃第' + i + '个包子');
}
```

# **代码规范**

1. 标识符命名规范

- 变量、函数的命名必须要有意义
- 变量的名称一般用名词
- 函数的名称一般用动词

2. 操作符规范

   ```js
   // 操作符的左右两侧各保留一个空格
   for (var i = 1; i <= 5; i++) {
     if (i == 3) {
         break; // 直接退出整个 for 循环，跳到整个for循环下面的语句
     }
     console.log('我正在吃第' + i + '个包子呢');
   }
   ```

3. 单行注释规范

   ```js
    for (var i = 1; i <= 5; i++) {
     if (i == 3) {
         break; // 单行注释前面注意有个空格
     }
     console.log('我正在吃第' + i + '个包子呢');
   }
   ```

4. 其他规范

   ```js
   //关键词 操作符空格
   if (true) {}
   for (var i = 0; i<=10; i++) {}
   ```

   



