
# 入门

-   [安装`react-values`](#installing-react-values)
-   [构建组件](#building-a-component)
-   [介绍国家](#introducing-state)
-   [观察变化](#observing-changes)
-   [设置默认值](#settings-defaults)
-   [受控制与不受控制传播道具](#controlled-vs-uncontrolled)
-   [安装](#spreading-props)

## 安装`react-values`

使用纱线或Npm,只需: `react-values`然后,您可以将其任何助手导入您的代码库: 

```bash
yarn add react-values
```

```bash
npm install --save react-values
```

🤖如果你想进口

```js
import { BooleanValue, NumberValue } from 'react-values'
```

> 用一个`react-values`标记,您可以使用捆绑的构建: `<script>`这将揭露
>
> ```html
> <script src="https://unpkg.com/react-values/dist/react-values.min.js"></script>
> ```
>
> 全球及其组件. `ReactValues`构建组件

## 同

已安装,现在您可以开始使用它构建组件. `react-values`例如,让我们用. 构建一个切换帮手. `<BooleanValue>`首先,使用一些样式设置非交互式切换组件: 

您可以这样渲染: 

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

这样可行,但切换不是交互式的. 

```js
<Toggle />
```

它无法管理任何状态,所以它总是"关闭". 

## 介绍国家

为了使它成为有状态,让我们使用一个`<BooleanValue>`来自的助手`react-values`: 

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

现在你的切换推导出它`on`来自国家`value`道具传递给了`<BooleanValue>`零件. 

当您单击它时,它使用提供的`toggle`变换以翻转布尔值. 一旦发生这种情况,`<BooleanValue>`重新渲染,你的切换现在开启了!

> 🤖布尔是相当简单的状态,所以`toggle()`变换是你真正能做到的. 但取决于您使用的是哪种类型的价值`react-values`将提供各种方便的转换. 看看[API参考](./reference.md)获取完整列表. 

这太棒了,这是一个切换工作!

但是我们还没有完成......当它改变时,没有办法观察切换,所以它并不是那么有用. 我们来解决这个问题......

## 观察变化

要观察切换的状态,你可以传入一个`onChange`支持`<BooleanValue>`: 

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

现在,您可以通过传入来侦听切换的更改`onChange`处理: 

```js
<Toggle onChange={value => ...} />
```

## 设置默认值

如果要与其他人共享此组件,他们可能会要求您能够以"开启"状态而不是"关闭"状态启动组件. 

为此,请使用`defaultValue`支柱: 

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

## 受控制与不受控制可是等等!

如果有人想以"受控"的方式使用切换,就像你可以使用React的原生一样和`<input>`组件. `<select>`要做到这一点,你可以使用

支柱: `value`现在任何渲染切换的人都可以通过传递任何一个来选择是以"受控"方式还是以"不受控制"的方式使用它. 

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

或者a`value`: `defaultValue`传播道具

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

## 最后一个改变,只是为了简单起见. 

你会注意到我们是如何明确地传递道具的,但为了使你的代码更简单,你可以直接将它们传播到代替: `<BooleanValue>`就这样!

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

感谢

帮助组件为您处理状态管理,您已经在几行代码中实现了一个功能齐全的切换 - 它可以是受控的或不受控制的!`<BooleanValue>`和

处理的不仅仅是简单的布尔值. `react-values`检查完整[API参考](./reference.md)看你能做的一切. 
