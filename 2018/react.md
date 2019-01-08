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

### 组件间通信

### 组件间抽象

### 组件间性能优化

### 动画

### 测试

## 解读React源码

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

### Virtual DOM模型

构建Virtual DOM模型，所需要元素：标签名，节点属性（包含样式，属性，事件），子节点，标识id

Virtual DOM称为ReactNode，类型为：

* ReactElement，
	* ReactComponentElement
	* ReactDOMElament

* ReactFragment，

* eactText













