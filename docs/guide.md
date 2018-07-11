
# 入门

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [安装`react-values`](#%E5%AE%89%E8%A3%85react-values)
- [构建一个组件](#%E6%9E%84%E5%BB%BA%E4%B8%80%E4%B8%AA%E7%BB%84%E4%BB%B6)
- [介绍状态](#%E4%BB%8B%E7%BB%8D%E7%8A%B6%E6%80%81)
- [观察变化](#%E8%A7%82%E5%AF%9F%E5%8F%98%E5%8C%96)
- [设置默认值](#%E8%AE%BE%E7%BD%AE%E9%BB%98%E8%AE%A4%E5%80%BC)
- [受控制与不受控制](#%E5%8F%97%E6%8E%A7%E5%88%B6%E4%B8%8E%E4%B8%8D%E5%8F%97%E6%8E%A7%E5%88%B6)
- [传播props](#%E4%BC%A0%E6%92%ADprops)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


## 安装`react-values`

使用`yarn`或`npm`,简单: 

```bash
yarn add react-values
```

```bash
npm install --save react-values
```

你可以在你的代码前,导入一些 `react-values`的帮助函数

```js
import { BooleanValue, NumberValue } from 'react-values'
```

> 🤖如果你想导入`react-values`,通过 `<script>` 标记,您可以使用捆绑的构建:
>
> ```html
> <script src="https://unpkg.com/react-values/dist/react-values.min.js"></script>
> ```
>
> 这会暴露`ReactValues`以及它的组件到全局

## 构建一个组件

已安装`react-values`,现在您可以开始使用它构建组件. 例如,让我们用`<BooleanValue>`构建一个切换帮手. 

首先,使用一些样式 设置 非交互式的切换组件: 

```js
import React from 'react'
import styled from 'react-emotion'

const Track = styled('div')`
  position: relative;
  height: 25px;
  width: 50px;
  background-color: ${props => (props.on ? 'lightgreen' : 'lightgray')};
  border-radius: 999px;
  cursor: pointer;
`

const Thumb = styled('div')`
  position: absolute;
  transition: all 0.25s;
  height: 23px;
  width: 23px;
  top: 1px;
  left: ${props => (props.on ? '26px' : '1px')};
  background-color: white;
  border-radius: 999px;
  cursor: pointer;
`

const Toggle = () => (
  <Track>
    <Thumb />
  </Track>
)
```

您可以这样渲染: 


```js
<Toggle />
```

这样可行,但切换不是交互式的. 
它无法管理任何状态,所以它总是"关闭". 

## 介绍状态

为了使它成为有状态,让我们使用一个`<BooleanValue>`: 

```js
import { BooleanValue } from 'react-values'

const Toggle = () => (
  <BooleanValue>
    {({ value, toggle }) => (
      <Track on={value} onClick={toggle}>
        <Thumb on={value} />
      </Track>
    )}
  </BooleanValue>
)
```

现在你 切换操作`onchange`会 影响 `value`,进而影响到给`on`的值

当您单击它时,它使用提供的`toggle`变换以翻转布尔值. 一旦发生这种情况,`<BooleanValue>`重新渲染,你的切换现在 **开启** 了!

> 🤖布尔是相当简单的状态,所以`toggle()`变换是你真正能做到的. 但取决于您使用的是哪种类型值

>`react-values`将提供各种方便的转换. 看看[API参考](./reference.md)获取完整列表. 

这太棒了,这是一个切换工作!

但是我们还没有完成

当它改变时,没有办法观察切换,所以它并不是那么有用. 我们来解决这个问题

## 观察变化

要观察切换的状态,你可以传入一个`onChange`给`<BooleanValue>`: 

```js
const Toggle = ({ onChange }) => (
  <BooleanValue onChange={onChange}>
    {({ value, toggle }) => (
      <Track on={value} onClick={toggle}>
        <Thumb on={value} />
      </Track>
    )}
  </BooleanValue>
)
```

现在,您可以通过传入`onChange`处理函数来监听值的变化: 

```js
<Toggle onChange={value => ...} />
```

## 设置默认值

如果要与其他人共享此组件,他们可能会要求您能够以"开启"状态而不是"关闭"状态启动组件. 

为此,请使用`defaultValue` prop: 

```js
const Toggle = ({ defaultValue, onChange }) => (
  <BooleanValue defaultValue={defaultValue} onChange={onChange}>
    {({ value, toggle }) => (
      <Track on={value} onClick={toggle}>
        <Thumb on={value} />
      </Track>
    )}
  </BooleanValue>
)
```

人们可以这样做: 

```js
<Toggle
  defaultValue={true}
  onChange={value => ...}
/>
```

## 受控制与不受控制

可是等等!

如果有人想以"受控"的方式使用 切换,就像你可以使用 React的原生`<input>`和`<select>`组件

要做到这一点,你可以使用`value`prop


```js
const Toggle = ({ value, defaultValue, onChange }) => (
  <BooleanValue value={value} defaultValue={defaultValue} onChange={onChange}>
    {({ value, toggle }) => (
      <Track on={value} onClick={toggle}>
        <Thumb on={value} />
      </Track>
    )}
  </BooleanValue>
)
```

现在, 通过传递`value`或者`defaultValue`. 

渲染切换 的任何人都可以选择 是以"受控"方式 还是以"不受控制"的方式使用它

```js
<Toggle
  value={true}
  onChange={value => ...}
/>

<Toggle
  defaultValue={true}
  onChange={value => ...}
/>
```

## 传播props

最后一个改变,只是为了简单起见. 

你会注意到我们是如何明确地传递 props的,但为了使你的代码更简单,你可以直接用`传播{spread}`来代替:

```js
const Toggle = props => (
  <BooleanValue {...props}>
    {({ value, toggle }) => (
      <Track on={value} onClick={toggle}>
        <Thumb on={value} />
      </Track>
    )}
  </BooleanValue>
)
```

完

感谢`<BooleanValue>`组件为您处理状态管理,您已经在几行代码中实现了一个功能齐全的切换 - 它可以是受控的或不受控制的!

`react-values`处理的不仅仅是简单的布尔值. 

检查完整[API参考](./reference.md)看你能做的一切. 
