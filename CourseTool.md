# 开发工具

雀魂 Plus 支持使用额外的工具增强功能，仓库中的`./tool/desktopCreator`路径已经包含了一个示例工具，这个工具可以轻松生成一个桌布模组，替换默认桌布。
您可以参照这个工具进行修改和编辑

一个插件由一个`tool.json`文件和若干 Electron 的 BrowserWindow 所需文件组成，工具会在资源管理器加载时同步读取并展现，以下为`tool.json`的一个示例：

```json
{
  "name": "桌布制作工具",
  "author": "Handle",
  "description": "简单几步生成桌布Mod，桌布随心换",
  "//注释": "定义了 浏览器调用 Electron 的 BrowserWindow 时，要加载的入口页面",
  "index": "index.html",
  "//注释": "一个标准的 BrowserWindow 选项，详情请参考 https://electronjs.org/docs/api/browser-window#new-browserwindowoptions",
  "windowOptions": {
    "width": 640,
    "height": 360
  }
}
```

工具的开发限制极少，您甚至可以将其视作普通的 Electron 的 BrowserWindow 进行对待来进行开发，祝您愉快！