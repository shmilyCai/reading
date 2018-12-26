# ECMAScript6入门

## 总结

需要深入学习


## let和const命令

es6中存在6种声明变量的方法：var， function，let，const，import，class

### let

命令所声明的变量只在所在的代码块内有效

不存在变量提升现象，所以，变量一定要在声明后使用，否则会报错

如果区块中存在let和const命令，则这个区块对这些命令声明的变量从一开始就形成封闭作用

使用let命令声明变量之前，该变量都是不可用的，这在语法上称为暂时性死区

暂时性死区和不存在变量提升，主要是为了减少运行时错误，防止在变量声明前就使用这个变量，从而导致意料之外的行为

不允许在相同作用域内重复声明同一个变量

在严格模式下，函数只能在顶层作用域或者函数内声明，其它情况（如if代码块，循环代码块）下的声明都会报错

### const命令

用来声明常量，一旦声明，其值就不能改变

只在声明所在的块级作用域内有效

const命令声明的常量也不提升，同样存在暂时性死区，只能在声明后使用

对于复合类型的变量，变量名不指向数据，而是指向数据所在的地址

ES6规定，var命令和function命令声明的全局变量依旧是全局对象的属性，也规定，let，const，class命令声明的全局变量不属于全局对象的属性

## 变量的解构赋值

### 数组的解构赋值

这种写法属于“模式匹配”，只要等号两边的模式相同，左边的变量就会被赋予对应的值。

```
let [a, b, c] = [1, 2, 3];

let [head, ...tail] = [1, 2, 3, 4];
head // 1
tail // [2, 3, 4]

let [x, y = 'b'] = ['a', undefined]; // x='a', y='b' 可赋予默认值
```

### 对象的解构赋值

数组的元素是按次序排列的，变量的取值由它的位置决定，而对象的属性没有次序，变量必须与属性同名，才能取到正确的值。

```
let { bar, foo } = { foo: "aaa", bar: "bbb" };
foo // "aaa"
bar // "bbb"

let { baz } = { foo: "aaa", bar: "bbb" };
baz // undefined
```

变量名和属性名不相同时的写法：

```
let { foo: baz } = { foo: 'aaa', bar: 'bbb' };
baz // "aaa"

let obj = { first: 'hello', last: 'world' };
let { first: f, last: l } = obj;
f // 'hello'
l // 'world'
```

对象的嵌套：

```
let obj = {
  p: [
    'Hello',
    { y: 'World' }
  ]
};

let { p, p: [x, { y }] } = obj;
x // "Hello"
y // "World"
p // ["Hello", {y: "World"}]
```

### 字符串的解构赋值

字符串被转换成了一个类似数组的对象

```
const [a, b, c, d, e] = 'hello';
a // "h"
b // "e"
c // "l"
d // "l"
e // "o"

let {length : len} = 'hello';
len // 5
```

### 数值和布尔值的解构赋值

解构赋值时，如果等号右边是数值和布尔值，则会先转为对象

由于undefined和null无法转为对象，所以对它们进行解构赋值，会报错

```
let {toString: s} = 123;
s === Number.prototype.toString // true

let {toString: s} = true;
s === Boolean.prototype.toString // trues
```

### 函数参数的解构赋值

```
function add([x, y]){
  return x + y;
}

add([1, 2]); // 3

//设置默认值
function move({x = 0, y = 0} = {}) {
  return [x, y];
}

move({x: 3, y: 8}); // [3, 8]
move({x: 3}); // [3, 0]
move({}); // [0, 0]
move(); // [0, 0]
```

### 注意

1. 尽量不要在解构赋值的时候使用圆括号

### 用途

1. 交换变量的值

```
let x = 1;
let y = 2;

[x, y] = [y, x];
```

2. 从函数返回多个值

```
// 返回一个数组

function example() {
  return [1, 2, 3];
}
let [a, b, c] = example();

// 返回一个对象

function example() {
  return {
    foo: 1,
    bar: 2
  };
}
let { foo, bar } = example();
```

3. 函数参数的定义

```
// 参数是一组有次序的值
function f([x, y, z]) { ... }
f([1, 2, 3]);

// 参数是一组无次序的值
function f({x, y, z}) { ... }
f({z: 3, y: 2, x: 1});
```

4. 提取JSON数据

```
let jsonData = {
  id: 42,
  status: "OK",
  data: [867, 5309]
};

let { id, status, data: number } = jsonData;

console.log(id, status, number);
// 42, "OK", [867, 5309]
```

5. 函数参数的默认值

```
jQuery.ajax = function (url, {
  async = true,
  beforeSend = function () {},
  cache = true,
  complete = function () {},
  crossDomain = false,
  global = true,
  // ... more config
} = {}) {
  // ... do stuff
};
```

6. 遍历Map解构

```
const map = new Map();
map.set('first', 'hello');
map.set('second', 'world');

for (let [key, value] of map) {
  console.log(key + " is " + value);
}
// first is hello
// second is world

// 获取键名
for (let [key] of map) {
  // ...
}

// 获取键值
for (let [,value] of map) {
  // ...
}
```

7. 输入模块的指定方法

```
const { SourceMapConsumer, SourceNode } = require("source-map");
```

### 函数参数的解构赋值

## 字符串的扩展

## 正则的扩展

## 数值的扩展

## 函数的扩展

## 数组的扩展

## 对象的扩展

## 对象的新增方法

## Symbol

ES6引入的一种新的原始数据类型Symbol，表示独一无二的值。

凡事Symbol类型，都是独一无二的，可以保证不会与其它属性名产生冲突

Symbol值通过Symbol函数生成

对象的属性名现在有2种类型：

1. 是原来就有的字符串
2. 新增的Symbol类型，

```
let s = Symbol();

typeof s
// "symbol" 表明s是Symbol数据类型
```

Symbol函数可接受一个字符串作为参数，表示对Symbol实例的描述，为了在控制台显示的时候，容易区分

```
let s1 = Symbol('foo');
let s2 = Symbol('bar');

s1 // Symbol(foo)
s2 // Symbol(bar)

s1.toString() // "Symbol(foo)"   
s2.toString() // "Symbol(bar)"
```

### 注意

1. Symbol函数前不能使用new命令，否则会报错
2. Symbol值不能与其它类型的值进行运算，会爆粗
3. 相同参数的Symbol值，是不相等的
4. Symbol函数的参数，只是对当前Symbol值的描述
5. Symbol值可以显式转为字符串和布尔值，但是不能转为字符串

### 作为属性名的Symbol

用于对象的属性名，保证不会出现同名的属性，能防止某一个键不小心改写或者覆盖

注意：

1. Symbol值作为对象属性名时，不能用点运算符，
2. 只能放在方括号里面
3. Symbol值作为属性名时，该属性还是公开属性，不是私有属性
4. Symbol作为属性名时，该属性不会出现在for……in，for……of循环中，也不会被Object.keys()、Object.getOwnPropertyNames()、JSON.stringify()返回
5. Object.getOwnPropertySymbols方法，可以获取指定对象的所有 Symbol 属性名，该方法返回的是一个数组
6. Reflect.ownKeys方法可以返回所有类型的键名，包括常规键名和Symbol键名

### Symbol.for()和Symbol.keyFor()

Symbol.for()

	接受一个字符串作为参数，然后搜索有木有以该参数作为名称的Symbol值。如果有，就返回这个Symbol值，否则就新建并返回一个以该字符串为名称的Symbol值。

Symbol.keyFor()

	返回一个已登记的Symbol类型值的key

### 实例：模块的singleton模式

Singleton模式指的是调用一个类，任何时候返回的都是同一个实例

### 内置的Symbol值

Es提供了11个内置的Symbol值，指向语言内部使用的方法

Symbol.hasInstance

	指向一个内部方法，当其它对象使用instanceof运算符，判断是否为该对象的实例时，会调用这个方法

Symbol.isConcatSpreadable

	对象的Symbol.isConcatSpreadable属性等于一个布尔值，表示该对象用于Array.prototype.concat()时，是否可以展开

Symbol.species

	对象的Symbol.species属性，指向一个构造函数。创建衍生对象时，会使用该属性。

Symbol.match

	对象的Symbol.match属性，指向一个函数。当执行str.match(myObject)时，如果该属性存在，会调用它，返回该方法的返回值

Symbol.replace

	对象的Symbol.replace属性，指向一个方法，当该对象被String.prototype.replace方法调用时，会返回该方法的返回值。

Symbol.search

	对象的Symbol.search属性，指向一个方法，当该对象被String.prototype.search方法调用时，会返回该方法的返回值

Symbol.split

	对象的Symbol.split属性，指向一个方法，当该对象被String.prototype.split方法调用时，会返回该方法的返回值

Symbol.iterator

	对象的Symbol.iterator属性，指向该对象的默认遍历器方法

Symbol.toPrimitive

Symbol.toStringTag

Symbol.unscopables

## Set和Map数据结构

### Set

ES6提供了新的数据结构Set，类似于数组，但是成员的值都是唯一的，没有重复值

Set本身是一个构造函数，用来生成Set数据结构

```
const s = new Set();

[2, 3, 5, 4, 5, 2, 2].forEach(x => s.add(x)); //add方法向Set结构加入成员，表明Set结构不会添加重复值

for (let i of s) {
  console.log(i);
}
// 2 3 5 4
```

Set函数接受数组作为参数，

```
// 去除数组的重复成员
[...new Set(array)]
```

#### Set实例的属性和方法

实例：

	Set.prototype.constructor：构造函数，默认就是Set函数
	Set.prototype.size：返回Set实例的成员总数

操作方法：

	add(value), 添加某个值，返回set结构本身，加入值时，不会进行类型转换，5和“5”是不同值
	delete(value),删除某个值，返回一个布尔值，表示删除是否成功
	has(value),返回一个布尔值，表示该值是否为set成员
	clear(),清除所有成员，没有返回值

遍历操作方法：

	keys(), 返回键名的遍历器
	values(), 返回键值的遍历器
	entries(), 返回键值对的遍历器
	forEach(), 使用回调函数遍历每个成员
	for……of循环遍历

### WeakSet

WeakSet结构与Set类似，也是不重复的值的集合。

特点：

1. WeakSet的成员只能是对象，而不能是其它类型的值
2. WeakSet中的对象都是弱引用，即垃圾回收机制不考虑WeakSet对该对象的引用，即如果其它对象都不再引用该对象，那么垃圾回收机制会自动回收该对象所占用的内存，不考虑该对象还存在于WeakSet之中
3. 不可遍历
4. WeakSet是一个构造函数，可以使用new命令，创建WeakSet数据结构

方法：

	WeakSet.prototype.add(value)：向 WeakSet 实例添加一个新成员。
	WeakSet.prototype.delete(value)：清除 WeakSet 实例的指定成员。
	WeakSet.prototype.has(value)：返回一个布尔值，表示某个值是否在 WeakSet 实例之中

### Map

Map数据结构，类似于对象，也就是键值对的集合，键的范围不限于字符串，各种类型的值（包括对象）都可以当作键

```
const m = new Map();
const o = {p: 'Hello World'};

m.set(o, 'content')
m.get(o) // "content"

m.has(o) // true
m.delete(o) // true
m.has(o) // false
```

属性和方法：

	size，返回Map结构的成员总数
	set(key, value)，设置键名key对应的键值为value，然后返回整个Map结构，如果已经存在key值，则键值会被更新，否则就新生成该键
	get(key)，读取key对应的键值，如果找不到key，返回undefined
	has(key)，返回一个布尔值，表示某个键是否在当前Map对象之中
	delete(key)，删除某个键，返回true，如果删除失败，返回false
	clear()，清除所有成员，没有返回值

遍历方法：

	keys()：返回键名的遍历器
	values()：返回键值的遍历器
	entries()：返回所有成员的遍历器
	forEach()：遍历 Map 的所有成员

与其它数据结构的互相转换

1. Map转为数组，使用扩展运算符（...）

```
const myMap = new Map()
  .set(true, 7)
  .set({foo: 3}, ['abc']);
[...myMap]
// [ [ true, 7 ], [ { foo: 3 }, [ 'abc' ] ] ]
```

2. 数组转为Map，将数组传入Map构造函数，就可以转为Map

```
new Map([
  [true, 7],
  [{foo: 3}, ['abc']]
])
// Map {
//   true => 7,
//   Object {foo: 3} => ['abc']
// }
```

3. Map转为对象
4. 对象转为Map
5. Map转为JSON
6. JSON转为Map

结构与Map结构类似，也是用于生成键值对的集合

注意：
1. WeakMap只接受对象作为键名（null除外），不接受其它类型的值作为键名
2. WeakMap的键名所指向的对象，不计入垃圾回收机制
3. 没有属性和遍历操作

### WeakMap

## Proxy

## Reflect

##Promise对象

## Iterator和for……of对象

## Generator函数

## Generator函数的异步应用

## async函数

## Class的基本用法

## Class的继承

## Decorator

## Module的语法

## Module的加载实现











