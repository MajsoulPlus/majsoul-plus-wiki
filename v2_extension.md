# 开发扩展（Extension）

在 `2.x` 的雀魂 Plus 中，原本的插件（Execute）系统得到了扩展，进化为了现在的扩展系统。扩展包含资源包的全部功能，因此也可以说是资源包的超集。

## 扩展的特有字段

```typescript
export interface Extension extends Metadata {
  entry?: string | string[]
  loadBeforeGame?: boolean
  applyServer?: number[]
  resourcepack?: Array<string | ResourcePackReplaceEntry>
}
```

| 字段           | 类型                                       | 默认值      | 简介                                                     |
| -------------- | ------------------------------------------ | ----------- | -------------------------------------------------------- |
| entry          | `string | string[]`                        | `script.js` | 表示扩展需要执行的代码。                                 |
| loadBeforeGame | `boolean`                                  | `false`     | 表示扩展是否是在游戏加载前加载                           |
| applyServer    | `number[]`                                 | `[0, 1, 2]` | 表示扩展运行的服务器。0 表示国服，1 表示日服，2 表示美服 |
| resourcepack   | `Array<string | ResourcePackReplaceEntry>` | `[]`        | 扩展自带的资源包，格式与资源包的 `replace` 字段一致      |

## Node 兼容？

现在的扩展已经没有这样的功能了，但换来的是雀魂 Plus 可以在任意浏览器中运行以及解决了微信无法登录的问题。
