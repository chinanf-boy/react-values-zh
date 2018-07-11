
# API参考

-   [`<AnyValue>`](#anyvalue)
-   [`<ArrayValue>`](#arrayvalue)
-   [`<BooleanValue>`](#booleanvalue)
-   [`<DateValue>`](#datevalue)
-   [`<MapValue>`](#mapvalue)
-   [`<NumberValue>`](#numbervalue)
-   [`<SetValue>`](#setvalue)
-   [`<StringValue>`](#stringvalue)

* * *

### `<AnyValue>`

该`<AnyValue>`组件是最常见的组件,它是所有其他组件的基础. 

它需要一个`value`要么`defaultValue`和一个`onChange`处理程序. 取决于你是否使用`value`要么`defaultValue`,分别名为"受控"或"不受控制". 

```js
<AnyValue
  value={Any|undefined}
  defaultValue={Any|undefined}
  onChange={Function}
>
  {({
    value,
    set,
    clear,
    reset,
  }) => (
    ...
  )}
</AnyValue>
```

| 渲染props    | 类型                      | 描述                               |
| ------- | ----------------------- | -------------------------------- |
| `value` | `Any`                   | 状态的当前 值 .                         |
| `set`   | `Function` `set(value)` | 将值设置为新状态.                        |
| `clear` | `Function` `clear()`    | 将值设置为`undefined`.                |
| `reset` | `Function` `reset()`    | 将值重置为其初始值`value/defaultValue`状态.  |

* * *

### `<ArrayValue>`

一个`Array`值. 

```js
<ArrayValue
  value={Array|undefined}
  defaultValue={Array|undefined}
  onChange={Function}
>
  {({
    value,
    set,
    reset,
    concat,
    fill,
    filter,
    map,
    pop,
    push,
    reverse,
    shift,
    slice,
    sort,
    splice,
    unshift,
  }) => (
    ...
  )}
</ArrayValue>
```

| 渲染props      | 类型                                            | 描述                                                                                                                    |
| --------- | --------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| `value`   | `Array`                                       | 当前数组值.                                                                                                                |
| `set`     | `Function` `set(array)`                       | 将值设置为新状态.                                                                                                             |
| `clear`   | `Function` `clear()`                          | 将值设置为`[]`空数组.                                                                                                         |
| `reset`   | `Function` `reset()`                          | 将值重置为其初始值`value/defaultValue`状态.                                                                                       |
| `first`   | `Any`                                         | 当前数组值中的第一个元素.                                                                                                         |
| `last`    | `Any`                                         | 当前数组值中的最后一个元素.                                                                                                        |
| `concat`  | `Function` `concat(...values)`                | 运行[`Array.concat`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat).    |
| `fill`    | `Function` `fill(value)`                      | 运行[`Array.fill`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/fill).        |
| `filter`  | `Function` `filter(callback)`                 | 运行[`Array.filter`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter).    |
| `flat`    | `Function` `flat(depth)`                      | 运行[`Array.flat`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flat).        |
| `flatMap` | `Function` `flatMap(callback)`                | 运行[`Array.flatMap`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flatMap).  |
| `map`     | `Function` `map(callback)`                    | 运行[`Array.map`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map).          |
| `pop`     | `Function` `pop()`                            | 运行[`Array.pop`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop).          |
| `push`    | `Function` `push(...values)`                  | 运行[`Array.push`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push).        |
| `reverse` | `Function` `reverse()`                        | 运行[`Array.reverse`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse).  |
| `shift`   | `Function` `shift()`                          | 运行[`Array.shift`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift).      |
| `slice`   | `Function` `slice(begin, end)`                | 运行[`Array.slice`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice).      |
| `sort`    | `Function` `sort(comparator)`                 | 运行[`Array.sort`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort).        |
| `splice`  | `Function` `splice(start, remove, ...values)` | 运行[`Array.splice`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice).    |
| `unshift` | `Function` `unshift(...values)`               | 运行[`Array.unshift`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift).  |

* * *

### `<BooleanValue>`

一个`Boolean`值. 

```js
<BooleanValue
  value={Boolean|undefined}
  defaultValue={Boolean|undefined}
  onChange={Function}
>
  {({
    value,
    set,
    clear,
    reset,
    toggle,
  }) => (
    ...
  )}
</BooleanValue>
```

| 渲染props     | 类型                        | 描述                               |
| -------- | ------------------------- | -------------------------------- |
| `value`  | `Boolean`                 | 当前的布尔值.                          |
| `set`    | `Function` `set(boolean)` | 将值设置为新状态.                        |
| `clear`  | `Function` `clear()`      | 将值设置为`false`.                    |
| `reset`  | `Function` `reset()`      | 将值重置为其初始值`value/defaultValue`状态.  |
| `toggle` | `Function` `toggle()`     | 将布尔值设置为其相反值.                     |

* * *

### `<DateValue>`

一个`Date`值. 

```js
<DateValue
  value={Date|undefined}
  defaultValue={Date|undefined}
  onChange={Function}
>
  {({
    value,
    set,
    clear,
    reset,
    date,
    hours,
    milliseconds,
    minutes,
    month,
    seconds,
    year,
    setDate,
    setHours,
    setMilliseconds,
    setMinutes,
    setMonth,
    setSeconds,
    setYear,
    incrementDate,
    incrementHours,
    incrementMilliseconds,
    incrementMinutes,
    incrementMonth,
    incrementSeconds,
    incrementYear,
    decrementDate,
    decrementFullYear,
    decrementHours,
    decrementMilliseconds,
    decrementMinutes,
    decrementMonth,
    decrementSeconds,
  }) => (
    ...
  )}
</DateValue>
```

| 渲染props                    | 类型                                        | 描述                                                                                                                                        |
| ----------------------- | ----------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| `value`                 | `Date`                                    | 当前日期值.                                                                                                                                    |
| `set`                   | `Function` `set(date)`                    | 将值设置为日期.                                                                                                                                  |
| `clear`                 | `Function` `clear()`                      | 将值设置为`new Date()`.                                                                                                                        |
| `reset`                 | `Function` `reset()`                      | 将值重置为其初始值`value/defaultValue`状态.                                                                                                           |
| `year`                  | `Number`                                  | 目前的状态[`value.getFullYear()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getFullYear).          |
| `month`                 | `Number`                                  | 目前的状态[`value.getMonth()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getMonth).                |
| `date`                  | `Number`                                  | 目前的状态[`value.getDate()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getDate).                  |
| `hours`                 | `Number`                                  | 目前的状态[`value.getHours()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getHours).                |
| `minutes`               | `Number`                                  | 目前的状态[`value.getMinutes()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getMinutes).            |
| `seconds`               | `Number`                                  | 目前的状态[`value.getSeconds()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getSeconds).            |
| `milliseconds`          | `Number`                                  | 目前的状态[`value.getMilliseconds()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getMilliseconds).  |
| `setYear`               | `Function` `setYear(n)`                   | 运行[`Date.setFullYear`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/setFullYear).                |
| `setMonth`              | `Function` `setMonth(n)`                  | 调用错误修复版本[`Date.setMonth`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/setMonth).                |
| `setDate`               | `Function` `setDate(n)`                   | 运行[`Date.setDate`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/setDate).                        |
| `setHours`              | `Function` `setHours(n)`                  | 运行[`Date.setHours`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/setHours).                      |
| `setMinutes`            | `Function` `setMinutes(n)`                | 运行[`Date.setMinutes`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/setMinutes).                  |
| `setSeconds`            | `Function` `setSeconds(n)`                | 运行[`Date.setSeconds`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/setSeconds).                  |
| `setMilliseconds`       | `Function` `setMilliseconds(n)`           | 运行[`Date.setMilliseconds`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/setMilliseconds).        |
| `incrementYear`         | `Function` `incrementYear(n = 1)`         | 增加值的年份`n`.                                                                                                                                |
| `incrementMonth`        | `Function` `incrementMonth(n = 1)`        | 增加值的月份`n`.                                                                                                                                |
| `incrementDate`         | `Function` `incrementDate(n = 1)`         | 增加值的日期`n`.                                                                                                                                |
| `incrementHours`        | `Function` `incrementHours(n = 1)`        | 增加值的小时数`n`.                                                                                                                               |
| `incrementMinutes`      | `Function` `incrementMinutes(n = 1)`      | 增加值的分钟数`n`.                                                                                                                               |
| `incrementSeconds`      | `Function` `incrementSeconds(n = 1)`      | 增加值的秒数`n`.                                                                                                                                |
| `incrementMilliseconds` | `Function` `incrementMilliseconds(n = 1)` | 增加值的毫秒数`n`.                                                                                                                               |
| `decrementYear`         | `Function` `decrementYear(n = 1)`         | 减去 值 的年份`n`.                                                                                                                               |
| `decrementMonth`        | `Function` `decrementMonth(n = 1)`        | 递减值的月份`n`.                                                                                                                                |
| `decrementDate`         | `Function` `decrementDate(n = 1)`         | 减去值的日期`n`.                                                                                                                                |
| `decrementHours`        | `Function` `decrementHours(n = 1)`        | 减少值的小时数`n`.                                                                                                                               |
| `decrementMinutes`      | `Function` `decrementMinutes(n = 1)`      | 减去值的分钟数`n`.                                                                                                                               |
| `decrementSeconds`      | `Function` `decrementSeconds(n = 1)`      | 减去值的秒数`n`.                                                                                                                                |
| `decrementMilliseconds` | `Function` `decrementMilliseconds(n = 1)` | 减去值的毫秒数`n`.                                                                                                                               |

* * *

### `<MapValue>`

`Map`值. 

```js
<MapValue
  value={Map|undefined}
  defaultValue={Map|undefined}
  onChange={Function}
>
  {({
    value,
    set,
    clear,
    reset,
    unset,
    delete,
  }) => (
    ...
  )}
</MapValue>
```

| 渲染props     | 类型                                       | 描述                                                                                                                     |
| -------- | ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `value`  | `Any`                                    | 当前地图值.                                                                                                                 |
| `set`    | `Function` `set(key, value)`要么`set(map)` | 运行[`Map.set`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/set),或将值设置为新地图.     |
| `clear`  | `Function` `clear()`                     | 运行[`Map.clear`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/clear).           |
| `reset`  | `Function` `reset()`                     | 将值重置为其初始值`value/defaultValue`状态.                                                                                        |
| `delete` | `Function` `delete(key)`                 | 运行[`Map.delete`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/delete).         |
| `unset`  | `Function` `unset(key)`                  | 别名[`Map.delete`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/delete)这不是保留的命名.  |

* * *

### `<NumberValue>`

`Number`值. 

```js
<NumberValue
  value={Number|undefined}
  defaultValue={Number|undefined}
  onChange={Function}
>
  {({
    value,
    set,
    reset,
    increment,
    decrement,
  }) => (
    ...
  )}
</NumberValue>
```

| 渲染props        | 类型                            | 描述                               |
| ----------- | ----------------------------- | -------------------------------- |
| `value`     | `Number`                      | 当前的数值.                           |
| `set`       | `Function` `set(number)`      | 将值设置为新值`number`.                 |
| `clear`     | `Function` `clear()`          | 将值设置为`0`.                        |
| `reset`     | `Function` `reset()`          | 将值重置为其初始值`value/defaultValue`状态.  |
| `increment` | `Function` `increment(n = 1)` | 增加数量`n`.                         |
| `decrement` | `Function` `decrement(n = 1)` | 减少数量`n`.                         |

* * *

### `<SetValue>`

`Set`值. 

```js
<SetValue
  value={Set|undefined}
  defaultValue={Set|undefined}
  onChange={Function}
>
  {({
    value,
    set,
    clear,
    reset,
    add,
    remove,
    delete,
    toggle,
  }) => (
    ...
  )}
</SetValue>
```

| 渲染props     | 类型                                  | 描述                                                                                                                     |
| -------- | ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `value`  | `Set`                               | 当前的设定值.                                                                                                                |
| `set`    | `Function` `set(set)`               | 将值设置为新值`set`.                                                                                                          |
| `clear`  | `Function` `clear()`                | 运行[`Set.clear`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/clear).           |
| `reset`  | `Function` `reset()`                | 将值重置为其初始值`value/defaultValue`状态.                                                                                        |
| `add`    | `Function` `add(value)`             | 运行[`Set.add`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/add).               |
| `delete` | `Function` `delete(value)`          | 运行[`Set.delete`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/delete).         |
| `remove` | `Function` `remove(value)`          | 别名[`Set.delete`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/delete)这不是保留的命名.  |
| `toggle` | `Function` `toggle(value, boolean)` | 添加或删除`value`基于a`boolean`.                                                                                              |

* * *

### `<StringValue>`

`String`值. 

```js
<StringValue
  value={String|undefined}
  defaultValue={String|undefined}
  onChange={Function}
>
  {({
    value,
    set,
    clear,
    reset,
    concat,
    padEnd,
    padStart,
    repeat,
    replace,
    slice,
    substr,
    substring,
    toLowerCase,
    toUpperCase,
    trim,
    trimEnd,
    trimStart,
  }) => (
    ...
  )}
</StringValue>
```

| 渲染props          | 类型                              | 描述                                                                                                                              |
| ------------- | ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `value`       | `String`                        | 当前字符串值.                                                                                                                         |
| `set`         | `Function` `set(string)`        | 将值设置为新值`string`.                                                                                                                |
| `clear`       | `Function` `clear()`            | 将值设置为`''`空字符串.                                                                                                                  |
| `reset`       | `Function` `reset()`            | 将值重置为其初始值`value/defaultValue`状态.                                                                                                 |
| `concat`      | `Function` `concat(value)`      | 运行[`String.concat`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/concat).            |
| `padEnd`      | `Function` `padEnd(value)`      | 运行[`String.padEnd`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/padEnd).            |
| `padStart`    | `Function` `padStart(value)`    | 运行[`String.padStart`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/padStart).        |
| `repeat`      | `Function` `repeat(value)`      | 运行[`String.repeat`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/repeat).            |
| `replace`     | `Function` `replace(value)`     | 运行[`String.replace`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace).          |
| `slice`       | `Function` `slice(value)`       | 运行[`String.slice`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/slice).              |
| `substr`      | `Function` `substr(value)`      | 运行[`String.substr`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/substr).            |
| `substring`   | `Function` `substring(value)`   | 运行[`String.substring`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/substring).      |
| `toLowerCase` | `Function` `toLowerCase(value)` | 运行[`String.toLowerCase`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase).  |
| `toUpperCase` | `Function` `toUpperCase(value)` | 运行[`String.toUpperCase`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toUpperCase).  |
| `trim`        | `Function` `trim(value)`        | 运行[`String.trim`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/trim).                |
| `trimEnd`     | `Function` `trimEnd(value)`     | 运行[`String.trimEnd`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/trimEnd).          |
| `trimStart`   | `Function` `trimStart(value)`   | 运行[`String.trimStart`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/trimStart).      |
