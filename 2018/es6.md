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

### WeakMap

结构与Map结构类似，也是用于生成键值对的集合

注意：
1. WeakMap只接受对象作为键名（null除外），不接受其它类型的值作为键名
2. WeakMap的键名所指向的对象，不计入垃圾回收机制
3. 没有属性和遍历操作

## Proxy

Proxy可以理解成，在目标对象之前架设一层“拦截”，外界对该对象的访问，都必须通过这层拦截，因此提供了一种机制，可以对外界的访问进行过滤和改写。

```
var proxy = new Proxy(target, handler);
//new Proxy表示生成一个Proxy实例，
//target参数表示所要拦截的目标对象，
//handle参数是对象，定制拦截行为
```

### Proxy实例的方法

	get()，用于拦截某个属性的读取操作，接收参数依次为目标对象，属性名和peoxy实例本身，最后一个参数可选
	set(), 用来拦截某个属性的赋值操作，接收参数依次为目标对象，属性名，属性值和Proxy实例本身
	apply()，用于拦截函数的调用，call和apply操作
	has()，用于拦截HasProperty操作，即判断对象是否具有某个属性时，这个方法会生效，典型的操作就是in运算符
	contruct()，用于拦截new命令
	deleteProperty()，用于拦截delete操作，如果这个方法抛出错误或者false，当前属性就无法被delete命令操作
	defineProperty()，用于拦截Object.defineProperty操作
	getOwnPropertyDescriptor()，用于拦截Object.getOwnPropertyDescriptor
	getPrototypeOf()，用于拦截获取对象的原型
	isExtensiblie()，用于拦截Object.isExtensiblie操作
	ownKeys()，用于拦截对象自身属性的读取操作
	preventExtensions()，用于拦截Object.preventExtensions操作，该方法必须返回一个布尔值，否则会被自动转为布尔值
	setPrototypeOf()，用于拦截Object.setPrototypeOf方法

	Proxy.revocable()，返回一个可取消的Proxy实例

注意：

在Proxy代理的情况下，目标对象内部的this关键字会指向Proxy代理

## Reflect

Reflect对象与Proxy对象一样，设计目的：

1.  将Object对象的一些明显属于语言内部的方法（比如Object.defineProperty），放到Reflect对象上

2. 修改某些Object方法的返回结果，让其变得更合理

3. 让Object操作都变成函数行为

4. Reflect对象的方法与Proxy对象的方法一一对应，只要是Proxy对象的方法，就能在Reflect对象上找到对应的方法

```
// 老写法
try {
  Object.defineProperty(target, property, attributes);
  // success
} catch (e) {
  // failure
}

// 新写法
if (Reflect.defineProperty(target, property, attributes)) {
  // success
} else {
  // failure
}
```

### 静态方法

Object方法所拥有的部分方法

	Reflect.apply(target, thisArg, args)
	Reflect.construct(target, args)
	Reflect.get(target, name, receiver)
	Reflect.set(target, name, value, receiver)
	Reflect.defineProperty(target, name, desc)
	Reflect.deleteProperty(target, name)
	Reflect.has(target, name)
	Reflect.ownKeys(target)
	Reflect.isExtensible(target)
	Reflect.preventExtensions(target)
	Reflect.getOwnPropertyDescriptor(target, name)
	Reflect.getPrototypeOf(target)
	Reflect.setPrototypeOf(target, prototype)

## Promise对象

Promise是异步编程的一种解决方案，传统的解决方案是回调函数和事件

Promise，是一个对象，可以获取异步操作的消息。

特点：
1. 对象的状态不受外界影响。
2. 一旦状态改变，就不会再变，任何时候都可以得到这个结果。

状态：
pending（进行中），fulfilled（已成功），rejected（已失败）

只有2种状态改变：
1. 从pending变为fulfilled（resolved），
2. 从pending变为rejected

### 基本用法

```
const promise = new Promise(function(resolve, reject) {
  // ... some code

  if (/* 异步操作成功 */){
    resolve(value);
  } else {
    reject(error);
  }
});

promise.then(function(value) {
  // success
}, function(error) {
  // failure
});
```

Promise实例生成以后，可用then方法分别指定resolved状态和rejected状态的回调

### 方法

	Promise.prototype.then()，为实例添加状态改变时的回调函数
	Promise.prototype.catch()，是.then(null, rejection)的别名，用于指定发生错误时的回调函数
	Promise.prototype.finally()，用于指定不管promise对象最后状态如何，都会执行的操作
	Promise.all()，用于将多个Promise实例，包装成一个新的Promise实例
	Promise.race()，同样是将多个promise实例，包装成一个新的promise实例
	Promise.resolve()，将对象转换为promise对象
	Promise.reject(), 会返回一个新的Promise实例，该实例的状态为rejected
	Promise.try()，
		不知道或者不想区分，函数f是同步函数还是异步操作，但是想用 Promise 来处理它。因为这样就可以不管f是否包含异步操作，都用then方法指定下一步流程，用catch方法处理f抛出的错误
		用法：Promise.resolve().then(f)


## Iterator和for……of对象

### Iterator

是一种接口，为各种不同的数据结构提供统一的访问机制，任何数据结构只要部署Iterator接口，就可以完成遍历操作，即依次处理该数据结构的所有成员

作用：
1. 为各种数据结构，提供一个统一的，简便的访问接口
2. 使得数据结构的成员能够按某种次序排列
3. ES6创造了一种新的遍历命令for...of循环

遍历过程：
1. 创建一个指针对象，指向当前数据结构的起始位置，即遍历器对象本质上，就是一个指针对象
2. 第一次调用指针对象的next方法，可以将指针指向数据结构的第一个成员
3. 第二次调用指针对象的next方法，指针就指向数据结构的第二个成员
4. 不断调用指针对象的next方法，直到它指向数据结构的结束位置

每一次调用next方法，都会返回数据结构的当前成员的信息，即返回一个包含value（当前成员）和done（true和false，表示是否结束）两个属性的对象。

原生具备了Iterrator接口的数据结构如下：
（即原生拥有Symbol.iterator属性）
1. Array
2. Map
3. Set
4. String
5. TypedArray
6. 函数的arguments对象
7. NodeList对象

#### 调用Iterator接口的场合

即默认调用Iterator接口

1. 解构赋值
2. 扩展运算
3. yield*
4. 数组的遍历会调用遍历器接口，任何接收数组作为参数的场合

	for...of
	Array.from()
	Map(), Set(), WeakMap(), WeakSet()（比如new Map([['a',1],['b',2]])）
	Promise.all()
	Promise.race()

#### 字符串的Iterator接口

	字符串是一个类似数组的对象，即具有Iterator接口

#### 方法

.next(),
.return(), for...of循环提前退出（通常因为出错或者有break）,
.throw(),配合Generator函数使用

### for...of循环

遍历所有数据结构的统一方法

一个数据结构只要部署了Symbol.iterator属性，就被视为具有 iterator 接口，就可以用for...of循环遍历它的成员。也就是说，for...of循环内部调用的是数据结构的Symbol.iterator方法
	

## Generator函数

Generator函数是一个状态机，封装了多个内部状态

执行Generator函数会返回一个遍历器对象，返回的遍历器对象可以依次遍历generator函数内部的每一个状态

特征：
1. function关键字与函数名之间有一个星号
2. 函数体内部使用yield表达式，定义不同的内部状态

### yield，暂停标志

yield，暂停执行

next，恢复执行

遍历器对象的next方法的运行逻辑如下：
1. 遇到yield表达式，就暂停执行后面的操作，并将紧跟在yield后面的表达式的值，作为返回的对象的value属性值
2. 下一次调用next方法时，再继续往下执行，直到遇到下一个yield表达式
3. 如果没有再遇到新的yield表达式，就一直运行到函数结束，直到return语句为止，并将return语句后面的表达式的值，作为返回的对象的value属性值
4. 如果该函数没有return语句，则返回的对象的value属性值为undefined

yield与return
1. 都能返回紧跟在语句后面的那个表达式的值


## Generator函数的异步应用

## async函数

## Class的基本用法

## Class的继承

## Decorator

## Module的语法

## Module的加载实现











