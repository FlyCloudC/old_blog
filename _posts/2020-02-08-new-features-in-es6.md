---
layout: post
title: ECMAScript6 新特性
---

这几天趁着有电脑用，用ES6重写了之前写的几个网页，在重写的过程中学到了几个ES6的技巧，所以来记录一下。

## let声明变量

let的功能与var相似，都是声明一个变量。但是let的好处就是，变量的作用域会限制在块级作用域中，不会泄露到全局作用域。

```javascript
for(var i = 0; i < 5; ++i){
  //......
}

for(let j = 0; j < 5; ++j){
  //......
}

console.log(i);//5
console.log(j);//error: j is not defined
```

在新的ES6编码规范中，建议不再使用var。

## 模板字符串

简单的说，就是可以用更简洁的方式，把变量(或表达式)放进字符串里面。

```javascript
//ES5
var x = '今天是' + year + '年' + month + '月' + day + '日';

//ES6
let x = `今天是${year}年${month}月${day}日`;
```

原本交界处有8个字符，用模板字符串只要3个字符，代码更加紧凑。

## for...of 循环

声明一个循环变量，该变量会取遍数组里的每个元素。

```javascript
var arr = [2, 3, 3, 3, 3];
var sum = 0;

//ES5
for(var i = 0; i < arr.length; ++i)
  sum += arr[i];
//or
for(var i in arr) sum += arr[i];

//ES6
for(let x of arr) sum += x;
```

当你循环中用到i的地方全部都是arr[i]时，不妨用for...of试试。

## 箭头函数

这是定义匿名函数的一种方法，箭头前写参数，箭头后写返回值或代码块。

```javascript
var arr = [2, 3, 4 ,5, 6];

//ES5
arr.map(function (x) { return x * x; });

//ES6
arr.map(x => x * x);
```

瞬间清爽不少。

## 解构赋值

解构赋值就是用数组或对象同时给多个变量赋值。

```javascript
let [a, b] = [1, 2];
console.log(a);//1
console.log(b);//2

let {x, y} = { y: 0, x: 1 };
console.log(x);//1
console.log(0);//0
```

有了它可以在一行内优雅地交换变量的值。

```javascript
var a = 1, b = 2;

//ES5
var tmp = a;
a = b;
b = tmp;

//ES6
[a, b] = [b, a];
```

再配上箭头函数和数组的map()方法，获取DOM元素的时候就方便多了。

```javascript
var a, b, c;

//ES5
window.onload = function () {
  a = document.getElementById('a');
  b = document.getElementById('b');
  c = document.getElementById('c');
}

//ES6
window.onload = () => {
  [a, b, c] = ['a', 'b', 'c'].map(x => document.getElementById(x));
}
```

一般来说，"解构赋值+map()+箭头函数"可以用在对不同变量执行相同操作，比如说坐标的变换。

```javascript
[x, y] = [x, y].map(x => Math.floor(x / blockSideLen));
```

解构赋值配上for...of循环也是一个利器。

```javascript
let list = [
  ['Alex', 21],
  ['Bob', 20],
  ['David', 22]
];

window.onload = () => {
  for(let [name, age] of list)
    console.log(`${name} is ${age}.`);
}
```

只要在list数组中存储每个链接的标题和链接，网页的链接列表就可以用这种方法创建。

此外，函数的参数部分也可以使用解构赋值。因为传参实际上也是一种赋值。

对于某些事件的回调函数，第一个参数往往是一个对象，而有时候我们只需要用到其中的几个值，这时候就可以在函数的参数表中运用解构赋值，将这个对象解构。

```javascript
//ES5
button.onclick = function (event) {
  var x = event.offsetX;
  var y = event.offsetY;
  //......
}

//ES6
button.onclick = ({ offsetX: x , offsetY: y }) => {
  //......
}
```

## 数据结构Map和Set

前面多是语法上的优化，而这个是性能上的优化。

在ES6中，新增加了几种数据结构，用于储存集合(Set)或键值对(Map)。

Map和Set的内部实现是Hash表，也就是说可以进行O(1)的增删改查。而数组如果要在任意位置插入或删除一个元素的时间复杂度是O(n)。所以，在需要不停增加或删除的场合，Map和Set就排上了用场。

此外，Map和Set也支持for...of循环，Set返回的是单个元素，Map返回的是键值对数组。

## 结尾

事实上，ES6是大多数浏览器支持的最新版本，也是特性变化比较多的版本。ES6的变化，远不止这些，比如class、async函数、模块化等等，还有太多的东西值得去学。

最后放上我学习ES6的链接：

[《ECMAScript 6 入门教程》by 阮一峰](http://es6.ruanyifeng.com/)
