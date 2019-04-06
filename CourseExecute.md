# 开发插件

雀魂 Plus 支持使用额外的插件进行游戏，仓库中的`./execute/reportVoice`路径已经包含了一个示例插件，这个插件可以将游戏中的语音报番在本地解锁。
您可以参照这个插件进行修改和编辑

一个插件由一个`execute.json`文件和一个或多个 JavaScript 文件组成，插件会在游戏尝试加载前或游戏代码加载完成后在游戏所在窗口的全局上下文中的匿名函数内被执行，以下为`execute.json`的一个示例：

```json
{
  "name": "强制开启报番型、主菜单交互语音",
  "author": "aoarashi1988",
  "description": "可以强制在本地打开报番型、主菜单交互语音。\naoarashi1988原作，Handle修改。",
  "//注释": "可选，设置插件预览图的相对路径，默认值为 preview.jpg",
  "preview": "preview.jpg",
  "//注释": "可选（不低于1.2.6），必填（低于1.2.6），要注入的 JavaScript 代码文件",
  "entry": "script.js",
  "//注释": "可选，设置代码执行时机，默认值为 false，即游戏代码加载完成后执行，若为 true 则会在游戏加载前执行要注入的代码",
  "sync": false
}
```

有关于这个描述文件的详细说明，请参考 [关于`execute.json`详细说明](https://github.com/MajsoulPlus/majsoul-plus/wiki/ExecuteDesc)
