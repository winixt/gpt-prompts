# logic 页面状态逻辑模块

## addTemporaryState

- **类型**: `Function`
- **详情**: 新增 `temporaryState` 临时状态
- **参数**:
  - id: `temporaryState` id, 以英文小驼峰命名，视做变量
  - value: `temporaryState` 的初始值，值为 javascript 表达式
- **返回值**: 无

## updateTemporaryState

- **类型**: `Function`
- **详情**: 更新 `temporaryState` 临时状态
- **参数**:
  - id: 需要变更的 `temporaryState` id
  - value: `temporaryState` 的初始值，值为 javascript 表达式
- **返回值**: 无

## addComputed

- **类型**: `Function`
- **详情**: 新增 `computed` 逻辑
- **参数**:
  - id: `computed` id, 以英文小驼峰命名，视做变量
  - funcBody: 函数体，以已有的状态算出新的状态
- **返回值**: 无

## updateComputed

- **类型**: `Function`
- **详情**: 更新 `computed` 逻辑
- **参数**:
  - id: 需要变更的 `computed` id
  - funcBody: 函数体，以已有的状态算出新的状态
- **返回值**: 无

## addFunction

- **类型**: `Function`
- **详情**: 新增 `function` 函数
- **参数**:
  - id: `function` id, 以英文小驼峰命名，视做变量
  - funcBody: 函数
- **返回值**: 无

## updateFunction

- **类型**: `Function`
- **详情**: 更新 `function` 函数
- **参数**:
  - id: 需要变更的 `function` id
  - funcBody: javascript 函数
- **返回值**: 无

## addRestAPIQuery

- **类型**: `Function`
- **详情**: 新增数据源类型为 `rest` 的 `query`
- **参数**:
  - id: `query` id, 以英文小驼峰命名，最终以变量的方式引用
  - api: 接口路径
  - method: 接口方法
  - resourceType: 为 `rest`
  - params: 请求参数，值为 javascript 表达式
  - runWhenPageLoads: [boolean], 是否在页面加载时自动运行
  - enableTransformer: 是否开启响应数据数据转换
  - transformer: 响应数据数据转换函数，函数作用域内可直接访问变量 `data`, 其中 `data` 为原始数据
- **返回值**: 无

## updateRestAPIQuery

- **类型**: `Function`
- **详情**: 更新数据源类型为 `rest` 的 `query`
- **参数**:
  - id: 需要变更的 `query` id
  - api: 接口路径
  - method: 接口方法
  - resourceType: 为 `rest`
  - params: 请求参数，值为 javascript 表达式
  - runWhenPageLoads: [boolean], 是否在页面加载时自动运行
  - enableTransformer: 是否开启响应数据数据转换
  - transformer: 响应数据数据转换函数，函数作用域内可直接访问变量 `data`, 其中 `data` 为原始数据
- **返回值**: 无

## addCustomQuery

- **类型**: `Function`
- **详情**: 新增自定义逻辑 `query`
- **参数**:
  - id: `query` id, 以英文小驼峰命名，最终以变量的方式引用
  - resourceType: 为 `query`
  - query: [function], 自定义请求逻辑
  - runWhenPageLoads: [boolean], 是否在页面加载时自动运行
  - enableTransformer: 是否开启响应数据数据转换
  - transformer: 响应数据数据转换函数，函数作用域内可直接访问变量 `data`, 其中 `data` 为原始数据
- **返回值**: 无

## updateCustomQuery

- **类型**: `Function`
- **详情**: 更新自定义逻辑 `query`
- **参数**:
  - id: 需要变更的 `query` id
  - resourceType: 为 `query`
  - query: [function], 自定义请求逻辑
  - runWhenPageLoads: [boolean], 是否在页面加载时自动运行
  - enableTransformer: 是否开启响应数据数据转换
  - transformer: 响应数据数据转换函数，函数作用域内可直接访问变量 `data`, 其中 `data` 为原始数据
- **返回值**: 无

## removeCodeItem

- **类型**: `Function`
- **详情**: 移除 code 逻辑
- **参数**:
  - id: code 的 id
- **返回值**: 无
