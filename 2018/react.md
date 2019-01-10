# 深入React技术栈

## 1. react世界

### Virtual DOM

把真实的DOM转换成JavaScript对象树

ReactDOM，每次数据更新后，重新计算virtual DOM，并和上一次生成的virtual DOM做对比，对发生变化的部分做批量更新

优点：方便和其它平台集成，比如react-native是基于Virtual DOM渲染出原生控件，因为React组件可以映射为对应的原生控件。

React是通过创建与更新虚拟元素（Virtual element）来管理整个Virtual DOM的。

### JSX

JSX使用类XML语法，可任意嵌套，可以像HTML一样清晰的看到DOM树状结构及其属性。

语法注意

* 定义标签时，只允许被一个标签包裹
* 标签一定要闭合
* DOM元素对应小写字母
* 组件元素对应大写字母
* 注释，在组件的子元素位置使用注释要用{}包起来
* DOCTYPE，通过构造一个保存HTML的变量，将DOCTYPE与整个HTML标签渲染后的结果串联起来
* class属性修改为className
* for属性修改为htmlFor
* Boolean属性值默认设置为true，false必须使用表达式
* 自定义属性，使用data-前缀
* 属性值的表达式使用{}，
* React会将所有要显示到DOM的字符串转义，防止XSS

### 组件

组件使用render方法，核心函数之一

Web Component，通过定义自定义元素的方式来统一组件。每个自定义元素可以定义自己对外提供的属性，方法，事件，内部专注于实现功能来完成对组件的封装。

Web Component组成部分：

1. HTML Tempalte
2. Custom Elements
3. Shadow DOM
4. HTML Imports

### React组件

React组件接收参数或者自身状态，一旦接收到的参数或者自身状态有所改变，React组件就会执行相应的生命周期方法，最后渲染。

React组件由组件的构建方式，组件内的属性状态与生命周期方法组成

#### 有状态组件

#### 无状态组件

使用无状态函数构建的组件称为无状态组件。

无状态组件只传入props和context

无创建组件始终保持一个实例

#### 数据流

自顶向下单向流动，即从父组件到子组件。


#### props

props是React用来让组件之间互相联系的一种机制，就像方法的参数一样。

若把组件看成一个函数，props作为参数。

组件的props来自于默认属性或者通过父组件传递而来

children，代表组件的子组件集合

props传入的是组件时，称为component props，定义组件的某一个prop，让其具备多种类型，来做到简单配置和自定义配置组合在一起的效果，

#### propTypes

用于规范props的类型与必需的状态

若定义流propTypes，就会对组件的props值的类型作检查。

类型检查：

* 函数类型，propTypes.func
* 布尔类型，propTypes.bool

#### state

state只关心每个组件自己内部的状态，这些状态只能在组件内改变。

若把组件看成一个函数，state作为内部参数

setState，组件会尝试重新渲染，异步操作，一个生命周期内所有的setState方法会合并操作

#### 生命周期

React组件的生命周期分为挂载，渲染和卸载。

##### 当组件挂载或卸载时

componentWillMount, render之前执行

componentDidMount，render之后执行

componentWillUnmount， 卸载前状态

##### 当组件接收新数据时，即更新

更新过程是指父组件向下传递props或者组件自身执行setState方法时发生的一系列更新动作

componentWillReceiveProps，

shouldComponentUpdate，接收需要更新的props和state

componentWillUpdate，更新过程中渲染前

componentDidUpdate，更新过程中渲染后

### ReactDOM

findDOMNode，获取真正的DOM元素，只对挂载的组件有效

render，

refs，React组件中特殊的prop，可以附加到任何一个组件上。当组件被调用时会新建一个该组件的实例，而refs就会指向这个实例，可获取子组件的引用

this，获取当前组件


## 漫谈React

### 事件系统

### 表单
 
### 样式处理

#### CSS Modules

解决的问题：
 css样式导入与导出

遇到的问题：
1. 全局污染
2. 命名混乱
3. 依赖管理不彻底
4. 无法共享变量
5. 代码压缩不彻底

模块化方案：

```
:imoport
:export
```
compose组合样式

### 组件间通信

1. 父组件向子组件通信
	
	props

2. 子组件向父组件通信

	回调函数
	自定义事件机制

3. 没有嵌套关系的组件之间通信

	EventEmitter（利用全局对象来保存事件，用广播的方式去处理事件）

4. 跨级组件通信

	context

### 组件间抽象

#### mixin

用于组合公共组件，实现继承

##### 高阶组件

高阶函数：这种函数接受函数作为输入，或者是输出一个函数

高阶组件：接受react组件作为输入，输出一个新的React组件

实现方法：

1. 属性代理，高阶组件通过被包裹的react组件来操作props

2. 反向继承，高阶组件继承于被包裹的react组件

	特点：
	渲染劫持，
	控制state

### 组件间性能优化

#### 纯函数

构成：
1. 给定相同的输入，总是返回相同的输出
2. 过程没有副作用
3. 没有额外的状态依赖

#### PureRender

PureRender中的Pure指的就是组件满足纯函数的条件，即组件的渲染是被相同的props和state渲染进而得到相同的结果

#### Immutable Data
 
Immutable Data就是一旦创建，就不能再更改的数据

Immutable 实现原理是持久化的数据结构，即使用旧数据创建新数据时，要保证旧数据同时可用而且不变。

为了避免深拷贝把所有节点都复制一篇带来的性能损耗，Immutable使用了结构共享，即如果对象树中一个节点发生变化，只修改这个节点和受它影响的父节点，其他节点则进行共享。

重要数据结构说明：
1. Map，键值对集合，对应于Object
2. List，有序可重复的列表，对应于Array
3. ArraySet，无序并且不可重复的列表

优点：
1. 降低“可变”带来的复杂度
2. 节省内存
3. 撤销/重做，复制/粘贴，实现简单
4. 并发安全
5. 拥抱函数式编程

缺点：
1. 与原生对象很难区分
2. 

### 动画

### 测试

Jest特点：
1. 自动找到测试
2. 自动mock模拟依赖包，达到单元测试的目的
3. 并不需要真实DOM环境执行，而是JSDOM模拟的DOM
4. 多进程并行执行测试

#### 自动化测试

## 3. 解读React源码

### 目录介绍

addons, 包含一系列的工具方法插件，

isomorphic,包含一系列同构方法

shared，包含一些公用或者常用方法

test，包含一些测试方法

core/test，包含一些边界错误的测试用例

renderes，React代码的核心部分，包含了大部分功能实现

renderes，分为dom和shared

	DOM（client，server，shared）
	shared（event，reconciler）


Virtual DOM，是JavaScript对象

主要包括Virtual DOM模型（Virtual DOM机制是将更新的数据实时反应到UI上），生命周期的维护，性能高效的diff算法和Virtual DOM展示为原生DOM的patch方法

当数据更新时，会通过diff寻找到需要变更的DOM节点，并只对变化的部分进行实际的浏览器DOM更新，而不是重新渲染整个DOM树。

### Virtual DOM模型

构建Virtual DOM模型，所需要元素：标签名，节点属性（包含样式，属性，事件），子节点，标识id

Virtual DOM称为ReactNode，类型为：

* ReactElement，
	* ReactComponentElement
	* ReactDOMElament

* ReactFragment，

* eactText

Virtunal DOM模型通过createElement创建虚拟元素。

### 生命周期

React的主要是通过构建可复用组件来构建用户界面。

所谓组件，其实就是有限状态机，通过状态渲染对应的界面，且每个组件都有自己的生命周期，它规定了组件的状态和方法需要在哪个阶段改变和执行。

有限状态机，表示有限个状态以及在这些状态之间的转移和动作等行为的模型。一般通过状态，事件，转换和动作来描述有限状态机。

通过管理状态实现对组件的管理。


#### 无状态组件

只接收props渲染生成DOM结构，没有状态变化

### duff算法

计算一棵树形结构转换成另一棵树形结构的最少操作。

传统diff算法：通过循环递归对节点进行依次对比。

React将Virtual DOM树转换成actual DOM树的最少操作的过程称为调和。

1. diff策略

	1. Web UI中DOM节点跨层级的移动操作特别少，可以忽略不计
	2. 拥有相同类的两个组件将会生成相似的树形结构，拥有不同类的两个组件将会生成不同的树形结构
	3. 对于同一层级的一组子节点，它们可以通过唯一id进行区分

2. tree diff

	React对树的算法进行了简洁明了的优化，即对树进行分层比较，两棵树只会对同一层次的节点进行比较

3. component diff

	如果是同一类型的组件，按照原策略继续比较Virtual DOM树即可
	如果不是，则将该组件判断为dirty component，从而替换整个组件下的所有子节点
	对于同一类型的组件，有可能其Virtual DOM没有任何变化。

4. element diff

	当节点处于同一层级时，diff提供了3种节点操作，分别为INSERT_MARKUP（插入），MOVE_EXISTING（移动）和REMOVE_NODE（删除）

	INSERT_MARKUP，新的组件类型不在旧集合里，即全新的节点，需要对新节点执行插入操作

	MOVE_EXISTING， 旧集合中有新组件类型，而且element是可更新的类型，

	REMOVE_NODE，旧组件类型，在新集合里也有，但对应的element不同则不能直接复用和更新，需要执行删除操作。


优化策略：允许开发者对同一层级的同组子节点，添加唯一key进行区分。

### React Patch

Patch，就是将tree diff计算出来的DOM差异队列更新到真实的DOM节点上，最终让浏览器能够渲染出更新的数据。

差异队列实现


## 4. 认识Flux架构模式

fetch API，由WHATWG提出的新一代浏览器Ajax请求标准，目前已经获得主流浏览器的支持

fetch的主要特点是运用promise来对请求作了包装，

### React独立结构

### MV * 与Flux

#### MVC

MVC是一种架构设计模式，通过关注数据界面分离，来鼓励改进应用程序结构。

MVC强制将业务数据（Model）与用户界面（View）隔离，用控制器（Controller）管理逻辑和用户输入。

MVC模式中的3种角色：

1. Model

Model负责保存应用数据，和后端交互同步应用数据或者校验数据。

主要与业务数据有关，与应用内交互状态无关

2. View

View是Model的可视化表示，表示当前状态的视图。

前端View负责构建和维护DOM元素

3. Controller

负责连接View和Model，Model的任何改变会应用到View中，View的操作会通过Controller应用到Model中

MVC缺点：
项目越大后，数据流向很混乱

#### MVVM

VM（ViewModel）代替了C（Controller），其关键的改进是数据绑定

View的数据状态发生变化可以直接影响VM，反之亦然，angularJS的核心特色之一。



#### Flux的解决方案

Flux提出主要是针对现有前端MVC框架的局限总结出来的一套基于dispatcher的前端应用架构模式。

Flux的核心思想就是数据和逻辑永远单向流动

### Flux的基本概念

3大组成部分：

1. dispatcher，负责分发事件

	register方法用来注册一个监听器，而dispatch方法用来分发一个action

	action是一个普通的js对象，一般包含type，payload等字段，用于描述一个事件以及需要改变的相关数据

2. store，负责保存数据，同时响应事件并更新数据

	store负责保存数据，并定义修改数据的逻辑，同时调用dispatcher的register方法将自己注册为一个监听器。

	store对外只暴露getter，只能读取store中的数据而不能进行任何修改

3. controller-view

	主要进行store与react组件（即view层）之间的绑定，定义数据更新以及传递的方式

4. view，负责订阅store中的数据，并使用这些数据渲染相应的页面	

	在flux中，view除了显示界面，还约定如果界面操作需要修改数据，则必须使用dispatcher分发一个action

5. actionCreater

	用来创造action的
	

### Flux应用实例

### 解读Flux

Flux的中心化控制让所有的请求与改变都只能通过action发出，统一由dispatcher来分配。

优点是保持高度简洁，不需要关心太多的逻辑，只需要关心传入的数据，中心化还控制了所有数据，发生问题时可以方便查询。

缺点：冗余代码太多

## 5. 深入Redux应用架构

三大原则：
1. 单一数据源

	使用单一数据源的好处在于整个应用状态都保存在一个对象中，这样我们随时可以提取出整个应用的状态进行持久化。

2. 状态是只读的

	reducer的功能是根据当前触发的action对当前应用的状态（state）进行迭代，这里并没有直接修改应用的状态，而是返回了一份全新的状态

3. 状态修改均由纯函数完成

### 简介

核心API：createSore，

#### createSore，

包含4个方法：
1. getState()，获取store中当前的状态
2. dispatch(action)，分发一个action，并返回这个action，唯一能改变store中数据的方式
3. subscribe(listener)，注册一个监听者，它在store发生变化时被调用
4. replaceReducer(nextReducer)，更新当前store里的reducer，只在开发模式中调用该方法

#### react-redux，

redux官方提供的react绑定，为什么存在？前端架构趋势，尽量做到平台无关

提供了一个组件和一个api绑定redux和react进行绑定，

`<Provider/>`，接受一个store作为props，是整个redux应用的顶层组件

connect()，提供了在整个React应用的任意组件中获取store中数据的功能

### middleware

分类处理action的机会，

Redux中一个简单的同步数据流动场景，点击button后，在回调中分发一个action，reducer收到action后，更新state并通知view重新渲染。

柯里化函数是一种使用匿名单参数函数来实现多参数函数的方法。

### redux异步流

1. redux-thunk

Thunk函数实现上就是针对多参数的currying以实现对函数的惰性求值。任何函数，只要参数有回调函数，就能写成Thunk函数的形式。

Thunk 函数替换的不是表达式，而是多参数函数，将其替换成单参数的版本，且只接受回调函数作为参数


2. redux-promise

3. redux-composable-fetch

middle处理复杂异步流

1. 轮询
2. 多异步串联
3. 

### redux与路由

路由的基本原理：即是保证View和URL同步，而View可以看成是资源的一种表现

### Redux应用实例

## 6. Redux高阶运用

### 高阶reducer

reducer是纯函数，职责是根据previousState和action计算出新的state

高阶函数是指将函数作为参数或者返回值的函数

高阶reducer就是指将reducer作为参数或者返回值的函数

### redux与表单

1. redux-form-utils
2. redux-form

## 7. React服务端渲染

服务端渲染，即前端代码可以在服务端作渲染，进而达到在同步请求HTML时，直接返回渲染好的页面

优点：
1. 利于SEO
2. 加速首屏渲染
服务端和客户端可以共享某些代码，避免重复定义

ReactDom，react渲染到DOM中的方法

React.renderToString，把react元素转成一个HTML字符串并在服务端标识reactid

React.renderToStaticMarkup，简化版本的renderToString

## 8. 玩转React可视化





















