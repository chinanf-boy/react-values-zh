
<p align="center">
  <a href="#"><img src="./docs/images/banner.png" /></a>
</p>

<p align="center">
  一个<em>小小的</em>集合 关于, React 组合 components <br/>
   控制 <b>状态{state}</b> 来 影响 <b>渲染{render}</b>的 <b>道具{props}</b>.
</p>
<br/>

<p align="center">
  <a href="#%E4%B8%BA%E4%BB%80%E4%B9%88"><strong>为啥?</strong></a> ·
  <a href="#%E5%8E%9F%E7%90%86"><strong>原理</strong></a> ·
  <a href="#%E4%BE%8B%E5%AD%90"><strong>示例</strong></a> ·
  <a href="#%E6%96%87%E6%A1%A3"><strong>文档</strong></a> ·
  <a href="#%E5%B8%AE%E5%BF%99"><strong>帮忙!</strong></a>
</p>
<br/>

<p align="center">
  <a href="https://www.npmjs.com/package/react-values">
    <img src="https://img.shields.io/npm/dt/react-values.svg?maxAge=3600">
  </a>
  <a href="https://unpkg.com/react-values/dist/react-values.min.js">
    <img src="https://img.badgesize.io/https://unpkg.com/react-values/dist/react-values.min.js?compression=gzip&amp;label=react--values">
  </a>
  <a href="https://travis-ci.org/ianstormtaylor/react-values">
    <img src="https://travis-ci.org/ianstormtaylor/react-values.svg?branch=master">
  </a>
  <a href="./packages/react-values/package.json">
    <img src="https://img.shields.io/npm/v/react-values.svg?maxAge=3600&label=react-values&colorB=007ec6">
  </a>
  <a href="./License.md">
    <img src="https://img.shields.io/npm/l/react-values.svg?maxAge=3600">
  </a>
</p>
<br/>

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


`react-values`为您提供一组简单,可组合的帮助程序,使您可以构建更复杂,有状态的UI组件,如

- **切换,下拉列表,列表,复选框组,弹出窗口,工具提示**
- **toggles, dropdowns, lists, checkbox groups, popovers, tooltips**
- 或者您可以命名它!

它使用基于`render-prop`的 小API 来实现这一点,它提供了有用的转换`toggle`,`increment`,`filter`等等,取决于值的类型,所有都基于 JavaScripts 原生值类型...

-   `Any`值 提供简单的转换像`set`和`clear`. 
-   `Array`值 提供原生方法`push`,`pop`,`filter`等
-   `Boolean`值 提供`toggle`,当然我们也能重新实现100次. 
-   `Date`值 提供了非常有用的转换`setHours`和`incrementMonth`. 
-   `Map`值 提供原生方法`set`,`delete`和`clear`. 
-   `Number`值 提供`increment`和`decrement`,也在每个代码库中重写. 
-   `Set`值 提供原生方法`add`,`delete`和`clear`. 
-   `String`值 提供原生方法`concat`,`repeat`,`trim`等

这样可以避免您不断重写 相同的状态 管理逻辑,这样您就可以将组件集中在 **行为**和 **表示** 上. 

例如,这是一个`<Toggle>`的实现,通过使用`<BooleanValue>`了了几行就搞定: 

```js
import { BooleanValue } from 'react-values'

const Toggle = ({ value, defaultValue, onChange }) => (
  <BooleanValue value={value} defaultValue={defaultValue} onChange={onChange}>
    {({ value: on, toggle }) => (
      <Track on={on} onClick={toggle}>
        <Thumb on={on} />
      </Track>
    )}
  </BooleanValue>
)

const Track = styled.div`
  position: relative;
  height: 25px;
  width: 50px;
  background-color: ${props => (props.on ? 'lightgreen' : 'lightgray')};
  border-radius: 50px;
`

const Thumb = styled.div`
  position: absolute;
  left: ${props => (props.on ? '25px' : '0')};
  height: 25px;
  width: 25px;
  background-color: white;
  border-radius: 50px;
`
```

<br/>

### 为什么?

在使用 **React** 构建应用程序时,您最终会在此过程中构建大量有状态组件. 无论哪个级别的 UI组件,都会有,如 `切换,工具提示,复选框组,下拉列表` 等,还是在 应用程序级别的组件`模态框,弹出窗口,排序,过滤` 等. 

在此过程中,无论是否使用`this.setState`，你最终都会重新实现 折磨般的状态的处理逻辑的运行 - 或者通过一遍又一遍地构建相同的行为创建者. 还有可能为了使您的组件 在 您的应用程序中可以很好地重用,您会使用`value`要么`defaultValue`来增强处理"受控"和"不受控制"的使用. 

为了使事情更容易管理,你重新发明了常见的转换函数`open`,`close`,`toggle`,`increment`,`decrement`等等,在许多不同的组件. 如果您正在与团队合作,那么您最终会在 整个代码库 中以 不同的方式 完成所有这些一样工作. 

最后,您现在 维护的逻辑 比 **必要的** 多得多,在许多不同的地方仅仅是略微不同方式的复制. 您的应用程序包的大小越来越大. 

`react-values`用一些原则解决所有的这些......

<br/>

### 原理

1.  **利用渲染道具{render props}.** 它使用基于`render-prop`的API,通过灵活的`function-as-children`模式向您展示 其状态 和 一些 方便的转换函数. 

2.  **遵循React的惯例.** 它的组件遵循 `React` 自己的命名约定,使用熟悉的概念`value/defaultValue`. 这使得插入现有代码库或框架非常容易. 

3.  **遵循JavaScript的约定.** 它暴露了JavaScript熟悉的内置方法,如`setDate/setHours`,`push/pop`,`filter`,`concat`等,以避免重新发明轮子,并强迫您不断阅读文档. 

4.  **非常轻巧.** 它非常轻巧 (树抖动) ,大多数组件只有几百字节,因此您甚至可以从面向公众的组件库中导入它. 

5.  **优先考虑方便.** 它旨在提供方便的功能,如`increment`,`toggle`和聪明的像`incrementDate`,`decrementMonth`,因此您可以在几行代码中构建复杂的交互. 

<br/>

### 例子

了解您的使用方法`react-values`,看看几个例子: 

-   [**基本切换**](https://ianstormtaylor.github.io/react-values/#/basic-toggle)- 用一个`Boolean`创建一个简单的切换组件. 
-   [**可重复使用的切换**](https://ianstormtaylor.github.io/react-values/#/reusable-toggle)- 展示如何将其切换为您自己的UI工具包中的受控组件. 
-   [**计数器**](https://ianstormtaylor.github.io/react-values/#/counter)- 使用简单计数器`Number`及其便利性转变. 
-   [**时间选择器**](https://ianstormtaylor.github.io/react-values/#/time-picker)- 一个更复杂的时间选择器组件,使用`Date`及其便利性转变. 
-   [**过滤**](https://ianstormtaylor.github.io/react-values/#/filtering)- 一个基本的`String`用于过滤列表的值. 
-   [**复选框设置**](https://ianstormtaylor.github.io/react-values/#/checkbox-set)- 用一个`Set`跟踪复选框组. 
-   [**简单的工具提示**](https://ianstormtaylor.github.io/react-values/#/tooltip)- 一个简单的工具提示实现为`Boolean`. 
-   [**简单模态框**](https://ianstormtaylor.github.io/react-values/#/modal)- 一个简单的模式实现为`Boolean`. 

如果您有一个显示常见用例的示例,请拉取请求!

<br/>

### 文档

如果你正在使用`react-values`这是第一次看看[入门](./docs/guide.md)指导您熟悉它的工作原理. 一旦你完成了,你可能想要查看全部[API参考](http://docs.slatejs.org/react-values-core). 

-   [**入门**](./docs/guide.md)
    -   [安装`react-values`](./docs/guide.md#installing-react-values)
    -   [构建组件](./docs/guide.md#building-a-component)
    -   [介绍状态](./docs/guide.md#introducing-state)
    -   [观察变化](./docs/guide.md#observing-changes)
    -   [设置默认值](./docs/guide.md#settings-defaults)
    -   [受控制与不受控制](./docs/guide.md#controlled-vs-uncontrolled)
    -   [传播 props](./docs/guide.md#spreading-props)
-   [**参考**](./docs/reference.md)
    -   [`<AnyValue>`](./docs/reference.md#anyvalue)
    -   [`<ArrayValue>`](./docs/reference.md#arrayvalue)
    -   [`<BooleanValue>`](./docs/reference.md#booleanvalue)
    -   [`<DateValue>`](./docs/reference.md#datevalue)
    -   [`<MapValue>`](./docs/reference.md#mapvalue)
    -   [`<NumberValue>`](./docs/reference.md#numbervalue)
    -   [`<SetValue>`](./docs/reference.md#setvalue)
    -   [`<StringValue>`](./docs/reference.md#stringvalue)

即使这还不够,你也可以,[阅读源码](./src),这很简单!

<br/>

### 帮忙

非常·欢迎!

看看[贡献指示](./Contributing.md)了解更多信息!

板岩是[MIT许可](./License.md). 
