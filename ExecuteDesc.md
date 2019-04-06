# 关于`execute.json`详细说明

`execute.json` 是一个标准的 Json 格式文件，雀魂 Plus 会读取存在于插件目录内的该文件以加载插件信息并进行控制。

`execute.json` 内的内容为一个对象，必须包含有以下多个属性以用于雀魂 Plus

| 值                    | 类型               | 说明                                                                                                                        |
| --------------------- | ------------------ | --------------------------------------------------------------------------------------------------------------------------- |
| `name`                | `string`           | 插件的名字，不能为空                                                                                                        |
| `author`?             | `string`           | 作者名，可选                                                                                                                |
| `description`?        | `string`           | 描述信息，可选                                                                                                              |
| `preview`?            | `string`           | 浏览图对比 Json 文件的相对路径，默认值为`preview.jpg`                                                                       |
| `entry`?              | `string\|string[]` | 要注入的 JS 文件相对路径，默认值为`script.js`，当这个属性的值的类型为数组时，会在同一个作用域内依次执行数组内的每个 JS 文件 |
| `sync`?               | `boolean`          | 设置代码执行时机，默认值为`false`，即在游戏加载完毕后执行，如果为`true`则为游戏加载前执行                                   |
| `executePreferences`? | `object`           | 声明插件需要使用到的权限，对于部分权限必须先声明再使用，详细说明请参照(插件权限声明)[#插件权限声明]                         |

## 插件权限声明

插件需要在 `execute.json` 或是 `mod.json` 的 `execute` 属性下使用 `executePreferences` 对象，以键值对方式声明插件会使用到的权限，一个典型的 `execute.json` 举例如下

```json
{
  "name": "雀魂Plus插件",
  "author": "Majsoul Plus Team",
  "description": "这个插件申请了文档对象，本地存储对象的访问权和对全局对象的写入权",
  "entry": "main.js",
  "executePreferences": {
    "document": true,
    "localStorage": true,
    "writeableWindowObject": true
  }
}
```

对于 `executePreferences` 对象，在当前版本雀魂 Plus 环境下可以拥有以下可选属性，插件开发者可以根据需求进行使用。

| 属性名                | 说明                                 | 默认值 |
| --------------------- | ------------------------------------ | ------ |
| nodeRequire           | 是否允许使用 node require 语句       | false  |
| document              | 是否允许访问和编辑 document 对象     | false  |
| localStorage          | 是否允许访问和编辑 localStorage 对象 | false  |
| XMLHttpRequest        | 是否允许使用 XHR 对象                | false  |
| WebSocket             | 是否允许使用 WebSocket 对象          | false  |
| writeableWindowObject | 是否允许写入全局对象                 | false  |
