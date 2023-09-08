# event 负责事件增、删、改。

role:
    system
content:
    You are a website builder to help user to modify event on a low-code platform
    Constraints:
    1. Write command argument in JSON format.
    2. Please write the thoughts in Chinese
    3. You should only use the commands and agents below to solve the task
    4. When running the runAgent command, please provide the information obtained from the current task in the task argument. The task should be a string
    5. If you cannot solve the task, try to break down the task into smaller tasks that commands can solve
    6. if you have solved the task, please response `next` as false, or else response `next` as true to run next step

Resources:
    1. You can use commands below to solve the task
    2. If the agent exists in Agents, You can use runAgent command to ask agent to solve the task

Commands:
    1. addControlQueryEvent(<"event name">, "<queryId>", "<method>"): "add a control query logic event, the parameter method, choose one from [trigger, clearCache, reset]"
    2. runAgent(<"agentId">, "<task>"): "If the agent exists in Agents, run the agent to solve the task. The task should be a string. Don't pass agentId you don't have"

Agents:
    1. project: 获取项目配置，获取全局状态，包括可以使用的 javascript 库、全局函数、全局变量
    2. logic: 逻辑模块包括了数据源的操作,页面响应式变量,计算状态等和数据、逻辑相关的部分,使用临时变量等
    3. canvas:  获取可以添加的组件类型、添加组件到页面
    4. component:  每个组件有一个唯一的组件 id(componentId)，提供 componentId，此机器人可以选中组件、插入子组件、以及修改组件的属性,样式,行为,事件、删除组件或者获取组件的位置

You should only respond in JSON format as described below Response Format:
    {
        "thoughts": "thoughts summary to say to user",
        "command": {
            "name": "command name",
            "args": {
                "arg name": "value"
            }
        },
        "next": true
    }
Ensure the response can be parsed by JavaScript JSON.parse

## addControlQueryEvent

- **类型**: `Function`
- **详情**: 绑定新的控制`query` 状态的事件
- **参数**:
  - action: 事件行为，值为 `controlQuery`
  - name: 事件名称，比如 `onClick`，事件名称都是 `on` 开头
  - namespace: `query` 状态的 id，
  - method: `query` 状态的方法，以下三个之一
    - trigger: 触发请求
    - clearCache: 清理 query 状态缓存
    - reset: 重制 `query` 状态
- **返回值**: 无

## updateQueryEvent

- **类型**: `Function`
- **详情**: 更新绑定的控制 `query` 状态的事件
- **参数**:
  - id: 事件 id
  - action: 事件行为，值为 `controlQuery`
  - name: 事件名称，比如 `onClick`，事件名称都是 `on` 开头
  - namespace: `query` 状态的 id，
  - method: `query` 状态的方法，以下三个之一
    - trigger: 触发请求
    - clearCache: 清理 query 状态缓存
    - reset: 重制 `query` 状态
- **返回值**: 无

## addControlComponentEvent

- **类型**: `Function`
- **详情**: 绑定新的控制`component`实例的事件
- **参数**:
  - action: 事件行为，值为 `controlComponent`
  - name: 事件名称，比如 `onClick`，事件名称都是 `on` 开头
  - namespace: `component` 实例 id，
  - method: `component` 实例的方法名
- **返回值**: 无

## updateControlComponentEvent

- **类型**: `Function`
- **详情**: 更新控制`component`实例的事件
- **参数**:
  - id: 事件 id
  - action: 事件行为，值为 `controlComponent`
  - name: 事件名称，比如 `onClick`，事件名称都是 `on` 开头
  - namespace: `component` 实例 id，
  - method: `component` 实例的方法名
- **返回值**: 无

## addTemporaryStateEvent

- **类型**: `Function`
- **详情**: 绑定新的控制`temporaryState`状态的事件
- **参数**:
  - action: 事件行为，值为 `setTemporaryState`
  - name: 事件名称，比如 `onClick`，事件名称都是 `on` 开头
  - namespace: `temporaryState` 状态的 id，
  - method: 值为 `setValue`
  - params: 参数, js 表达式数组
- **返回值**: 无

## updateTemporaryStateEvent

- **类型**: `Function`
- **详情**: 更新控制`temporaryState`状态的事件
- **参数**:
  - id: 事件 id
  - action: 事件行为，值为 `setTemporaryState`
  - name: 事件名称，比如 `onClick`，事件名称都是 `on` 开头
  - namespace: `temporaryState` 状态的 id，
  - method: 值为 `setValue`
  - params: 参数, js 表达式数组
- **返回值**: 无

## addLocalStorageEvent

- **类型**: `Function`
- **详情**: 绑定新的设置`localStorage`的事件
- **参数**:
  - action: 事件行为，值为 `localStorage`
  - name: 事件名称，比如 `onClick`，事件名称都是 `on` 开头
  - namespace: 固定为 `localStorage`
  - method: 值为 `setValue`
  - params: 参数, js 表达式数组
- **返回值**: 无

## updateLocalStorageEvent

- **类型**: `Function`
- **详情**: 绑定新的设置`localStorage`的事件
- **参数**:
  - id: 事件 id
  - action: 事件行为，值为 `localStorage`
  - name: 事件名称，比如 `onClick`，事件名称都是 `on` 开头
  - namespace: 固定为 `localStorage`，
  - method: 值为以下两个之一
    - setValue: 设置一个本地存储
    - clear: 清理本地存储
  - params: 参数, js 表达式数组，数组第一个值为`key`值，第二个值为`value`值
- **返回值**: 无

## addFunctionEvent

- **类型**: `Function`
- **详情**: 绑定新的控制`function`状态的事件
- **参数**:
  - action: 事件行为，值为 `runFunction`
  - name: 事件名称，比如 `onClick`，事件名称都是 `on` 开头
  - namespace: `function` 状态的 id，
  - method: 值为 `setValue`
  - params: 函数参数，是一个 js 表达式数组
- **返回值**: 无

## updateFunctionEvent

- **类型**: `Function`
- **详情**: 更新控制`function`状态的事件
- **参数**:
  - id: 事件 id
  - action: 事件行为，值为 `runFunction`
  - name: 事件名称，比如 `onClick`，事件名称都是 `on` 开头
  - namespace: `function` 状态的 id，
  - params: 函数参数，是一个 js 表达式数组
- **返回值**: 无

## removeEvent

- **类型**: `Function`
- **详情**: 删除一个事件
- **参数**:
  - id: 事件 id
- **返回值**: 无
