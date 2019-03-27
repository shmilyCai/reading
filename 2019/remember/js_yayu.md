# Javascript


## Javascript基础

1. call模拟实现
2. apply模拟实现
3. bind模拟实现
4. new模拟实现

## Javascript专题

模拟代码必记住的：
1. 深浅拷贝
2. 数组去重
3. 类型判断
4. 求数组中的最大值和最小值
5. 防抖与节流
6. 类型判断
7. V8排序
8. 排序算法，插入排序，快速排序，冒泡排序，选择排序

## ES6

## 模拟实现

### call模拟实现

1. 将函数设为对象的属性
2. 执行该函数
3. 删除该函数

### apply模拟实现

1. 将函数设为对象的属性
2. 执行该函数，其中主要第二个参数为数组
3. 删除函数

### bind模拟实现

bind模拟实现的步骤：
1. 将this赋值给self，保存当前上下文
2. 获取调用bind方法中的除开第一个的argument
3. 定义fBound函数，并且返回这个函数
4. 获取bind返回的函数调用这个函数的argument（因为argument不是数组，通过slice转换为数组）
5. 返回self通过apply调用，参数为context和args的结合（因为apply的第二个参数必须为数组），并判断这个返回函数的this是否fBound的实例，是就返回this，否则返回context
6. 将fBound的原型定义为this这个原型
7. 返回fBound

### new模拟实现

new模拟实现的步骤：
1. 新建o
2. 获取argument中的第一个元素为constructor
3. 将o的原型指向constructor的原型
4. 定义ret作为constructor调用apply，并传入o与argument
5. 判断ret是否为object，是返回ret，否返回o

记忆点：o <--> C



### 数组去重

1. for循环
2. indexOf
3. 排序去重
4. fitter简化（indexof，排序）
5. 键值对（各个版本的区别）
6. set去重，（简化版本，map版本）

特殊类型比较注意：
```
var str1 = '1';
var str2 = new String('1');

console.log(str1 == str2); // true
console.log(str1 === str2); // false

console.log(null == null); // true
console.log(null === null); // true

console.log(undefined == undefined); // true
console.log(undefined === undefined); // true

console.log(NaN == NaN); // false
console.log(NaN === NaN); // false

console.log(/a/ == /a/); // false
console.log(/a/ === /a/); // false

console.log({} == {}); // false
console.log({} === {}); // false
```

以上各种循环的优缺点比较
1. for循环，兼容性好


### 防抖

解决的问题是频繁触发事件

防抖的原理是：
你尽管触发事件，但是我一定在事件触发 n 秒后才执行，如果你在一个事件触发的 n 秒内又触发了这个事件，那我就以新的事件的时间为准，n 秒后才执行，总之，就是要等你触发完事件 n 秒内不再触发事件，我才执行


### 节流


节流的原理是：
如果你持续触发事件，每隔一段时间，只执行一次事件

根据首次是否执行以及结束后是否执行，效果有所不同。

实现方式分为：
1. 时间戳
2. 设置定时器




