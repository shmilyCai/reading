# javascript语言精粹

## 总结

这本书大多数都是基础知识，不想总结的


## 对象

对象是属性的容器，其中每个属性都拥有名字和值

对象通过引用来传递，它们永远不会被复制

每个对象都连接到一个原型对象，并且它可以从中继承属性，所有通过对象字面量创建的对象都连接到Object.prototype，zhesh是js中的原型定义

原型连接只有在检索值的时候才被用到，如果我们尝试去获取对象的某个属性值，但该对象没有此属性名，那么js会试着从原型对象中获取属性值。如果那个原型对象也没有改属性，那么再从它的原型中寻找

请注意原型链中的任何属性都会产生值

delete运算符可以用来删除对象的属性，如果对象包含该属性，那么该属性就会被删除


## Array

### 属性

.length，

.prototype，

### 方法

Array.form()，

Array.isArray(),

Array.of()，

.concat(item...)，产生一个新数组，包含一份array的浅复制并把一个或者多个参数item附加在其中

.copyWithin()

.entries()

.every()

.fill()

.filter()

.find()

.findIndex()

.forEach()

.includes()

.indexOf()

.join(separator)，把一个array构造成一个字符串，接着用一个separator分隔符把他们连接在一起，默认separator是逗号“，”

.keys()

.lastIndexOf()

.map()

.pop()，移除array中的最后一个元素并返回该元素

.push(item...)，把一个或者多个参数item附加到一个数组的尾部

.reduce()

.reverse()，反转array里的元素的顺序

.shift()，移除数据array中的第一个元素并返回该元素

.slice()，对array中的一段做浅复制

.some()

.sort()，对array中的内容进行排序

.splice(start, deleteCount, item...)，从array中移除一个或者多个元素，并用item替换它们，最主要的用处是从一个数组中删除元素

.toString()

.unshift()，把元素添加到数组中，把item插入到array的开始部分

.values()

## Function

### 属性

.arguments
.caller
.length
.prototype
.name

### 方法

.apply(thisArg, argArray)，apply调用function，传递一个会被绑定到this上的对象和一个可选的数组作为参数

.bind()

.call()

.toSource()

.toString()

## Number

toExponential(fractionDigits)，把number转换成一个指数形式的字符串

toFixed(fractionDigits)，把number转换成为一个十进制数形式的字符串

toPrecision(precision)，把number转换成为一个十进制数形式的字符串

toString(radix)，把number转换成为一个字符串

## Object

### 属性

._proto_

.constructor

### 方法

.has

.isProperty()

.isPrototypeOf()

.setPrototypeOf(),

.hasOwnProperty(name)，如果object包含一个名为name的属性，那么hasOwnProperty方法返回true，原型链中的同名属性是不会被检查的

## RegExp

.exec(string)，是使用正则表达式的最强大防范，成功的匹配regexp和字符串string，返回一个数组

.test(string)，使用正则表达式的最简单防范，如果该regexp匹配string，返回true，否则，返回false

## String

### 属性

.prototype

.length

### 方法

.formCharCode()

fromCodePoint()

.charAt(pos)，在string中pos位置出的字符串，如果pos小于0或者大于等于字符串的长度，则返回空字符串

.charCodeAt(pos)，同charAt意义，返回的是以整数形式表示的在string中的pos位置处的字符的字符码位

.concat()

.endsWith()

.includes()

.indeOf(searchString， position)，在string内查找另一个字符串searchString，找到返回第一个匹配的字符的位置，否则返回-1

lastIndexOf(searchString， position)，从字符串的末尾开始查找，与indexof类似

.localCompare(that)，比较两个字符串，如果string比字符串that小，结果为负数，如果相等，结果为0

.match(regexp)，让字符串和一个正则表达式进行匹配

.padEnd()

.padStart()

.repeat()

.replace(searchValue, replaceValue)，对string进行查找和替换操作，并返回一个新的字符串

.search(regexp)，接受一个正则表达式作为参数而不是一个字符串，与indexof类似

.slice(start, end)，复制string的一部分来构造一个新的字符串

.split(separator, limit)，把string分割成片段来创建一个字符串数组

.subString(start, end)，与slice一样

.toLocalLowerCase()，返回一个新的字符串，使用本地化的规则把这个string中的所有字母转换为小写字母
	
.toLocalUpperCase()，返回一个新字符串，使用本地化的规则把这个string中的所有字母转换为大写格式

.toLowerCase()，返回一个新的字符串，将string中的所有字母都被转换为小写字母

.toUpperCase()，返回一个新的字符串，将string中的所有字母都被转换为大写字母

.formCharCode(char...)，根据一串数字编码返回一个字符串

.trim()

.trimRight()

.trimLeft()

.valuesOf()

.raw()























