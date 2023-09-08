# code 页面状态和逻辑

概述页面状态和逻辑的属性都是响应式的，总共有四种类型

- temporaryState: 页面临时状态
- computed: 计算状态，可由其他状态转换为新的状态
- query: 远程数据源处理
- function: 纯函数

## temporaryState 临时状态

temporaryState 主要用于存储页面临时状态。

用法

```js
// 获取 temporaryState 的值
[temporaryStateId].value// 设置 temporayState 的值
[temporaryStateId]
  .setValue(value);
// 或者[temporaryStateId].value = value
```

## computed 计算状态

类似 vue 的 computed，由其他属性计算得到新的属性。

用法

```js
// 获取 computed 的值
[computedId].value;
```

## query 远程数据源处理

query 用于请求远程数据，可以自定义逻辑，letgo 也支持直接填 rest api。

用法

```js
// query 是否正在请求数据
[queryId].loading// 获取 query 获取的值
[queryId].data// 获取 query 获取异常状态
[queryId].error// 触发 query 执行
[queryId]
  .trigger()
  // 清理 query 缓存
  [queryId].clearCache()
  // 重制请求结果和缓存
  [queryId].reset();
```

## function 纯函数

纯函数，自定义业务逻辑

用法

```js
// 执行函数
[functionId]();
```
