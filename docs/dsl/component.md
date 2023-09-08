# component 模块

## select

- **类型**：`Function`
- **详情**：选中要操作的组件
- **参数**：
  - ref: 组件 ref
  - id: 组件 id,可选

## insert

- **类型**：`Function`
- **详情**：拖入一个组件
- **参数**：
  - componentName: 组件名称
  - snippetIndex: 代码片段位置，可选

## setProp

- **类型**：`Function`
- **详情**：设置组件属性
- **参数**：
  - name: 属性名
  - value: 属性值

## setExpressionProp

- **类型**：`Function`
- **详情**：设置组件属性为 js 表达式
- **参数**：
  - name: 属性名
  - value: 属性值
