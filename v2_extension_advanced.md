# 扩展（进阶）

## Majsoul_Plus 全局变量

雀魂 Plus 2.x 在 `code.js` 的开头声明了 `const Majsoul_Plus = {}`。

此后，对每一个加载了的扩展声明了 `Majsoul_Plus.${extension.id} = {}`。

该全局变量用以存放扩展愿意向外界暴露的内容。如非必须，扩展**不应该**污染全局作用域。

## context

对于每个扩展，其实际是包裹在匿名函数中执行的，因此各自的局部变量不会受到影响。此外，匿名函数还传入了一个参数，为 `context`。

`context` 可以使扩展本身暴露出一些内容供附属使用。其初始值为 `{}`，使用方法类似 `exports`，直接修改将无法修改。

## 加载远端脚本？

在 `entry` 中，你可以填写远端脚本。雀魂 Plus 2.x 会先获取脚本后尝试加载。案例见 [`yoFix`](https://github.com/MajsoulPlus/majsoul-plus/tree/master/extension/yoFix)。

## 如何获取本地文件？

对于每个位于 `assets` 目录下的文件，都可以通过 `http/https` 形式获得（具体取决于用户设置）。

以 id 为 `test` 的**扩展**为例，想要获得 `test/assets/1.txt`，可以采用如下形式：

```js
fetch(`${document.location.href}majsoul_plus/extension/test/1.txt`).then(
  ctx => {
    // 想干什么干什么.png
  }
)
```
